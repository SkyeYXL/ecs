# ECS instance lifecycle

The lifecycle of an ECS instance begins when the instance is created and ends when the instance is released. This topic describes the states that an ECS instance may go through during its lifecycle.

## Instance states

The following table describes the states that an ECS instances may go through during its lifecycle.

|State|State in an API response|State attribute|Description|Visible in the ECS console|
|:----|------------------------|:--------------|:----------|:-------------------------|
|Preparing|Pending|Transitory|After an instance is created, it is in this state before it enters the **Running** state. If the instance remains in this state for an extended period of time, an exception occurs.|No|
|Starting|Starting|Transitory|After you start or restart an instance by using the ECS console or by calling an API operation, the instance enters this state before it enters the **Running** state. If the instance remains in this state for an extended period of time, an exception occurs.|Yes|
|Running|Running|Stable|If an instance runs properly, it is in this state. **Note:** An ECS instance can be externally accessed only when it is in the **Running** state.

|Yes|
|Expiring|Running|Stable|A subscription instance remains in the **Expiring** state for 15 days before it expires. If your instance enters the Expiring state, we recommend that you renew the instance in a timely manner. For more information, see [t9590.md\#](/intl.en-US/Pricing/Renew instances/Overview.md).|Yes|
|Stopping|Stopping|Transitory|When you stop an instance by using the ECS console or by calling an API operation, the instance enters this state before it enters the **Stopped** state. If the instance remains in this state for an extended period of time, an exception occurs.|Yes|
|Stopped|Stopped|Stable|After an instance is stopped or after an instance is created but has not started, it is in the **Stopped** state. **Note:** An ECS instance can be externally accessed only when it is in the **Running** state.

|Yes|
|Expired|Stopped|Stable|When a subscription instance expires or when a pay-as-you-go instance is stopped due to overdue payments, the instance enters the **Expired** state. For more information about the changes of resource status, see [Subscription](/intl.en-US/Pricing/Subscription.md) and [Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md). **Note:** An ECS instance can be externally accessed only when it is in the **Running** state.

|Yes|
|Locked|Stopped|Stable|If you have an overdue payment in your account or if your account is insecure, your instance enters the Locked state. You can submit a ticket to unlock the instance.|Yes|
|To Be Released|Stopped|Stable|If you apply for a refund for a subscription instance before the instance expires, the instance enters the To Be Released state.

|Yes|

## Instance status in API responses

You can call the [DescribeInstanceStatus](/intl.en-US/API Reference/Instances/DescribeInstanceStatus.md) or [DescribeInstances](/intl.en-US/API Reference/Instances/DescribeInstances.md) operation to query the instance status. The following figure shows the transition between instance statuses in API responses.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4103993851/p5105.png)

