# Basic security services

Alibaba Cloud Security Center provides ECS with basic security services such as suspicious logon detection, vulnerability scan, and baseline check. You can check the security status of your ECS instances in the ECS console or Security Center console.

Alibaba Cloud Security Center provides basic security services for free, such as vulnerability detection, security alerting, and baseline check, and collects and virtualizes security logs and fingerprints of ECS assets. You can view security information about ECS assets on the **Overview** page of the ECS console or in the Security Center console. For more information, see [Security Center documentation](/intl.en-US/Product Introduction/What is Security Center?.md).

The billing methods of basic security services are as follows:

-   In Security Center Basic Edition, basic security services for ECS are provided for free.
-   If you want to upgrade to Security Center Advanced or Enterprise Edition, log on to the [Security Center console](https://yundunnext.console.aliyun.com/) for a free trial or purchase of Security Center Advanced or Enterprise Edition. For the billing methods of Security Center Advanced Edition and Enterprise Edition, see the [Billing methods](/intl.en-US/Pricing/Billing methods.md) in *Security Center documentation*.

## Use the Security Center Agent

The Security Center agent is a lightweight security control that can be installed on ECS instances. If your ECS instance does not have the Security Center agent installed, your ECS instance will not be protected by Security Center. The security data of this instance, such as vulnerabilities, alerts, baseline vulnerabilities, and asset fingerprints, will not be displayed in the ECS console. For the installation paths of the Security Center agent, see [Security Center agent overview](/intl.en-US/Access Cloud Security Center/Security Center agent overview.md).

You can perform the following steps to install or uninstall the Security Center agent:

-   Have the Security Center agent automatically installed when you create an ECS instance.

    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
    2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
    3.  In the top navigation bar, select a region.
    4.  When you create an ECS instance, select **Security Hardening** in the **Image** section. The Security Center agent is then automatically installed on the new ECS instance. For more information, see [Create an instance by using the provided wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the provided wizard.md).

        ![Select Security Enhancement.](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2220613061/p49036.png)

    **Note:** If you call the [RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md) operation to create an ECS instance, you can also have the Security Center agent automatically installed on the instance by setting `SecurityEnhancementStrategy` to Active.

-   Manually install the Security Center agent on an existing ECS instance.
    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
    2.  On the Overview page, click **Handle** in the **Security Score** section to go to the Security Center console.
    3.  Install the agent. For more information, see the [Install the Security Center agent](/intl.en-US/Access Cloud Security Center/Install the Security Center agent.md) in *Security Center documentation*.
-   Uninstall the Security Center agent
    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
    2.  On the Overview page, click **Handle** in the **Security Score** section to go to the Security Center console.
    3.  Uninstall the agent. For more information, see the [Uninstall the Security Center agent](/intl.en-US/Access Cloud Security Center/Uninstall the Security Center agent.md) in *Security Center documentation*.

## Check the security status of your ECS instance

You can perform the following steps to check the security status of your ECS instance:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Check the security status of your ECS instance by using one of the following methods:

    -   Method 1: On the **Instances** page, view the Alibaba Cloud Security icon in the Monitoring column corresponding to your ECS instance. If the icon is orange, there are vulnerability or security alerts in the instance. You can click the icon to log on to the Security Center console and view the alert details.

        ![Go to Security Center from the Instances page](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8834129951/p49045.png)

    -   Method 2: Click the instance ID to go to the **Instance Details** page. On the **Instance Details** page, view the Alibaba Cloud Security icon. If the icon is orange, there are vulnerability or security alerts in the instance. You can click the icon to log on to the Security Center console and view the alert details.

        ![Go to Security Center from the Instance Details page](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9834129951/p49046.png)


## Set alert notifications

Basic security services allow you to configure alert notifications for security alert items. The alert notifications can be sent by SMS, emails, or internal messages. Perform the following steps to configure alert notifications:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  On the Overview page, click **Handle** in the **Security Score** section to go to the Security Center console.

3.  In the left-side navigation pane, choose **Operation** \> **Settings** and click the **Notifications** tab.

4.  In the **Alerts** row, select severities and configure the methods and time for sending alert notifications.

    ![Set security alert parameters](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9834129951/p49039.png)

    **Note:** If you have upgraded to Security Center Advanced or Enterprise Edition, see the [Overview](/intl.en-US/Threat Detection/Events/Overview.md) in *Security Center documentation* to learn more alert notification methods.


**Documentation**  


[Feature comparison among Basic/Advanced/Enterprise Edition](/intl.en-US/Product Introduction/Features.md)

[RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md)

