---
keyword: [OOS, automated O&M, create an image, patch upgrade, ECS, application update, elasticity]
---

# Use OOS to update custom images

This topic describes how to update custom images by using Operation Orchestration Service \(OOS\). OOS provides public templates to update images automatically. To create an immediate or scheduled O&M task, you only need to select a source image and specify required parameters such as the Cloud Assistant command in a public template. The O&M task is then automatically executed based on the definitions in the template.

You must have registered an Alibaba Cloud account before you follow the instructions provided in the tutorial. If not, [create a new Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm) first.

You can use the ACS-ECS-UpdateImage template to sequentially execute the following tasks to update the image to a new custom image:

1.  Check whether the name of the new custom image already exists and make sure that the name complies with the naming conventions.
2.  Create and launch a temporary ECS instance based on parameters such as the instance type, source image ID, and security group ID that you have configured.
3.  Check whether the Cloud Assistant client is installed on the temporary ECS instance. If not, install the Cloud Assistant client.
4.  Run scripts by using Cloud Assistant to update the system environment of the instance.

    **Note:** OOS calls Cloud Assistant API operations to run shell, bat, or PowerShell scripts to update the system environments of ECS instances. For more information, see [Overview](/intl.en-US/Deployment & Maintenance/Cloud assistant/Overview.md).

5.  Stop the temporary ECS instance.
6.  Create a custom image from the temporary ECS instance.
7.  Release the temporary ECS instance.

## Procedure

1.  Log on to the [OOS console](https://oos.console.aliyun.com/).

2.  If you are using OOS for the first time, click **Enable Now** to activate OOS.

3.  In the left-side navigation pane, click **Public Templates**.

4.  In the top navigation bar, select a region.

5.  In the **ACS-ECS-UpdateImage** section, click **Create Execution**.

6.  On the Create page, perform the following operations:

    1.  In the **Basic Information** step, retain the default settings and click **Next: Parameter Settings**.

    2.  In the **Parameter Settings** step, specify parameters to automatically create or update custom images. The following table describes these parameters.

        |Parameter|Description|Example|
        |---------|-----------|-------|
        |targetImageName|The name of the new custom image. The name must comply with the regular expression /^\[A-Za-z0-9\\-\_\]\*$/, and cannot be the same as an existing image name.|add\_testtxt\_20191010|
        |sourceImageId|The ID of the image that you want to update. **Note:** If you have not created a custom image, you can use a public image, such as centos\_7\_06\_64\_20G\_alibase\_20190711.vhd.

|m-bp13y4of6mdoqw\*\*\*\*\*\*|
        |instanceType|The instance type of the temporary ECS instance to be created. For more information, see [Instance families](/intl.en-US/Instance/Instance families.md).|ecs.g5.xlarge|
        |securityGroupId|The ID of the security group to which the temporary ECS instance belongs.|sg-bp1azkttqpldxg\*\*\*\*\*\*|
        |vSwitchId|The ID of the VSwitch for the temporary ECS instance. The VSwitch and the security group must be in the same VPC.|vsw-bp1s5fnvk4gn2tw\*\*\*\*\*\*|
        |ramRoleName|The RAM role of the temporary ECS instance.|TestRAMRole|
        |commandType|The type of the script that you plan to run by using Cloud Assistant.         -   RunShellScript: shell scripts for Linux instances.
        -   RunBatScript: bat scripts for Windows instances.
        -   RunPowerShellScript: PowerShell scripts for Windows instances.
|RunShellScript|
        |tags|The tag of the image.        -   **Tag Key \(Required\)**: the tag key of the image.
        -   **Tag Value \(Optional\)**: the tag value of the image.
        -   **Attach Resource Tag to Execution**: binds resource tags to the OOS template. This option is selected by default. After resource tags are bound to the OOS template, you can use tags to filter the execution results of resources.
|        -   Tag key: ECS
        -   Tag value: Image |
        |commandContent|The content of the script to be run on the temporary ECS instance.|        ```
echo "hello world" >/root/test.txt.
        ``` |
        |**Permissions**|Optional. Valid values:         -   **Use Existing Permissions of Current Account**: This is the default value. You have all the permissions granted to your account. Make sure that you have the permissions to call the ECS API operations required to create custom images.
        -   **Specify RAM Role and Use Permissions Granted to This Role**: If a RAM role is specified, OOS performs O&M tasks by assuming that RAM role.
|**Use Existing Permissions of Current Account**|

    3.  Click **Next: OK**.

    4.  Confirm O&M task details and high-risk operations. Then, click **Confirm and Create**.

7.  In the left-side navigation pane, click **Executions** to view the created O&M task.


If the O&M task is created and is in the **Running** state, the custom image is being updated. When **Execution Status** changes to **Success**, the image is updated. You can view the ID of the new image in the execution details.

![Image update result](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9963559951/p64664.png)

**Note:** To view the update process, click **Details** of the O&M task to view **Logs**.

**References**  


[Introduction to OOS](https://www.alibabacloud.com/help/doc-detail/120556.htm)

