# DescribeInstanceRamRole

You can call this operation to query the instance RAM roles assigned to one or more ECS instances.

## Description

When you call an API operation by using Alibaba Cloud CLI, you must specify request parameter values of different data types in required formats. For more information, see [CLI parameter format](~~110340~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceRamRole&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceRamRole|The operation that you want to perform. Set the value to DescribeInstanceRamRole. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance RAM role. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|PageNumber|Integer|No|1|The number of the page to return.

Pages start from page 1.

Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page.

Valid values: 1 to 50.

Default value: 10. |
|InstanceIds|String|No|\["i-bp67acfmxazb1p\*\*\*\*", "i-bp67acfmxazb2p\*\*\*\*", "bp67acfmxazb3p\*\*\*\*"…\]|The IDs of instances. A maximum of 100 instance IDs can be entered at a time. You must specify at least one of the `InstanceIds` and `RamRoleName` parameters. |
|RamRoleName|String|No|EcsServiceRole-EcsDocGuideTest|The name of the instance RAM role. This parameter can be used to query all the ECS instances to which the instance RAM role is assigned. You can call the [ListRoles](~~28713~~) operation provided by RAM to query the instance RAM roles that you have created. You must specify at least one of the `InstanceIds` and `RamRoleName` parameters. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceRamRoleSets|Array of InstanceRamRoleSet| |Details about the instance RAM roles. |
|InstanceRamRoleSet| | | |
|InstanceId|String|i-bp67acfmxazb4p\*\*\*\*|The ID of the instance. |
|RamRoleName|String|EcsServiceRole-EcsDocGuideTest|The name of the instance RAM role. |
|RegionId|String|cn-hangzhou|The region ID of the instance RAM role. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|1|The total number of returned instance RAM roles. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceRamRole
&RegionId=cn-hangzhou
&InstanceIds=["i-bp67acfmxazb1p****", "i-bp67acfmxazb2p****", "bp67acfmxazb3p****"]
&PageNumber=1
&PageSize=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceRamRoleResponse>
      <RequestId>8F4CAE3F-7892-4662-83A5-2C2FFD639553</RequestId>
      <InstanceRamRoleSets>
            <InstanceRamRoleSet>
                  <InstanceId>i-bp67acfmxazb4p****</InstanceId>
                  <RamRoleName>EcsServiceRole-EcsDocGuideTest</RamRoleName>
            </InstanceRamRoleSet>
      </InstanceRamRoleSets>
      <TotalCount>1</TotalCount>
      <PageNumber>1</PageNumber>
      <PageSize>1</PageSize>
</DescribeInstanceRamRoleResponse>
```

`JSON` format

```
{
    "RequestId": "8F4CAE3F-7892-4662-83A5-2C2FFD639553",
    "InstanceRamRoleSets": {
        "InstanceRamRoleSet": [
            {
                "InstanceId": "i-bp67acfmxazb4p****",
                "RamRoleName": "EcsServiceRole-EcsDocGuideTest"
            }
        ]
    },
    "TotalCount": 1,
    "PageNumber": 1,
    "PageSize": 1
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidInstanceIds.Malformed|The specified instanceIds are not valid.|The error message returned because the specified InstanceIds parameter is invalid.|
|404|InvalidInstanceId.NotFound|The specified instanceId does not exist|The error message returned because a specified instance does not exist.|
|403|InvalidNetworkType.MismatchRamRole|Ram role cannot be applied to instances of Classic network type.|The error message returned because an instance RAM role can be used only for instances in VPCs, not for instances in the classic network.|
|403|InvalidParameter.AllEmpty|%s|The error message returned because no parameters are specified. Specify required parameters.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

