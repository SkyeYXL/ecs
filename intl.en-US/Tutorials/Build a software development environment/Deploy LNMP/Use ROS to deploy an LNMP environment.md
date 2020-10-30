# Use ROS to deploy an LNMP environment

LNMP is an acronym of the names of its original four open source components: the Linux operating system, NGINX web server, MySQL relational database management system, and PHP programming language. This topic describes how to use Alibaba Cloud Resource Orchestration Service \(ROS\) to deploy an LNMP environment.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, go to the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   The first time that you use ROS, you are prompted to activate it. ROS is a free service. You can activate ROS free of charge.

You do not need to download or install anything to use ROS. You can use ROS to create stack templates in the JSON format. In the ROS console, you can also use a sample template to create a stack. For more information, see [Sample Templates](https://ros.console.aliyun.com/#/template/list).

You can also use other sample templates provided in the ROS console to build other environments, such as Java web test environments, Node.js development and test environments, Ruby web development and test environments, or Hadoop and Spark distributed systems. This topic uses the **Deploy a LNMP \(Linux, NGINX, MySQL, and PHP\) Stack** template to demonstrate how to use ROS to automatically create an ECS instance and deploy an LNMP environment on the instance.

For more information about ROS, see [ROS documentation](/intl.en-US/Product Introduction/What is ROS?.md).

1.  Log on to the [ROS console](https://ros.console.aliyun.com/).

2.  In the left-side navigation pane, choose **Templates** \> **Sample Templates**.

3.  In the top navigation bar, select a region.

4.  Find the **Deploy a LNMP \(Linux, NGINX, MySQL, and PHP\) Stack** template.

    ![Find the sample template](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1129919951/p12071.png)

5.  Click **View Details** to check the template in the JSON format. The following table lists the top-level fields in the JSON file.

    |Top-level field|Description|
    |:--------------|:----------|
    |`"ROSTemplateFormatVersion" : "2015-09-01"`|The version of the template.|
    |    ```
"Description": "Deploy LNMP(Linux+Nginx+MySQL+PHP) stack on 1 ECS instance. ***
              WARNING *** Only support CentOS-7."
    ```

|Description of the template.|
    |`"Parameters" : { }`|Some parameters of the template. In this example, this field specifies the default image ID and instance type.|
    |`"Resources" : { }`|The Alibaba Cloud resources that you can use the template to create. In this example, this field declares that the resources to be created include an ECS instance and a security group. The properties of these resources are defined in the `Parameters` field.|
    |`"Outputs": { }`|The resource information that the stack generates after ROS creates the specified resources. In this example, the stack generates the ID and public IP address of the ECS instance, and the ID of the security group.|

6.  Click **Create Stack**.

7.  Configure the parameters and click **Create Stack**.

    |Parameter|Description|
    |---------|-----------|
    |**Stack Name**|Specify a unique stack name. You cannot change the stack name after the stack is created.|
    |**Available Zone ID**|Required. Specify the zone ID of the resource that you want to create.|
    |**Image ID**|Specify the ID of the image that ROS uses to create the ECS instance.|
    |**Instance Type**|Specify the instance type of the ECS instance that you want to create.|
    |**System Disk Category**|Select the category of the system disk.|
    |**Instance Password**|Required. Set the logon password of the ECS instance. The password must contain at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters.|
    |**DB Name**|Specify the name of the MySQL database.|
    |**DB Username**|Specify the username of the MySQL database.|
    |**DB Password**|Required. Set the password used to access the MySQL database. The password must be 6 to 32 characters in length and can contain letters, digits, and underscores \(\_\).|
    |**DB Root Password**|Required. Set the password of the MySQL root user. The password must be 6 to 32 characters in length and can contain letters, digits, and underscores \(\_\).|
    |**Nginx Download Url**|Specify the URL used to download NGINX. Use the default value.|

8.  In the left-side navigation pane, click **Stacks** to check the status of the stack that you have created.

    ![Stack management](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1129919951/p14331.png)

9.  Click the name of the new stack, click the **Outputs** tab, and then check the `NginxWebsiteURL` value.

    You can use the URL to connect to the LNMP environment that you have created.

    ![Check the stack overview](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1129919951/p14341.png)

    **Note:**

    -   On the **Resources** tab, you can check all of the resources in the stack.
    -   On the **Events** tab, you can check the operations that ROS performs in the process of creating the stack. The causes of failed operations are also displayed in the list.

