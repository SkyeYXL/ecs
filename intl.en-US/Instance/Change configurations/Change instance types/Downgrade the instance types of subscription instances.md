---
keyword: [Alibaba Cloud, ECS, downgrade instance configurations, subscription, privileges and quotas, reduce memory, downgrade CPU]
---

# Downgrade the instance types of subscription instances

When the configurations \(vCPUs and memory\) of a subscription instance exceed your business requirements and your account has the configuration downgrade privilege, you can downgrade the instance type of the instance in real time. Start the instance after it is downgraded to make the changes take effect.

Make sure that the subscription instance for which you want to downgrade the instance type meets the following requirements:

-   Your account does not have any overdue payments and has the configuration downgrade privilege.

    **Note:** You can click **Privileges** on the **Overview** page. On the Privileges and Quotas page, click the Privileges tab, and check whether your account has the configuration downgrade privilege.

-   The instance is in the **Stopped** \(`Stopped`\) state.
-   The instance family to which the instance belongs supports downgrades. For more information, see [Change instance types of instances](/intl.en-US/Instance/Change configurations/Change instance types/Change instance types of instances.md).
-   The instance does not have a renewal and configuration downgrade task in process. If the instance has a renewal and configuration downgrade task in process, you must wait until the task is complete to perform the configuration downgrade operation.

Take note of the following limits when you use the configuration downgrade feature to downgrade the instance type:

-   The usage of your ECS instances determines whether the configuration downgrade feature is supported.
-   You must select a different instance type for the instance. You cannot downgrade only vCPUs or memory size.
-   You can downgrade the configurations of an instance multiple times, but you must wait at least five minutes between two consecutive operations.
-   Up to three refunds can be made for each subscription instance. A refund is made if you use the configuration downgrade feature to downgrade the instance type, downgrade the bandwidth, or change the billing method of disks from subscription to pay-as-you-go.

    **Note:** A configuration downgrade may result in a refund. The following formula is used to calculate the refund amount: Refund amount = Remaining amount of the configuration price before the downgrade - Price of the new configurations.


In addition to downgrading the instance type, you can also use the configuration downgrade feature to perform the following operations:

-   Downgrade public bandwidths.
-   Change the billing method for network usage from pay-by-bandwidth to pay-by-traffic.
-   Change the billing method of disks attached to instances from subscription to pay-as-you-go.

## Downgrade the instance type of a single instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the subscription instance whose instance type you want to downgrade and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the Upgrade/Downgrade Wizard dialog box, select **Downgrade** and **Instance Type** and then click **Continue**.

6.  On the **Downgrade** page, complete the instance type settings.

    **Note:** You can select only an instance type of lower configurations. You can check whether the instance can have its instance type downgraded and the instance types that you can use for the downgrade.

7.  Read the notice. If you do not have any questions, select *ECS Service Terms*.

8.  Confirm the refund amount, click **Downgrade Now**, and then perform the subsequent operations as instructed on the page.

9.  Start the instance.

    The new instance type takes effect immediately after the instance is started.


## Downgrade the instances type of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select subscription instances whose instance types you want to downgrade. In the lower part of the page, choose **More** \> **Configuration Change** \> **Upgrade/Downgrade**.

5.  In the **Upgrade/Downgrade Wizard** dialog box, select **Downgrade Instance Type \(Only for Stopped Instances of the Same Instance Type\)** and click **Continue**.

6.  On the **Downgrade Instance Type** page, complete the instance type settings.

    If an instance does not have the same instance type as other instances or if it is located in a different zone from other instances, this instance is filtered out. You can continue to perform operations only on the qualified instances, as shown in the following figure.

    ![Downgrade the instance types of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1557240061/p135081.png)

7.  Read the notice. If you do not have any questions, select *ECS Service Terms*.

8.  Confirm the refund amount, click **Downgrade Now**, and then perform the subsequent operations as instructed on the page.

9.  Start the instances.

    The new instance type takes effect immediately after the instances are started.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyPrepayInstanceSpec](/intl.en-US/API Reference/Instances/ModifyPrepayInstanceSpec.md)

