# Overview

Preemptible instances are a type of on-demand instances that are offered at a discounted price compared to pay-as-you-go instances. Preemptible instances are designed to minimize ECS instance costs in certain scenarios.

## Introduction

The following table describes the features of preemptible instances.

|Feature|Description|
|-------|-----------|
|Bidding mode|The market price of a preemptible instance fluctuates based on changes to the supply and demand of its instance type. When you create a preemptible instance, you must specify a maximum price per hour to bid for a specific instance type. If your bid price is higher than the current market price and the stock of the instance type is sufficient, your instance is created and incurs charges at the current market price.After a preemptible instance is created, it can be used in the same manner as a pay-as-you-go instance. You can also use it with other cloud resources such as cloud disks or elastic IP address \(EIP\). |
|Protection period|A preemptible instance has a protection period of one hour after it is created. When you call an API operation to create a preemptible instance, you are allowed to disable the protection period feature.-   If the protection period feature is enabled for a preemptible instance, the preemptible instance is not released due to fluctuations in market price during the protection period. You can continue to perform operations on the preemptible instance.
-   The price of a preemptible instance without the protection period is discounted an additional 10% compared to the price of a preemptible instance with the protection period.

**Note:** You can only enable the protection period when you create a preemptible instance by calling an API operation. For more information, see SpotDuration in [RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md) and [CreateInstance](/intl.en-US/API Reference/Instances/CreateInstance.md). |
|Recycling|After the protection period ends, the system checks the market price and resource stock of the instance type every five minutes. If the market price is higher than your bid price or if the stock of the instance type is insufficient, the preemptible instance is released.**Note:** After an instance is released, its data cannot be recovered. We recommend that you create a snapshot for the instance to back up its data before the instance is released. For more information, see [Snapshot overview](/intl.en-US/Snapshots/Snapshot overview.md).

You can view the release rates of specific instance types on the buy page. The release rates are applicable to preemptible instances with or without the protection period. The release rate is subject to the supply and demand of instance types and the bid policy of preemptible instances. A lower release rate indicates that preemptible instances are less likely to be reclaimed. |

Silicon Valley Zone B and ecs.c5.8xlarge are used in this example. Assume that:

-   The original price of the current pay-as-you-go instance is 1.52 USD/hour.
-   A preemptible instance with a protection period of one hour is discounted 10% compared to the original price of the pay-as-you-go instance for a price of 0.152 USD/hour.

If the protection period feature is disabled when a preemptible instance is created, the price of the instance is discounted an additional 10%. As a result, the price for the instance is 0.152 × 0.9 = 0.137 USD/hour.

**Note:** The original price of pay-as-you-go instances and the discount for preemptible instances are subject to change. Prices in this example are for reference only.

![spot-price-example-intl](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2406724061/p170590.png)

## Lifecycle

The following figure shows the lifecycle of a preemptible instance that has a protection period of one hour.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3890359951/p59675.png)

After a preemptible instance is created, you can release the instance at any time. For more information, see [Release an instance](/intl.en-US/Instance/Manage instances/Release an instance.md). When the market price exceeds your bid price or when the stock of the instance type is insufficient, your instance will enter the Recycling state. After five minutes, the instance is automatically released. You can check whether the instance enters the Recycling state based on the instance metadata or the `OperationLocks` information returned by calling the DescribeInstances operation.

You can check whether your preemptible instance enters the Recycling state and store a small amount of data while you wait for the release of the instance. However, we recommend that you optimize the application design to ensure that the application runs normally after your preemptible instance is released. You can try to manually release your preemptible instance to check whether the application runs normally after the preemptible instance is released.

Typically, the system first releases the instance that has the lowest bid price. If multiple preemptible instances have the same bid price, the system randomly determines the order in which the instances are released.

## Limits

-   Whether you can purchase a preemptible instance depends on your ECS instance resource usage.
-   Preemptible instances cannot be converted to subscription instances.
-   The instance types of preemptible instances cannot be changed.
-   For information about the service quota of preemptible instances, see the "Instance limits" section in [Limits](/intl.en-US/Product Introduction/Limits.md).

## Scenarios

Preemptible instances are ideal for stateless applications, such as scalable web services, image rendering, big data analysis, and large-scale parallel computing. Preemptible instances are applicable to applications that require a high level of distribution, scalability, and fault tolerance capabilities. Preemptible instances help reduce costs and increase the throughput of these applications.

You can use preemptible instances for the following business:

-   Real-time analysis
-   Big data
-   Geospatial surveys
-   Image and media coding
-   Scientific computing
-   Scalable websites and web crawlers
-   Tests

Preemptible instances are not suitable for stateful applications such as databases. When a preemptible instance is released due to a failed bid or other reasons, it is difficult to store application state data.

## Pricing and billing

-   Prices

    The price of a preemptible instance covers only the price of the instance type \(including vCPUs and memory\) and does not include the prices of resources such as system disks, data disks, and network bandwidth.

    -   System disks and data disks are charged on a pay-as-you-go basis. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Billing methods/Pay-as-you-go.md).
    -   Network bandwidth is charged based on the bandwidth billing method of pay-as-you-go instances. For more information, see [Public bandwidth](/intl.en-US/Pricing/Billing items/Public bandwidth.md).
-   Market prices

    The market price of a preemptible instance fluctuates based on changes to the supply and demand of its instance type. If your bid price is higher than the current market price of the specified instance type and the stock of the instance type is sufficient, a preemptible instance can be created.

    Within the first hour after a preemptible instance is created, the instance is charged based on the market price at the time of bidding. After one hour, the instance is charged based on the real-time market price.

    We recommend that you evaluate the market price fluctuations to minimize computing costs and increase throughput when you purchase preemptible instances.

-   Billing methods

    Preemptible instances are charged by second. The market price of a preemptible instance is an hourly price. You can divide the hourly price by 3,600 to get the price per second.

    The cost incurred by a preemptible instance from creation to release is accurate to two decimal places. Accrued costs of less than USD 0.01 are not charged.

-   Billing duration

    A preemptible instance is charged based on its actual usage period, which lasts from the creation to the release of the instance. If you stop an instance only by calling the StopInstance operation or by using the ECS console, the instance continues to be charged. When you no longer need a preemptible instance, we recommend that you create snapshots to back up your data and environment and then release the instance. You can purchase new preemptible instances at any time.


## FAQ

-   What resources are included in the price of preemptible instances?

    The price of preemptible instances includes only the instance type. Other resources such as cloud disks and network bandwidth are billed at the same prices as those of pay-as-you-go instances.

-   Will I be notified when my preemptible instances are about to be released?

    Yes, you will be notified when your preemptible instances are about to be released. When your preemptible instance needs to be released due to a market price change or insufficient resources, the instance will first enter the Recycling state and then be automatically released in five minutes.

-   Can the instance type of a preemptible instance be changed?

    No, the instance types of preemptible instances cannot be changed.

-   Which is more cost-effective: a preemptible instance with the protection period or a preemptible instance without the protection period?

    A preemptible instance with the protection period is more cost-effective than the one without the protection period. Preemptible instances with the protection period are discounted at an additional 10% compared to preemptible instances without the protection period.

-   Can I change the protection period settings of a preemptible instance?

    No, the protection period settings of a preemptible instance cannot be changed. By default, a preemptible instance has a protection period of one hour. You can enable the protection period feature only when you call an API operation to create a preemptible instance. You cannot change the protection period settings of the instance after it is created.

-   Is the release rate of preemptible instances without the protection period higher than that of preemptible instances with the protection period?

    You can view the release rates of specific instance types on the buy page. The release rates are applicable to preemptible instances with or without the protection period. The release rate is subject to the supply and demand of instance types and the bidding policy of preemptible instances.

    ![release-rate](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6554873061/p170286.png)


For more information about preemptible instances, see [Instance FAQ](/intl.en-US/Instance/ECS instance FAQ.md).

