---
keyword: [ECS, disk resizing, extend a partition]
---

# Resize disks online for Linux instances

You can resize a system disk or data disk to extend its capacity. This topic describes how to resize a disk for a Linux instance without stopping the instance.

The disk to be resized online and the instance to which the disk is attached meet the following requirements.

|Resource|Requirement|
|--------|-----------|
|Instance|-   The instance is I/O optimized.
-   The public image used by the instance supports online resizing of disks. For more information about images that support online resizing of disks, see [Operating systems that support resizing online](#section_cqo_5zn_ine).
-   Disks on instances of the ecs.ebmc4.8xlarge, ecs.ebmhfg5.2xlarge, and ecs.ebmg5.24xlarge instance types cannot be resized online.
-   The instance is in the **Running** \(Running\) state.
-   The Linux kernel version of the instance is not earlier than 3.6.0. You can run the `uname -a` command to check the kernel version.

If the version of the Linux kernel is earlier than 3.6.0, you can refer to [Procedure for instances with kernels earlier than 3.6.0](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux system disks.md) and [Resize partitions and file systems of Linux data disks](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux data disks.md) to extend partitions of a disk on the Linux instance.


**Note:** If your ECS instance does not meet the requirements to resize disks online, you can resize its disks offline. For more information, see [Resize disks offline \(Linux\)](/intl.en-US/Block Storage/Resize cloud disks/Resize disks offline (Linux).md). |
|Disk|-   The disk is in the **In Use** \(In Use\) state.
-   The disk is an enhanced SSD \(ESSD\), a standard SSD, or an ultra disk.
-   After you renew a subscription instance and downgrade its configurations, you cannot resize the subscription disks attached to the instance for the remainder of the current billing cycle.
-   When you resize a disk of a specific category, the specified new disk capacity cannot exceed the maximum single-disk capacity allowed for the disk category. For more information, see the "Elastic Block Storage limits" section in [Limits](/intl.en-US/Product Introduction/Limits.md).

**Note:** If an existing partition of a disk is in the master boot record \(MBR\) format, the disk cannot be resized to 2 TiB or greater in size. If you want to resize a disk that has an MBR partition to more than 2 TiB, we recommend that you create a disk of more than 2 TiB, and format the disk to the GUID Partition Table \(GPT\) partitions. Then, copy the data from the MBR partition to the GPT partitions. For more information about how to format the disk to GPT partitions, see [Partition and format a data disk larger than 2 TiB](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Partition and format a data disk larger than 2 TiB.md). |

The following table lists configurations of the instance and disks that are used in the examples of this topic.

|Resource|Description|
|--------|-----------|
|Image used by the instance|Public image: Alibaba Cloud Linux 2.1903 LTS 64-bit|
|System disk|/dev/vda: uses the MBR format and ext4 file system, and is resized from 40 GiB to 60 GiB.|
|Data disk|-   /dev/vdb: uses the MBR format and ext4 file system, and is resized from 40 GiB to 60 GiB.
-   /dev/vdc: uses the GPT format and xfs file system, and is resized from 40 GiB to 60 GiB. |

## Step 1: Create a snapshot

Create a snapshot for the disk to back up the data on the disk before you resize the disk.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the instance whose disk you want to resize, and click the instance ID to go to the **Instance Details** page.

5.  In the left-side navigation pane, click **Disks**.

6.  Find the disk to be resized, and click **Create Snapshot** in the **Actions** column.

7.  In the dialog box that appears, enter a snapshot name, bind a tag, and then click **Create**.

8.  In the left-side navigation pane, click **Snapshots** to view the created snapshot.

    When **100%** appears in the **Progress** column corresponding to the snapshot, the snapshot is created. You can continue to perform the following operations.


## Step 2: Resize the disk in the console

1.  In the left-side navigation pane of the **Instance Details** page, click **Disks**.

2.  Find the disk to be resized and choose **More** \> **Resize Disk** in the **Actions** column.

    To batch resize disks, log on to the ECS console by using your Alibaba Cloud account and choose **Storage & Snapshots** \> **Disks** in the left-side navigation pane. On the Disks page, select the disks that you want to resize, and then click **Resize Disk** in the lower part of the page. Disks that are attached to the same instance cannot be batch resized.

3.  On the **Resize Disks** page, select **Online Resizing**, and set the **Size after Resize** parameter.

    The specified **Size after Resize** value cannot be less than the current capacity.

4.  Verify the price. Read and select *ECS Service Terms*, and then click **Confirm**.

5.  Read the notes, and click **I have read the notes. Resize** to complete the payment.


**Note:** After you resize the disk in the ECS console, you must resize the partitions and file systems of the disk within the instance before you can use the new capacity of the disk.

## Step 3: View the disk partitions

Log on to the ECS instance to view the partition types \(such as MBR and GPT\) and file system types \(such as ext4 and xfs\) of the system disks and data disks. Subsequent resizing operations vary based on the types of the partitions and file systems.

1.  Connect to the ECS instance. For more information, see [Connect to a Linux instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using VNC.md).

2.  Run the `fdisk -lu` command to view the disks attached to the instance.

    The following figure shows the three partitions of a system disk \(/dev/vda1\) and two data disks \(/dev/vdb1 and /dev/vdc1\).

    ![View the partitions of the disks](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2256420061/p135832.png)

    |No|Partition|Description|
    |--|---------|-----------|
    |①|`/dev/vda1`|A partition of the system disk. The **Linux** value of **System** indicates that the system disk is partitioned in the MBR format.|
    |②|`/dev/vdb1`|A partition of a data disk. The **Linux** value of **System** indicates that the data disk is partitioned in the MBR format.|
    |③|`/dev/vdc1`|A partition of a data disk. The **GPT** value of **System** indicates that the data disk is partitioned in the GPT format.|

3.  Run the `df -Th` command to check the file system types of the existing partitions.

    ![View the file systems](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5082909951/p135833.png)


## Step 4: Resize partitions

By checking the disk partitions, you can find that the partitions and file systems within the ECS instance have not been resized. This procedure describes how to resize the partitions of the resized disk within the ECS instance.

1.  Install the gdisk tool on the ECS instance.

    You must perform this step if the partition is in the GPT format. Skip this step if the partition is in the MBR format.

    ```
    yum install gdisk -y
    ```

2.  Run the `growpart /dev/vda 1` command to resize partitions.

    The partition of the system disk is resized in this example. Use a space to separate `/dev/vda` and `1`. To resize other partitions, modify the command accordingly.

    ![growpart](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5082909951/p135834.png)


## Step 5: Resize file systems

This procedure describes how to resize the file system of a partition within an ECS instance.

1.  Resize the file system within the ECS instance based on the file system type that you queried in Step 3.

    -   Resize the ext\* \(such as ext4\) file system: Run the `resize2fs /dev/vda1` command.

        ```
        # To resize the file system of the /dev/vda1 partition of the system disk, run the following command:
        resize2fs /dev/vda1
        
        # To resize the file system of the /dev/vdb1 partition of a data disk, run the following command:
        resize2fs /dev/vdb1          
        ```

        **Note:** `/dev/vda1` and `/dev/vdb1` are partition names. Change the commands based on your partition names.

    -   Resize the xfs file system: Run the `xfs_growfs /media/vdc`command.

        **Note:** `/media/vdc` is the mount point of the`/dev/vdc1` partition. Change the command based on the mount point of your partition.

2.  Run the `df -Th` command to check the resizing results.

    ![View the resizing results](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5082909951/p135835.png)

    After the disk is resized, check whether the new capacity of the disk is consistent with the expected results.

    -   If the resizing succeeds and the business programs in the instance can run properly, the resizing operation is complete.
    -   If the resizing fails, use the backup snapshot to roll back the disk.

## Operating systems that support resizing online

The following Linux public images and custom images that are derived from the following public images support resizing online:

-   Alibaba Cloud Linux: Alibaba Cloud Linux 2.1903 LTS 64-bit
-   CentOS: CentOS 6.8 and later, CentOS 7.2 and later, and CentOS 8 and later
-   Red Hat Enterprise Linux \(RHEL\): RHEL 6.9 and later, RHEL 7.4 and later, and RHEL 8 and later
-   Ubuntu: Ubuntu 16 and later
-   Debian: Debian 8 and later
-   SUSE: SUSE 12 SP2 and later.
-   openSUSE: openSUSE 42.3 and later

## FAQ

-   Problem description: When the `growpart /dev/vda 1` command is run, the `unexpected output in sfdisk --version [sfdisk, from util-linux 2.23.2]` error is prompted.

    Solution:

    1.  Run the `LANG=en_US.UTF-8` command to switch the character encoding type of the ECS instance.
    2.  If the problem persists, run the `reboot` command to restart the ECS instance.
    3.  If the problem persists, run the `localectl set-locale LANG=en_US.UTF-8` command to change the local environment variable, and then restart the instance.
-   Problem description: When the `growpart /dev/vda 1` command is run, the `-bash: growpart: command not found` error is prompted.

    Solution:

    1.  Run the `uname -a` command to check whether the version of the Linux kernel is 3.6.0 or later.

        If the version of the Linux kernel is earlier than 3.6.0, you can refer to [Procedure for instances with kernels earlier than 3.6.0](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux system disks.md) and [Resize partitions and file systems of Linux data disks](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux data disks.md) to extend partitions of a disk on the Linux instance.

    2.  Install the growpart tool based on the version of the Linux kernel.
        -   CentOS 7 and later: Run the `yum install -y cloud-utils-growpart` command.
        -   Debian 9 and later, or Ubuntu14 and later: Run the `apt install -y cloud-guest-utils` command.

## Other scenarios for disk resizing

-   If you want to create partitions on the resized disk, see [Option 2: Add and format MBR partitions](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux data disks.mdsection_gg7_ilv_h3j)or [Option 4: Add and format GPT partitions](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux data disks.mdsection_4hl_5l7_87s).
-   If no partition is created on your data disk and a file system is created on the raw device, see [Option 5: Resize the file system of a raw data disk](/intl.en-US/Best Practices/Block Storage/Resize partitions and file systems of Linux data disks.mdsection_f88_ax7_y8i) to extend the file system.

**Related topics**  


[RebootInstance](/intl.en-US/API Reference/Instances/RebootInstance.md)

[ResizeDisk](/intl.en-US/API Reference/Disk/ResizeDisk.md)

[AttachDisk](/intl.en-US/API Reference/Disk/AttachDisk.md)

