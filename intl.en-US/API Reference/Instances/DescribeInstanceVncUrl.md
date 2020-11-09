# DescribeInstanceVncUrl

You can call this operation to query the URL of an VNC management terminal of an ECS instance.

## Description

When you call this operation, take note of the following items:

-   The URL of an VNC management terminal is valid only for 15 seconds. If a connection is not established within 15 seconds after a successful query, the URL expires and you must query it again.
-   The **KeepAlive** time of a connection to an VNC management terminal is 60 seconds. If you do not interact with the VNC management terminal within 60 seconds, the VNC management terminal is automatically disconnected.
-   When the VNC management terminal is disconnected, you can only reconnect to the VNC management terminal a maximum of 30 times a minute.
-   You must append the following parameters to the end of the `https://g.alicdn.com/aliyun/ecs-console-vnc2/0.0.8/index.html?` URL: `vncUrl`, `instanceId`, `isWindows` \(True or `False`\), and `password`. Connect these parameters with ampersands \(`&`\).
    -   `vncUrl`: the `VncUrl` value returned after a successful query.
    -   `instanceId`: the ID of your instance.
    -   `isWindows`: specifies whether the operating system of the instance is Windows. If the parameter is set to `true`, the operating system is Windows. If the value is set to `false`, the operating system is not Windows.
    -   `password`: Optional. The VNC password used to connect to the VNC management terminal. It must be six characters in length and can contain digits and letters. You can use this parameter to eliminate the need to enter your password when you connect to the VNC management terminal.

        Examples:

        ```
        
        https://g.alicdn.com/aliyun/ecs-console-vnc2/0.0.8/index.html?vncUrl=ws%3A%2F%****&instanceId=i-wz9hhwq5a6tm****&isWindows=true
               
        ```

        Or:

        ```
        
        https://g.alicdn.com/aliyun/ecs-console-vnc2/0.0.8/index.html?vncUrl=ws%3A%2F%****&instanceId=i-wz9hhwq5a6tm****&isWindows=true&password=****
               
        ```


## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceVncUrl&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceVncUrl|The operation that you want to perform. Set the value to DescribeInstanceVncUrl. |
|InstanceId|String|Yes|i-bp1hzoinajzkh91h\*\*\*\*|The ID of the instance. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|VncUrl|String|wss%3A%2F%2Fhz01-vncproxy.aliyun.com%2Fwebsockify%2F%3Fs%3DDvh%252FIA%252BYc73gWO48cBx2gBxUDVzaAnSKr74pq30mzqUYgeUMcB%252FbkNixDxdEA996|The URL of the VNC management terminal. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceVncUrl
&InstanceId=i-bp1hzoinajzkh91h****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceVncUrlResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <VncUrl>wss%3A%2F%2Fhz01-vncproxy.aliyun.com%2Fwebsockify%2F%3Fs%3DDvh%252FIA%252BYc73gWO48cBx2gBxUDVzaAnSKr74pq30mzqUYgeUMcB%252FbkNixDxdEA996</VncUrl>
</DescribeInstanceVncUrlResponse>
```

`JSON` format

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
    "VncUrl": "wss%3A%2F%2Fhz01-vncproxy.aliyun.com%2Fwebsockify%2F%3Fs%3DDvh%252FIA%252BYc73gWO48cBx2gBxUDVzaAnSKr74pq30mzqUYgeUMcB%252FbkNixDxdEA996"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned because the specified RegionId parameter does not exist.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the instance is in the current state.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|InstanceNotReady|The specified instance is not ready for use|The error message returned because the specified instance cannot be connected for the moment. Try again later.|
|400|InvalidRegionInstance|The specified InstanceId does not exist in given region.|The error message returned because the instance does not exist in the specified region. Check whether the RegionId and InstanceId parameters are correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

