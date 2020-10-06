# DeleteInstance

You can call this operation to release a pay-as-you-go instance or an expired subscription instance.

## Description

-   After an instance is released, all the physical resources used by the instance are recycled. Relevant data is erased and cannot be recovered.
-   Disks attached to the instance:
    -   The disks for which `DeleteWithInstance` is set to false are retained as pay-as-you-go disks.
    -   The disks for which `DeleteWithInstance` is set to true are released along with the instance.
    -   For disks for which `DeleteAutoSnapshot` is set to false, the automatic snapshots are retained.
    -   For disks for which `DeleteAutoSnapshot` is set to true, the automatic snapshots are released.
    -   Manual snapshots are retained.
    -   If `OperationLocks` in the DescribeInstances response contains `"LockReason" : "security"` for an instance, the instance is locked for security reasons. Even if `DeleteWithInstance` is set to `false` for the data disks that are attached to the instance, this parameter is ignored and the data disks are released along with the instance. For more information, see [API behavior when an instance is locked for security reasons](~~25695~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteInstance&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Position|Type|Required|Example|Description|
|---------|--------|----|--------|-------|-----------|
|Action|Query|String|Yes|DeleteInstance|The operation that you want to perform. Set the value to DeleteInstance. |
|InstanceId|Query|String|Yes|i-bp1g6zv0ce8oghu7\*\*\*\*|The ID of the instance that you want to release. |
|Force|Query|Boolean|No|false|Specifies whether to forcibly release the instance in the **Running** \(`Running`\) state. Default value: false. Valid values:

-   true: forcibly releases the instance in the **Running** \(`Running`\) state. This operation is equivalent to the power-off operation. Temporary data in the memory and storage of the instance is erased and cannot be recovered.
-   false: normally releases the instance. This value is valid only for an instance in the **Stopped** \(`Stopped`\) state. |
|TerminateSubscription|Query|Boolean|No|false|Specifies whether to release an expired subscription instance.

Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteInstance
&InstanceId=i-bp1g6zv0ce8oghu7****
&Force=false
&TerminateSubscription=false
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteInstanceResponse>
      <RequestId>928E2273-5715-46B9-A730-238DC996A533</RequestId>
</DeleteInstanceResponse>
```

`JSON` format

```
{
    "RequestId": "928E2273-5715-46B9-A730-238DC996A533"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|403|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|The error message returned because the operation is not supported while the instance uses the current billing method.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|DependencyViolation.SLBConfiguring|Specified operation is denied as your instance is using by another product.|The error message returned because the instance is referenced by an SLB instance that is being configured.|
|400|DependencyViolation.RouteEntry|Specified instance is used by route entry.|The error message returned because custom routing entries that include the IP address of the specified instance exist in the current VPC.|
|400|InvalidParameter|The input parameter InstanceId is invalid.|The error message returned because the specified InstanceId parameter is invalid.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|403|IncorrectInstanceStatus.Initializing|The specified instance status does not support this operation.|The error message returned because the instance is being initialized and cannot be released. Try again later.|
|403|IncorrectInstanceStatus|The specified instance is still attached by volumes.|The error message returned because the specified instance still has data volumes.|
|403|InvalidOperation.DeletionProtection|%s|The error message returned because the operation is invalid. Disable release protection for the instance first.|
|403|InvalidOperation.EniLinked|%s|The error message returned because the operation is not supported while the instance is bound with elastic network interfaces \(ENIs\).|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

