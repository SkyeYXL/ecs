# Purchase reserved instances

This topic describes how to purchase reserved instances in the ECS console.

-   Before you purchase reserved instances, make sure that the pay-as-you-go instances that you want to match meet the requirements for applying reserved instances. For more information, see [Reserved instance overview](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Reserved instance overview.md).
-   You cannot manually manage how reserved instances and pay-as-you-go instances are matched. Make sure that you understand the matching rules for reserved instances. For more information, see [Match between reserved instances and pay-as-you-go instances](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Match between reserved instances and pay-as-you-go instances.md).

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Reserved Instances**.

3.  In the top navigation bar, select a region.

4.  Click **Purchase Reserved Instance**.

5.  Configure region-related parameters.

    1.  Select a region.

    2.  Set Resource Reservation.

        **Note:** Only zonal reserved instances support resource reservation. Regional reserved instances apply to pay-as-you-go instances of different sizes in different zones within the same region.

    3.  Select a zone.

6.  Configure instance-related parameters.

    1.  Select an instance type.

        **Note:** You must select an instance type when you purchase a regional reserved instance. The regional reserved instance can match any pay-as-you-go instances of the specified instance family within the specified region regardless of size.

    2.  Set Operating System Platform.

        You can select **Linux** or **Windows**.

        **Note:** The reserved instance matches only pay-as-you-go instances that use the selected type of operating system. The operating system of an reserved instance cannot be changed after you purchase the reserved instance.

        To apply a reserved instance to pay-as-you-go instances created from Bring Your Own License \(BYOL\) images, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

    3.  Set Payment Option.

        **All Upfront**, **Partial Upfront**, and **No Upfront** are available. For more information, see [Reserved instance billing](/intl.en-US/Pricing/Billing methods/Reserved instance billing.md).

7.  Configure purchase-related parameters.

    1.  Set Name.

    2.  Set Term.

        You can select **1 Month**, **1 Year**, **3 Years**, or **5 Years**.

    3.  Set Quantity.

        The reserved instance can match the specified number of pay-as-you-go instances of the specified instance type. For example, if the instance type is ecs.g5.large and Quantity is set to 3, the reserved instance can match three pay-as-you-go instances of the ecs.g5.large instance type.

8.  Configure tags.

    You can add tags for multiple types of Alibaba Cloud resources. You can use tags to perform cost sharing, monitoring by group, and automated O&M by group. For more information, see [Overview](/intl.en-US/Tag & Resource/Tags/Overview.md).

9.  Read and select *ECS Terms of Service* and then click **Purchase**.

10. In the message that appears, confirm that the parameters are correct and click **Create Order**.

11. Read the payment information and then click **Subscribe**.


After you purchase a reserved instance, you can immediately use it to offset bills when the reserved instance matches one or more pay-as-you-go instances. You can also manage the reserved instance in response to pay-as-you-go instance changes.

**Related topics**  


[PurchaseReservedInstancesOffering](/intl.en-US/API Reference/Reserved Instances/PurchaseReservedInstancesOffering.md)

[Split a reserved instance](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Split a reserved instance.md)

[Merge reserved instances](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Merge reserved instances.md)

[Modify a reserved instance](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Modify a reserved instance.md)

