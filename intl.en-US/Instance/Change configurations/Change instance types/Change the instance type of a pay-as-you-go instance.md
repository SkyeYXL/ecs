---
keyword: [Alibaba Cloud, ECS, upgrade and downgrade, pay-as-you-go]
---

# Change the instance type of a pay-as-you-go instance

This topic describes how to change the instance type \(vCPUs and memory\) of a pay-as-you-go instance.

Make sure that the instance whose instance type you want to change meets the following requirements:

-   The instance is in the **Stopped** \(`Stopped`\) state.

    **Note:**

    -   Select **Retain Instance and Continue Charging After Instance is Stopped** for the stop mode when you attempt to stop the instance.
    -   Service interruptions may occur when you stop an instance. We recommend that you perform this operation during off-peak hours.
-   The instance family to which the instance belongs supports instance type changes. For more information, see [Change instance types of instances](/intl.en-US/Instance/Change configurations/Change instance types/Change instance types of instances.md).

Take note of the following limits when you use the instance type change feature:

-   The number of vCPUs and memory size can only be changed by changing the instance type. They cannot be changed seperately.
-   You can change the instance type of an instance multiple times, but you must wait at least five minutes between two consecutive operations.

## Change the instance type of a single instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the pay-as-you-go instance for which you want to change the instance type and click **Change Instance Type** in the **Actions** column.

5.  On the **Change Instance Type** page, select a new instance type.

6.  Confirm the configuration costs and click **Change**.

7.  Start the instance.

    The new instance type takes effect immediately after the instance is started.


## Change the instance types of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the pay-as-you-go instances for which you want to change the instance types. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Pay-as-you-go Instance Type**.

5.  On the **Change Instance Type** page, select a new instance type.

    If an instance does not have the same instance type as other instances or if it is located in a different zone from other instances, this instance is filtered out. You can continue to perform operations only on the qualified instances, as shown in the following figure.

    ![Change the instance types of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9249443061/p139381.png)

6.  Confirm the configuration costs and click **Change**.

7.  Start the instances.

    The new instance type takes effect immediately after the instances are started.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md)

