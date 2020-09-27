# ModifyStorageCapacityUnitAttribute

You can call this operation to modify the name or description of a storage capacity unit \(SCU\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyStorageCapacityUnitAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyStorageCapacityUnitAttribute|The operation that you want to perform. If you use a custom HTTP or HTTPS URL to make an API request, you must specify the Action parameter. Set the value to ModifyStorageCapacityUnitAttribute. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SCU. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|StorageCapacityUnitId|String|Yes|scu-bp67acfmxazb4p\*\*\*\*|The ID of the SCU. |
|Name|String|No|NewScu|The name of the SCU. It must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter but cannot start with http:// or https://. |
|Description|String|No|NewScu|The description of the SCU. It must be 2 to 256 characters in length and cannot start with http:// or https://. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyStorageCapacityUnitAttribute
&RegionId=cn-qingdao
&Name=NewScu
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyStorageCapacityUnitAttributeResponse>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyStorageCapacityUnitAttributeResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter.RegionId|The specified RegionId should not be null.|The error message returned because the RegionId parameter is not specified.|
|400|InvalidParameter.Name|The specified Name is invalid.|The error message returned because the specified Name parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

