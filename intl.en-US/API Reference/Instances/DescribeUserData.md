# DescribeUserData

You can call this operation to query the user data of an ECS instance.

## Description

-   The returned user data is encoded in Base64.
-   If the instance does not have any user data, an empty string is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeUserData&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeUserData|The operation that you want to perform. Set the value to DescribeUserdata. |
|InstanceId|String|Yes|i-bp14bnftyqhxg9ij\*\*\*\*|The ID of the instance. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceId|String|i-bp14bnftyqhxg9ij\*\*\*\*|The ID of the instance. |
|RegionId|String|cn-hangzhou|The region ID of the instance. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|UserData|String|ZWNobyBoZWxsbyBlY321ABC|The user data of the instance. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action= DescribeUserdata
&RegionId=cn-shenzhen
&InstanceId=i-bp14bnftyqhxg9ij****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeUserdataResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <UserData>ZWNobyBoZWxsbyBlY321ABC</UserData>
      <InstanceId>i-bp14bnftyqhxg9ij****</InstanceId>
      <RegionId>cn-shenzhen</RegionId>
</DescribeUserdataResponse>
```

`JSON` format

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
    " UserData ": "ZWNobyBoZWxsbyBlY321ABC",
    " InstanceId ": "i-bp14bnftyqhxg9ij****",
    " RegionId": "cn-shenzhen"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

