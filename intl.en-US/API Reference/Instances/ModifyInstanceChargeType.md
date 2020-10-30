# ModifyInstanceChargeType

You can call this operation to change the billing method of one or more ECS instances. You can change the billing methods of instances between pay-as-you-go and subscription, or change the billing method of all data disks attached to an instance from pay-as-you-go to subscription.

## Description

Before you call this operation, make sure that you have fully understood the billing methods and pricing schedule of [ECS](https://www.alibabacloud.com/product/ecs#pricing).

When you call this operation, take note of the following items:

-   The instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) state and has no overdue payments.
-   After you change the billing method, automatic payment is enabled by default. Make sure that you have sufficient balance in your account. Otherwise, your order becomes invalid and must be canceled. If your account balance is insufficient, you can set `AutoPay` to `false`. Then, an order is generated. You can log on to the [ECS console](https://ecs.console.aliyun.com/) to pay for it.
-   **Change the billing method from subscription to pay-as-you-go**:
    -   Whether you can change the billing method depends on your ECS usage.
    -   After you change the billing method from subscription to pay-as-you-go, the new billing method takes effect for the entire lifecycle of the instance. The price difference is refunded to the payment account you used. Price differences of coupon purchases are not refunded.
    -   **Refund rule**: You can apply for only a certain quota of refund within a month, and the refund quota that is not used within the current month is not accumulated to the next month. After you have used up the refund quota for the current month, you can only change the billing method when the next month arrives. The refund amount incurred when you change the billing method is calculated based on the following formula: **Number of vCPUs × \(Number of remaining days × 24 ± Number of remaining or elapsed hours\)**.
-   **Change the billing method from pay-as-you-go to subscription**:
    -   You can change all pay-as-you-go data disks attached to an instance to subscription ones.
    -   This operation cannot be called if the automatic release time has been set for a pay-as-you-go instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceChargeType&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceChargeType|The operation that you want to perform. Set the value to ModifyInstanceChargeType. |
|InstanceIds|String|Yes|\["i-bp67acfmxazb4p\*\*\*\*","i-bp67acfmxazb4d\*\*\*\*"\]|The IDs of the instances. The value can be a JSON array that consists of up to 20 instance IDs. Separate multiple instance IDs with commas \(,\). |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Period|Integer|No|1|The renewal period of the subscription instance. If the ECS instance is hosted on a dedicated host, the renewal period of the ECS instance cannot exceed the subscription period of the dedicated host. Valid values:

-   When the `PeriodUnit` parameter is set to Month, valid values of the `Period` parameter are 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60. |
|PeriodUnit|String|No|Month|The unit of the renewal duration \(`Period`\). Default value: Month. Valid values:

-   Month |
|IncludeDataDisks|Boolean|No|false|Specifies whether to change all pay-as-you-go data disks attached to the instance to subscription ones.

Default value: false. |
|DryRun|Boolean|No|false|Specifies whether to check the validity of the request without actually making the request. Default value: false. Valid values:

-   true: The validity of the request is checked but resources are not queried. The system checks whether your AccessKey pair is valid, whether RAM users are authorized, and whether required parameters are specified. If the request fails the check, the corresponding error code is returned. If the request is determined as valid, the `DryRunOperation` error code is returned.
-   false: The validity of the request is checked. If the request is determined as valid, a 2XX HTTP status code is returned and the request is made. |
|AutoPay|Boolean|No|false|Specifies whether to enable automatic payment. Default value: true. Valid values:

-   true: Automatic payment is enabled. Make sure that you have sufficient balance in your account. Otherwise, your order becomes invalid and must be canceled.
-   false: An order is generated but no payment is made.

**Note:** If your account balance is insufficient, you can set the AutoPay parameter to false to prevent your order from becoming invalid. Then, you can log on to the ECS console to pay for the order. |
|InstanceChargeType|String|No|PrePaid|The new billing method. Default value: PrePaid. Valid values:

-   PrePaid: changes the billing method from pay-as-you-go to subscription.
-   PostPaid: changes the billing method from subscription to pay-as-you-go. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must make sure that it is unique among different requests. The **ClientToken** value must contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|IsDetailFee|Boolean|No|false|Specifies whether to return cost details of the order when the billing method is changed from subscription to pay-as-you-go.

Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|FeeOfInstances|Array of FeeOfInstance| |Details about the cost of the order. |
|FeeOfInstance| | | |
|Currency|String|CNY|The unit of currency for the bill. |
|Fee|String|0|The cost value. |
|InstanceId|String|i-bp67acfmxazb4p\*\*\*\*|The ID of the instance. |
|OrderId|String|20413515388\*\*\*\*|The ID of the generated order. |
|RequestId|String|B61C08E5-403A-46A2-96C1-F7B1216DB10C|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceChargeType
&RegionId=cn-hangzhou
&InstanceIds=["i-bp67acfmxazb4p****","i-bp67acfmxazb4d****"]
&Period=1
&PeriodUnit=Month
&AutoPay=false
&IncludeDataDisks=false
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceChargeTypeResponse>
      <RequestId>B61C08E5-403A-46A2-96C1-F7B1216DB10C</RequestId>
      <OrderId>20413515388****</OrderId>
      <FeeOfInstances>
            <FeeOfInstance>
                  <Fee>0</Fee>
                  <InstanceId>i-bp67acfmxazb4p****</InstanceId>
                  <Currency>CNY</Currency>
            </FeeOfInstance>
            <FeeOfInstance>
                  <Fee>0</Fee>
                  <InstanceId>i-bp67acfmxazb4d****</InstanceId>
                  <Currency>CNY</Currency>
            </FeeOfInstance>
      </FeeOfInstances>
</ModifyInstanceChargeTypeResponse>
```

`JSON` format

```
{
    "RequestId":"B61C08E5-403A-46A2-96C1-F7B1216DB10C",
    "OrderId":"20413515388****",
    "FeeOfInstances":
    {
        "FeeOfInstance":[
            {
                "Fee":"0",
                "InstanceId":"i-bp67acfmxazb4p****",
                "Currency":"CNY"
            },
            {
                "Fee":"0",
                "InstanceId":"i-bp67acfmxazb4d****",
                "Currency":"CNY"
            }
        ]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter.InstanceIds|The specified InstanceIds are invalid.|The error message returned because the specified InstanceIds parameter is invalid.|
|400|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|400|InvalidStatus.ValueNotSupported|%s|The error message returned because the operation is not supported while the resource is in the current state.|
|400|InvalidInstanceChargeType.ValueNotSupported|%s|The error message returned because the specified InstanceChargeType parameter is not supported. Check related information and try again.|
|400|ExpiredInstance|The specified instance has expired.|The error message returned because the specified instance has expired.|
|403|InvalidInstance.TempBandwidthUpgrade|Cannot switch to Pay-As-You-Go during the period of temporary bandwidth upgrade.|The error message returned because you cannot change the billing method to pay-as-you-go when the bandwidth is being temporarily upgraded.|
|400|InstancesIdQuotaExceed|The maximum number of Instances is exceeded.|The error message returned because the maximum number of instances has been reached.|
|400|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|The error message returned because the specified client token is invalid.|
|400|InvalidInternetChargeType.ValueNotSupported|%s|The error message returned because the specified InternetChargeType parameter is not supported. Check whether the parameter is correct.|
|403|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type does not exist or you are not authorized to manage instances of this instance type.|
|403|InstanceType.Offline|%s|The error message returned because the instance type is retired or instances of this instance type are insufficient.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|ReleaseTimeHaveBeenSet|The specified instance has been set released time.|The error message returned because the automatic release time has been set for the specified instance.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. Add funds to your account before you proceed.|
|403|Account.Arrearage|Your account has an outstanding payment.|The error message returned because you have overdue payments in your account.|
|400|Throttling|Request was denied due to request throttling, please try again after 5 minutes.|The error message returned because your request is denied due to throttling. Try again five minutes later.|
|403|InvalidParameter.NotMatch|%s|The error message returned because the specified parameter is invalid. Check whether the parameter conflicts with another parameter.|
|403|InvalidAction|%s|The error message returned because this operation is invalid.|
|400|Throttling|%s|The error message returned because the request is denied due to throttling.|
|400|QuotaExceed.AfterpayInstance|The maximum number of Pay-As-You-Go instances is exceeded: %s|The error message returned because the pay-as-you-go instances of the specified instance type are insufficient. Reduce the number of instances to be created.|
|400|InvalidParameter.Bandwidth|%s|The error message returned because the specified bandwidth is invalid.|
|400|InvalidPeriod.UnitMismatch|The specified Period must be correlated with the PeriodUnit.|The error message returned because the specified Period parameter is not associated with PeriodUnit.|
|400|InvalidImageType.NotSupported|%s|The error message returned because the specified image type is invalid. Check whether this image type is supported in the region.|
|400|InvalidPeriod.ExceededDedicatedHost|Instance expired date can't exceed dedicated host expired date.|The error message returned because the expiration date of the instance is later than that of the dedicated host.|
|400|InvalidMarketImageChargeType.NotSupport|The specified chargeType of marketImage is unsupported.|The error message returned because the billing method of the Alibaba Cloud Marketplace image is not supported.|
|403|QuotaExceed.PostPaidDisk|Living postPaid disks quota exceeded.|The error message returned because the maximum number of pay-as-you-go disks has been reached.|
|403|ImageNotSupportInstanceType|The specified instanceType is not supported by instance with marketplace image.|The error message returned because the specified Alibaba Cloud Marketplace image does not support the instance type.|
|403|InvalidInstanceType.PhasedOut|This instanceType is no longer offered.|The error message returned because the specified instance type is no longer available.|
|400|InvalidSystemDiskCategory.ValueNotSupported|%s|The error message returned because the operation is not supported by the specified system disk category.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|RealNameAuthenticationError|Your account has not passed the real-name authentication yet.|The error message returned because you have not completed real-name verification. Complete real-name verification and try again.|
|403|QuotaExceed.ElasticQuota|No additional quota is available for the specified ECS instance type.|The error message returned because the maximum number of instances of the specified instance type that can be created in the current region has been reached. Try another region or instance type, or reduce the purchase quantity. You can also go to the ECS console or Quota Center to request a quota increase.|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type.|The error message returned because the maximum number of instances of the specified instance type that can be created in the current region has been reached. Try another region or instance type, or reduce the purchase quantity. You can also go to the ECS console or Quota Center to request a quota increase.|
|403|QuotaExceed.ElasticQuota|The number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|The error message returned because the maximum number of vCPUs for all instance types has been reached. Go to the ECS console or Quota Center to request a quota increase.|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type, or the number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|The error message returned because the maximum number of instances of the specified instance type that can be created in the current region has been reached, or because the maximum number of vCPUs for all instance types has been reached. Go to the ECS console or Quota Center to request a quota increase.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

