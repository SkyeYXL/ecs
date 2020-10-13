# SendFile

调用SendFile向一台或多台ECS实例下发远程文件。

## 接口说明：

-   目标ECS实例的状态必须为运行中（`Running`）。
-   目标ECS实例必须预先安装云助手客户端。详情请参见[InstallCloudAssistant](~~85916~~)。
-   云助手客户端版本需要高于以下对应的版本才能支持下发文件。如果结果返回`ClientNeedUpgrade`错误码，请参见[升级或禁止升级云助手客户端](~~134383~~)文档，将客户端更新至最新版本。
    -   Linux：1.0.2.569
    -   Windows：1.0.0.149
-   文件内容在进行Base64编码后，大小不能超过32 KB。
-   文件下发可能会因为目标ECS实例的状态异常、网络异常或云助手客户端异常而出现失败的情况。请调用[DescribeSendFileResults](~~~~)进行问题排查。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=SendFile&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SendFile|系统规定参数。取值：SendFile |
|RegionId|String|是|cn-hangzhou|目标ECS实例所在的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|Name|String|是|file.txt|文件名称。支持全字符集，长度不得超过255个字符。 |
|InstanceId.N|RepeatList|是|i-bp185dy2o3o6n\*\*\*\*|需要执行命令的ECS实例列表。最多能指定50台ECS实例ID。N的取值范围：1~50 |
|TargetDir|String|是|/home|文件下发目标ECS实例中的目录。如不存在则会自动创建。 |
|Content|String|是|\#!/bin/bash echo "Current User is :" echo $\(ps \| grep "$$" \| awk '\{print $2\}'\) -------- oss://bucketName/objectName|文件内容。文件内容在Base64编码后，大小不能超过32 KB。

 -   当`ContentType`参数为`PlainText`时，该字段为明文格式的普通文本。
-   当`ContentType`参数为`Base64`时，该字段为Base64编码的文本。 |
|Description|String|否|This is a test file.|描述信息。支持全字符集，长度不得超过512个字符。 |
|ContentType|String|否|PlainText|文件内容类型。

 -   PlainText：普通文本
-   Base64：Base64编码

 默认值：PlainText |
|Timeout|Long|否|60|下发文件的超时时间。单位：秒

 -   当因为进程原因、缺失模块、缺失云助手客户端等原因无法下发文件时，会出现超时现象。
-   当设置的超时时间小于10秒时，为确保下发成功，系统会将超时时间自动设置为10秒。

 默认值：60 |
|FileOwner|String|否|root|文件的用户。只对Linux实例生效，默认为root。 |
|FileGroup|String|否|root|文件的用户组。只对Linux实例生效，默认为root。 |
|FileMode|String|否|0644|文件的权限。只对Linux实例生效，设置方式与chmod命令相同。

 默认值为0644，表示用户具有读写权限，用户组和其它用户具有只读权限。 |
|Overwrite|Boolean|否|true|如果同名文件在目标目录已存在，是否覆盖文件。

 -   true：覆盖
-   false：不覆盖

 默认值：false |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|InvokeId|String|f-7d2a745b412b46\*\*\*\*|命令执行ID。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=SendFile
&Content='echo hello'
&InstanceId.1=i-bp185dy2o3o6n****
&Name=file.txt
&RegionId=cn-hangzhou
&TargetDir=/home
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SendFileResponse>
          <RequestId>E69EF3CC-94CD-42E7-8926-F133B86387C0</RequestId>
          <InvokeId>f-7d2a745b412b46****</InvokeId>
</SendFileResponse>
```

`JSON` 格式

```
{
    "RequestId": "E69EF3CC-94CD-42E7-8926-F133B86387C0",
    "InvokeId": "f-7d2a745b412b46****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError.Dispatch|An error occurred when you dispatched the request.|发送请求时发生错误，请稍后重试。|
|403|FileSize.ExceedLimit|The length of file content exceeds limit.|文件内容长度超过上限。|
|403|FileName.ExceedLimit|The length of file name exceeds limit.|文件名称长度超过上限。|
|403|FileDesc.ExceedLimit|The length of file description exceeds limit.|文件描述长度超过上限。|
|403|FileTargetDir.Invalid|The target directory of file is invalid.|目标路径TargetDir参数无效。|
|403|InstanceIds.ExceedLimit|The number of instance IDs exceeds the upper limit.|目标实例数量超过上限。|
|403|FileMode.Invalid|The mode of file is invalid.|文件权限FileMode参数无效。|
|403|FileContent.DecodeError|The Content can not be base64 decoded.|文件内容Base64解码错误。|
|403|FileContentType.Invalid|The ContentType of file is invalid.|文件内容类型ContentType参数无效。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

