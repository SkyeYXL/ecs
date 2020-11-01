# Create a preemptible instance

This topic describes how to create a preemptible instance in the ECS console.

To create and use a preemptible instance, take note of the following items:

-   Set an appropriate bidding price and take into account the estimated market price fluctuations. An appropriate bidding price can result in a higher probability of creating a preemptible instance and ensure that the instance is not released due to small changes in price. The bidding price must also meet your business expectations.

    **Note:** If you do not know what price to bid for your preemptible instances, we recommend that you use the market price at the time of purchase as the bidding price.

-   Use an image that contains the configurations of all the required software to ensure that the instance can be started any time after it is created. You can also use user data of the instance to run commands when you start the instance. For more information, see [Prepare user data](/intl.en-US/Instance/Manage instances/User data/Prepare user data.md).
-   To prevent data loss caused by instance release, store important data in a storage medium that is not affected when preemptible instances are released, such as separately created cloud disks, OSS buckets, or ApsaraDB for RDS instances.
-   Break your jobs down into smaller tasks by using grids, Hadoop, or queue-based architecture, or use checkpoints to save calculation results.
-   Monitor the status of a preemptible instance by checking the instance release notifications from ECS. ECS updates the instance metadata five minutes before ECS releases a preemptible instance. You can obtain the status of a preemptible instance every minute by checking instance metadata. For more information, see [Metadata](/intl.en-US/Instance/Manage instances/Metadata/Metadata.md).
-   Run your applications on a pay-as-you-go instance and release the instance to verify whether your applications can automatically adjust themselves when the instance is released.

You can use developer tools such as Alibaba Cloud CLI, OpenAPI Explorer, and Alibaba Cloud SDK to call the RunInstances operation and create a preemptible instance.

**Note:** You can set the SpotStrategy parameter to SpotAsPriceGo to use the market price at the time of purchase. Alternatively, you can set the SpotStrategy parameter to SpotWithPriceLimit to use the acceptable maximum price.

This topic describes configurations to create a preemptible instance. For more information about other configurations for creating an instance, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  On the **Instances** page, click **Create Instance**.

4.  Set **Billing Method** to **Preemptible Instance**.

5.  In the **Maximum Price for Instance Type** section, specify your bidding price.

    The preemptible instance you request is created at the market price only if your bidding price is higher than or equal to the market price and resources are sufficient. You can bid for a preemptible instance only once. The following bidding modes are supported:

    -   **Use Automatic Bid**: The market price at the time of purchase is used as the bidding price.
    -   **Set Maximum Price**: You must set the highest price you are willing to pay for the instance type.

        **Note:** In the displayed price range, the maximum price is equal to the price for the pay-as-you-go instance of the same instance type. Your bidding price must be based on the displayed price range, your business requirements, and the estimated price fluctuations. If you set your bidding price while taking the estimated price fluctuations into consideration, you can retain a preemptible instance for a long period of time. Otherwise, the instance may be released at any time after the protection period ends.

6.  Select or enter the quantity of instances that you want to purchase.

7.  Complete other settings.

8.  Confirm the order information and click **Create Instance**.


After a preemptible instance is created, you can view its information in the instance list. A preemptible instance is marked as **Pay-As-You-Go Preemptible Instance** in the Billing Method column. Click the instance ID to go to the Instance Details page. In the **Payment Information** section, you can view the bidding policy configured when you create the instance.

**Related topics**  


[RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md)

