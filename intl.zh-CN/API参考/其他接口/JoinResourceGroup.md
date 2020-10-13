# JoinResourceGroup

调用JoinResourceGroup将一个ECS资源或者服务加入一个资源组。

## 接口说明

资源是您在阿里云创建的云服务实体，例如，一台ECS实例、一个ECS弹性网卡或者一份ECS镜像等都可以是资源。资源组是项目、环境或者栈的基础设施集合，在资源组里管理资源能集中监控和执行任务，免去了您在多种阿里云服务间反复查看的负担。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=JoinResourceGroup&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|JoinResourceGroup|系统规定参数。取值：JoinResourceGroup |
|ResourceType|String|否|securitygroup|ECS资源的类型。取值范围：

 -   instance：实例
-   disk：块存储
-   snapshot：快照
-   image：镜像
-   securitygroup：安全组
-   ddh：专有宿主机
-   ddhcluster：专有宿主机集群
-   eni：弹性网卡
-   keypair：密钥对
-   launchtemplate：启动模板

 以上参数取值均大小写敏感。 |
|ResourceId|String|否|sg-bp67acfmxazb4p\*\*\*\*|资源类型的ID标识符。例如，当ResourceType=instance时，则ResourceId可以理解为InstanceId。 |
|RegionId|String|否|cn-hangzhou|资源所在的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|ResourceGroupId|String|否|rg-bp67acfmxazb4p\*\*\*\*|目标资源组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=JoinResourceGroup
&RegionId=cn-hangzhou
&RsourceType=securitygroup
&ResourceId=sg-bp67acfmxazb4p****
&ResourceGroupId=rg-bp67acfmxazb4p****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<JoinResourceGroupResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</JoinResourceGroupResponse>
```

`JSON` 格式

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|MissingParameter|The input parameter "ResourceId" that is mandatory for processing this request is not supplied.|参数ResourceId不能为空。|
|403|MissingParameter|The input parameter "ResourceGroupId" that is mandatory for processing this request is not supplied.|参数ResourceGroupId不能为空。|
|403|MissingParameter|The input parameter "RegionId" that is mandatory for processing this request is not supplied.|RegionId不得为空。|
|404|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|指定的资源类型不存在。|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|资源组并不在记录中。|
|404|InvalidResourceId.NotFound|The ResourceId provided does not exist in our records.|指定的资源不存在。|
|403|InvalidResourceGroup.Duplicate|The ResourceId provided has a ResourceGroup in our records.|该资源已加入到其它资源组。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

