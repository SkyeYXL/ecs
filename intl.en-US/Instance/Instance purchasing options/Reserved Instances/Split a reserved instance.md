# Split a reserved instance

You can split a single reserved instance into multiple reserved instances to match smaller pay-as-you-go instances. For ease of description, the reserved instance to be split is referred to as the original reserved instance. The resulting reserved instances are referred to as the destination reserved instances.

-   The original reserved instance is in the **Active** state.
-   No ongoing requests for splitting, merging, or modifying reserved instances exist.

When you split a reserved instance, take note of the following items:

-   Reserved instances that belong to the gn6i and t5 instance families cannot be split.
-   You can change the instance type of a reserved instance. However, you cannot change the instance family of a reserved instance.
-   You cannot change the zone or region of a reserved instance.
-   The total computing power of destination reserved instances must be equal to that of the original reserved instance. For more information about computing power, see [Match between reserved instances and pay-as-you-go instances](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Match between reserved instances and pay-as-you-go instances.md). The following figure shows an example of splitting a reserved instance.

    ![Split a reserved instance](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9890359951/p111720.png)


1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Reserved Instances**.

3.  On the **Reserved Instances** page, find the original reserved instance and click **Split** in the **Actions** column.

4.  In the **Split Reserved Instance** pane, configure the names, instance types, and quantities of the destination reserved instances.

5.  Click **OK**.


After you submit the request for instance splitting, the original reserved instance enters the **Updating** state, and the destination reserved instances in the Creating state are displayed. You cannot cancel the ongoing request for splitting a reserved instance. If you want to roll back the change made by the splitting operation, you can merge the destination reserved instances to obtain the original reserved instance.

After the request for splitting a reserved instance is processed, you can obtain one of the following results:

-   If the reserved instance is split:
    -   The original reserved instance enters the **Inactive** state and expires on the hour when it is split. The price becomes USD 0.
    -   The destination reserved instances enter the **Active** state and take effect on the hour when the original reserved instance is split. If the destination reserved instances are zonal reserved instances, the type of reserved resources is updated automatically.
    -   If the destination reserved instances match pay-as-you-go instances, the billing discounts provided by these reserved instances are applied to the matched pay-as-you-go instances starting from the hour when the destination reserved instances take effect.
-   If the original reserved instance fails to be split, this reserved instance remains active.

Assume that you split an ecs.g5.2xlarge zonal reserved instance into two ecs.g5.xlarge zonal reserved instances at 20:30 of May 28, 2020. The following figure shows the time when the original reserved instance expires and the time when the destination reserved instances take effect.

![The time when the splitting takes effect](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9890359951/p111831.png)

**Related topics**  


[ModifyReservedInstances](/intl.en-US/API Reference/Reserved Instances/ModifyReservedInstances.md)

[DescribeReservedInstances](/intl.en-US/API Reference/Reserved Instances/DescribeReservedInstances.md)

