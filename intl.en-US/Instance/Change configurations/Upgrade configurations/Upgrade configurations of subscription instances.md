# Upgrade configurations of subscription instances

This topic describes how to upgrade configurations such as instance type and public bandwidth for subscription instances.

When you upgrade the configurations of a subscription instance, you are charged for the price difference between the configurations for the remainder of the current billing cycle.

You can use the configuration upgrade feature to perform the following operations:

-   Upgrade instance types.
-   Upgrade public bandwidths.
-   Convert the billing method for network usage from pay-by-traffic to pay-by-bandwidth.
-   Convert the billing method of disks attached to instances from pay-as-you-go to subscription.

The configuration upgrade feature has the following limits:

-   You can upgrade the configurations of an instance multiple times. However, the interval between two consecutive upgrades must be at least five minutes.
-   If you have renewed an instance and downgraded its configurations within the current billing cycle, you cannot upgrade the configurations of this instance until the next billing cycle.
-   When you upgrade instance types, take note of the following items:
    -   The instance families of the instance types to be upgraded must support configuration changes. For more information, see [Change instance types of instances](/intl.en-US/Instance/Change configurations/Change instance types of instances.md).
    -   You must specify both the vCPU and memory specifications of the instance type to which the instance is to upgrade. You cannot upgrade only the vCPU or memory specification.
    -   You must set the restart time for the instance whose instance type to upgrade. The new instance type takes effect only after the instance is restarted.
-   When you upgrade the public bandwidth of an instance, take note of the following items:
    -   The instance must be a VPC-type instance that has no elastic IP address associated or a classic network-type instance. To change the bandwidth of a VPC-type instance that has no elastic IP address associated, see [t1845712.md\#](/intl.en-US/Instance/Change configurations/Modify the bandwidth of an Elastic IP address.md).
    -   When you upgrade the public bandwidth of a classic network-type instance from 0 Mbit/s for the first time, you must restart the instance for the new configurations to take effect. You can restart the instance by using the ECS console or by calling the RebootInstance operation.

        **Note:** When you upgrade the public bandwidth of a VPC-type instance from 0 Mbit/s for the first time, you do not need to restart the instance.

-   Billing methods for system disks cannot be changed.

## Upgrade the instance type and bandwidth of a single subscription instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the subscription instance to be upgraded and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the **Upgrade/Downgrade Wizard** dialog box, select **Upgrade**, and click **Continue**.

6.  On the **Upgrade** page, complete the relevant settings.

    The following table lists the configurations that can be upgraded.

    |Configuration type|Description|
    |------------------|-----------|
    |Instance type|Select an instance type with higher specifications. You can check whether the instance can have its instance type upgraded and which instance types it can be upgraded to on the Upgrade page.**Note:** If you select the instance type to which the instance is to upgrade, you must continue to set the restart time of the instance. |
    |Public bandwidth|If the instance is a VPC-type instance that has no elastic IP address associated or a classic network-type instance, you can change the public bandwidth of the instance.**Note:** If you do not purchase a public bandwidth during instance creation, the instance is not associated with a public IP. To obtain a public IP address, you can set the public bandwidth to a non-zero value.

    -   If the billing method for network usage is pay-by-traffic, you can adjust the peak bandwidth value or change the billing method to pay-by-bandwidth.
    -   If the billing method for network usage is pay-by-bandwidth, you can adjust the public bandwidth value. |
    |Billing method of disks|If a pay-as-you-go data disk is attached to your instance, you can select this data disk and convert its billing method to subscription.|

7.  Read the Notice. If you do not have any questions, select *ECS Service Terms*.

8.  Verify the price, click **Create Order**, and then complete the payment.

9.  When you upgrade the public bandwidth of a classic network-type instance from 0 Mbit/s for the first time, you must restart the instance for the new configurations to take effect. You can restart the instance by using the ECS console or by calling the RebootInstance operation.


## Batch upgrade the instance type of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances to be upgraded. In the lower part of the page, choose **More** \> **Configuration Change** \> **Upgrade/Downgrade**.

5.  In the **Upgrade/Downgrade Wizard** dialog box, select **Upgrade Instance \(Only for Same Instance Type\)** and then click **Continue**.

6.  On the **Upgrade Instance Type** page, complete the instance type settings.

    If an instance does not have the same instance type as other instances or if it is located in a different zone from the other instances, this instance is filtered out. You can continue to perform operations on only the qualified instances, as shown in the following figure.

    ![Batch upgrade the instance type of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6775240061/p134726.png)

    1.  Select the instance type to which the instance is to upgrade.

    2.  Set the restart time of the instances.

    3.  Read the Notice. If you do not have any questions, select *ECS Service Terms*.

    4.  Verify the price and then click **Upgrade**.

7.  Complete the payment.

    The new instance type is displayed for the corresponding instances in the ECS console after you complete the payment. However, it does not take effect until you restart the instances.


## Batch upgrade the public bandwidth value of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances to be upgraded. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Subscription Instance Bandwidth**.

5.  In the **Change Subscription Instance Bandwidth** dialog box, select **Upgrade Bandwidth**, and then click **Continue**.

6.  On the **Upgrade Bandwidth** page, complete the bandwidth settings.

    If an instance is not associated with a public IP address or if its billing method for network usage is not pay-by-bandwidth, this instance is filtered out. You can continue to perform operations on only the qualified instances, as shown in the following figure.

    ![Batch upgrade the public bandwidth value of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6775240061/p135172.png)

    1.  Specify a greater public bandwidth value.

    2.  Read the Notice. If you do not have any questions, select *ECS Service Terms*.

    3.  Verify the price and then click **Upgrade**.

7.  Complete the payment.

8.  When you upgrade the public bandwidth of a classic network-type instance from 0 Mbit/s for the first time, you must restart the instance for the new configurations to take effect. You can restart the instance by using the ECS console or by calling the RebootInstance operation.


## Batch upgrade the peak bandwidth value of multiple instances

Pay-by-traffic is a pay-as-you-go billing method. You are charged for the traffic that you actually used. Therefore, you are not charged for upgrading only the peak traffic bandwidth. You can configure a bandwidth limit for outbound traffic to avoid unmanageable fees caused by outbound traffic bursts.

**Note:** If you change the billing method for network usage from pay-by-traffic to pay-by-bandwidth, you must pay for the bandwidth upfront.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances to be upgraded. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Subscription Instance Bandwidth**.

5.  In the **Change Subscription Instance Bandwidth** dialog box, select **Modify Peak Bandwidth Value**, and then click **Continue**.

6.  On the **Change Bandwidth** page, complete the bandwidth settings.

    If an instance is not associated with a public IP address or if its billing method for network usage is not pay-by-traffic, this instance is filtered out. You can continue to perform operations on only the qualified instances, as shown in the following figure.

    ![Batch upgrade the peak bandwidth value of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6775240061/p135057.png)

    1.  On the Change Bandwidth page, use one of the following methods to upgrade the bandwidth:

        -   Specify a greater peak bandwidth value.
        -   Change the billing method for network usage from pay-by-traffic to pay-by-bandwidth and set the public bandwidth.
    2.  Read the Notice. If you do not have any questions, select *ECS Service Terms*.

    3.  Verify the price and click **Confirm**.

7.  If you change the billing method for network usage from pay-by-traffic to pay-by-bandwidth, complete the payment.

8.  When you upgrade the public bandwidth of a classic network-type instance from 0 Mbit/s for the first time, you must restart the instance for the new configurations to take effect. You can restart the instance by using the ECS console or by calling the RebootInstance operation.


**Related topics**  


[RebootInstance](/intl.en-US/API Reference/Instances/RebootInstance.md)

[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

