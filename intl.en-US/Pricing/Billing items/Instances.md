---
keyword: [ECS billing, instance billing, subscription, pay-as-you-go]
---

# Instances

This topic describes the billing methods of ECS instances, comparison of these billing methods, and how to choose billing methods based on scenarios.

## Overview

ECS instances are charged based on instance types, including vCPUs and memory. Prices of an instance type may vary with regions. For more information, see the[Pricing](https://www.alibabacloud.com/product/ecs) tab on the Elastic Compute Service page.

**Note:** If you select an instance type that is equipped with local disks, the price of the instance type includes that of local disks.

## Billing methods

The following table describes the billing methods of ECS instances and each billing method.

|Billing method|Description|Reference|
|--------------|-----------|---------|
|Subscription|A billing method that allows you to use ECS instances only after you pay for them. Price = Unit price of an instance type × Subscription duration.

|[Subscription](/intl.en-US/Pricing/Billing methods/Subscription.md)|
|Pay-as-you-go|A billing method that allows you to use ECS instances before you pay for them. Price = Unit price of an instance type × Billing duration. The billing cycle is accurate to seconds.

|[Pay-as-you-go](/intl.en-US/Pricing/Billing methods/Pay-as-you-go.md)|
|Preemptible instance|Preemptible instances are on-demand instances that you can use before you pay. Compared with pay-as-you-go instances, preemptible instances offer more discounts. Preemptible instances are charged based on the actual usage duration, and their prices fluctuate based on the changes to supply and demand.|[Preemptible instances](/intl.en-US/Pricing/Billing methods/Preemptible instances.md)|
|Reserved instance|Reserved instances are coupons that must be used together with pay-as-you-go instances. Compared with pay-as-you-go instances, reserved instances offer some discounts. Prices of reserved instances are determined based on the region, instance type, operating system, payment option, term, and instance quantity. Reserved instances are used to offset bills of pay-as-you-go instances based on the resources that you specified when you purchased the reserved instances. Reserved instances are applied only when they match pay-as-you-go instances.

|[Reserved instances](/intl.en-US/Pricing/Billing methods/Reserved instances.md)|

## Comparison of billing methods

The following table describes the comparison of billing methods.

|Comparison item|Subscription|Pay-as-you-go|Preemptible instance|Reserved instance|
|---------------|------------|-------------|--------------------|-----------------|
|Usage|All operations are linked to a single instance.|All operations are linked to a single instance.|All operations are linked to a single instance.|Resources are decoupled from bills. Reserved instances must be used together with pay-as-you-go instances.|
|Payment option|You make a full payment for ECS instances before you use them.|You pay for ECS instances after you use them. The ECS instances are charged by second and billed by hour.|You pay for ECS instances after you use them. The ECS instances are charged by second and billed by hour.|You can choose All Upfront, Partial Upfront, or No Upfront.|
|Feature of price|Subscription instances are more cost-effective than pay-as-you-go instances.|Pay-as-you-go instances are the least cost-effective.|Prices of preemptible instances fluctuate based on the changes to supply and demand. The discounts can be up to 90% of pay-as-you-go prices.|Compared with pay-as-you-go instances, reserved instances offer some discounts. The discounted prices are close to those of subscription instances.|
|Instance release|You can manually release instances or they can be released by the system. If you want to release an instance before it expires, you must cancel the subscription of the instance or change its billing method to pay-as-you-go. If you do not renew an instance within the required period of time after it expires, the instance is automatically released.|You can release instances at any time.|You can manually release instances or they can be released by the system. Preemptible instances can be reclaimed and may be automatically released after the protection period expires.|Reserved instance must be used together with pay-as-you-go instances. Pay-as-you-go instances that match reserved instances can be released at any time. After the pay-as-you-go instances are released, the reserved instances can be used to match and offset bills of new pay-as-you-go instances.|
|Scenario|Subscription instances are applicable to services that run for 24 hours a day and 7 days a week, such as web services and databases.|Pay-as-you-go instances are applicable to services that experience traffic spikes, such as temporary scaling, interim testing, and scientific computing.|Preemptible instances are applicable to services that experience traffic spikes, such as temporary scaling, interim testing, and scientific computing.|Reserved instances are used to match and offset bills of pay-as-you-go instances, and applicable to web services and databases.|

You can choose appropriate billing methods for ECS instances on which different applications are deployed to reduce costs. The following figure shows the recommended combinations of billing methods.

![Combination of billing methods ](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4227393061/p171214.jpg)

For stable business loads, you can use the subscription billing method or reserved instances to obtain some discounts. When ECS instances have the same subscription duration, reserved instances are more flexible than subscription. The following table describes the comparison between subscription and reserved instances.

|Feature|Subscription|Reserved instance|
|-------|------------|-----------------|
|Discount limits|Discounts are offered only for a single instance.|A reserved instance can match a maximum of 100 pay-as-you-go instances to offer discounts.|
|Resource reservation|Supported.|Supported. You must use zonal reserved instances.|
|Use across services|Not supported.|Supported. Reserved instances can be used in ECS and Elastic Container Instance \(ECI\).|
|Use across zones in the same region|Not supported.|Supported. You must use regional reserved instances.|
|Use across instance families|Not supported.|Not supported.|
|Use across instance types in the same instance family|Not supported.|Supported.|
|Use across operating systems|Not supported.|Not supported.|
|Use across accounts \(based on the established trusteeship\)|Not supported.|Supported.|
|Installment|Not supported.|Supported. You can choose All Upfront, Partial Upfront, or No Upfront.|

## Examples of typical scenarios

The following figure shows some typical scenarios to which you can refer to choose appropriate billing methods.

![Scenarios of instance billing](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4227393061/p171036.png)

|Business type|Linked pattern|Stable pattern|Burstable pattern|Hybrid pattern|
|-------------|--------------|--------------|-----------------|--------------|
|Business characteristics|All businesses are closely linked. When traffic loads of one business increase, traffic loads of other businesses also increase.|Business loads are stable with no obvious peak hours or off-peak hours.|All businesses are loosely linked. Business loads may become burstable at some points in time.|Multiple businesses exist. Each business has a unique requirement for computing power during a specific time period. The businesses have different priorities.|
|Example scenarios|Hot issues, e-commerce promotions, and traffic spikes of IoT|Stable online businesses, such as office automation \(OA\) systems|Event-based tasks, job tasks, and simulation tasks|Scenarios where online, offline, and job tasks are deployed in a hybrid manner and where multiple environments are used alternately, such as blue green deployment|
|Recommended billing methods|Pay-as-you-go and reserved instances|-   Subscription
-   Pay-as-you-go and reserved instances

|Pay-as-you-go.You can combine pay-as-you-go instances with reserved instances if traffic bursts frequently.

|Pay-as-you-go and reserved instances|

## References

You can change the billing method of an instance from subscription to pay-as-you-go or from pay-as-you-go to subscription.

-   For information about how to change a billing method from subscription to pay-as-you-go, see [Change the billing method of an instance from subscription to pay-as-you-go](/intl.en-US/Pricing/Change the billing method/Change the billing method of an instance from subscription to pay-as-you-go.md).
-   For information about how to change a billing method from pay-as-you-go to subscription, see [Change the billing method of an instance from pay-as-you-go to subscription](/intl.en-US/Pricing/Change the billing method/Change the billing method of an instance from pay-as-you-go to subscription.md).

