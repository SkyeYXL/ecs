# UnassignPrivateIpAddresses

You can call this operation to unassign one or more secondary private IP addresses from an elastic network interface \(ENI\).

## Description

-   The ENI from which you want to unassign private IP addresses must be in the **Available** \(Available\) or **InUse** \(InUse\) state.
-   When you perform this operation on the primary ENI, the instance to which the ENI is bound must be in the **Running** \(Running\) or **Stopped** \(Stopped\) state.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=UnassignPrivateIpAddresses&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UnassignPrivateIpAddresses|The operation that you want to perform. Set the value to UnassignPrivateIpAddresses. |
|NetworkInterfaceId|String|Yes|eni-bp67acfmxazb4ph\*\*\*\*|The ID of the ENI. |
|PrivateIpAddress.N|RepeatList|Yes|192.168.\*\*. \*\*|The secondary private IP addresses to be unassigned. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the ENI. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=UnassignPrivateIpAddresses
&NetworkInterfaceId=eni-bp67acfmxazb4ph****
&PrivateIpAddress.1=192.168. **. **
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UnassignPrivateIpAddressesResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE70008</RequestId>
</UnassignPrivateIpAddressesResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE70008"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidUserType.NotSupported|%s|The error message returned because your account does not support this operation.|
|403|Abs.InvalidAccount.NotFound|%s|The error message returned because your Alibaba Cloud account does not exist or your AccessKey pair has expired.|
|403|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|Forbidden.NotSupportRAM|%s|The error message returned because RAM users are not authorized to perform this operation.|
|400|UnsupportedParameter|%s|The error message returned because a specified parameter is not supported.|
|403|Forbidden.SubUser|%s|The error message returned because your account is not authorized to manage the specified resource. Contact the owner of the Alibaba Cloud account for authorization.|
|400|InvalidParameter|%s|The error message returned because a specified parameter is invalid.|
|400|InvalidInstanceID.Malformed|%s|The error message returned because the specified InstanceId parameter is invalid.|
|400|InvalidOperation.InvalidEcsState|%s|The error message returned because the operation is not supported while the instance is in the current state.|
|400|InvalidOperation.InvalidEniState|%s|The error message returned because the operation is not supported while the ENI is in the current state.|
|400|InvalidOperation.DetachPrimaryEniNotAllowed|%s|The error message returned because you cannot unbind the primary ENI from the instance.|
|404|InvalidEcsId.NotFound|%s|The error message returned because the specified instance ID does not exist.|
|404|InvalidEniId.NotFound|%s|The error message returned because the specified NetworkInterfaceId parameter does not exist.|
|404|InvalidVSwitchId.NotFound|%s|The error message returned because the specified VSwitch ID does not exist.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|MaxEniCountExceeded|%s|The error message returned because the maximum number of ENIs that can be managed has been reached.|
|403|EniPerInstanceLimitExceeded|%s|The error message returned because the maximum number of ENIs that can be bound to the specified instance has been reached.|
|403|InvalidOperation.AvailabilityZoneMismatch|%s|The error message returned because the operation is invalid.|
|403|InvalidOperation.VpcMismatch|%s|The error message returned because the operation is invalid. Check whether the VPC in the operation corresponds to other parameters.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|403|InvalidSecurityGroupId.NotVpc|%s|The error message returned because the specified SecurityGroupId parameter is invalid and the security group is not of the VPC type.|
|403|InvalidOperation.InvalidEniType|%s|The error message returned because the operation is not supported by the ENI type.|
|404|InvalidInstanceId.NotFound|%s|The error message returned because the specified instance does not exist.|
|403|InvalidVSwitchId.IpInvalid|%s|The error message returned because the specified private IP address is invalid.|
|403|InvalidIp.IpUnassigned|%s|The error message returned because the specified IP address is not assigned.|
|403|Operation.Conflict|%s|The error message returned because this operation conflicts with another operation in progress. Try again later.|
|400|Forbidden.RegionId|%s|The error message returned because the service is not available in the current region.|
|400|InvalidAction|%s|The error message returned because the operation is invalid.|
|403|InvalidOperation.EniServiceManaged|%s|The error message returned because the operation is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

