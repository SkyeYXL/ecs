# DeleteNetworkInterface

You can call this operation to delete an Elastic Network Interface \(ENI\).

## Description

-   The ENI must be in the Available \(Available\) state.
-   If the ENI is already attached to an ECS instance, you can delete the ENI only after it is detached from the ECS instance \([DetachNetworkInterface](~~58514~~)\).
-   After an ENI is deleted:
    -   The primary private IP address of the ENI is automatically released.
    -   The deleted ENI is automatically removed from all security groups to which the ENI was added.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteNetworkInterface&type=RPC&version=2014-05-26)

## Request Parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|NetworkInterfaceId|String|Yes|eni-bp14v2sdd3v8htlnm\*\*\*|The ID of the ENI. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the ENI. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Action|String|Yes|DeleteNetworkInterface|The operation that you want to perform. Set the value to DeleteNetworkInterface. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|F3CD6886-D8D0-4FEE-B93E-1B73239673DE|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteNetworkInterface
&NetworkInterfaceId=eni-bp14v2sdd3v8htlnm***
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteNetworkInterfaceResponse>
      <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</DeleteNetworkInterfaceResponse>
```

`JSON` format

```
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidUserType.NotSupported|%s|The error message returned because your account type is not supported.|
|403|Abs.InvalidAccount.NotFound|%s|The error message returned because your Alibaba Cloud account does not exist or your AccessKey pair has expired.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|Forbidden.NotSupportRAM|%s|The error message returned because RAM users are not allowed to perform this operation.|
|400|UnsupportedParameter|%s|The error message returned because the specified parameter is not supported.|
|403|Forbidden.SubUser|%s|The error message returned because the RAM user is not authorized to perform operations on this resource.|
|400|InvalidParameter|%s|The error message returned because the parameter is invalid.|
|400|InvalidInstanceID.Malformed|%s|The error message returned because the InstanceId parameter is invalid.|
|400|InvalidOperation.InvalidEcsState|%s|The error message returned because the private IP address cannot be released while the instance is in the current state.|
|400|InvalidOperation.InvalidEniState|%s|The error message returned because the private IP address cannot be released while the ENI is in the current state.|
|400|InvalidOperation.DetachPrimaryEniNotAllowed|%s|The error message returned because primary ENIs cannot be detached from their instances.|
|404|InvalidEcsId.NotFound|%s|The error message returned because the specified instance ID does not exist.|
|404|InvalidEniId.NotFound|%s|The error message returned because the specified ENI ID does not exist.|
|404|InvalidVSwitchId.NotFound|%s|The error message returned because the specified VSwitch ID does not exist.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|MaxEniCountExceeded|%s|The error message returned because the maximum number of ENIs that can be managed has been reached.|
|403|EniPerInstanceLimitExceeded|%s|The error message returned because the maximum number of ENIs for the specified instance type has been reached.|
|403|InvalidOperation.AvailabilityZoneMismatch|%s|The error message returned because the specified VSwitch, ENI, and instance do not belong to the same zone.|
|403|InvalidOperation.VpcMismatch|%s|The error message returned because the specified ENI and security group do not belong to the same VPC.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|403|InvalidSecurityGroupId.NotVpc|%s|The error message returned because the specified security group is not of the VPC type.|
|403|InvalidOperation.InvalidEniType|%s|The error message returned because the ENI type does not support the operation.|
|400|Forbidden.RegionId|%s|The error message returned because this feature is not supported in the region.|
|400|InvalidParams.EniId|%s|The error message returned because the format of the specified ENI ID is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

