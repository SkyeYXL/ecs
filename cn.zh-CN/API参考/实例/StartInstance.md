# StartInstance

调用StartInstance启动一台ECS实例，接口调用成功后实例进入启动中状态。

## 接口说明

调用该接口时，您需要注意：

-   ECS实例状态必须为**已停止**（`Stopped`）。
-   被[安全控制](~~25695~~)的实例`OperationLocks`中标记了`"LockReason" : "security"`的锁定状态时，不能启动实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=StartInstance&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartInstance|系统规定参数。取值：StartInstance |
|InstanceId|String|是|i-bp67acfmxazb4p\*\*\*\*|指定启动的实例ID。 |
|InitLocalDisk|Boolean|否|true|适用于实例规格族d1、i1或者i2等包含本地盘的实例。当d1、i1或者i2的本地盘出现故障时，可通过此参数指定启动实例时，是否将实例恢复到最初的健康状态。取值范围：

 -   true：将实例恢复到最初的健康状态，实例原有本地盘中的数据将会丢失。
-   false（默认）：不做任何处理，维持现状。 |
|DryRun|Boolean|否|true|是否只预检查此次请求。取值范围：

 -   true：仅检查此次请求，不会启动实例。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码DryRunOperation。
-   false（默认）：发送正常请求，请求通过检查后，返回2XX HTTP状态码并直接启动实例。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=StartInstance
&InstanceId=i-bp67acfmxazb4p****
&InitLocalDisk=true
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<StartInstanceResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</StartInstanceResponse>
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
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|实例被安全锁定，指定的操作无法完成。|
|403|InsufficientBalance|Your account does not have enough balance.|账户余额不足，请先充值再操作。|
|500|InstanceNotReady|The specified instance is not ready for use|暂时无法连接指定的实例，请稍后再试。|
|500|InternalError|The request processing has failed due to some unknown error.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|403|DiskError|IncorrectDiskStatus.|指定的磁盘状态不合法。|
|403|InstanceExpired|The postPaid instance has been expired.Please ensure your account have enough balance.|按量付费的实例已过期。请确保您的帐户有足够的余额。|
|403|InstanceExpired|The prePaid instance has been expired.|包年包月实例已到期。|
|403|InstanceNotReady|The specified instance is not ready for use.|该资源目前的状态不支持此操作，请您等待一段时间再进行操作，并确认实例目前状态与操作是否冲突。|
|403|DiskInArrears|The specified operation is denied as your disk has expired.|磁盘欠费过期。|
|403|OperationDenied.NoStock|The requested resource is sold out in the specified zone; try other types of resources or other regions and zones.|库存不足。|
|403|OperationDenied.SpotPriceLowerThanPublicPrice|The spot instance price is lower than public price.|抢占式实例的竞价价格不能低于公开的价格。|
|403|IncorrectInstanceStatus|%s|当前实例的状态不支持此操作。|
|403|InvalidParameter.KMSKeyId.KMSUnauthorized|ECS service have no right to access your KMS.|ECS服务无权访问您的KMS。|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|403|QuotaExceed.ElasticQuota|No additional quota is available for the specified ECS instance type.|您在当前地域选择的实例规格所要创建的台数超出系统限额，您可以选择其他地域、实例规格或减少台数重新购买，也可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type.|您在当前地域选择的实例规格所要创建的台数超出系统限额，您可以选择其他地域、实例规格或减少台数重新购买，也可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|您的全实例规格vCPU配额超出系统限额，您可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type, or the number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|您在当前地域选择的实例规格所要创建的台数超出系统限额，或者全实例规格vCPU配额超出系统限额，您可以前往ECS管理控制台或配额中心申请提高限额。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

