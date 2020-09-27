# ModifyStorageCapacityUnitAttribute

调用ModifyStorageCapacityUnitAttribute修改一个存储容量单位包SCU的名称或者描述信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=ModifyStorageCapacityUnitAttribute&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyStorageCapacityUnitAttribute|系统规定参数。取值：ModifyStorageCapacityUnitAttribute |
|RegionId|String|是|cn-hangzhou|SCU所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|StorageCapacityUnitId|String|是|scu-bp67acfmxazb4p\*\*\*\*|SCU ID。 |
|Name|String|否|testNewScuName|SCU的新名称，长度为2~128个英文或中文字符。必须以大小写字母或中文开头，不能以http://和https://开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。 |
|Description|String|否|testNewScuDescription|SCU的新描述信息，长度为2~256个英文或中文字符，不能以http://和https://开头。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=ModifyStorageCapacityUnitAttribute
&RegionId=cn-qingdao
&StorageCapacityUnitId=scu-bp67acfmxazb4p****
&Name=testNewScuName
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyStorageCapacityUnitAttributeResponse>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyStorageCapacityUnitAttributeResponse>
```

`JSON` 格式

```
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter.RegionId|The specified RegionId should not be null.|RegionId是必选参数。|
|400|InvalidParameter.Name|The specified Name is invalid.|指定的Name参数无效。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

