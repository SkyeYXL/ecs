# ModifyPrepayInstanceSpec

调用ModifyPrepayInstanceSpec升级或者降低一台包年包月ECS实例的实例规格，新实例规格将会覆盖实例的整个生命周期。

## 接口说明

请确保在使用该接口前，您已充分了解[云服务器ECS](https://www.aliyun.com/price/product#/ecs/detail)的计费方式和产品定价。

升级或者降低包年包月实例规格前，您可以通过[DescribeResourcesModification](~~66187~~)查询当前实例支持变配的实例规格。详情请参见Python SDK示例[查询ECS变配的可用资源实践](~~109517~~)。

调用该接口时，您需要注意：

-   已过期实例无法修改实例规格，您可以续费后重新操作。
-   降低实例规格时，您需要注意：
    -   实例必须处于**已停止**（`Stopped`）状态。
    -   您必须指定操作类型，即`OperatorType=downgrade`。
    -   每台实例降低配置次数不能超过三次，即价格差退款不会超过三次。降低配置包括降低实例规格、降低带宽配置、包年包月云盘转换为按量付费云盘等操作。
    -   降低前后的实例规格价格差退款会退还到您的原付费方式中，已使用的代金券不退回。
-   本接口属于异步操作，等待约5~10秒后配置变更完成。随后，您必须调用API或者在控制台重启一次实例，否则规格变更不会生效，重启操作系统无效。
    -   若实例处于**已停止**状态，仅需启动实例，无需重启。
    -   若实例设置了`RebootWhenFinished=true`，则无需单独重启。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=ModifyPrepayInstanceSpec&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyPrepayInstanceSpec|系统规定参数。取值：ModifyPrepayInstanceSpec |
|InstanceId|String|是|i-bp67acfmxazb4ph\*\*\*\*|实例ID。 |
|InstanceType|String|是|ecs.g5.xlarge|需要变配的目标实例规格。取值请参见[实例规格族](~~25378~~)或者调用[DescribeInstanceTypes](~~25620~~)。 |
|RegionId|String|是|cn-hangzhou|实例所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|OperatorType|String|否|upgrade|操作类型。取值范围：

 -   upgrade（默认）：升级实例规格。请确保您的账户支付方式余额充足。
-   downgrade：降配实例规格。当`InstanceType`设置的实例规格低于当前实例规格时，您必须设置`OperatorType=downgrade`。

 **说明：** 升级或降低实例规格的注意事项请参见上文接口说明章节。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。更多详情，请参见[如何保证幂等性](~~25693~~)。 |
|AutoPay|Boolean|否|true|升级实例规格时，是否自动支付。取值范围：

 -   true（默认）：自动支付。

**说明：** 您需要确保支付方式余额充足，否则会生成异常订单，只能作废订单。如果您的支付方式余额不足，可以将参数`AutoPay`置为`false`，此时会生成未支付订单，您可以登录ECS管理控制台自行支付。

-   false：只生成订单不扣费。

 当参数`OperatorType`被置为`downgrade`时，将忽略参数`AutoPay`。 |
|MigrateAcrossZone|Boolean|否|false|是否支持跨集群升级实例规格。

 默认值：false

 当参数MigrateAcrossZone取值为true时，一旦您根据返回信息升级了云服务器，请留意以下注意事项：

 经典网络类型实例：

 -   对于[已停售的实例规格](~~55263~~)，非I/O优化实例变配到I/O优化实例时，实例私网IP地址、磁盘设备名和软件授权码会发生变化。对于Linux实例，普通云盘（cloud）会被识别为xvda或者xvdb等，高效云盘（cloud\_efficiency）和SSD云盘（cloud\_ssd）会被识别为vda或者vdb等。
-   对于[正常售卖的实例规格族](~~25378~~)，实例的私网IP地址会发生变化。

 专有网络VPC类型实例：对于已停售的实例规格，非I/O优化实例变配到I/O优化实例时，云服务器磁盘设备名和软件授权码会发生变化。Linux实例的普通云盘（cloud）会被识别为xvda或者xvdb等，高效云盘（cloud\_efficiency）和SSD云盘（cloud\_ssd）会被识别为vda或者vdb等。 |
|SystemDisk.Category|String|否|cloud\_efficiency|更换系统盘类型。该参数只有在从[已停售的实例规格](~~55263~~)升级到[正常售卖的实例规格族](~~25378~~)，并将非I/O优化实例规格升级为I/O优化实例规格时有效。取值范围：

 -   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD云盘 |
|RebootTime|String|否|2018-01-01T12:05Z|实例的重启时间。按照[ISO8601](~~25696~~)标准表示，使用UTC+0时间。格式为：yyyy-MM-ddTHH:mmZ。 |
|EndTime|String|否|2018-01-01T12:05Z|临时变更的终止时间。按照[ISO8601](~~25696~~)标准表示，使用UTC+0时间。格式为：yyyy-MM-ddTHH:mmZ。 |
|RebootWhenFinished|Boolean|否|false|实例变配结束后是否立即重启。取值范围：

 默认值：false

 **说明：** 若实例处于**停止中**状态，即使您设置了`RebootWhenFinished=true`，也会保持原状态不变，并不会执行任何操作。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|String|1234567890|生成的订单ID。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=ModifyPrepayInstanceSpec
&RegionId=cn-hangzhou
&InstanceId=i-bp67acfmxazb4ph****
&InstanceType=ecs.g5.xlarge
&AutoPay=true
&OperatorType=upgrade
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyPrepayInstanceSpecResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <OrderId>1234567890</OrderId>
</ModifyPrepayInstanceSpecResponse>
```

`JSON` 格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "OrderId": "1234567890"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|指定的地域ID不存在。|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|指定的实例规格未授权使用。|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|您指定的实例规格不存在，或者您没有权限操作此规格的实例。|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|404|BillingMethodNotFound|The account has not chosen any billing method.|该帐户没有选择任何计费方法。|
|403|OperationDenied.NoStock|The specified instance is out of usage.|指定的实例库存不足。|
|400|InvalidBillingMethod.ValueNotSupported|The operation is not permitted due to an invalid billing method of the instance.|由于实例的计费方式无效，该操作不允许。|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|指定的实例不存在，请您检查实例ID是否正确。|
|400|InvalidInstance.PurchaseNotFound|The specified instance has no purchase history.|该实例的订购记录不存在。|
|400|InvalidInstanceType.NotSupported|The specified InstanceType is not Supported.|不支持指定的InstanceType。|
|400|OrderCreationFailed|Order creation failed, please check your params and try it again later.|订单创建失败，请修改参数后重试。|
|400|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|请求被流控，请稍后重试。|
|400|Account.Arrearage|Your account has an outstanding payment.|您的账号存在未支付的款项。|
|403|InvalidUser.PassRoleForbidden|The RAM user does not have privilege to pass a role.|RAM子账号不具备授予ECS RAM角色的权限。|
|400|InvalidRebootTime.MalFormed|The specified rebootTime is not valid.|指定的RebootTime不合法。|
|400|InvalidRebootTime.ValueNotSupported|The specified RebootTime is not valid.|指定的重启时间不合法。|
|403|ImageNotSupportInstanceType|The specified image does not support the specified InstanceType.|指定的镜像不支持指定的实例规格。|
|403|InstanceType.Offline|%s|实例规格已停售或者供货不足。|
|400|IdempotenceParamNotMatch|Request uses a client token in a previous request but is not identical to that request.|与相同ClientToken的请求参数不符合。|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|400|IdempotenceParamNotMatch|%s|幂等参数不匹配。|
|400|InvalidInstanceChargeType.ValueNotSupported|%s|暂不支持此付款类型，请核对相关信息后重试。|
|400|InvalidStatus.NotStopped|Instance status must be stopped.|实例只有在已停止的状态下，才能进行此操作。|
|400|InvalidAction|%s|操作无效。|
|400|InstanceDowngrade.QuotaExceed|Quota of instance downgrade is exceed.|您的实例降配已超额度，无法进行此操作。|
|400|InvalidInstanceType.ValueNotSupported|%s|该操作暂不支持指定的实例类型。|
|403|InvalidParameter.InstanceId|%s|指定的参数InstanceId无效。|
|400|InvalidParameter|%s|无效的参数。|
|403|OperationDenied|%s|拒绝操作。|
|403|ImageNotSupportInstanceType|The specified instanceType is not supported by instance with marketplace image.|指定的市场镜像不支持该实例规格。|
|403|InvalidInstanceStatus|The current status of the instance does not support this operation.|当前实例的状态不支持此操作。|
|403|InvalidInstance.PreInstanceExpired|Instance business status is not Expired|当前实例已经过期。|
|403|InvalidInstance.EipNotSupport|The special instance with eip not support operate, please unassociate eip first.|已绑定EIP的实例不支持该操作，请优先解绑EIP。|
|400|OperationDenied|The current user does not support this operation.|您使用的账号暂不支持此操作。|
|403|OperationDenied.LocalDiskUnsupported|The configuration change is not allowed when the specified instance has local disks mounted.|实例挂载本地盘后不支持规格变配。|
|403|OperationDenied.NoStock|The resource is out of stock in the specified zone. Please try other types, or choose other regions and zones.|指定的资源在指定可用区中无货。请尝试其他类型，或选择其他可用区和地域。|
|400|LastOrderProcessing|The previous order is still processing, please try again later.|订单正在处理中，稍后重试。|
|403|InvalidOperation.Ipv4CountExceeded|%s|IPv4数量达到上限，导致该操作无效。|
|403|InvalidOperation.Ipv6CountExceeded|%s|IPv6数量达到上限，导致该操作无效。|
|403|InvalidOperation.Ipv6NotSupport|%s|IPv6不支持当前操作。|
|500|InternalError|The request processing has failed due to some unknown error.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|403|QuotaExceed.ElasticQuota|No additional quota is available for the specified ECS instance type.|您在当前地域选择的实例规格所要创建的台数超出系统限额，您可以选择其他地域、实例规格或减少台数重新购买，也可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type.|您在当前地域选择的实例规格所要创建的台数超出系统限额，您可以选择其他地域、实例规格或减少台数重新购买，也可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|您的全实例规格vCPU配额超出系统限额，您可以前往ECS管理控制台或配额中心申请提高限额。|
|403|QuotaExceed.ElasticQuota|The number of the specified ECS instances has exceeded the quota of the specified instance type, or the number of vCPUs assigned to the ECS instances has exceeded the quota in the zone.|您在当前地域选择的实例规格所要创建的台数超出系统限额，或者全实例规格vCPU配额超出系统限额，您可以前往ECS管理控制台或配额中心申请提高限额。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

