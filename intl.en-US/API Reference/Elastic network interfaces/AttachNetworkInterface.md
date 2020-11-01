# AttachNetworkInterface

You can call this operation to bind an elastic network interface \(ENI\) to an ECS instance in a VPC.

## Description

When you call this operation, take note of the following items:

-   The ENI must be in the **Available** \(`Available`\) state. Each ENI can be bound to a single instance.
-   The instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) state. When you bind ENIs to instances of some instance types, the instances must be in the **Stopped** \(`Stopped`\) state. For more information, see [Shared instance families](~~108489~~) and [Burstable instance overview](~~59977~~).

**Note:** If the last start time of the instance \(including the last start time of the instance if it is newly purchased, the last restart time of the instance, and the last reactivation time of the instance\) is before April 1, 2018 and the instance stays in the Running state, you must call the RebootInstance operation to restart the instance. Otherwise, the ENI cannot be bound to the instance.

-   You can bind multiple ENIs to a single instance. For information about the maximum number of ENIs that can be bound to instances of each instance type, see [ENI overview](~~58496~~).
-   The instance must be in the same zone and the same VPC as the VSwitch to which the ENI is connected.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=AttachNetworkInterface&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|AttachNetworkInterface|The operation that you want to perform. Set the value to AttachNetworkInterface. |
|InstanceId|String|Yes|i-bp16qstyvxj9gpqw\*\*\*\*|The ID of the instance. |
|NetworkInterfaceId|String|Yes|eni-bp17pdijfczax1huji\*\*\*\*|The ID of the ENI. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=AttachNetworkInterface
&RegionId=cn-hangzhou
&InstanceId=i-bp16qstyvxj9gpqw****
&NetworkInterfaceId=eni-bp17pdijfczax1huji****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<AttachNetworkInterfaceResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</AttachNetworkInterfaceResponse>
```

`JSON` format

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidUserType.NotSupported|%s|The error message returned because your account does not support this operation.|
|403|Abs.InvalidAccount.NotFound|%s|The error message returned because your Alibaba Cloud account does not exist or your AccessKey pair has expired.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|Forbidden.NotSupportRAM|%s|The error message returned because RAM users are not authorized to perform this operation.|
|400|UnsupportedParameter|%s|The error message returned because a specified parameter is not supported.|
|403|Forbidden.SubUser|%s|The error message returned because your account is not authorized to manage the specified resource. Contact the owner of the Alibaba Cloud account for authorization.|
|400|InvalidParameter|%s|The error message returned because a specified parameter is invalid.|
|400|InvalidInstanceID.Malformed|%s|The error message returned because the specified InstanceId parameter is invalid.|
|400|InvalidOperation.InvalidRegion|%s|The error message returned because the specified RegionId parameter is invalid.|
|400|InvalidOperation.InvalidEcsState|%s|The error message returned because the operation is not supported while the instance is in the current state.|
|400|InvalidOperation.InvalidEniState|%s|The error message returned because the operation is not supported while the ENI is in the current state.|
|400|InvalidOperation.DetachPrimaryEniNotAllowed|%s|The error message returned because you cannot unbind the primary ENI from the instance.|
|404|InvalidEcsId.NotFound|%s|The error message returned because the specified InstanceId parameter does not exist.|
|404|InvalidEniId.NotFound|%s|The error message returned because the specified NetworkInterfaceId parameter does not exist.|
|404|InvalidVSwitchId.NotFound|%s|The error message returned because the specified VSwitch ID does not exist.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|MaxEniCountExceeded|%s|The error message returned because the maximum number of ENIs that can be managed has been reached.|
|403|EniPerInstanceLimitExceeded|%s|The error message returned because the maximum number of ENIs that can be bound to the specified instance has been reached.|
|403|InvalidOperation.AvailabilityZoneMismatch|%s|The error message returned because the operation is invalid.|
|403|InvalidOperation.VpcMismatch|%s|The error message returned because the operation is invalid. Check whether the VPC in the operation corresponds to other parameters.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|403|InvalidSecurityGroupId.NotVpc|%s|The error message returned because the specified SecurityGroupId parameter is invalid and the security group is not of the VPC type.|
|403|InvalidOperation.InvalidEniType|%s|The error message returned because the ENI type does not support this operation.|
|400|Forbidden.RegionId|%s|The error message returned because the service is not available in the current region.|
|403|InvalidInstanceId.NotFound|%s|The error message returned because the specified InstanceId parameter does not exist.|
|400|InvalidOperation.InvalidGeneration|%s|The error message returned because the operation is invalid.|
|400|InvalidParams.EniId|%s|The error message returned because the specified NetworkInterfaceId parameter is invalid.|
|403|InvalidOperation.Ipv4CountExceeded|%s|The error message returned because the maximum number of IPv4 addresses has been reached.|
|403|InvalidOperation.EniServiceManaged|%s|The error message returned because the operation is invalid.|
|403|InvalidOperation.Ipv6NotSupport|%s|The error message returned because IPv6 does not support this operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

