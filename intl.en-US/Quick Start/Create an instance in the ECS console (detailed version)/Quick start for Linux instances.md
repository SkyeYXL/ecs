---
keyword: [quick start, ECS, starter, user guide, Alibaba Cloud]
---

# Quick start for Linux instances

This tutorial walks you through the procedure to configure Apache for an instance that is of the ecs.g6.large instance type and runs Alibaba Cloud Linux 2.1903 LTS 64-bit. You can use this tutorial to familiarize yourself with operations in the ECS console.

## Preparations

1.  Create an account and complete the account information.

    -   [Sign up with Alibaba Cloud](https://www.alibabacloud.com/help/doc-detail/50482.htm).
    -   Bind your credit card or PayPal account. For more information, see [Add a payment method](https://www.alibabacloud.com/help/doc-detail/50517.htm).
    -   To purchase ECS instances in mainland China regions, you must complete real-name verification. For more information, see [Real-name registration FAQ](https://www.alibabacloud.com/help/doc-detail/52595.htm).
2.  Alibaba Cloud provides a default Virtual Private Cloud \(VPC\). If you do not want to use the default VPC, you can create a VPC and a VSwitch in the target region.

    For more information, see [Create an IPv4 VPC network](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).

3.  Alibaba Cloud provides a default security group. If you do not want to use the default security group, you can create a security group in the target region.

    For more information about how to create a security group, see [Create a security group](/intl.en-US/Security/Security groups/Create a security group.md).


## Step 1: Create an ECS instance

1.  Go to the [Custom Launch](https://ecs-buy.aliyun.com/wizard/#/) tab in the ECS console.

2.  In the first four configuration steps of the buy page, complete the instance launch configurations.

    The following configurations are used in this tutorial. Keep the default settings for parameters that are not described in this tutorial.

    |Step|Parameter|Example|Description|
    |----|---------|-------|-----------|
    |**Basic Configurations**|**Billing Method**|Pay-As-You-Go|The pay-as-you-go billing method allows more flexible operations. For more information, see [Billing overview](/intl.en-US/Pricing/Billing overview.md). **Note:** If an ICP filing is required for your domain name, you must select **Subscription**. |
    |**Region**|    -   Region: China \(Hangzhou\)
    -   Zone: Random
|You cannot change the region or zone after the instance is created. Exercise caution when you configure this parameter.|
    |**Instance Type**|    -   Family: General Purpose Type g6
    -   Instance Type: ecs.g6.large
|Instance types that are available are determined by the region you select and the inventory in the region. You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region. |
    |**Image**|    -   Type: Public Image
    -   Version: Alibaba Cloud Linux 2.1903 LTS 64-bit
|After the instance is started, the operating system and application data of the image are copied to the system disk.|
    |**Networking**|**VPC**|\[Default\]vpc-bp1opxu1zkhn00g\*\*\*\*|Select a created VPC based on your actual needs. Resources that are prefixed with **\[Default\]** are automatically created in the ECS console.|
    |**Assign Public IP Address**|Select Assign Public IP Address.|The system allocates a public IPv4 address if you select Assign Public IP Address.|
    |**Bandwidth Billing**|Pay-By-Traffic|In **Pay-By-Traffic** mode, bandwidth is billed based on the network usage. For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md).|
    |**Peak Bandwidth**|2 Mbps|None.|
    |**Security Group**|\[Default\]sg-bp1bhjjsoiyx44hd\*\*\*\*|Select a created security group based on your actual needs. Resources that are prefixed with **\[Default\]** are automatically created in the ECS console.|
    |**System Configurations \(Optional\)**|**Logon Credentials**|Password|In this tutorial, select **Password** and set a password for remote connection and logon to the ECS instance.|
    |**Logon Password**|Ecs123456|You must set the Logon Password and Confirm Password parameters if you set **Logon Credentials** to **Password**. The `root` logon username and the logon password you set are required when you connect to the ECS instance.|
    |**Instance Name**|    ```
EcsQuickStart
    ```

|In this tutorial, EcsQuickStart is used as the instance name.|
    |**Grouping \(Optional\)**|**Tags**|ECS:Documentation|If multiple instances are created, we recommend that you bind tags to these instances to facilitate management.|

3.  Click **Next: Preview**. In the Preview step, confirm **Configurations Selected** or click the ![Edit - Icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1953230061/p77356.png) icon to modify configurations.

    ![Quick start - Linux](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7857219951/p77040.png)

4.  Click **Save as Launch Template**. Set Template Name and Version Description.

    ![Quick start - Launch template](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3957219951/p77611.png)

    **Note:** Save the configurations selected for the current instance as a launch template. You can create an instance in one click by using the template.

5.  Read and select **ECS Terms of Service**. Click **Create Instance**.

6.  In the **Created** message that appears, click **Console** to go to the Instances page and view the creation progress.

    If the instance status is **Running**, the instance is created. Copy the public IP address for use when you connect to the ECS instance.

    ![Quick start - Linux - Created](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3957219951/p77051.png)


## Step 2: Add security group rules

If you do not add rules to the default security group when you create an instance or the instance is added to a new security group, perform the following operations:

1.  Click the instance ID to go to the instance details page.

2.  In the left-side navigation pane, click **Security Groups**. Click the security group ID to go to the security group details page.

3.  On the **Security Groups Rules** page, click the **Inbound** tab.

4.  Click **Quick Rule Creation** and add security group rules as described in the following table. Keep the default settings for parameters that are not described in this tutorial.

    ![Quick start - Linux - Add security group rules](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3957219951/p77063.png)

    |Action|Common Port \(TCP\)|Authorization Object|
    |------|-------------------|--------------------|
    |Allow|    -   SSH \(22\)
    -   RDP \(3389\)
    -   HTTP \(80\)
    -   HTTPS \(443\)
|0.0.0.0/0|

    **Note:**

    -   For **Common Port \(TCP\)**, select the ports that must be enabled for applications that run on the ECS instance. For example, if you want to use SSH and Apache in [Step 4: Configure Apache](#ApacheConfig), you must select SSH \(22\) and HTTP \(80\) in this step. Otherwise, the instance will not respond in subsequent operations.
    -   0.0.0.0/0 indicates that devices in all CIDR blocks are allowed to access the specified ports. If you know the IP address of the requester, we recommend that you set Authorization Object to a specific IP address range that contains this IP address.
5.  Click **OK**.


## Step 3: Connect to the ECS instance

1.  Return to the Instances page and find the EcsQuickStart instance.

2.  In the **Actions** column, click **Connect**.

3.  In the **Enter VNC password** dialog box that appears, click **Modify VNC password**.

4.  Change the password as prompted. In the **Enter VNC password** dialog box that appears, enter your new password. Click **OK**.

5.  Configure the logon credentials.

    -   **Username**: Enter root.
    -   **Password**: Enter the **Logon Password** value that you set in the **Logon Credentials** section. `Ecs123456` is used in this tutorial.
    When you are entering the password, the section next to Password: remains black and no messages are displayed.

    ![Password for root](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8857219951/p65893.png)


## Step 4: Configure Apache

1.  Install Apache.

    ```
    yum install -y httpd
    ```

2.  Start Apache.

    ```
    systemctl start httpd
    ```

3.  Enable Apache to run at system startup.

    ```
    systemctl enable httpd
    ```

4.  Check whether Apache is running.

    ```
    systemctl status httpd
    ```

    The `active (running)` command output indicates that Apache is running.

5.  Open a web page in the current browser. Enter the public IP address of the instance in the address bar and press the Enter key.

    ```
    http://<Public IP address of the instance>
    ```

    ![Quick start - Linux - Test page](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8857219951/p77103.png)


## Step 5: \(Optional\) Resolve domain names

Direct access to Apache by using the public IP address of the instance may degrade server security. If you already have a domain name or want to register one for the Apache website, follow these steps:

1.  Register the domain name.

    For more information, see [Register adomain name](/intl.en-US/Quick Start/Register a genericdomain name.md).

2.  If the website to which the domain name points is hosted on an ECS instance in a mainland China region, you must apply for an ICP filing for the domain name.

    For more information, see [ICP filing application overview]().

3.  Resolve the domain name to point to the public IP address of the instance.

    Domain name resolution is a prerequisite for using domain names to access your website. For more information, see [Add and manage records](https://www.alibabacloud.com/help/doc-detail/58131.htm).

4.  Use the resolved domain name to access Apache. Example: https://ecs-quickstarts.info.


## Step 6: \(Optional\) Release the ECS instance

You can release the instance if you no longer need it. After the instance is released, billing stops and data cannot be recovered.

**Note:** You can follow the instructions in this section to release only pay-as-you-go instances.

1.  Return to the Instances page and find the EcsQuickStart instance.

2.  In the **Actions** column, choose **More** \> **Instance Status** \> **Release**.

3.  In the Release dialog box that appears, set Release Mode to **Release Now**, and then click **Next**.

4.  Verify the instance to be released and then click **OK**.


## Step 7: View bills

1.  In the top navigation bar, choose **Billing** \> **User Center**.

2.  In the left-side navigation pane, choose **Spending Summary** \> **Instance Spending Detail**.

3.  Set **Search By** to **Instance ID**. Enter the ID of the EcsQuickStart instance. Press the Enter key to start the search.


-   For more information about ECS instance families that are available for purchase, see [Instance families](/intl.en-US/Instance/Instance families.md).
-   For more information about how to create an ECS instance, see [Creation method overview](/intl.en-US/Instance/Create an instance/Creation method overview.md).
-   For more information about images, see [Image overview](/intl.en-US/Images/Image overview.md).
-   For more information about security groups, see [Overview](/intl.en-US/Security/Security groups/Overview.md).
-   For more information about VPCs, see [What is a VPC?](/intl.en-US/Product Introduction/What is a VPC?.md).
-   For more information about the common operations of ECS, see [Quick reference](/intl.en-US/Best Practices/Quick reference.md).
-   For more information about the APIs operations provided by ECS, see [List of operations by function](/intl.en-US/API Reference/List of operations by function.md).

