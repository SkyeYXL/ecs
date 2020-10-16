# LeaveSecurityGroup

调用LeaveSecurityGroup将一台ECS实例移出指定的安全组。

## 接口说明

**说明：** 该API已不推荐使用。推荐您调用[ModifyInstanceAttribute](~~25503~~)接口将ECS实例加入或移除安全组；调用[ModifyNetworkInterfaceAttribute](~~58513~~)接口将弹性网卡（ENI）加入或移除安全组。

调用该接口时，您需要注意：

-   移出安全组之前，实例必须处于**已停止**（Stopped）或者**运行中**（Running）状态。
-   一台实例必须至少加入一个安全组，当该实例只加入了一个安全组时，则LeaveSecurityGroup请求会失败。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=LeaveSecurityGroup&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|LeaveSecurityGroup|系统规定参数。取值：LeaveSecurityGroup |
|InstanceId|String|是|i-bp67acfmxazb4p\*\*\*\*|实例ID。 |
|SecurityGroupId|String|是|sg-bp67acfmxazb4p\*\*\*\*|安全组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=LeaveSecurityGroup
&InstanceId=i-bp67acfmxazb4p****
&SecurityGroupId=sg-bp67acfmxazb4p****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<LeaveSecurityGroupResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</LeaveSecurityGroupResponse>
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
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|指定的实例不存在，请您检查实例ID是否正确。|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|指定的安全组在该用户账号下不存在，请您检查安全组ID是否正确。|
|403|InstanceLastSecurityGroup|The specified security group is the last security group for the instance.|指定的安全组是实例的最后一个安全组。|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|实例被安全锁定，指定的操作无法完成。|
|403|InstanceNotInSecurityGroup|The instance not in the group.|指定的实例不在安全组内。|
|504|RequestTimeout|The request encounters an upstream server timeout.|上游服务器超时，请求被拒绝。|
|400|InvalidInstanceId.Malformed|The specified parameter "InstanceId" is not valid.|指定的参数InstanceId格式有误。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

