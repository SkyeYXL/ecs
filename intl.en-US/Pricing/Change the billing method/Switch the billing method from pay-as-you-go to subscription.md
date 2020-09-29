---
keyword: [subscription, pay-as-you-go, switch billing methods]
---

# Switch the billing method from pay-as-you-go to subscription

This topic describes how to switch the billing method of your instance from pay-as-you-go to subscription in the ECS console. After you create a pay-as-you-go instance, you can convert its billing method to subscription to have resource reservation and a discounted rate.

The ECS instance whose billing method you want to switch must meet the following requirements:

-   The instance belongs to your account.
-   The instance is of none of the following instance types:

    -   Instance types in Generation I instance families: t1, s1, s2, s3, m1, m2, c1, and c2.
    -   Instance types in the n1, n2, and e3 instance families.
    **Note:** For more information about these instance types, see [Phased-out instance types](/intl.en-US/Instance/Phased-out instance types.md).

-   The instance cannot be a preemptible instance.
-   You have no unpaid order to switch the billing method of the instance.

    If you have an unpaid order to switch the billing method of the instance, you must cancel the unpaid order and then place another order to switch the billing method.

-   Automatic release is not set for the instance.

    If automatic release has been set for an instance, you must disable the automatic release configuration and then switch the billing method. For more information, see [Disable automatic release](/intl.en-US/Instance/Manage instances/Release an instance.md).

-   The instance is in the **Running** or **Stopped** state.

    Example: An order to switch the billing method has been placed when the ECS instance is in the Running or Stopped state. However, the instance status changed when the payment was attempted. The preceding requirement is not met. The order fails and the billing method does not change. You can go to the Billing Management console and pay for the order when the instance is in the Running or Stopped state again.


You can switch the billing method of a maximum of 20 instances from pay-as-you-go to subscription at a time.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).

3.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

4.  In the top navigation bar, select a region.

5.  Select one or more pay-as-you-go instances. Click **Switch to Subscription** under the instance list.

6.  On the Switch to Subscription page, click **Batch Change**.

7.  In the dialog box that appears, configure the parameters including:

    1.  Duration: You can set the length of service time for the subscription instance.

        Instances whose billing methods are converted at the same time must have the same length of service time.

    2.  Data disk: If pay-as-you-go data disks are attached to the selected instances, you can set whether to also switch the billing method of the disks to subscription.

8.  Click **OK**.

9.  Complete the payment as prompted.


