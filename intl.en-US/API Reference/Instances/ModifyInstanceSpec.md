# ModifyInstanceSpec

You can call this operation to change the instance type and public bandwidth of a pay-as-you-go instance.

## Description

For more information about the SDK for Python used to change resource configurations, see [Query available resources for configuration changes](~~109517~~).

When you call this operation, take note of the following points:

-   The account must have no overdue payments.
-   You can change the public bandwidth only when the instance is in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) state.
-   Before you change the instance type of the pay-as-you-go instance, you can call the [DescribeResourcesModification](~~66187~~) operation to query the instance types to which you can change.
-   You can change the instance type only when the instance is in the **Stopped** \(`Stopped`\) state.
-   You can only change either the instance type or the public bandwidth each time.
-   After a successful modification, you must wait five minutes before you can initiate another modification.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceSpec&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceSpec|The operation that you want to perform. If you use a custom HTTP URL or HTTPS URL to make an API request, you must specify the `Action` parameter. Set the value to ModifyInstanceSpec. |
|InstanceId|String|Yes|i-bp67acfmxazb4ph\*\*\*|The ID of the specified instance. |
|InstanceType|String|No|ecs.g5.large|The target instance type. For more information, see [Instance type families](~~25378~~) or call the [DescribeInstanceTypes](~~25620~~) operation to query the most recent instance type list. |
|InternetMaxBandwidthOut|Integer|No|10|The maximum outbound public bandwidth. Unit: Mbit/s. Valid values: 0 to 100.

**Note:** The bandwidth that you specify when the pay-by-traffic billing method is used is the peak outbound bandwidth. In the event of resource contention, this bandwidth cannot be guaranteed. If you want a guaranteed bandwidth for your instance, use the pay-by-bandwidth billing method. |
|InternetMaxBandwidthIn|Integer|No|10|The maximum inbound public bandwidth. Unit: Mbit/s. Valid values:

-   When the purchased outbound bandwidth is less than 10 Mbit/s: 1 to 10. Default value: 10.
-   When the purchased outbound bandwidth is greater than 10 Mbit/s: 1 to the value of `InternetMaxBandwidthOut`. The `InternetMaxBandwidthOut` value is used by default. |
|Temporary.StartTime|String|No|2017-12-05T22:40:00Z|The start time of the temporary bandwidth upgrade. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|Temporary.EndTime|String|No|2017-12-05T22:40:00Z|The end time of the temporary bandwidth upgrade. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|Temporary.InternetMaxBandwidthOut|Integer|No|50|The maximum outbound public bandwidth after temporary bandwidth upgrade. Valid values: 1 to 100.

**Note:** We recommend that you use other parameters to ensure future compatibility. |
|Async|Boolean|No|false|Specifies whether to submit an asynchronous request.

Default value: false. |
|AllowMigrateAcrossZone|Boolean|No|false|Specifies whether to enable cross-cluster instance type upgrade.

Default value: false.

When `AllowMigrateAcrossZone` is set to true and you have updated the ECS instance based on the responses, take note of the following points:

Instances in the classic network:

-   For [phased-out instance types](~~55263~~), when a non-I/O optimized instance is upgraded to an I/O optimized instance, the private IP address, driver name, and software authorization code are modified. For Linux instances, basic disks \(`cloud`\) are identified as **xvda** or **xvdb**, and ultra disks \(`cloud_efficiency`\) and standard SSDs \(`cloud_ssd`\) are identified as **vda** or **vdb**.
-   For [instance families available on the Alibaba Cloud market](~~25378~~), the private IP address is modified after instance type upgrade.

Instances in VPCs: For [phased-out instance types](~~55263~~), when a non-I/O optimized instance is upgraded to an I/O optimized instance, the driver name and software authorization code are modified. For Linux instances, basic disks \(`cloud`\) are identified as **xvda** or **xvdb**, and ultra disks \(`cloud_efficiency`\) and standard SSDs \(`cloud_ssd`\) are identified as **vda** or **vdb**. |
|SystemDisk.Category|String|No|cloud\_ssd|The category of the system disk. This parameter is valid only when you upgrade one of the [phased-out instance types](~~55263~~) to one of the [instance families available on the Alibaba Cloud market](~~25378~~) and upgrade a non-I/O optimized instance to an I/O optimized instance. Valid values:

-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD |
|ClientToken|String|No|0c593ea1-3bea-11e9-b96b-88e9fe637760|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value can only contain ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceSpec
&InstanceId=i-bp67acfmxazb4ph***
&InstanceType=ecs.s1.large
&InternetMaxBandwidthOut=10
&ClientToken=0c593ea1-3bea-11e9-b96b-88e9fe637760
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceSpecResponse>
     <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceSpecResponse>
```

`JSON` format

```
{
   "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|The error message returned because the specified InternetChargeType parameter does not exist.|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type does not exist or you are not authorized to manage instances of this instance type.|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|The error message returned because you are not authorized to use the specified instance type.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist. Check whether the instance ID is correct.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type does not exist or you are not authorized to manage instances of this instance type.|
|400|InvalidParameter|The specified parameter "InternetMaxBandwidthOut" is not valid.|The error message returned because the specified InternetMaxBandwidthOut parameter is invalid.|
|400|InvalidParameter.Mismatch|Too many parameters in one request.|The error message returned because the request contains invalid parameters.|
|403|CategoryViolation|The specified instance does not support this operation because of its disk category.|The error message returned because the instance types of instances that are attached with local disks cannot be changed.|
|403|InvalidStatus.ValueNotSupported|The current status of the resource does not support this operation.|The error message returned because this operation is not supported while the resource is in the current state.|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. You must top up your account before proceeding.|
|403|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|The error message returned because the billing method of the instance does not support this operation.|
|403|OperationDenied|The specified instance is out of usage.|The error message returned because the specified instance is out of stock.|
|400|BandwidthUpgradeDenied.EipBoundInstance|The specified VPC instance has bound EIP, temporary bandwidth upgrade is denied.|The error message returned because the instance is associated with an Elastic IP address \(EIP\) and the instance bandwidth cannot be temporarily upgraded.|
|404|MissingTemporary.StartTime|Temporary.StartTime is not specified.|The error message returned because the Temporary.StartTime parameter is not specified.|
|404|MissingTemporary.EndTime|Temporary.EndTime is not specified.|The error message returned because the Temporary.EndTime parameter is not specified.|
|400|InvalidTemporary.StartTime|The specifed Temporary.StartTime is not valid.|The error message because the specified Temporary.StartTime parameter is invalid.|
|400|InvalidTemporary.EndTime|The specifed Temporary.EndTime is not valid.|The error message returned because the specified Temporary.EndTime parameter is invalid.|
|403|LastTokenProcessing|The last token request is processing.|The error message returned because the last token request is being processed. Try again later.|
|400|Downgrade.NotSupported|Downgrade operation is not supported.|The error message returned because the downgrade operation is not supported.|
|403|InstanceSpecModification.NotEffective|The specified instance has been reserved for making a spec modification and not taken effective in the current contract period.|The error message returned because the instance is reserved due to specification changes. The changes cannot take effect during the current contract period.|
|400|DependencyViolation.InstanceType|The current InstanceType cannot be changed to the specified InstanceType.|The error message returned because the current instance cannot be changed to an instance of the specified instance type.|
|403|InvalidInstanceType.ValueNotSupported|The specified zone does not offer the specified instancetype.|The error message returned because instances of the specified instance type are unavailable in the specified region.|
|403|ImageNotSupportInstanceType|The specified image do not support the InstanceType instance.|The error message returned because the specified image does not support instances of the specified instance type.|
|400|Account.Arrearage|Your account has an outstanding payment.|The error message returned because your account has an overdue payment.|
|400|InvalidParameter.Bandwidth|The specified parameter Bandwidth is not valid.|The error message returned because the specified Bandwidth parameter is invalid.|
|400|InvalidParameter.Conflict|The specified image does not support the specified instance type.|The error message returned because the specified image cannot be used for instances of the specified instance type.|
|400|InvalidParameter.AllowMigrateAcrossZone|The specified parameter CanMigrateAcrossZone is not valid.|The error message returned because the specified AllowMigrateAcrossZone parameter is invalid.|
|400|InvalidParam.SystemDiskCategory|The specified param SystemDisk.Category is not valid.|The error message returned because the specified SystemDisk.Category parameter is invalid.|
|400|Throttling|Request was denied due to request throttling, please try again after 5 minutes.|The error message returned because your request is throttled. Try again five minutes later.|
|400|InvalidInstanceStatus.NotStopped|The specified Instance status is not stopped.|The error message returned because the specified instance is not in the Stopped state.|
|403|InstanceType.Offline|The specified InstanceType has been offline|The error message returned because the specified instance type is phased-out. Select instances of other instance types and try again.|
|400|InvalidAction|Specified action is not valid.|The error message returned because this operation is invalid.|
|400|IdempotenceParamNotMatch|There is a idempotence signature mismatch between this and last request.|The error message returned because the idempotence signature of this request does not correspond to that of the last request.|
|400|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|The error message returned because the specified ClientToken parameter is invalid.|
|400|Price.PricePlanResultNotFound|The internetMaxBandwidthIn or internetMaxBandwidthOut provided is invalid.|The error message returned because specified internetMaxBandwidthIn or internetMaxBandwidthOut parameter is invalid.|
|403|InvalidParameter.NotMatch|%s|The error message returned because the specified parameter is invalid. Check whether the parameter conflicts with another parameter.|
|403|InvalidInstance.EipNotSupport|The specified instance with eip is not supported, please unassociate eip first.|The error message returned because the operation is not supported while an EIP is associated to this instance. Disassociate the EIP first.|
|400|InvalidAction.NotSupport|The ecs on dedicatedHost not support modify instanceType.|The error message returned because you cannot change the instance type of instances on the dedicated host.|
|400|InvalidMarketImageStatus.NotSupported|The status of specified market image does not support this operation.|The error message returned because this operation is not supported while the specified Alibaba Cloud Marketplace image is in the current state.|
|403|OperationDenied.NoStock|The resource is out of usage.|The error message returned because the instance is not in the Running state. Start the instance or check whether the operation is valid.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|OperationDenied|%s|The error message returned because the operation is denied.|
|403|InvalidOperation.Ipv4CountExceeded|%s|The error message returned because the maximum number of IPv4 addresses has been reached.|
|403|InvalidOperation.Ipv6CountExceeded|%s|The error message returned because the maximum number of IPv6 addresses has been reached.|
|403|InvalidOperation.Ipv6NotSupport|%s|The error message returned because the IPv6 address does not support the current operation.|
|403|InvalidOperation.InstanceWithEipNotSupport|The special instance with eip not support operate, please unassociate eip first.|The error message returned because the operation is not supported while an EIP is associated to this instance. Disassociate the EIP first.|
|403|SecurityRisk.3DVerification|We have detected a security risk with your default credit or debit card. Please proceed with verification via the link in your email.|The error message returned because risks are detected in your default credit card or debit card. Click the link in the email for verification.|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|The error message returned because the specified InstanceChargeType parameter does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

