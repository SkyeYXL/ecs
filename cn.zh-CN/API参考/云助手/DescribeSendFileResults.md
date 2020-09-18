# DescribeSendFileResults

调用DescribeSendFileResults查询云助手下发文件列表及状态。

## 接口说明

-   当您下发文件后，不代表文件一定成功下发。您需要通过接口返回值查看实际下发结果，并以实际输出结果为准。
-   您可以查询最近2周的下发记录，下发记录的保留上限为10万条。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeSendFileResults&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSendFileResults|系统规定参数。取值：DescribeSendFileResults |
|RegionId|String|是|cn-hangzhou|ECS实例所在的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|InvokeId|String|否|f-hz0jdfwd9f\*\*\*\*|执行ID。 |
|InstanceId|String|否|i-hz0jdfwd9f\*\*\*\*|实例ID。传入该参数后，将查询该实例所有的文件下发记录。 |
|Name|String|否|test.txt|文件名称。传入该参数后，将查询该名称文件的所有的下发记录。 |
|PageNumber|Long|否|1|当前页码。

 起始值：1

 默认值：1 |
|PageSize|Long|否|10|分页查询时设置的每页行数。

 最大值：50

 默认值：10 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Invocations|Array of Invocation| |文件下发记录。 |
|Invocation| | | |
|Content|String|\#!/bin/bash echo "Current User is :" echo $\(ps \| grep "$$" \| awk '\{print $2\}'\)|文件内容。 |
|ContentType|String|PlainText|文件内容类型。可能值：

 -   PlainText：普通文本
-   Base64：Base64编码 |
|CreationTime|String|2019-12-20T06:15:54Z|文件下发任务创建时间。 |
|Description|String|This is a test file.|描述信息。 |
|FileGroup|String|root|文件的用户组。 |
|FileMode|String|777|文件的权限。 |
|FileOwner|String|root|文件的用户。 |
|InvocationStatus|String|Success|文件的总下发状态。总状态取决于本次下发的全部实例的共同执行状态，可能值：

 -   Pending：系统正在校验或下发文件。存在至少一台实例的下发状态为Pending，则总状态为Pending。
-   Running：文件创建任务正在实例上运行。存在至少一台实例的状态为Running，则总状态为Running。
-   Success：各个实例上的文件下发状态均为Success，则总执行状态为Success。
-   Failed：各个实例上的文件下发状态均为Failed，则总执行状态为Failed。实例上的文件下发状态一项或多项为以下状态时，返回值均为Failed状态：
    -   校验失败（Invalid）
    -   文件发送失败（Aborted）
    -   文件创建失败（Failed）
    -   文件下发超时（Timeout）
    -   文件下发异常（Error）
-   PartialFailed：部分实例下发成功且部分实例执行失败。存在且只存在实例下发状态为Success与Failed时，则总执行状态为PartialFailed。 |
|InvokeId|String|f-hz0jdfwd9f\*\*\*\*|执行ID。 |
|InvokeInstances|Array of InvokeInstance| |下发文件目标实例集类型。 |
|InvokeInstance| | | |
|CreationTime|String|2019-12-20T06:15:54Z|文件下发任务的创建时间。 |
|ErrorCode|String|InstanceNotExists|文件下发的失败原因代码。可能值：

 -   空：文件下发正常。
-   InstanceNotExists：指定的实例不存在或已释放。
-   InstanceReleased：下发文件期间，该实例被释放。
-   InstanceNotRunning：创建下发文件任务时，该实例不在运行中。
-   AccountNotExists：指定的帐号不存在。
-   ClientNotRunning：云助手客户端未运行。
-   ClientNotResponse：云助手客户端无响应。
-   ClientIsUpgrading：云助手客户端正在升级中。
-   ClientNeedUpgrade：云助手客户端需要升级。
-   DeliveryTimeout：发送文件超时。
-   FileCreateFail：文件创建失败。
-   FileAlreadyExists：相同路径下存在同名文件。
-   FileContentInvalid：文件内容不合法。
-   FileNameInvalid：文件名不合法。
-   FilePathInvalid：文件路径不合法。
-   FileAuthorityInvalid：文件权限不合法。 |
|ErrorInfo|String|the instance is not running when create task|文件下发的失败或执行失败原因详情。可能值：

 -   空：文件下发正常。
-   the specified instance does not exists：指定的实例不存在或已释放。
-   the instance has released when create task：下发文件期间，该实例被释放。
-   the instance is not running when create task：创建下发文件任务时，该实例不在运行中。
-   the specified account does not exists：指定的帐号不存在。
-   the aliyun service is not running on the instance：云助手客户端未运行。
-   the aliyun service in the instance does not response：云助手客户端无响应。
-   the aliyun service in the instance is upgrading now：云助手客户端正在升级中。
-   the aliyun service in the instance need upgrade：云助手客户端需要升级。
-   the command delivery has been timeout：下发文件超时。
-   Unexpected error during creating：文件创建失败。
-   File already exists：相同路径下存在同名文件。
-   File content error：文件内容不合法。
-   File name is invalid：文件名不合法。
-   File path is invalid：文件路径不合法。
-   Owner not exists：用户不存在。
-   Group not exists：用户组不存在。
-   Mode is invalid：文件权限设置不合法。 |
|FinishTime|String|2019-12-20T06:15:54Z|下发任务的结束时间。 |
|InstanceId|String|i-uf614fhehhz\*\*\*\*|实例ID。 |
|InvocationStatus|String|Success|下发任务的状态。 |
|StartTime|String|2019-12-20T06:15:54Z|下发任务在实例中开始执行的时间。 |
|UpdateTime|String|2019-12-20T06:15:54Z|任务状态的更新时间。 |
|Name|String|test.txt|文件名称。 |
|Overwrite|String|false|是否允许覆盖。 |
|TargetDir|String|/root|目标路径。 |
|VmCount|Integer|1|下发实例的数量。 |
|PageSize|Long|10|每页行数。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |
|TotalCount|Long|2|脚本总个数。 |
|PageNumber|Long|1|查询结果的当前页码。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=DescribeSendFileResults
&RegionId=cn-hangzhou
&InvokeId=f-hz0vk9****
&Name=test.txt
&InstanceId=i-bp1hsglsw****
&PageNumber=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeSendFileResultsResponse>
      <TotalCount>1</TotalCount>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <PageSize>10</PageSize>
      <PageNumber>1</PageNumber>
      <Invocations>
            <Invocation>
                  <FileMode>0644</FileMode>
                  <Overwrite>false</Overwrite>
                  <InvocationStatus>Success</InvocationStatus>
                  <Description>This is a test file.</Description>
                  <ContentType>PlainText</ContentType>
                  <VmCount>1</VmCount>
                  <TargetDir>/root</TargetDir>
                  <FileGroup>root</FileGroup>
                  <FileOwner>root</FileOwner>
                  <InvokeInstances>
                        <InvokeInstance>
                              <InvocationStatus>Success</InvocationStatus>
                              <FinishTime>2020-09-11T08:30:55Z</FinishTime>
                              <InstanceId>i-bp1hsglsw****</InstanceId>
                              <ErrorInfo></ErrorInfo>
                              <CreationTime>2020-09-11T08:30:55Z</CreationTime>
                              <StartTime>2020-09-11T08:30:55Z</StartTime>
                              <UpdateTime>2020-09-11T08:30:55Z</UpdateTime>
                              <ErrorCode></ErrorCode>
                        </InvokeInstance>
                  </InvokeInstances>
                  <Name>test.txt</Name>
                  <Content>ZWNobyBoZWxsbw==</Content>
                  <CreationTime>2020-09-11T08:30:55Z</CreationTime>
                  <InvokeId>f-hz0vk9****</InvokeId>
            </Invocation>
      </Invocations>
</DescribeSendFileResultsResponse>
```

`JSON` 格式

```
{
  "TotalCount": 1,
  "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
  "PageSize": 10,
  "PageNumber": 1,
  "Invocations": {
    "Invocation": [
      {
        "FileMode": "0644",
        "Overwrite": false,
        "InvocationStatus": "Success",
        "Description": "This is a test file.",
        "ContentType": "PlainText",
        "VmCount": 1,
        "TargetDir": "/root",
        "FileGroup": "root",
        "FileOwner": "root",
        "InvokeInstances": {
          "InvokeInstance": [
            {
              "InvocationStatus": "Success",
              "FinishTime": "2020-09-11T08:30:55Z",
              "InstanceId": "i-bp1hsglsw****",
              "ErrorInfo": "",
              "CreationTime": "2020-09-11T08:30:55Z",
              "StartTime": "2020-09-11T08:30:55Z",
              "UpdateTime": "2020-09-11T08:30:55Z",
              "ErrorCode": ""
            }
          ]
        },
        "Name": "test.txt",
        "Content": "ZWNobyBoZWxsbw==",
        "CreationTime": "2020-09-11T08:30:55Z",
        "InvokeId": "f-hz0vk9****"
      }
    ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError.Dispatch|An error occurred when you dispatched the request.|发送请求时发生错误，请稍后重试。|
|403|InvalidParam.PageNumber|The specified parameter is invalid.|指定的PageNumber参数无效。|
|403|InvalidParam.PageSize|The specified parameter is invalid.|指定的PageSize参数无效。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

