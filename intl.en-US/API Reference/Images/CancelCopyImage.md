# CancelCopyImage

You can call this operation to cancel an ongoing image copy \(CopyImage\) task.

## Description

When you call this operation, take note of the following items:

-   After you cancel the image copy task, the image copy created in the destination region is deleted, and the source image remains unchanged.
-   If the image copy task is complete, the CancelCopyImage operation fails and an error is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CancelCopyImage&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CancelCopyImage|The operation that you want to perform. Set the value to CancelCopyImage. |
|ImageId|String|Yes|m-bp1caf3yicx5jlfl\*\*\*\*|The ID of the image being copied. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the image copy. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=CancelCopyImage
&ImageId=m-bp1caf3yicx5jlfl****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CancelCopyImageResponse>
      <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CancelCopyImageResponse>
```

`JSON` format

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned because the specified RegionId parameter does not exist.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist in this account.|
|400|ImageCreatedNotFromCopy|The specified image is not the target image of a copy action.|The error message returned because the specified image ID is not the ID of the image that is being copied.|
|400|IncorrectImageStatus|The image is copied finished.|The error message returned because the image copy task is complete.|
|400|InvalidDescription.Malformed|The specified description is wrongly formed.|The error message returned because the specified description is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|IncorrectImageStatus|The specified snapshot is not coping.|The error message returned because the specified snapshot is not being copied.|
|400|IncorrectImageStatus|The specified image is not coping.|The error message returned because the specified image is not being copied.|
|400|IncorrectImageStatus|The image has completed copy.|The error message returned because the image copy task is complete.|
|400|IncorrectImageStatus|The Image copy has been failed.|The error message returned because the specified image failed to be copied.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|CancelNotSupported|The specified image coping can not be cancelled.|The error message returned because the specified image copy task cannot be canceled.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

