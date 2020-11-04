# DescribeSnapshotsUsage

You can call this operation to query the number of snapshots stored in a region and the total size of the snapshots.

If you want to view the snapshot usage information about each disk in the current region, we recommend that you call the [DescribeSnapshotLinks](~~55837~~) operation to query snapshot chain information.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSnapshotsUsage&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSnapshotsUsage|The operation that you want to perform. Set the value to DescribeSnapshotsUsage. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the snapshot. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|SnapshotCount|Integer|5|The number of snapshots stored in the current region. |
|SnapshotSize|Long|122|The total size of snapshots stored in the current region. Unit: byte. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeSnapshotsUsage
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSnapshotsUsageResponse>
      <SnapshotCount>5</SnapshotCount>
      <SnapshotSize>122</SnapshotSize>    
      <RequestId>ED5CF6DD-71CA-462C-9C94-A61A78A01479</RequestId>
</DescribeSnapshotsUsageResponse>
```

`JSON` format

```
{
    "SnapshotCount": "5",
    "SnapshotSize": "122",
    "RequestId": "ACD9BBB0-A9D1-46D7-9630-B7A69889E110"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidParam.RegionId|The specified region is not exist.|The error message returned because the specified RegionId parameter does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

