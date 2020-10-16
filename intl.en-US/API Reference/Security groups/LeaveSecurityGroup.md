# LeaveSecurityGroup

You can call this operation to remove an ECS instance from a security group.

## Description

**Note:** This operation is not recommended. We recommend that you call the [ModifyInstanceAttribute](~~25503~~) operation to add or remove ECS instances to or from a security group, and call the [ModifyNetworkInterfaceAttribute](~~58513~~) operation to add or remove elastic network interfaces \(ENIs\) to or from a security group.

When you call this operation, take note of the following items:

-   Before you remove an instance from a security group, make sure that the instance is in the **Stopped** \(Stopped\) or **Running** \(Running\) state.
-   An instance must belong to at least one security group. Therefore, if the instance to be removed belongs to only a single security group, the LeaveSecurityGroup request fails.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates a sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=LeaveSecurityGroup&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|LeaveSecurityGroup|The operation that you want to perform. Set the value to LeaveSecurityGroup. |
|InstanceId|String|Yes|i-bp67acfmxazb4p\*\*\*\*|The ID of the instance. |
|SecurityGroupId|String|Yes|sg-bp67acfmxazb4p\*\*\*\*|The ID of the security group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=LeaveSecurityGroup
&InstanceId=i-bp67acfmxazb4p****
&SecurityGroupId=sg-bp67acfmxazb4p****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<LeaveSecurityGroupResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</LeaveSecurityGroupResponse>
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
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist in this account. Check whether the security group ID is correct.|
|403|InstanceLastSecurityGroup|The specified security group is the last security group for the instance.|The error message returned because the specified security group is the only security group to which the instance belongs.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|403|InstanceNotInSecurityGroup|The instance not in the group.|The error message returned because the specified instance does not belong to the security group.|
|504|RequestTimeout|The request encounters an upstream server timeout.|The error message returned because the request is denied due to an upstream server timeout.|
|400|InvalidInstanceId.Malformed|The specified parameter "InstanceId" is not valid.|The error message returned because the specified InstanceId parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

