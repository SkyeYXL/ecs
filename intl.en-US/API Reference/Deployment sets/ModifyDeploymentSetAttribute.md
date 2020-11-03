# ModifyDeploymentSetAttribute

You can call this operation to modify the name and description of a deployment set.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyDeploymentSetAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyDeploymentSetAttribute|The operation that you want to perform. Set the value to ModifyDeploymentSetAttribute. |
|DeploymentSetId|String|Yes|ds-bp1frxuzdg87zh4p\*\*\*\*|The ID of the deployment set. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the deployment set. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Description|String|No|TestDescription|The new description of the deployment set. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DeploymentSetName|String|No|DeploymentSetTestName|The new name of the deployment set. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyDeploymentSetAttribute
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1frxuzdg87zh4p****
&DeploymentSetName=DeploymentSetTestName
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyDeploymentSetAttributeResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyDeploymentSetAttributeResponse>
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
|400|MissingParameter|The input parameter RegionId that is mandatory for processing this request is not supplied.|The error message returned because the required RegionId parameter is not specified.|
|400|InvalidDeploymentSetName.Malformed|Specified deployment set name is not valid.|The error message returned because the specified DeploymentSetName parameter is invalid.|
|400|InvalidDescription.Malformed|The specified parameter Description is not valid.|The error message returned because the specified Description parameter is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|InvalidDeploymentSetId.NotFound|The specified DeploymentSetId does not exist.|The error message returned because the specified DeploymentSetId parameter does not exist. Check whether the deployment set ID is correct.|
|403|QuotaExceed.DeploymentSetInstanceQuotaFull|instance quota in one deployment set exceeded.|The error message returned because the maximum number of instances in the current deployment set has been reached.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

