# RedeployDedicatedHost

You can call this operation to migrate instances from a failed dedicated host

## Description

If a dedicated host is in the UnderAssessment state, we recommend that you call this operation to migrate instances on the dedicated host to prevent permanent failures. You can call the [DescribeDedicatedHosts](~~134242~~) operation to query the status of a dedicated host.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=RedeployDedicatedHost&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RedeployDedicatedHost|The operation that you want to perform. Set the value to RedeployDedicatedHost. |
|DedicatedHostId|String|Yes|dh-bp165p6xk2tlw61e\*\*\*\*|The ID of the dedicated host. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the dedicated host. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|FCED4B7A-53D5-4C04-ABE3-26D4F3890D57|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=RedeployDedicatedHost
&RegionId=cn-hangzhou
&DedicatedHostId=dh-bp165p6xk2tlw61e****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RedeployDedicatedHostResponse>
      <RequestId>FCED4B7A-53D5-4C04-ABE3-26D4F3890D57</RequestId>
</RedeployDedicatedHostResponse>
```

`JSON` format

```
{
    "RequestId":"FCED4B7A-53D5-4C04-ABE3-26D4F3890D57"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidDedicatedHostId.NotFound|The specified DedicatedHostId does not exist.|The error message returned because the specified DedicatedHostId parameter does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

