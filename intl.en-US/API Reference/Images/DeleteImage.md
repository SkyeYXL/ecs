# DeleteImage

You can call this operation to delete a custom image.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteImage&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteImage|The operation that you want to perform. Set the value to DeleteImage. |
|ImageId|String|Yes|m-bp67acfmxazb4p\*\*\*\*|The ID of the image. If the specified custom image does not exist, the request will be ignored. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the custom image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Force|Boolean|No|false|Specifies whether to forcibly delete the custom image. Valid values:

-   true: forcibly deletes the custom image, regardless of whether the image is being used by other instances.
-   false: verifies that the image is not being used by other instances and then deletes the image.

Default value: false |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteImage
&ImageId=m-bp67acfmxazb4p****
&RegionId=cn-hangzhou
&Force=false
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteImageResponse>
       <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteImageResponse>
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
|403|ImageUsingByInstance|The specified image has been used to create instances.|The error message returned because the specified image is being used for instance creation and cannot be deleted.|
|403|ImageUseShared|The specified image has been shared to others.|The error message returned because the specified image is already shared with other accounts.|
|403|OperationDenied.ImageCopying|The Image is coping.|The error message returned because the source image is being copied. Try again later.|
|403|ImageIsImporting|The specified Image is importing.|The error message returned because the specified image is being imported and cannot be managed.|
|403|ImageIsExporting|The specified Image is exporting. Please cancel task first.|The error message returned because the specified image is being exported. Cancel the export task first.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist in this account. Check whether the image ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

