---
keyword: [subscription, renewal, downgrade instance configurations during renewal, billing cycle, change configurations]
---

# Downgrade the configurations of an instance during renewal

This topic describes how to downgrade the configurations of a subscription instance when you renew the instance. The new configurations take effect starting from the next billing cycle. The original configurations remain unchanged during the remainder of the current billing cycle.

You can renew an instance and downgrade its configurations during the following periods of time:

-   Within 15 days before the instance expires
-   After the instance expires but before the instance is automatically released

When you renew an instance and downgrade its configurations, you can downgrade the following configurations:

-   You can downgrade the instance type.

    **Note:** When you perform renewal and configuration downgrade after an instance expires but before the instance is automatically released, you cannot change the instance type.

-   You can change the public bandwidth configurations. You can downgrade the public bandwidth or change the billing method to pay-by-traffic and set a peak value for the bandwidth.
-   You can change the billing method of data disks from subscription to pay-as-you-go.

When you renew an instance and downgrade its configurations, take note of the following items:

-   After the instance is renewed and its configurations are downgraded, the new configurations take effect starting from the next billing cycle. The original configurations remain unchanged during the remainder of the current billing cycle.
-   If you perform the following operations when you renew an instance and downgrade its configurations, you must restart the instance by using the console or calling the RebootInstance operation within the first seven days of the new billing cycle to make the new configurations take effect. The operations include:
    -   Change the instance type.
    -   Change the public bandwidth value of a classic network-type instance from 0 Mbit/s to a non-zero value for the first time.
-   If you perform renewal and configuration downgrade for an instance before it expires, you cannot perform the following operations during the remainder of the current billing cycle:
    -   Upgrade the instance type.
    -   Temporarily upgrade the public bandwidth.
    -   Resize disks, including the partitions and file systems.

## Procedure

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the ECS instance that you want to renew and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the Upgrade/Downgrade Wizard dialog box, select **Renewal and Downgrade** and click **Continue**.

6.  On the Renewal and Downgrade page, perform the following operations:

    1.  Select an instance type.

        The instance types to which you can downgrade the instance are displayed on the page.

        **Note:** When you perform renewal and configuration downgrade after an instance expires but before the instance is automatically released, you cannot change the instance type.

    2.  Set the restart time of the instance.

        This operation is required only when you change the instance type. The restart time cannot be later than the seventh day of the next billing cycle. We recommend that you set the restart time to a point in time during off-peak hours.

    3.  Set the public bandwidth.

        |Current billing method|Supported operation|
        |:---------------------|:------------------|
        |Pay-by-bandwidth|        -   Reduce the bandwidth value.

If you reduce the bandwidth value to 0 Mbit/s, the following impacts on public IP addresses apply:

            -   For classic network-type ECS instances, public IP addresses are not changed.
            -   For VPC-type ECS instances, public IP addresses are released when the next billing cycle starts.
        -   Change the billing method to pay-by-traffic and set a peak value for the bandwidth. |
        |Pay-by-traffic|Set a peak value for the bandwidth.|

    4.  Change the billing method of data disks from subscription to pay-as-you-go.

        If you do not change the billing method, the data disks and the instance will have the same billing cycle starting from the next billing cycle.

    5.  Set the renewal duration.

7.  Select *ECS Service Terms* and click **Create Order**.

8.  Follow the instructions to complete the payment.


## References

For information about how to upgrade or downgrade configurations of other ECS resources, see [Overview of instance upgrade and downgrade](/intl.en-US/Instance/Change configurations/Overview of instance upgrade and downgrade.md).

