# DeleteSnapshot

You can call this operation to delete a snapshot. If you call this operation to delete a snapshot that is being created, the snapshot creation task is canceled.

## Description

When you call this operation, take note of the following items:

-   If the specified snapshot ID does not exist, the request is ignored.
-   A snapshot that has been used to create custom images cannot be deleted. The snapshot can be deleted only after the created custom images are deleted \([DeleteImage](~~25537~~)\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteSnapshot&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteSnapshot|The operation that you want to perform. Set the value to DeleteSnapshot. |
|SnapshotId|String|Yes|s-bp1c0doj0taqyzzl\*\*\*\*|The ID of the snapshot to be deleted. |
|Force|Boolean|No|false|Specifies whether to forcibly delete the snapshot that has been used to create disks.

**Note:** After an snapshot is deleted, the disks created from this snapshot cannot be re-initialized. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteSnapshot
&SnapshotId=s-bp1c0doj0taqyzzl****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteSnapshotResponse>
       <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteSnapshotResponse>
```

`JSON` format

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|SnapshotCreatedImage|The snapshot has been used to create user defined image\(s\).|The error message returned because the specified snapshot has been used to create custom images. You must delete the created custom images before you can delete the snapshot. If you forcibly delete the snapshot, the images created from the snapshot become unavailable.|
|403|SnapshotCreatedDisk|The snapshot has been used to create disk\(s\).|The error message returned because the specified snapshot has been used to create disks.|
|400|MissingParameter|The input parameter SnapshotId that is mandatory for processing this request is not supplied.|The error message returned because the required SnapshotId parameter is not specified.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|404|InvalidSnapshotId.NotFound|The specified snapshot is not found|The error message returned because the specified SnapshotId parameter does not exist.|
|403|Operation.Conflict|The operation may conflicts with others, please retry later.|The error message returned because the operation conflicts with other operations. Try again later.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

