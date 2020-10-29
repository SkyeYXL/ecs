# ModifyInstanceNetworkSpec

You can call this operation to modify the bandwidth configurations of an instance. You can modify the bandwidth configurations of an instance to improve network performance if necessary.

## Description

When you call this operation, take note of the following points:

-   When you modify the bandwidth configurations of a subscription \(PrePaid\) instance, you can perform the following operations:
    -   You can upgrade or downgrade the bandwidth billed in the pay-by-traffic \(PayByTraffic\) method. You can only upgrade the bandwidth billed in the pay-by-bandwidth \(PayByBandwidth\) method.
    -   When you upgrade the outbound public bandwidth \(`InternetMaxBandwidthOut`\) from 0 Mbit/s, a public IP address will be assigned to the instance.
    -   You can call the ModifyInstanceNetworkSpec operation to change the bandwidth billing method from pay-by-traffic \(PayByTraffic\) to pay-by-bandwidth \(PayByBandwidth\).
    -   You can use only the [ECS console](https://ecs.console.aliyun.com) to change the bandwidth billing method from pay-by-bandwidth \(PayByBandwidth\) to pay-by-traffic \(PayByTraffic\).
-   When you modify the bandwidth configurations of a pay-as-you-go \(PostPaid\) instance, you can perform the following operations:
    -   You can upgrade or downgrade the bandwidth.
    -   When the outbound public bandwidth is upgraded from 0 Mbit/s, no public IP address is allocated. You must call the [AllocatePublicIpAddress](~~25544~~) operation to allocate a public IP address to the instance.
    -   You can change the bandwidth billing method from pay-by-traffic \(PayByTraffic\) to pay-by-bandwidth \(PayByBandwidth\).
    -   You can change the bandwidth billing method from pay-by-bandwidth \(PayByBandwidth\) to pay-by-traffic \(PayByTraffic\).
-   For an instance in the classic network, when the outbound public bandwidth \(InternetMaxBandwidthOut\) is upgraded from 0 Mbit/s, the instance must be in the Stopped state.
-   After the bandwidth is upgraded, AutoPay is set to true by default. Make sure that your account has sufficient balance. Otherwise, your order becomes invalid and you have to cancel this order. If your account balance is insufficient, you can set the AutoPay parameter to false to generate an unpaid order. Then, you can log on to the ECS console to pay for the order.
-   You can downgrade the public bandwidth of each subscription instance for a maximum of three times. Therefore, a maximum of three refunds for price difference can be made.
-   The price difference will be refunded to the payment account you used. Used coupons cannot be refunded.
-   Each time a modification of bandwidth configurations succeeds, you cannot modify the bandwidth of the instance within five minutes.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceNetworkSpec&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceNetworkSpec|The operation that you want to perform. Set the value to ModifyInstanceNetworkSpec. |
|InstanceId|String|Yes|i-bp67acfmxazb4ph\*\*\*|The ID of the instance for which you want to modify network configurations. |
|InternetMaxBandwidthOut|Integer|No|10|The maximum outbound public bandwidth. Unit: Mbit/s. Valid values: 0 to 100.

**Note:** The bandwidth that you specify when the pay-by-traffic billing method is used is the peak outbound bandwidth. In the event of resource contention, this bandwidth cannot be guaranteed. If you want a guaranteed bandwidth for your instance, use the pay-by-bandwidth billing method. |
|InternetMaxBandwidthIn|Integer|No|10|The maximum inbound public bandwidth. Unit: Mbit/s. Valid values:

-   If the purchased outbound bandwidth is less than 10 Mbit/s, valid values are 1 to 10. Default value: 10.
-   If the purchased outbound bandwidth is greater than 10 Mbit/s, valid values are 1 to the value of `InternetMaxBandwidthOut`. Default value: the value of `InternetMaxBandwidthOut`. |
|NetworkChargeType|String|No|PayByTraffic|The billing method for network usage. Valid values:

-   PayByBandwidth
-   PayByTraffic

**Note:** The bandwidth that you specify when the pay-by-traffic billing method is used is the peak outbound bandwidth. In the event of resource contention, this bandwidth cannot be guaranteed. If you want a guaranteed bandwidth for your instance, use the pay-by-bandwidth billing method. |
|AllocatePublicIp|Boolean|No|false|Specifies whether to allocate a public IP address.

Default value: false. |
|StartTime|String|No|2017-12-05T22:40Z|The start time of the temporary bandwidth upgrade. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddThh:mmZ format. The time must be in UTC and accurate to **minutes** \(mm\). |
|EndTime|String|No|2017-12-06T22Z|The end time of the temporary bandwidth upgrade. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddThhZ format. The time must be in UTC and accurate to **hours** \(hh\). |
|AutoPay|Boolean|No|true|Specifies whether to enable automatic payment. Valid values:

-   true: After the bandwidth is upgraded, the payment is automatically made. Make sure that your account has sufficient balance when you set Autopay to true. If your account has insufficient balance, your order cannot be paid in the ECS console and becomes invalid. You have to cancel it.
-   false: After the bandwidth is upgraded, an order is generated but it is not paid. If your account balance is insufficient, you can set AutoPay to false to generate an unpaid order. Then, you can log on to the [ECS console](https://ecs.console.aliyun.com) to pay for the order.

Default value: true. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value can only contain ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|OrderId|String|1111111111111111111111110|The ID of the generated order. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceNetworkSpec
&InstanceId=i-bp67acfmxazb4ph***
&InternetMaxBandwidthOut=10
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceNetworkSpecResponse>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
        <OrderId>1111111111111111111111110</OrderId>
</ModifyInstanceNetworkSpecResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "OrderId": "1111111111111111111111110"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist. Check whether the instance ID is correct.|
|400|InvalidInternetMaxBandwidthIn.ValueNotSupported|The specified InternetMaxBandwidthIn is beyond the permitted range.|The error message returned because the specified value of the InternetMaxBandwidthIn parameter is not within the permitted range.|
|400|InvalidInternetMaxBandwidthOut.ValueNotSupported|The specified InternetMaxBandwidthOut is beyond the permitted range.|The error message returned because the specified value of the InternetMaxBandwidthOut parameter is not within the permitted range.|
|403|IncorrectInstanceStatus|The current status of the instance does not support this operation.|The error message returned because this operation is not supported while the instance is in the current state.|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|The error message returned because the subscription of the instance has expired. Renew the instance and try again.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|ChargeTypeViolation|The operation is not permitted due to billing method of the instance.|The error message returned because this operation is not supported by the billing method.|
|403|OperationDenied|The operation is denied due to the instance is PrePaid.|The error message returned because the instance is a subscription instance.|
|400|OperationDenied|Specified instance is in VPC.|The error message returned because the specified instance is in a VPC.|
|400|InvalidParameter.Bandwidth|%s|The error message returned because the specified Bandwidth parameter is invalid.|
|400|InvalidParameter.Conflict|%s|The error message returned because the specified parameter is invalid. Check whether the parameter conflicts with other parameters.|
|400|InvalidStartTime.ValueNotSupported|%s|The error message returned because the end time is earlier than the start time.|
|400|Account.Arrearage|Your account has an outstanding payment.|The error message returned because your account has an overdue payment.|
|400|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is invalid.|The error message returned because the specified InstanceChargeType parameter is invalid.|
|400|DecreasedBandwidthNotAllowed|%s|The error message returned because the bandwidth cannot be downgraded.|
|400|BandwidthUpgradeDenied.EipBoundInstance|The specified VPC instance has bound EIP, temporary bandwidth upgrade is denied.|The error message returned because the instance is associated with an EIP and the instance bandwidth cannot be temporarily upgraded.|
|400|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|The error message returned because the specified ClientToken parameter is invalid.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. You must top up your account before proceeding.|
|403|InvalidInstance.UnPaidOrder|The specified Instance has unpaid order.|The error message returned because you have unpaid orders for the specified instance. Pay for the orders and try again.|
|400|Throttling|Request was denied due to request throttling, please try again after 5 minutes.|The error message returned because your current request is denied due to throttling. Try again five minutes later.|
|400|InvalidAction|Specified action is not valid.|The error message returned because this operation is invalid.|
|400|IpAllocationError|Allocate public ip failed.|The error message returned because the allocation of public IP addresses fails.|
|400|InvalidParam.AllocatePublicIp|The specified param AllocatePublicIp is invalid.|The error message returned because the specified AllocatePublicIp parameter is invalid.|
|400|InstanceDowngrade.QuotaExceed|Quota of instance downgrade is exceed.|The error message returned because the quota of the instance downgrade is exceeded and the operation is denied.|
|400|InvalidBandwidth.ValueNotSupported|Instance upgrade bandwidth of temporary not allow less then existed.|The error message returned because the target bandwidth for the temporary upgrade is lower than the current bandwidth.|
|403|InvalidInstance.InstanceNotSupported|The special vpc instance with eip not need bandwidth.|The error message returned because the VPC-type instance is associated with an EIP and you cannot specify the public bandwidth for the instance.|
|400|InvalidInstanceStatus|The specified instance status does not support this action.|The error message returned because this operation is not supported while the instance is in the current state.|
|403|InvalidInstanceStatus|The current status of the instance does not support this operation.|The error message returned because this operation is not supported while the instance is in the current state.|
|400|InvalidInstance.UnPaidOrder|Unpaid order exists in your account, please complete or cancel the payment in the expense center.|The error message returned because you have unpaid orders in your account. Pay for the orders and try again.|
|400|OperationDenied|After downgrade, you cannot upgrade or downgrade your instances again in the remaining time of the current billing cycle.|The error message returned because you cannot upgrade or downgrade your instance specifications after the downgrade until a new billing cycle begins.|
|400|InvalidInternetChargeType.ValueNotSupported|%s|The error message returned because the specified InternetChargeType parameter is invalid.|
|400|LastOrderProcessing|The previous order is still processing, please try again later.|The error message returned because the previous order is being processed. Try again later.|
|400|OperationDenied|The current user does not support this operation.|The error message returned because your account does not support this operation.|
|403|NAT\_PUBLIC\_IP\_BINDING\_FAILED|Binding nat public ip failed|The error message returned because the public IP address failed to be bound to the gateway.|
|403|InvalidInstance.EipNotSupport|The specified instance with eip is not supported, please unassociate eip first.|The error message returned because the operation is not supported while an EIP is associated with this instance. Disassociate the EIP first.|
|403|InvalidNetworkType.ValueNotSupported|The specified parameter NetworkType is not valid.|The error message returned because the specified network type is invalid.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

