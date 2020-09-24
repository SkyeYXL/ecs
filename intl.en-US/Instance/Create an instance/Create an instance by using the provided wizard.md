# Create an instance by using the provided wizard

This topic describes how to create an ECS instance by using the wizard in the ECS console. To create an ECS instance, you must specify the instance type, image, storage, network, and security group. The wizard provides a variety of extended configuration features to meet your custom deployment and management requirements.

You must complete the following preparations to create an ECS instance:

1.  Create an account and complete the account information.
    -   Create an Alibaba Cloud account. For more information, see [Sign up with Alibaba Cloud](https://www.alibabacloud.com/help/doc-detail/50482.htm).
    -   Bind your credit card or PayPal account. For more information, see [Add a payment method](https://www.alibabacloud.com/help/doc-detail/50517.htm).
    -   To purchase ECS instances in mainland China regions, you must complete real-name verification. For more information, see [Real-name registration FAQ](https://www.alibabacloud.com/help/doc-detail/52595.htm).
2.  Alibaba Cloud provides a default VPC. If you do not want to use the default VPC, you can create a VPC and a VSwitch in the specified region. For more information, see [Create an IPv4 VPC network](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).
3.  Alibaba Cloud provides a default security group. If you do not want to use the default security group, you can create a security group in the region where the instance is created. For more information, see [Create a security group](/intl.en-US/Security/Security groups/Create a security group.md).

If you need other extended features, you must complete corresponding preparations:

-   To specify an SSH key pair when you create a Linux instance, you must create an SSH key pair in the corresponding region. For more information, see [Create an SSH key pair](/intl.en-US/Security/Key pairs/Use an SSH key pair/Create an SSH key pair.md).
-   To configure user data, you must first prepare user data. For more information about how to prepare user data, see [Prepare user data](/intl.en-US/Instance/Manage instances/User data/Prepare user data.md).
-   To associate an ECS instance with an instance RAM role, you must create the RAM role, assign a permission policy to the role, and then bind the role to the instance. For more information, see [Bind an instance RAM role](/intl.en-US/Security/Instance RAM roles/Bind an instance RAM role.md).

1.  Go to the [Custom Launch](https://ecs-buy.aliyun.com/wizard/#/) tab.

2.  Perform the following operations in the Basic Configurations step:

    1.  Set **Billing Method** to **Subscription**, **Pay-As-You-Go**, or Preemptible Instance. For more information, see [Preemptible instances](/intl.en-US/Instance/Instance purchasing options/Preemptible instances/Overview.md).

        **Note:** For information about how to create a preemptible instance, see [Create a preemptible instance](/intl.en-US/Instance/Instance purchasing options/Preemptible instances/Create a preemptible instance.md).

    2.  Select a region and zone.

        By default, a zone is randomly assigned by the system. You can select a zone based on your business requirements. For more information about how to select a region and zone, see [Regions and zones](/intl.en-US/Product Introduction/Regions and zones.md).

        **Note:** You cannot change the region or zone after the instance is created.

    3.  Select an instance type and specify the number of instances.

        Instance types that are available are determined by the selected region. You can go to the [ECS Instance Types Available for Each Region](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) page to view the instance types available in each region. For information about the scenarios for each instance type, see [Instance families](/intl.en-US/Instance/Instance families.md).

        **Note:**

        -   The quota of pay-as-you-go or preemptible instances for your account is displayed on the page.
        -   To use elastic network interfaces \(ENIs\), select an enterprise-level instance type equipped with no less than two vCPUs, or an entry-level instance type equipped with no less than four vCPUs. For more information about the maximum number of ENIs that can be bound to instances of each instance type, see [Instance families](/intl.en-US/Instance/Instance families.md).
        -   To use a standard SSD, select an I/O optimized instance.
    4.  Select an image. You can select an image from Public Image, Custom Image, Shared Image, or Marketplace Image.

        **Note:**

        -   To use an SSH key pair, you must select a Linux image.
        -   To configure user data, you can select only specified images. For more information, see [Prepare user data](/intl.en-US/Instance/Manage instances/User data/Prepare user data.md).
        -   To use a Red Hat public image, you must make sure that the instance family supports Red Hat images. For more information, see the [Which instance families do Red Hat Enterprise Linux \(RHEL\) images support?](/intl.en-US/Images/Image FAQ.md) section in Image FAQ.
        -   Public images contain only initial system environments. You can find more images in Alibaba Cloud Marketplace.
    5.  Select a storage space.

        -   **System Disk**: required. You must create a system disk for the operating system. Select a disk category and specify the size for the system disk.
            -   Disk category: Categories are available based on the selected region and instance type.
            -   Size: The default size of the system disk is 40 GiB. If the selected image file is greater than 40 GiB, the disk size is increased to support the image file. The minimum size of the system disk is related to the image. The actual size is displayed on the buy page.

                |Image|System disk capacity \(GiB\)|
                |:----|:---------------------------|
                |Linux \(excluding CoreOS and Red Hat\)|\[max\{20, image file size\}, 500\]|
                |FreeBSD|\[max\{30, image file size\}, 500\]|
                |CoreOS|\[max\{30, image file size\}, 500\]|
                |Red Hat|\[max\{40, image file size\}, 500\]|
                |Windows|\[max\{40, image file size\}, 500\]|

        -   **Data Disk**: optional. To create a data disk while you are creating an instance, you must select the disk type, and specify the size and quantity of the disk. You must also determine whether to encrypt the disk. For more information, see [Encryption overview](/intl.en-US/Block Storage/Encrypt a disk/Encryption overview.md). You can create an empty data disk or create a data disk from a snapshot. You can add up to 16 data disks.

            **Note:**

            An data disk that is created together with the instance has the following features:

            -   The billing method of the data disk is the same as that of the instance.
            -   A subscription data disk must be released together with the instance. A pay-as-you-go data disk can be released either separately or together with the instance.
        -   **NAS File System**: optional. You can select from existing file systems. Up to five file systems can be specified. For more information, see [Mount a NAS file system when you purchase an ECS instance]().
        -   If you have selected an instance family that is equipped with local disks \(such as i1, d1, or d1ne\), the local disk information is displayed. You cannot specify the quantity or category of local disks because these settings depend on the selected instance type. For more information about the local disks that are supported by different instance types, see [Instance families](/intl.en-US/Instance/Instance families.md).
3.  Click **Next: Networking** to configure networking and security groups for the instance.

    1.  Select the network type.

        -   **VPC**: You must select a VPC and a VSwitch. If you do not have a VPC and a VSwitch, you can use the default ones.
        -   **Classic**: If you purchase an ECS instance for the first time after 12:00, June 16, 2016 \(UTC+8\), you can no longer select the classic network.
    2.  Set the public bandwidth.

        -   To assign a public IP address to the instance, you must select **Assign Public IP Address**. Then, select **Pay-By-Traffic** or **Pay-By-Bandwidth** as the billing method for network usage and specify the bandwidth. Public IP addresses that are assigned this way cannot be disassociated from the instance. For more information about the billing methods for network usage, see [Billing methods for network usage](/intl.en-US/Pricing/Billing methods of public bandwidth.md).
        -   If your instance does not need to access the Internet or your VPC-type instance uses an elastic IP address \(EIP\) to access the Internet, you do not need to assign a public IP address. You can associate an EIP with or disassociate an EIP from an instance at any time.
    3.  Select a security group.

        If you have not created a security group, you can use the default security group. For more information about rules of the default security group, see [Overview](/intl.en-US/Security/Security groups/Overview.md).

    4.  Add an ENI.

        If the instance type that you selected supports ENIs, you can add an ENI and specify a VSwitch.

        **Note:** By default, the added ENI is released together with the instance. You can use the [ECS console](/intl.en-US/Network/Elastic Network Interfaces/Detach an ENI from an instance.md) or call the [DetachNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md) operation to unbind the ENI from the instance.

4.  Click **Next: System Configurations** to complete the following configurations:

    1.  Select and set logon credentials.

        Select a credential based on the image:

        -   Linux: You can select a password or an SSH key pair as the logon credential.
        -   Windows: You can select only a password as the logon credential.
        You can also set the logon credential for an instance after the instance is created. For more information, see [Reset the logon password of an instance](/intl.en-US/Instance/Manage instances/Reset the logon password of an instance.md).

    2.  Specify the instance name that you want to display in the ECS console, and the hostname that can be obtained from within the guest operating system.

    3.  Set advanced options.

        -   RAM Role: Assign a RAM role to the instance.
        -   User Data: Customize the startup behavior of the instance or pass data into the instance.
5.  Click **Next: Grouping** to group the instance you have created.

    1.  Add tags.

        If you have created multiple instances, you can use tags to facilitate management. For more information, see [Overview](/intl.en-US/Tag & Resource/Tags/Overview.md).

    2.  Select a resource group.

        Resource groups are designed for enterprise users. Enterprise users can use this feature to organize and manage their resources owned by multiple accounts and credited to multiple projects. For more information, see [Resource groups](/intl.en-US/Tag & Resource/Resource/Resource groups.md).

    3.  Select a deployment set.

        Deployment sets are designed to manage the deployment of instances. Instances in the same deployment set can be assigned to different physical servers. This policy can ensure high availability of services and is used to support the disaster recovery capability of the infrastructure. For more information, see [Create a deployment set](/intl.en-US/Elasticity/Deployment sets/Create a deployment set.md).

    4.  Select a dedicated host.

        You can select **Random DDH Supporting Automatic Deployment / AutoPlacement** or specify a dedicated host.

        A dedicated host is flexible and elastic, and provides you with exclusive access to its resources. For more information, see [Features](/intl.en-US/Product Introduction/Features.md).

6.  Confirm the order.

    1.  In the **Configurations Selected** section, confirm all the configurations. You can also click the Edit icon to change the configurations.

        -   Optional. Click **Save as Launch Template** to save your configurations as a launch template that can be used later. For more information, see [Launch templates](/intl.en-US/Elasticity/Launch template/Launch templates.md).
        -   Optional. Click **View Open API** to view best-practice API scripts. On the left side of the dialog box, the **API Workflow** section describes the API operations related to the current operation and lists the request parameters and their values. On the right side of the dialog box, programming language-specific SDK examples are provided. **Java** and **Python** examples are available. For more information, see [API Introduction](/intl.en-US/API Reference/Introduction.md).
        -   Optional. Click **Save as ROS Template** to save your configurations as a ROS template that can be used to create stacks. For more information, see [Create a stack](/intl.en-US/Stack management/Create a stack.md).
    2.  If the billing method is **Pay-As-You-Go**, you can select **Automatic Release**.

    3.  If the billing method is **Subscription**, you can specify the duration and specify whether to select **Enable Auto-renewal**.

    4.  Confirm the configuration fees.

        The following table lists the billing methods for instances and network usage that are used to calculate the fees that you must pay.

        |Instance billing method|Billing method for network usage|Billed item|
        |:----------------------|:-------------------------------|:----------|
        |Pay-as-you-go or preemptible instance|Pay-by-traffic|Internet traffic fee and configuration fee. The configuration fee consists of fees for the instance type \(vCPUs and memory\), the system disk, data disks \(if any\), and local disks \(if any\).|
        |Pay-by-bandwidth|The configuration fee consists of fees for the instance type \(vCPUs and memory\), the system disk, data disks \(if any\), local disks \(if any\), and the public bandwidth.|
        |Subscription|Pay-by-bandwidth|The configuration fee consists of fees for the instance type \(vCPUs and memory\), the system disk, data disks \(if any\), local disks \(if any\), and the public bandwidth.|
        |Pay-by-traffic|Internet traffic fee and configuration fee. The configuration fee consists of fees for the instance type \(vCPUs and memory\), the system disk, data disks \(if any\), and local disks \(if any\).|

    5.  Read and confirm **ECS Terms of Service**.

7.  Confirm to create the instance based on the instance billing method.

    -   Subscription instance: Click **Create Order**.
    -   Pay-as-you-go instance: Click **Create Instance**.

After the instance is activated, click **Console** to view the instance details in the ECS console. On the **Instances** page, you can view the information of the new instance, such as the instance name, public IP address, internal IP address, and private IP address.

-   You can build an FTP site on the ECS instance to upload local files to the instance. For more information, see [Manually build an FTP site on a Windows instance](/intl.en-US/Tutorials/Build an application/Build an FTP site on an ECS instance/Manually build an FTP site on a Windows instance.md).
-   To secure your instance after you create the instance, we recommend that you perform security compliance inspection and configuration:
    -   For Linux instances, see [Harden operating system security for Linux](https://www.alibabacloud.com/help/doc-detail/49809.htm) in *Security Advisories*.
    -   For Windows instances, see [Harden operating system security for Windows](https://www.alibabacloud.com/help/doc-detail/49781.htm) in *Security Advisories*.
-   If you have added data disks when you create the instance, you must format the partitions before you can use the data disks. For more information, see [Format a data disk for a Windows ECS instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Windows ECS instance.md) or [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md).

