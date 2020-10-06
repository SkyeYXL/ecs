# StartInstances

You can call this operation to start one or more ECS instances that are in the Stopped state. After the operation is called, the instances enter the Starting state.

## Description

When you call this operation, take note of the following items:

-   The ECS instances to be started must be in the **Stopped** \(`Stopped`\) state.
-   If the response contains `{"OperationLocks": {"LockReason" : "security"}}` when you query information of an instance, the instance is locked for security reasons and all operations are prohibited on the instance.
-   Batch operations are supported. You can use the `BatchOptimization` parameter to specify the batch operation mode.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=StartInstances&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Position|Type|Required|Example|Description|
|---------|--------|----|--------|-------|-----------|
|Action|Query|String|Yes|StartInstances|The operation that you want to perform. Set the value to StartInstances. |
|InstanceId.N|Query|RepeatList|Yes|i-bp67acfmxazb4p\*\*\*\*|The ID of instance N that you want to start. Valid values of N: 1 to 100. |
|RegionId|Query|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|DryRun|Query|Boolean|No|false|Specifies whether to check the validity of the request without actually making the request. Valid values:

-   true: The validity of the request is checked but the request is not made. Check items include the request format, instance status, and whether the required parameters are specified. If the check fails, the corresponding error is returned. If the check succeeds, `DRYRUN.SUCCESS` is returned.

**Note:** If you set `BatchOptimization` to `SuccessFirst` and `DryRun` to true, only `DRYRUN.SUCCESS` is returned regardless of whether the check succeeds.

-   false: The validity of the request is checked, and the request is made if the check succeeds.

Default value: false. |
|BatchOptimization|Query|String|No|AllTogether|The batch operation mode. Valid values:

-   AllTogether: In this mode, if all instances are started, a success message is returned. If an instance fails the verification, all instances fail to start and an error message is returned.
-   SuccessFirst: In this mode, each instance is started separately. The response contains the operation results for each instance.

Default value: AllTogether. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceResponses|Array of InstanceResponse| |Details about the instance responses, which contain the status of each instance before and after the operation is called and the result of the operation. |
|InstanceResponse| | | |
|Code|String|200|The error code of the operation result. The return value 200 indicates success. For more information, see the "Error codes" section in this topic. |
|CurrentStatus|String|Starting|The current status of the instance. |
|InstanceId|String|i-bp67acfmxazb4p\*\*\*\*|The ID of the instance. |
|Message|String|success|The error message for an instance operation. The return value Success indicates operation success. For more information, see the "Error codes" section in this topic. |
|PreviousStatus|String|Stopped|The status of the instance before the operation is called. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=StartInstances
&InstanceId.1=i-bp67acfmxazb4p****
&InstanceId.2=i-bp67acfmxazb4p****
&RegionId=cn-hangzhou
$BatchOptimization=SuccessFirst
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StartInstancesResponse>
      <RequestId>FF53E96D-3F1A-42F0-8373-1C2B39D72D44</RequestId>
      <InstanceResponses>
            <InstanceResponse>
                  <Message>success</Message>
                  <InstanceId>i-bp67acfmxazb4p****</InstanceId>
                  <PreviousStatus>Stopped</PreviousStatus>
                  <CurrentStatus>Starting</CurrentStatus>
                  <Code>200</Code>
            </InstanceResponse>
            <InstanceResponse>
                  <Message>success</Message>
                  <InstanceId>i-bp67acfmxazb4p****</InstanceId>
                  <PreviousStatus>Stopped</PreviousStatus>
                  <CurrentStatus>Starting</CurrentStatus>
                  <Code>200</Code>
            </InstanceResponse>
            <InstanceResponse>
                  <Message>The specified InstanceId does not exist. </Message>
                  <InstanceId>i-TestID</InstanceId>
                  <PreviousStatus></PreviousStatus>
                  <CurrentStatus></CurrentStatus>
                  <Code>InvalidInstanceId.NotFound</Code>
            </InstanceResponse>
      </InstanceResponses>
</StartInstancesResponse>
```

`JSON` format

```
{
    "RequestId": "FF53E96D-3F1A-42F0-8373-1C2B39D72D44",
    "InstanceResponses": {
        "InstanceResponse": [
            {
                "Message": "success",
                "InstanceId": "i-bp67acfmxazb4p****",
                "PreviousStatus": "Stopped",
                "CurrentStatus": "Starting",
                "Code": "200"
            },
            {
                "Message": "success",
                "InstanceId": "i-bp67acfmxazb4p****",
                "PreviousStatus": "Stopped",
                "CurrentStatus": "Starting",
                "Code": "200"
            },
            {
                "Message": "The specified InstanceId does not exist.",
                "InstanceId": "i-TestID",
                "PreviousStatus": "",
                "CurrentStatus": "",
                "Code": "InvalidInstanceId.NotFound"
            }
        ]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|%s|The error message returned because the specified instance ID does not exist.|
|403|IncorrectInstanceStatus|%s|The error message returned because the operation is not supported while the instance is in the current state.|
|403|OperationDenied.NoStock|The requested resource is sold out in the specified zone; try other types of resources or other regions and zones.|The error message returned because the requested resources are insufficient in the specified zone. Try other resource types, regions, or zones.|
|403|OperationDenied.SpotPriceLowerThanPublicPrice|The spot instance price is lower than public price.|The error message returned because the user-defined maximum hourly price of a preemptible instance is lower than the spot price.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified instance ID does not exist.|
|403|InsufficientBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. Add funds to your account and try again.|
|403|InstanceNotReady|The specified instance is not ready for use.|The error message returned because the operation is not supported while the resource is in the current state. Try again later.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

