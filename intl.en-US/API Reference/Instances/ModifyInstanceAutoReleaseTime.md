# ModifyInstanceAutoReleaseTime

You can call this operation to set or cancel the auto-release time for a pay-as-you-go instance. Exercise caution when you set the auto-release time because the instance will be automatically released upon expiration.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceAutoReleaseTime&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceAutoReleaseTime|The operation that you want to perform. Set the value to ModifyInstanceAutoReleaseTime. |
|InstanceId|String|Yes|i-bp1env7nl3mijm2t\*\*\*\*|The ID of the ECS instance to be automatically released. |
|RegionId|String|No|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|AutoReleaseTime|String|No|2018-01-01T01:02:03Z|The time scheduled for the instance to be automatically released. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

-   If the value of the field `ss` is not `00`, the field is automatically set to the start time of the current minute \(`mm`\).
-   The release time must be at least 30 minutes later than the current time.
-   The release time must be at most three years from the current time.

If `AutoReleaseTime` is not specified, the automatic release feature is disabled and the ECS instance will not be automatically released. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceAutoReleaseTime
&InstanceId=i-bp1env7nl3mijm2t****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceAutoReleaseTimeResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceAutoReleaseTimeResponse>
```

`JSON` format

```
{ 
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E209A9012A8"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter|InstanceId should not be null.|The error message returned because the InstanceId parameter is not specified.|
|400|InvalidAutoReleaseTime.Malformed|The specified paramter autoReleaseTime is not valid.|The error message returned because the specified AutoReleaseTime parameter is invalid. Specify the time in the ISO 8601 standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|UnsupportedParameter|The parameters is unsupported.|The error message returned because a specified parameter is invalid.|
|403|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|The error message returned because the billing method of the instance does not support this operation.|
|404|NoSuchResource|The specified resource is not found.|The error message returned because the specified resource does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

