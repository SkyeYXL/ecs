# DeleteDeploymentSet

You can call this operation to delete a deployment set.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteDeploymentSet&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteDeploymentSet|The operation that you want to perform. Set the value to DeleteDeploymentSet. |
|DeploymentSetId|String|Yes|ds-bp1g5ahlkal88d7x\*\*\*\*|The ID of the deployment set. You cannot delete a deployment set that contains instances. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the deployment set. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteDeploymentSet
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1g5ahlkal88d7x****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteDeploymentSetResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteDeploymentSetResponse>
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
|400|MissingParameter|The input parameter "DeploymentSetId" that is mandatory for processing this request is not supplied.|The error message returned because the required DeploymentSetId parameter is not specified.|
|403|DependencyViolation.NotEmpty|There are still instance\(s\) in the specified DeploymentSetId.|The error message returned because the specified deployment set contains instances. You must remove the instances before you can delete the deployment set.|
|403|DependencyViolation.ReferByHPC|The specified deployment set is still referred by an HPC cluster.|The error message returned because the specified deployment set is associated with other HPC clusters.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

