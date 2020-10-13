# DescribeSendFileResults

You can call this operation to query the files sent by Cloud Assistant and their status.

## Description

-   When you send a file, the file may fail to be sent to specified instances. You must call this operation to check the file sending results.
-   You can call this operation to query the file sending records of the last two weeks. A maximum of 100,000 file sending records can be retained.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSendFileResults&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSendFileResults|The operation that you want to perform. Set the value to DescribeSendFileResults. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InvokeId|String|No|f-hz0jdfwd9f\*\*\*\*|The ID of the execution. |
|InstanceId|String|No|i-hz0jdfwd9f\*\*\*\*|The ID of the instance for which you want to query file sending results. |
|Name|String|No|test.txt|The name of the file about which you want to query sending records. |
|PageNumber|Long|No|1|The number of the page to return.

Pages start from page 1.

Default: 1 |
|PageSize|Long|No|10|The number of entries to return on each page.

Valid values: 1 to 50.

Default value: 10 |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Invocations|Array of Invocation| |Details about the file sending records. |
|Invocation| | | |
|Content|String|\#! /bin/bash echo "Current User is :" echo $\(ps \| grep "$$" \| awk '\{print $2\}'\)|The content of the file. |
|ContentType|String|PlainText|The content type of the file. Valid values:

-   PlainText
-   Base64 |
|CreationTime|String|2019-12-20T06:15:54Z|The time when the file sending task was created. |
|Description|String|This is a test file.|The description of the file. |
|FileGroup|String|root|The group of the file. |
|FileMode|String|777|The permissions on the file. |
|FileOwner|String|root|The owner of the file. |
|InvocationStatus|String|Success|The overall sending status of the file. The overall sending status of the file depends on its sending status on all the destination instances. Valid values:

-   Pending: The system is verifying or sending the file. If the sending status of the file on at least one instance is Pending, the overall sending status of the file is Pending.
-   Running: The file creation task is running on the instances. If the sending status of the file on at least one instance is Running, the overall sending status of the file is Running.
-   Success: If the sending status of the file on all the instances is Success, the overall sending status of the file is Success.
-   Failed: If the sending status of the file on all the instances is Failed, the overall sending status of the file is Failed. If the sending status of the file on one or more instances is one of the following values, the overall sending status of the file is Failed:
    -   Invalid: The file is invalid.
    -   Aborted: The file failed to be sent.
    -   Failed: The file failed to be created.
    -   Timeout: The file sending task timed out.
    -   Error: An error occurred while the file is being sent.
-   PartialFailed: The file was sent to some of the specified instances and failed to be sent to the others. The overall sending status of the file is PartialFailed only when its sending status is Success on some instances and is Failed on the others. |
|InvokeId|String|f-hz0jdfwd9f\*\*\*\*|The ID of the execution. |
|InvokeInstances|Array of InvokeInstance| |Details about the destination instances. |
|InvokeInstance| | | |
|CreationTime|String|2019-12-20T06:15:54Z|The time when the file sending task was created. |
|ErrorCode|String|InstanceNotExists|The error code returned when the file failed to be sent to the instance. If this parameter is empty, the file was sent to the instance. Valid values:

-   InstanceNotExists: The instance does not exist or was released.
-   InstanceReleased: The instance is released while the file is being sent.
-   InstanceNotRunning: The instance is not running when the file sending task is being created.
-   AccountNotExists: The specified account does not exist.
-   ClientNotRunning: The Cloud Assistant client is not running.
-   ClientNotResponse: The Cloud Assistant client does not respond.
-   ClientIsUpgrading: The Cloud Assistant client is being upgraded.
-   ClientNeedUpgrade: The Cloud Assistant client needs to be upgraded.
-   DeliveryTimeout: The file sending task timed out.
-   FileCreateFail: The file failed to be created.
-   FileAlreadyExists: A file with the same name already exists in the specified directory.
-   FileContentInvalid: The file content is invalid.
-   FileNameInvalid: The file name is invalid.
-   FilePathInvalid: The specified directory is invalid.
-   FileAuthorityInvalid: The specified permissions on the file are invalid. |
|ErrorInfo|String|the instance is not running when create task|The error message returned when the file failed to be sent to the instance or the file sending task failed to be executed on the instance. If this parameter is empty, the file was sent to the instance. Valid values:

-   the specified instance does not exists
-   the instance has released when create task
-   the instance is not running when create task
-   the specified account does not exists
-   the aliyun service is not running on the instance
-   the aliyun service in the instance does not response
-   the aliyun service in the instance is upgrading now
-   the aliyun service in the instance need upgrade
-   the command delivery has been timeout
-   Unexpected error during creating
-   File already exists
-   File content error
-   File name is invalid
-   File path is invalid
-   Owner not exists
-   Group not exists
-   Mode is invalid |
|FinishTime|String|2019-12-20T06:15:54Z|The time when the file sending task finished being executed. |
|InstanceId|String|i-uf614fhehhz\*\*\*\*|The ID of the instance. |
|InvocationStatus|String|Success|The status of the file sending task. |
|StartTime|String|2019-12-20T06:15:54Z|The time when the file sending task started to be executed on the instance. |
|UpdateTime|String|2019-12-20T06:15:54Z|The time when the task status was updated. |
|Name|String|test.txt|The name of the file. |
|Overwrite|String|false|Indicates whether a file in the destination directory is overwritten if the file has the same name as the sent file. |
|TargetDir|String|/root|The destination directory. |
|VmCount|Integer|1|The number of instances to which you attempted to send the file. |
|PageSize|Long|10|The number of entries returned on each page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Long|2|The total number of file sending tasks. |
|PageNumber|Long|1|The page number of the returned page. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeSendFileResults
&RegionId=cn-hangzhou
&InvokeId=f-hz0vk9****
&Name=test.txt
&InstanceId=i-bp1hsglsw****
&PageNumber=1
&PageSize=10
&<Common request parameters>
```

Sample success responses

`XML` format

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
                  <Description>This is a test file. </Description>
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

`JSON` format

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

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|500|InternalError.Dispatch|An error occurred when you dispatched the request.|The error message returned because an error occurred when the request was sent. Try again later.|
|403|InvalidParam.PageNumber|The specified parameter is invalid.|The error message returned because the specified PageNumber parameter is invalid.|
|403|InvalidParam.PageSize|The specified parameter is invalid.|The error message returned because the specified PageSize parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

