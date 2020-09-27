# PurchaseStorageCapacityUnit

调用PurchaseStorageCapacityUnit购买一个或多个存储容量单位包SCU（Storage Capacity Unit）。SCU是一种预付费的存储容量资源包，可以抵扣同一地域下按量付费云盘的计费账单。

## 接口说明

请确保在使用该接口前，已充分了解存储容量单位包SCU的收费方式和价格。详情请参见[存储容量单位包计费方式](~~137897~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=PurchaseStorageCapacityUnit&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|PurchaseStorageCapacityUnit|系统规定参数。取值：PurchaseStorageCapacityUnit |
|RegionId|String|是|cn-hangzhou|SCU所属的地域ID。确定地域后，SCU只能抵扣该地域下云盘的按量付费账单。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|Capacity|Integer|是|20|SCU容量大小，单位为GiB。取值范围：\{20, 40, 100, 200, 500, 1024, 2048, 5120, 10240, 20480, 51200\} |
|Name|String|否|ScuPurchaseDemo|SCU的名称，长度为2~128个英文或中文字符。必须以大小写字母或中文开头，不能以http://和https://开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 默认值：空 |
|Description|String|否|ScuPurchaseDemo|SCU的描述信息，长度为2~256个英文或中文字符，不能以http://和https://开头。

 默认值：空 |
|PeriodUnit|String|否|Month|SCU的有效期时长单位。取值范围：

 -   Month：月。此时Period参数的有效取值为\{1, 2, 3, 6\}
-   Year：年。此时Period参数的有效取值为\{1, 3, 5\}

 默认值：Month |
|Period|Integer|否|1|SCU的有效期时长。取值范围：\{1, 2, 3, 5, 6\}

 默认值：1 |
|StartTime|String|否|2020-09-09T02:00:00Z|SCU的生效时间，不得早于创建时间和晚于创建时间六个月内。按照ISO8601标准表示，并使用UTC +0时间，格式为yyyy-MM-ddTHH:mm:ssZ。

 默认值：无，表示从创建时间开始生效。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。更多详情，请参见[如何保证幂等性](~~25693~~)。 |
|Amount|Integer|否|1|购买的SCU的数量。取值范围：1~20

 默认值：1 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|String|204135153880\*\*\*\*|订单ID。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |
|StorageCapacityUnitIds|List|scu-bp67acfmxazb4p\*\*\*\*|SCU ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=PurchaseStorageCapacityUnit
&Capacity=20
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<PurchaseStorageCapacityUnitResponse>
      <OrderId>204135153880***</OrderId>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <StorageCapacityUnitIds>
            <StorageCapacityUnitId>scu-bp67acfmxazb4p****</StorageCapacityUnitId>
      </StorageCapacityUnitIds>
</PurchaseStorageCapacityUnitResponse>
```

`JSON` 格式

```
{
    "OrderId": "204135153880****",
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
    "StorageCapacityUnitIds": {
        "StorageCapacityUnitId": "scu-bp67acfmxazb4p****"
    }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter.Period|The specified Period is not valid.|指定的生效日期无效。|
|400|MissingParameter.RegionId|The specified RegionId should not be null.|RegionId是必选参数。|
|400|InvalidParameter.Name|The specified Name is invalid.|指定的Name参数无效。|
|400|InvalidParameter.Capacity|The specified Capacity is invalid.|指定的Capacity参数不在有效取值范围内。|
|400|MissingParameter.Capacity|The specified Capacity should be not null.|Capacity为必选参数。|
|400|InvalidParameter.PeriodUnit|The specified PeriodUnit is not supported.|指定的PeriodUnit参数不在有效的取值范围内。|
|400|InvalidParameter.CapacityExceed|The specified Capacity exceeds the limitation of quota.|指定的Capacity参数超出了最大有效取值。|
|400|InvalidStartTime.NotSupported|The specified StartTime should be within 180 calendar days from the current date, and you must specify a precision to hour.|指定的StartTime参数不在有效取值范围内。|
|400|InvalidStartTime.MalFormed|The specified StartTime is out of the permitted range.|指定的StartTime参数超出了最大有效取值。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

