# ModifyNetworkInterfaceAttribute

You can call this operation to modify the properties such as the name, description, and security group of an elastic network interface \(ENI\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyNetworkInterfaceAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyNetworkInterfaceAttribute|The operation that you want to perform. Set the value to ModifyNetworkInterfaceAttribute. |
|NetworkInterfaceId|String|Yes|eni-bp67acfmxazb4p\*\*\*\*|The ID of the ENI. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the ENI. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|SecurityGroupId.N|RepeatList|No|sg-bp67acfmxazb4p\*\*\*\*|The ID of security group N to which the ENI finally belongs. If a security group to which the ENI has belonged is in the ID list, that security group is removed from the list. Valid values of N: 1, 2, 3, 4, and 5.

**Note:** After you modify the security group, the modification will take effect after a short delay. |
|NetworkInterfaceName|String|No|eniTestName|The name of the ENI. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\).

This parameter is empty by default. |
|QueueNumber|Integer|No|8|The number of ENI queues. Valid values: 1 to 2048.

-   You can modify only the queue numbers of secondary ENIs.
-   You can modify the queue number of a secondary ENI only when the ENI is in the `Available` state or the secondary ENI is bound \(`InUse`\) to an instance that is in the `Stopped` state.
-   The maximum queue number of a single secondary ENI cannot exceed the service quota of queues allowed by the instance type of the instance to which the secondary ENI is bound. The total queue number of all ENIs that are bound to the instance also cannot exceed the total queue quota allowed by the instance type of the instance. To learn the queue quotas for a single ENI and all ENIs bound to an instance, you can call the [DescribeInstanceTypes](~~25620~~) operation to query the `MaximumQueueNumberPerEni` and `TotalEniQueueQuantity` fields. |
|Description|String|No|testDescription|The description of the ENI. The description must be 2 to 256 characters in length and cannot start with http:// or https://.

This parameter is empty by default. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyNetworkInterfaceAttribute
&NetworkInterfaceId=eni-bp67acfmxazb4p****
&RegionId=cn-hangzhou
&SecurityGroupId.1=sg-bp67acfmxazb4p****
&NetworkInterfaceName=eniTestName
&Description=testDescription
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DetachNetworkInterfaceResponse>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DetachNetworkInterfaceResponse>
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
|403|InvalidUserType.NotSupported|%s|The error message returned because the current account does not support this operation.|
|403|Abs.InvalidAccount.NotFound|%s|The error message returned because your Alibaba Cloud account does not exist or your AccessKey pair has expired.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|Forbidden.NotSupportRAM|%s|The error message returned because RAM users are not authorized to perform this operation.|
|400|UnsupportedParameter|%s|The error message returned because the specified parameter is not supported.|
|403|Forbidden.SubUser|%s|The error message returned because you are not authorized to manage this resource. Apply for permissions to the Alibaba Cloud account.|
|400|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|400|InvalidInstanceID.Malformed|%s|The error message returned because the specified InstanceId parameter is invalid.|
|400|InvalidOperation.InvalidEcsState|%s|The error message returned because the operation is not supported while the instance is in the current state.|
|400|InvalidOperation.InvalidEniState|%s|The error message returned because the operation is not supported while the ENI is in the current state.|
|400|InvalidOperation.DetachPrimaryEniNotAllowed|%s|The error message returned because you cannot unbind the primary ENI from the instance.|
|400|InvalidParams.EniId|%s|The error message returned because the specified EniId parameter is invalid.|
|404|InvalidEcsId.NotFound|%s|The error message returned because the specified instance ID does not exist.|
|404|InvalidEniId.NotFound|%s|The error message returned because the specified ENI ID does not exist.|
|404|InvalidVSwitchId.NotFound|%s|The error message returned because the specified VSwitch ID does not exist.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|MaxEniCountExceeded|%s|The error message returned because the maximum number of ENIs that can be managed has been reached.|
|403|EniPerInstanceLimitExceeded|%s|The error message returned because the maximum number of ENIs that can be bound to the specified instance has been reached.|
|403|InvalidOperation.AvailabilityZoneMismatch|%s|The error message returned because this operation is invalid.|
|403|InvalidOperation.VpcMismatch|%s|The error message returned because this operation is invalid. Check whether the VPC in the operation corresponds to other parameters.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|403|InvalidSecurityGroupId.NotVpc|%s|The error message returned because the specified SecurityGroupId parameter is invalid and the network type of the security group is not VPC.|
|403|InvalidOperation.InvalidEniType|%s|The error message returned because the ENI type does not support this operation.|
|400|Forbidden.RegionId|%s|The error message returned because the service is unavailable in the current region.|
|403|InvalidOperation.EniServiceManaged|%s|The error message returned because this operation is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

