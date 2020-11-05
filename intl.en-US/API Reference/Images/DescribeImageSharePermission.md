# DescribeImageSharePermission

You can call this operation to query the accounts to which a custom image is shared. The response can be displayed by page. By default, ten entries are displayed on each page.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeImageSharePermission&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeImageSharePermission|The operation that you want to perform. Set the value to DescribeImageSharePermission. |
|ImageId|String|Yes|m-bp1caf3yicx5jlfl\*\*\*\*|The ID of the custom image. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the custom image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|PageNumber|Integer|No|1|The number of the page to return. Pages start from page 1.

Default value: 1 |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100.

Default value: 10 |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Accounts|Array of Account| |The Alibaba Cloud accounts. |
|Account| | | |
|AliyunId|String|1234567890|The ID of the Alibaba Cloud account. |
|ImageId|String|m-bp1caf3yicx5jlfl\*\*\*\*|The ID of the custom image. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RegionId|String|cn-hangzhou|The region ID of the image. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|ShareGroups|Array of ShareGroup| |The shared groups. |
|ShareGroup| | | |
|Group|String|all|The shared group. |
|TotalCount|Integer|1|The total number of entries returned. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeImageSharePermission
&ImageId=m-bp1caf3yicx5jlfl****
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=10
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeImageSharePermissionResponse>
      <ImageId>m-bp1caf3yicx5jlfl****</ImageId>
      <PageNumber>1</PageNumber>
      <PageSize>10</PageSize>
      <RegionId>cn-qingdao</RegionId>
      <TotalCount>1</TotalCount>
      <RequestId>441CF898-42FF-47CF-9348-3C3BFF557278</RequestId>
      <ShareGroups>
            <ShareGroup>
                  <Group>all</Group>
            </ShareGroup>
      </ShareGroups>
      <Accounts>
            <Account>
                  <AliyunId>1234567890</AliyunId>
            </Account>
      </Accounts>
</DescribeImageSharePermissionResponse>
```

`JSON` format

```
{
    "ShareGroups": {
        "ShareGroup": [
            {
                "Group": "all"
            }
        ]
    },
    "Accounts": {
        "Account": [
            {
                "AliyunId": "1234567890"
            }
        ]
    },
    "ImageId": "m-bp1caf3yicx5jlfl****",
    "PageNumber": 1,
    "PageSize": 10,
    "RegionId": "cn-qingdao",
    "TotalCount": 1,
    "RequestId": "9AD96F49-0BE5-4868-A66A-224352549CEC"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter|The input parameter "RegionId "that is mandatory for processing this request is not supplied.|The error message returned because the required RegionId parameter is not specified.|
|400|MissingParameter|The input parameter "ImageId "that is mandatory for processing this request is not supplied.|The error message returned because the required ImageId parameter is not specified.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist in this account.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

