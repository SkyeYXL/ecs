# ResetDisk

You can call this operation to roll back a disk to a specific state based on a snapshot of the disk.

## Description

When you call this operation, take note of the following items:

-   The disk must be in the In Use \(In\_Use\) state.
-   The instance to which the disk is attached must be in the Stopped \(Stopped\) state.
-   The specified snapshot must be created from the disk specified by the DiskId parameter.
-   When you call the [DescribeInstances](~~25506~~) operation to query the instance information and if the responses contain `{"OperationLocks": {"LockReason" : "security"}}`, the instance is locked for security reasons and all operations are denied.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ResetDisk&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ResetDisk|The operation that you want to perform. Set the value to ResetDisk. |
|DiskId|String|Yes|d-bp199lyny9b3\*\*\*\*|The ID of the disk. |
|SnapshotId|String|Yes|s-bp199lyny9b3\*\*\*\*|The ID of the snapshot that is used to roll back the disk to a specific state. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|F3CD6886-D8D0-4FEE-B93E-1B73239673DE|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ResetDisk
&DiskId=d-bp199lyny9b3****
&SnapshotId=s-bp199lyny9b3****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ResetDiskResponse>
      <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</ResetDiskResponse>
```

`JSON` format

```
{
    "RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidDiskId.NotFound|The specified disk does not exist.|The error message returned because the specified disk does not exist. Check whether the disk ID is correct.|
|404|Disk.NotFound|The specified disk does not exist.|The error message returned because the specified disk does not exist. Check whether the disk ID is correct.|
|404|InvalidSnapshotId.NotFound|The specified SnapshotId does not exist.|The error message returned because the specified snapshot does not exist. Check whether the snapshot ID is correct.|
|403|IncorrectDiskStatus|The current disk status does not support this operation.|The error message returned because the operation is not supported while the disk is in the current state. Make sure that the disk is available and you have no overdue payments.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|InstanceLockedForSecurity|The instance is locked due to security.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|403|InvalidParameter.Mismatch|The specified snapshot is not created from the specified disk.|The error message returned because the encrypted snapshot is not created from the unencrypted disk.|
|403|InvalidSnapshot.TooOld|The snapshotId is created before 2013-07-15, it cannot be restored since the first time the disk detached.|The error message returned because snapshots created before July 15, 2013 do not support this operation.|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|The error message returned because the subscription instance has expired. Renew the instance first.|
|403|OperationDenied|The specified snapshot dees not support ResetDisk.|The error message returned the specified snapshot does not support the ResetDisk operation.|
|403|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|The error message returned because the specified snapshot is being created.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|DiskCategory.OperationNotSupported|The operation is not supported to the specified disk due to its disk category|The error message returned because the specified disk category does not support the operation.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. Top up your account before proceeding.|
|403|InvalidAccountStatus.SnapshotServiceUnavailable|Snapshot service has not been opened yet.|The error message returned because the operation is not supported while the snapshot service is not activated.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified instance does not exist. Check whether the instance ID is correct.|
|403|Operation.Conflict|The operation may conflicts with others.|The error message returned because the specified operation conflicts with other operations.|
|403|UserNotInTheWhiteList|The user is not in disk white list.|The error message returned because you are not in the whitelist to manage the disk. Try again when you are in the whitelist.|
|400|InvalidRegionId.MalFormed|The specified RegionId is not valid|The error message returned because the specified RegionId parameter is invalid.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|InvalidParameter.KMSKeyId.KMSUnauthorized|ECS service have no right to access your KMS.|The error message returned because ECS is not authorized to access your KMS resources.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

