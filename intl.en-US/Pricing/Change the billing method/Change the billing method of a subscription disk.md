# Change the billing method of a subscription disk

You can use the downgrade feature to change the billing method of a disk from subscription to pay-as-you-go.

-   The billing method of a subscription disk can be changed to pay-as-you-go only when it is used as a data disk.
-   The subscription instance to which the subscription disk is attached is in the **Running** or **Stopped** state.

The downgrade feature has the following limits:

-   Whether this feature is supported depends on your ECS usage.
-   The configurations of only one subscription instance can be downgraded at a time.
-   The interval between two consecutive downgrade operations must be at least 5 minutes.

A configuration downgrade may result in a refund. The refund amount is the calculation result of the following formula: Refund amount = Price of the new configurations - Remaining amount of the purchase price before the downgrade.

**Note:** A maximum of three refunds can be made for each instance, including refunds incurred when you downgrade the instance type, downgrade the public bandwidth, or convert subscription disks to pay-as-you-go disks.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the target instance and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the Upgrade/Downgrade Wizard dialog box, choose **Configuration Downgrade** \> **Disk charge type to pay-as-you-go**, and click **Continue**.

6.  Select a disk and confirm the refund amount.

7.  Select *ECS Service Terms* and click **Downgrade Now**.


By default, after the billing method of a disk is changed to pay-as-you-go, the disk is not released together when its attached instance is released. You can configure whether the disk is released with its attached instance in the ECS console. For more information, see [Release a disk](/intl.en-US/Block Storage/Cloud disks/Release a disk.md).

**Related topics**  


[ModifyDiskChargeType](/intl.en-US/API Reference/Disk/ModifyDiskChargeType.md)

