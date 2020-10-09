---
keyword: [Cloud Assistant, remote command, ECS, Alibaba Cloud, O&M]
---

# Run a command at creation

You can create and run a command simultaneously by using the immediate execution feature.

-   The ECS instances on which you will run the command are in the **Running** state.
-   You can retain a maximum of 100 Cloud Assistant commands within an Alibaba Cloud region. The service quota of commands may increase based on your ECS usage. When you use the immediate execution feature and turn off **Save Command** for a command, the command that is being created does not consume your command quota.

    **Note:** You can also call the DescribeAccountAttributes operation and set the AttributeName.N parameter to max-axt-command-count to query the maximum number of Cloud Assistant commands that you can retain within a region.

-   You can run Cloud Assistant commands up to 5,000 times within a region per day. The quota may increase with your ECS usage.

    **Note:** You can also call the DescribeAccountAttributes operation, with the AttributeName.N parameter set to max-axt-invocation-daily, to query the maximum number of times you can run Cloud Assistant commands within in a region per day.


When you use the immediate execution feature, take note of the following items:

-   A command cannot exceed 16 KB in size after it is encoded in Base64.
-   A maximum of 20 custom parameters can be specified in a Cloud Assistant command.
-   You can run a command on a maximum of 50 instances at a time by calling an API operation.
-   When you create a command, you must check whether the syntax, logic, and algorithm of the command are correct.

    For example, assume that you have created the /backup directory \(`mkdir /backup`\) in the instance, you can run the following shell commands to archive a file in this directory:

    ```
    #! /bin/bash 
    OF=/backup/my-backup-$(date +%Y%m%d).tgz
    tar -cf $OF {{file}}
    ```

    **Note:** In this example, `{{file}}` is a custom parameter. When you run the commands, you can set this custom parameter to the name of the file to be archived, such as /app/usrcredential. Custom parameters can be used in scenarios of dynamic values and multi-purpose values. We recommend that you specify custom parameters for data that is security-sensitive or changes based on the environment, such as AccessKey pairs, instance IDs, authorization codes, time parameters, and critical system files.


1.  Log on to the ECS console and navigate to the [Cloud Assistant](https://ecs.console.aliyun.com/#/cloudAssistant/region/cn-hangzhou) page.

2.  In the top navigation bar, select a region.

3.  Click **Create or Run Command**.

4.  In the **Command Information** section, configure the corresponding parameters.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |Command Source|The source of the command.    -   **New Command**: Create a command.
    -   **Existing Command**: Select a command from the existing ones. |
    |Command Name|The name of the command.|
    |Command Type|The type of the command.    -   For Linux instances, select **Shell**.
    -   For Windows instances, select **Bat** or **PowerShell**. |
    |Command|The content of the command. You can enter or paste the command content.For more information about shell commands, see [View instance configurations](/intl.en-US/Deployment & Maintenance/Cloud assistant/DevOps practice/View instance configurations.md). |
    |Use Parameters|The option that specifies whether to enable parameters.If you turn on **Use Parameters**, you can specify custom parameters in the `{{key}}` format in the **Command** field. |
    |Command Parameters|The values of the custom parameters specified in the **Command** field in the `{{key}}` format.This parameter is available only when **Use Parameters** is turned on. |
    |Save Command|The option that specifies whether to save the command.|
    |Command Description|The description of the command. We recommend that you enter information such as the purpose of the command to facilitate subsequent management and maintenance.|
    |Execution Path|The custom execution path of the command. The following list provides default execution paths for instances that have different operating systems:    -   For Linux instances, the default execution path is the /home directory of the root user.
    -   For Windows instances, the default execution path is the directory where the process of the Cloud Assistant client is located, such as C:\\ProgramData\\aliyun\\assist\\$\(version\). |
    |Timeout Period|The **timeout period** for the command to run instances. If the command times out, Cloud Assistant forcibly stops the execution process.Unit: seconds. Default value: 60. Minimum value: 10. If you set **Timeout Period** to a value less than 10 seconds, the system changes the value to 10 seconds to ensure that the execution succeeds. |

5.  In the **Select Instances** section, select the instances on which you want to run the command.

6.  Click **Create Task**.


[Query execution results and fix common problems](/intl.en-US/Deployment & Maintenance/Cloud assistant/Use the cloud assistant/Query execution results and fix common problems.md)

**Related topics**  


[RunCommand](/intl.en-US/API Reference/Cloud assistant/RunCommand.md)

[DescribeAccountAttributes](/intl.en-US/API Reference/Others/DescribeAccountAttributes.md)

