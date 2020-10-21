# AllocatePublicIpAddress

调用AllocatePublicIpAddress为一台ECS实例分配一个固定公网IP地址。

## 接口说明

调用该接口时，您需要注意：

-   分配公网IP地址之前，实例必须处于**运行中**（`Running`）或者**已停止**（`Stopped`）状态。
-   被[安全控制](~~25695~~)的实例的`OperationLocks`中标记了`"LockReason" : "security"`时，不能分配公网IP地址。
-   一台实例只能分配一个公网IP地址。如果实例已经拥有一个公网IP地址，将报错`AllocatedAlready`。
-   重启实例（[RebootInstance](~~25502~~)）或者启动实例（[StartInstance](~~25500~~)）后，新的公网IP地址生效。

除分配公网IP之外，您还可以给VPC类型ECS实例绑定弹性公网IP（EIP）。详情请参见[AssociateEipAddress](~~36017~~)。

**说明：** 当VPC类型实例绑定了EIP后，则无法再分配公网IP。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=AllocatePublicIpAddress&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AllocatePublicIpAddress|系统规定参数。取值：AllocatePublicIpAddress |
|InstanceId|String|是|i-bp1gtjxuuvwj17zr\*\*\*\*|需要分配IP地址的实例ID。 |
|IpAddress|String|否|112.124.\*\*.\*\*|实例的公网IP地址。如果该参数值为空，则默认由系统随机分配IP地址。 |
|VlanId|String|否|100|VLAN ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IpAddress|String|112.124.\*\*.\*\*|实例的公网IP地址。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=AllocatePublicIpAddress
&InstanceId=i-bp1gtjxuuvwj17zr****
&IpAddress=112.124.**.**
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<AllocatePublicIpAddressResponse>
      <RequestId>F2EF6A3B-E345-46B9-931E-0EA094818567</RequestId>
      <IpAddress>112.124.**.**</IpAddress>
</AllocatePublicIpAddressResponse>
```

`JSON` 格式

```
{
    "RequestId": "F2EF6A3B-E345-46B9-931E-0EA094818567",
    "IpAddress": "112.124.**.**"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|指定的实例不存在，请您检查实例ID是否正确。|
|400|InvalidIpAddress.Malformed|The specified parameter "IpAddress" is not valid.|指定的IpAddress不合法。|
|404|InvalidVlanId.NotFound|The VlanId provided does not exist in our records.|指定的虚拟局域网ID不存在。|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|403|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|实例被安全锁定，指定的操作无法完成。|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|包年包月实例已过期，请您续费后再进行操作。|
|404|InvalidIpAddress.NotFound|The specified IP is not in the specified vlan.|指定的IP不在指定的虚拟局域网内。|
|403|IpInUse|The specified IP is already in use.|使用指定IP进行绑定时，IP已经被使用在别的机器上。|
|403|AllocatedAlready|There is an IpAddress allocated already for the specified instance.|使用指定IP进行绑定时，该实例已经被分配了别的IP地址。|
|400|OperationDenied|Specified operation is denied as your instance is in VPC.|由于实例存在于VPC中，指定的操作不合法。|
|400|InsufficientPublicIp|Ip address not found|未找到IP地址。|
|400|AllocateIpInvalidInstanceBandwidth|OperationDenied The InternetMaxBandwidthOut of the specified instance cannot be less than 0.|当前操作无效，请保证最大输出带宽大于0。|
|400|OperationDenied|The specified parameter "VlanId" is not valid or vlan has not enough IP address.|指定的VlanId不合法，或已超出最大IP地址数限制。|
|403|NAT\_PUBLIC\_IP\_BINDING\_FAILED|Binding nat public ip failed|公网IP绑定网关失败。|
|403|NAT\_PUBLIC\_IP\_ALLOCATE\_FAILED|Nat public ip binding failed.|公网IP绑定失败。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

