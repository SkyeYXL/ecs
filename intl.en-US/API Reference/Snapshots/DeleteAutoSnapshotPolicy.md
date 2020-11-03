# DeleteAutoSnapshotPolicy

You can call this operation to delete an automatic snapshot policy. After you delete an automatic snapshot policy, the policy will no longer be applied to the disks that it previously took effect on.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteAutoSnapshotPolicy&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteAutoSnapshotPolicy|The operation that you want to perform. Set the value to DeleteAutoSnapshotPolicy. |
|autoSnapshotPolicyId|String|Yes|sp-bp14yziiuvu3s6jn\*\*\*\*|The ID of the automatic snapshot policy. You can call the [DescribeAutoSnapshotPolicyEx](~~25530~~) operation to query the available automatic snapshot policies. |
|regionId|String|Yes|cn-hangzhou|The region ID of the automatic snapshot policy. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteAutoSnapshotPolicy
&autoSnapshotPolicyId=sp-bp14yziiuvu3s6jn****
&regionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteAutoSnapshotPolicyResponse>
      <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId> 
</DeleteAutoSnapshotPolicyResponse>
```

`JSON` format

```
{
    "RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|ParameterInvalid|The specified automatic snapshot policy does not exist.|The error message returned because the specified autoSnapshotPolicyId parameter does not exist. Check whether the policy ID is correct.|
|404|ParameterInvalid|The specified automatic snapshot policy does not exist in the region.|The error message returned because the specified automatic snapshot policy does not exist in this region. Check whether the policy ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

