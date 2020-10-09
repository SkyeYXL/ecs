---
keyword: [initialize, reset, master reset, data disk, ]
---

# Re-initialize a data disk

When a data disk is attached to an ECS instance, you can re-initialize the disk to restore it to the status when it was created.

-   Data will be lost after the system disk is reinitialized. You must create a snapshot from the disk to back up data. For more information, see [Create a normal snapshot](/intl.en-US/Snapshots/Use snapshots/Create a normal snapshot.md).
-   The data disk is attached to an instance. For more information about how to attach a data disk to an instance, see [Attach a data disk](/intl.en-US/Block Storage/Cloud disks/Attach a data disk.md).
-   You must stop the ECS instance before reinitializing a system disk. In this case, your business will be interrupted. Proceed with caution. For more information, see [Stop an instance](/intl.en-US/Instance/Manage instances/Stop an instance.md).

    For a pay-as-you-go ECS instance, you must select **Retain Instance and Continue Charging After Instance Is Stopped** when you stop the instance.

    **Note:** If you select **No Charges After Instance Is Stopped**, you may not be able to start the instance after you reinitialize the system disk. For more information, see [No Fees for Stopped Instances \(VPC-Connected\)](/intl.en-US/Pricing/Billing methods/No Fees for Stopped Instances (VPC-Connected).md).

    ![Retain Instance and Continue Charging After Instance Is Stopped](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4872909951/p5328.png)

-   \(Applicable to Linux instances only\) If you create an empty data disk and add a command in the /etc/fstab file to mount partitions of the data disk at the system startup, the command is not executed and the instance cannot start up as expected after you re-initialize the data disk. We recommend that you comment out the command in the /etc/fstab file. Perform the following operations:
    1.  Connect to the instance. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).
    2.  Run the `vim /etc/fstab` command.
    3.  Press the `I` key to enter the edit mode.
    4.  Find the command used to mount data disk partitions and comment it out by using \#, as shown in the following line:

        ```
        # /dev/vdb1 /InitTest ext3 defaults 0 0
        ```

        **Note:** The /dev/vdb1 partition and the /InitTest mount point are used in this example. You can modify the command based on your actual conditions.

    5.  Press the `Esc` key to exit the edit mode. Then, enter :wq to save the file and exit.

The status of a data disk after it is re-initialized varies based on its original status when it was created and the operating system that the instance runs:

-   The data disk is restored to the initial status when it was created:
    -   The data disk becomes an empty disk if it was originally an empty disk.
    -   The data disk stores the data recorded in the source snapshot if it was created from a snapshot.
-   For a Windows instance, after you re-initialize its data disk, the data disk is ready for use without additional operations regardless of its original status.
-   For a Linux instance:
    -   If the data disk was created from a snapshot, the data disk stores only the data recorded in the source snapshot after it is re-initialized. You do not need to mount the partitions again, but all the data generated after the disk is created is lost.
    -   If the data disk was created as an empty disk, all the data and file systems on the disk are lost. You must reformat and partition the disk, and then mount the partitions again.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the ECS instance for which you want to re-initialize a data disk, and click the instance ID to go to the Instance Details page.

5.  In the left-side navigation pane, click **Disks**.

6.  Find the data disk that you want to re-initialize, and click **Reinitialize Disk** in the **Actions** column.

7.  In the Reinitialize Disk dialog box, read the notes and click **Confirm**.


-   \(Applicable to Linux instances only\) If the data disk was created as an empty disk, you must format the data disk after you re-initialize it. For more information, see [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md).
-   After the data disk is re-initialized, you must redeploy and configure applications to restore your business as soon as possible.

**Related topics**  


[ReInitDisk](/intl.en-US/API Reference/Disk/ReInitDisk.md)

[Reinitialize a system disk](/intl.en-US/Block Storage/Cloud disks/Reinitialize a cloud disk/Reinitialize a system disk.md)

