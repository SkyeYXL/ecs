# ApplyAutoSnapshotPolicy

You can call this operation to apply an automatic snapshot policy to one or more disks. If you apply an automatic snapshot policy to a disk that already has an automatic snapshot policy, the new policy replaces the original policy to take effect on the disk.

## Description

-   A disk can have only one automatic snapshot policy.
-   A single automatic snapshot policy can be applied to multiple disks.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ApplyAutoSnapshotPolicy&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ApplyAutoSnapshotPolicy|The operation that you want to perform. Set the value to ApplyAutoSnapshotPolicy. |
|regionId|String|Yes|cn-hangzhou|The region ID of the automatic snapshot policy and the disks. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|autoSnapshotPolicyId|String|Yes|sp-bp14yziiuvu3s6jn\*\*\*\*|The ID of the automatic snapshot policy. |
|diskIds|String|Yes|\["d-bp14k9cxvr5uzy54\*\*\*\*", "d-bp1dtj8v7x6u08iw\*\*\*\*", "d-bp1c0tyj9tfli2r8\*\*\*\*"\]|The IDs of the disks. The value is a JSON array that consists of disk IDs. Separate multiple disk IDs with commas \(,\). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ApplyAutoSnapshotPolicy
&autoSnapshotPolicyId=sp-bp14yziiuvu3s6jn****
&diskIds=["d-bp14k9cxvr5uzy54****", "d-bp1dtj8v7x6u08iw****", "d-bp1c0tyj9tfli2r8****"]
&regionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ApplyAutoSnapshotPolicyResponse>
      <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</ApplyAutoSnapshotPolicyResponse>
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
|404|ParameterInvalid|The specified automatic snapshot policy does not exist.|The error message returned because the specified autoSnapshotPolicyId parameter does not exist. Check whether the policy ID is correct.|
|404|ParameterInvalid|The specified automatic snapshot policy does not exist in the region.|The error message returned because the specified automatic snapshot policy does not exist in this region. Check whether the policy ID is correct.|
|404|InvalidDiskId.NotFound|The specified disk does not exist in the region.|The error message returned because the specified disk does not exist in the current region.|
|403|ParameterInvalid|The specified RegionId parameter is invalid.|The error message returned because the specified regionId parameter is invalid.|
|403|ParameterInvalid|The specified AutoSnapshotPolicyId parameter is invalid.|The error message returned because the specified autoSnapshotPolicyId parameter is invalid.|
|403|ParameterInvalid|The specified DiskIds are invalid.|The error message returned because the specified diskIds parameter is invalid.|
|400|DiskCategory.OperationNotSupported|The type of the specified disk does not support creating a snapshot.|The error message returned because the operation is not supported by the current disk category.|
|400|PartofDiskCategory.OperationNotSupported|The types of some disks in the disk list do not support creating snapshots.|The error message returned because some of the specified disks do not support this operation.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. Add funds to your account before you proceed.|
|403|InvalidAccountStatus.SnapshotServiceUnavailable|Snapshot service has not been opened yet.|The error message returned because the operation is not supported while the snapshot service is disabled.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

