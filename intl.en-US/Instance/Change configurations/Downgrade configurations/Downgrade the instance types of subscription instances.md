---
keyword: [Alibaba Cloud, ECS, configuration downgrade, subscription, privilege and quota, featured privilege]
---

# Downgrade the instance types of subscription instances

If your account has the featured privilege of configuration downgrade, you can downgrade the instance types of your subscription instances. The new instance types take effect immediately after you restart the instances.

The following requirements are met:

-   Your account has the featured privilege of configuration downgrade.

    **Note:** You can click **Privileges** on the **Overview** page of the ECS console. Then, you can check whether your account has the featured privilege of configuration downgrade.

-   Your account does not have overdue payments.
-   The subscription instance whose instance type you want to downgrade is in the **Stopped** \(`Stopped`\) state.
-   The instance does not have a renewal and configuration downgrade task in process. If the instance has a renewal and configuration downgrade task in process, you cannot perform the configuration downgrade operation until the renewal and configuration downgrade task is complete.

A configuration downgrade may result in a refund. You can use the following formula to calculate the refund amount: Refund amount = Remaining amount of the configuration price before the downgrade - Price of the new configurations.

The configuration downgrade feature has the following limits:

-   The usage of your ECS instances determines whether the configuration downgrade feature is supported.
-   Up to three refunds can be made for each subscription instance. A refund is made if you use the configuration downgrade feature to downgrade the instance type, downgrade the bandwidth, or convert the billing method of a disk to pay-as-you-go.
-   The interval between two consecutive configuration downgrades must be at least five minutes.
-   You can only change the instance type of a subscription instance to an instance type of lower specifications.

    **Note:** For information about whether the instance type of an instance can be downgraded, and to which instance types of an instance can be downgraded, see the information displayed on the Downgrade page.

-   You must specify both the vCPU and memory specifications of the instance type to which the instance is to downgrade. You cannot upgrade only the vCPU or memory specification.

## Downgrade the instance type of a single instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the subscription instance and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the Upgrade/Downgrade Wizard dialog box, select **Downgrade** and **Instance Type**, and then click **Continue**.

6.  On the **Downgrade** page, complete the instance type settings.

    1.  Select the instance type to which the instance is to downgrade.

    2.  Read the notice. If you have no questions, select *ECS Service Terms*.

    3.  Verify the expected refund amount of the instance and then click **Downgrade Now**.

7.  Start the instance.

    The new instance type takes effect immediately after the instance is started.


## Batch downgrade the instance type of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances. In the lower part of the page, choose **More** \> **Configuration Change** \> **Upgrade/Downgrade**.

5.  In the **Upgrade/Downgrade Wizard** dialog box, select **Downgrade Instance Type \(Only for Stopped Instances of the Same Instance Type\)** and then click **Continue**.

6.  On the **Downgrade Instance Type** page, complete the instance type settings.

    If an instance does not have the same instance type as other instances or if it is located in a different zone from the other instances, this instance is filtered out. You can continue to perform operations only on the qualified instances, as shown in the following figure.

    ![Batch downgrade the instance type of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1557240061/p135081.png)

    1.  Select the instance type to which the instances are to downgrade.

    2.  Read the notice. If you do not have any questions, select *ECS Service Terms*.

    3.  Verify the expected refund amount of the instance and then click **Downgrade Now**.

7.  Start the instance.

    The new instance type takes effect immediately after the instance is started.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyPrepayInstanceSpec](/intl.en-US/API Reference/Instances/ModifyPrepayInstanceSpec.md)

