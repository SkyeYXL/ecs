# ModifyInstanceVncPasswd

You can call this operation to modify the VNC password of an instance.

## Description

-   The password must be six characters in length and can contain only uppercase letters, lowercase letters, and digits.
-   The new password takes effect based on the following situations:
    -   For an I/O optimized instance, the new password takes effect immediately.
    -   For a non-I/O optimized instance, you must restart the instance in the console or call the [RebootInstance](~~25502~~) operation for the new password to take effect. For more information, see [Restart an instance](~~25440~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceVncPasswd&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceVncPasswd|The operation that you want to perform. Set the value to ModifyInstanceVncPasswd. |
|InstanceId|String|Yes|i-bp67acfmxazb4ph\*\*\*\*|The ID of the instance. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|VncPassword|String|Yes|Ecs123|The new VNC password of the instance. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceVncPasswd
&RegionId=cn-hangzhou
&InstanceId=i-bp67acfmxazb4ph****
&VncPassword=Ecs123
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceVncPasswdResponse>
      <RequestId>FDB6C963-9CE8-4B7F-BCA3-845F6BD29AFC</RequestId>
</ModifyInstanceVncPasswdResponse>
```

`JSON` format

```
{
      "RequestId": "FDB6C963-9CE8-4B7F-BCA3-845F6BD29AFC"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned because the specified RegionId parameter does not exist.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|400|IncorrectVncPassword.Malformed|The specified parameter VncPassword is not valid.|The error message returned because the specified VncPassword parameter is invalid.|
|404|NoSuchResource|The specified resource is not found.|The error message returned because the specified resource does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

