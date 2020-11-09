# ModifyInstanceMetadataOptions

You can call this operation to modify the metadata of an instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceMetadataOptions&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceMetadataOptions|The operation that you want to perform. Set the value to ModifyInstanceMetadataOptions. |
|HttpEndpoint|String|Yes|enabled|Specifies whether to enable the metadata HTTP endpoint on the instance. Valid values:

-   enabled
-   disabled

Default value: enabled.

**Note:** For more information about instance metadata, see [Metadata](~~49122~~). |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InstanceId|String|No|i-bp67acfmxaz\*\*\*\*|The ID of the instance. |
|HttpTokens|String|No|optional|Specifies whether to forcibly use the security-enhanced mode \(IMDSv2\) to access instance metadata. Valid values:

-   optional: The security-enhancement mode \(IMDSv2\) is not forcibly used.
-   required: The security-enhancement mode \(IMDSv2\) is forcibly used. After you set this parameter to required, you cannot access the instance metadata in normal mode.

Default value: optional.

**Note:** For more information about modes of accessing instance metadata, see [Access mode of instance metadata](~~150575~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
http(s)://ecs.aliyuncs.com/?Action=ModifyInstanceMetadataOptions
&RegionId=cn-hangzhou
&InstanceId=i-bp67acfmxaz****
&HttpEndpoint=enabled
&HttpTokens=required
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceMetadataOptionsResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyInstanceMetadataOptionsResponse>
```

`JSON` format

```
{
    "RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidHttpEndpoint.NotSupported|The specified HttpEndpoint not supported, you can use enabled\(default\) or disabled.|The error message returned because the specified HttpEndpoint parameter is invalid. Set the parameter to enabled \(default value\) or disabled.|
|400|InvalidHttpTokens.NotSupported|The specified HttpTokens not supported, you can use optional\(default\) or required.|The error message returned because the specified HttpTokens parameter is invalid. Set the parameter to optional \(default value\) or required.|
|400|InvalidHttpPutResponseHopLimit.NotSupported|The specified HttpPutResponseHopLimit not supported, more than 1 and less than 64 is reasonable.|The error message returned because the specified HttpPutResponseHopLimit parameter is invalid. The value must be in the range of 1 to 64.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

