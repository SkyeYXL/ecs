---
keyword: [Alibaba Cloud, ECS, configuration downgrade, subscription, privilege and quota, featured privilege]
---

# Downgrade the public bandwidths of subscription instances

If your account has the featured privilege of configuration downgrade, you can downgrade the public bandwidths of your subscription instances.

The following requirements are met:

-   Your account has the featured privilege of configuration downgrade.

    **Note:** You can click **Privileges** on the **Overview** page of the ECS console. Then, you can check whether your account has the featured privilege of configuration downgrade.

-   Your account does not have overdue payments.
-   The subscription instance whose bandwidth you want to downgrade is in the **Running** or **Stopped** state.
-   The instance does not have a renewal and configuration downgrade task in process. If the instance has a renewal and configuration downgrade task in process, you cannot perform the real-time configuration downgrade operation until the renewal and configuration downgrade task is complete.

A configuration downgrade may result in a refund. You can use the following formula to calculate the refund amount: Refund amount = Remaining amount of the configuration price before the downgrade - Price of the new configurations.

The configuration downgrade feature has the following limits:

-   The usage of your ECS instances determines whether the bandwidth of a subscription instance can be downgraded.
-   Up to three refunds can be made for each subscription instance. A refund is made if you use the configuration downgrade feature to downgrade the instance type, downgrade the bandwidth, or convert the billing method of a disk to pay-as-you-go.
-   The interval between two consecutive configuration downgrades must be at least five minutes.
-   If a VPC-type instance is associated with an elastic IP address \(EIP\), you cannot perform operations described in this topic on the instance. To change the bandwidth of a VPC-type instance that is associated with an EIP, see [t1845712.md\#](/intl.en-US/Instance/Change configurations/Modify the bandwidth of an Elastic IP address.md).

You can upgrade the bandwidth of a subscription instance. For more information, see [Upgrade configurations of subscription instances](/intl.en-US/Instance/Change configurations/Upgrade configurations/Upgrade configurations of subscription instances.md).

## Downgrade the public bandwidth of a single instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  Find the subscription instance and click **Upgrade/Downgrade** in the **Actions** column.

4.  In the **Upgrade/Downgrade Wizard** dialog box, choose **Downgrade** \> **Bandwidth Configuration**, and then click **Continue**.

5.  On the **Downgrade** page, complete the bandwidth settings.

    1.  Use one of the following methods to downgrade the bandwidth:

        -   If the current billing method for network usage is pay-by-bandwidth, you can perform the following operations:
            -   Reduce the fixed bandwidth.
            -   Change the billing method for network usage from pay-by-bandwidth to pay-by-traffic and set the peak bandwidth value.
        -   If the current billing method for network usage is pay-by-traffic, you can adjust the peak bandwidth value, but you cannot change the billing method for network usage to pay-by-bandwidth.

            **Note:** If you reduce the bandwidth of a VPC-type instance to 0 Mbit/s, the public IP address of the instance is disassociated.

    2.  Read the notice. If you have no questions, select *ECS Service Terms*.

    3.  Verify the expected refund amount of the instance and then click **Downgrade Now**.

    After you downgrade the bandwidth, you do not need to restart the instance for the new configurations to take effect immediately.


## Batch downgrade public bandwidths of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Subscription Instance Bandwidth**.

5.  In the **Change Subscription Instance Bandwidth** dialog box, select **Downgrade Bandwidth**, and then click **Continue**.

6.  On the **Downgrade Bandwidth** page, complete the bandwidth settings.

    If an instance is not associated with a public IP address or if its billing method for network usage is not pay-by-bandwidth, this instance is filtered out. You can continue to perform operations on only the qualified instances, as shown in the following figure.

    ![Batch downgrade public bandwidths of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5495240061/p135021.png)

    1.  Use one of the following methods to downgrade the bandwidth:

        -   Reduce the public bandwidth value.
        -   Change the billing method for network usage from pay-by-bandwidth to pay-by-traffic and set a peak bandwidth value.
    2.  Read the notice. If you have no questions, select *ECS Service Terms*.

    3.  Verify the expected refund amount of the instance and then click **Downgrade Now**.

    After you downgrade the bandwidth, you do not need to restart the instance for the new configurations to take effect immediately.


## Batch downgrade the peak bandwidth values of multiple instances

Pay-by-traffic is a pay-as-you-go billing method. You are charged for the traffic that you actually used. You can set a peak bandwidth to limit outbound traffic and avoid unmanageable fees caused by outbound traffic bursts.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the subscription instances. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Subscription Instance Bandwidth**.

5.  In the **Change Subscription Instance Bandwidth** dialog box, select **Modify Peak Bandwidth Value**, and then click **Continue**.

6.  On the **Change Bandwidth** page, complete the bandwidth settings.

    If an instance is not associated with a public IP address or if its billing method for network usage is not pay-by-traffic, this instance is filtered out. You can continue to perform operations on only the qualified instances, as shown in the following figure.

    ![Batch modify the peak bandwidth value of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6775240061/p135057.png)

    1.  Specify a smaller peak bandwidth value.

        **Note:** If you reduce the bandwidth of a VPC-type instance to 0 Mbit/s, the public IP address of the instance is disassociated.

    2.  Read the notice. If you do not have any questions, select *ECS Service Terms*.

    3.  Click **Confirm**.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyInstanceNetworkSpec](/intl.en-US/API Reference/Networks/ModifyInstanceNetworkSpec.md)

