# JoinResourceGroup

You can call this operation to add an ECS resource or service to a resource group.

## Description

A resource is a cloud service entity that you create in Alibaba Cloud, such as an ECS instance, elastic network interface \(ENI\), or image. A resource group is a collection of infrastructure for projects, environments, or stacks. In a resource group, you can manage resources and monitor and run tasks in a centralized manner without switching between Alibaba Cloud services.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=JoinResourceGroup&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|JoinResourceGroup|The operation that you want to perform. Set the value to JoinResourceGroup. |
|ResourceType|String|No|securitygroup|The type of the ECS resource. Valid values:

-   instance: instance
-   disk: Elastic Block Storage device
-   snapshot: snapshot
-   image: image
-   securitygroup: security group
-   ddh: dedicated host
-   ddhcluster: dedicated host cluster
-   eni: ENI
-   keypair: SSH key pair
-   launchtemplate: launch template

These values are case-sensitive. |
|ResourceId|String|No|sg-bp67acfmxazb4p\*\*\*\*|The ID of the resource. This parameter depends on the ResourceType value. For example, when ResourceType is set to instance, ResourceId can be interpreted as InstanceId. |
|RegionId|String|No|cn-hangzhou|The region ID of the resource. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which to add the resource. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=JoinResourceGroup
&RegionId=cn-hangzhou
&RsourceType=securitygroup
&ResourceId=sg-bp67acfmxazb4p****
&ResourceGroupId=rg-bp67acfmxazb4p****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<JoinResourceGroupResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</JoinResourceGroupResponse>
```

`JSON` format

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|MissingParameter|The input parameter "ResourceId" that is mandatory for processing this request is not supplied.|The error message returned because the ResourceId parameter is not specified.|
|403|MissingParameter|The input parameter "ResourceGroupId" that is mandatory for processing this request is not supplied.|The error message returned because the ResourceGroupId parameter is not specified.|
|403|MissingParameter|The input parameter "RegionId" that is mandatory for processing this request is not supplied.|The error message returned because the RegionId parameter is not specified.|
|404|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|The error message returned because the specified ResourceType parameter does not exist.|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|The error message returned because the specified ResourceGroupId parameter does not exist.|
|404|InvalidResourceId.NotFound|The ResourceId provided does not exist in our records.|The error message returned because the specified ResourceId parameter does not exist.|
|403|InvalidResourceGroup.Duplicate|The ResourceId provided has a ResourceGroup in our records.|The error message returned because the specified resource has already been added to another resource group.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

