# DescribeKeyPairs

调用DescribeKeyPairs查询一个或多个密钥对。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeKeyPairs&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeKeyPairs|系统规定参数。取值：DescribeKeyPairs |
|RegionId|String|是|cn-hangzhou|密钥对所在的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|KeyPairName|String|否|\*SshKey\*|密钥对名称。支持正则表达式模糊搜索，使用\*匹配子表达式，示例：

 -   `*SshKey`：查询以SshKey结尾的密钥对名称，包括SshKey。
-   `SshKey*`：查询以SshKey开头的密钥对名称，包括SshKey。
-   `*SshKey*`：查询名称中间有SshKey的密钥对，包括SshKey。
-   `SshKey`：精确匹配SshKey。 |
|KeyPairFingerPrint|String|否|ABC1234567|密钥对的指纹。根据RFC4716定义的公钥指纹格式，采用MD5信息摘要算法。更多详情，请参见[RFC4716](https://tools.ietf.org/html/rfc4716)。 |
|PageNumber|Integer|否|1|密钥对列表的页码。起始值：1

 默认值：1 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。最大值：50

 默认值：10 |
|Tag.N.Key|String|否|TestKey|密钥对的标签键。N的取值范围：1~20

 使用一个标签过滤资源，查询到该标签下的资源数量不能超过1000个；使用多个标签过滤资源，查询到同时绑定了多个标签的资源数量不能超过1000个。如果资源数量超过1000个，请使用[ListTagResources](~~110425~~)接口进行查询。 |
|Tag.N.Value|String|否|TestValue|密钥对的标签值。N的取值范围：1~20 |
|ResourceGroupId|String|否|rg-amnhr7u7c7hj\*\*\*\*|密钥对所在的企业资源组ID。使用该参数过滤资源时，资源数量不能超过1000个。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|KeyPairs|Array of KeyPair| |密钥对信息集合。 |
|KeyPair| | | |
|CreationTime|String|2019-12-04T13:35:00Z|密钥对的创建时间。 |
|KeyPairFingerPrint|String|ABC1234567|密钥对的指纹。 |
|KeyPairName|String|testKeyPairName|密钥对的名称。 |
|ResourceGroupId|String|rg-amnhr7u7c7hj\*\*\*\*|资源组ID。 |
|Tags|Array of Tag| |密钥对的标签。 |
|Tag| | | |
|TagKey|String|TestKey|密钥对的标签键。 |
|TagValue|String|TestValue|密钥对的标签值。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|10|每页行数。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |
|TotalCount|Integer|1|密钥对的总数。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=DescribeKeyPairs
&RegionId=cn-qingdao
&KeyPairFingerPrint=ABC1234567
&KeyPairName=SshKey
&PageNumber=1
&PageSize=20
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeKeyPairsResponse>
      <PageNumber>1</PageNumber>
      <PageSize>2</PageSize>
      <TotalCount>1</TotalCount>
      <KeyPairs>
            <KeyPair>
                  <CreationTime>2018-10-10T01:00Z</CreationTime>
                  <ResourceGroupId></ResourceGroupId>
                  <KeyPairName>testKeyPairName</KeyPairName>
                  <KeyPairFingerPrint>ABC1234567</KeyPairFingerPrint>
            </KeyPair>
      </KeyPairs>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DescribeKeyPairsResponse>
```

`JSON` 格式

```
{
	"PageNumber": 1,
	"PageSize": 2,
	"TotalCount": 1,
	"KeyPairs": {
		"KeyPair": [{
			"CreationTime": "2018-10-10T01:00Z",
			"ResourceGroupId": "",
			"KeyPairName": "testKeyPairName",
			"KeyPairFingerPrint": "ABC1234567"
		}]
	},
	"RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

