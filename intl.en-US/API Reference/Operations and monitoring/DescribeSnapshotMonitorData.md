# DescribeSnapshotMonitorData

You can call this operation to query the monitoring data of snapshot sizes in a region over the last 30 days.

## Description

When you call this operation, take note of the following points:

-   A maximum of 400 entries of monitoring data can be returned at a time. If the result of the `(EndTime - StartTime)/Period` formula is more than 400, an error is returned.
-   You can query monitoring data from up to the last 30 days. If the value of `StartTime` is more than 30 days earlier than the current time, an error is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSnapshotMonitorData&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSnapshotMonitorData|The operation that you want to perform. Set the value to DescribeSnapshotMonitorData. |
|EndTime|String|Yes|2019-05-10T03:00:00Z|The end of the time range to query. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. If the specified value of seconds \(ss\) is not 00, the time is rounded up to the next minute. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|StartTime|String|Yes|2019-05-10T00:00:00Z|The beginning of the time range to query. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. If the specified value of seconds \(ss\) is not 00, the time is rounded up to the next minute. |
|Period|Integer|No|60|The interval at which to query the monitoring data of snapshot sizes. Unit: seconds. Valid values:

-   60
-   600
-   3600

Default value: 60. |
|Category|String|No|Standard|The type of the snapshot. Valid values:

-   Standard: normal snapshot
-   Flash: local snapshot

Default value: Standard. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MonitorData|Array of DataPoint| |The collection of monitoring data of snapshot sizes. |
|DataPoint| | | |
|Size|Long|243036848128|The total size of the snapshots. Unit: bytes. |
|TimeStamp|String|2019-05-10T04:00:00Z|The timestamp that corresponds to a snapshot size. |
|RequestId|String|9F8163A8-F5DE-47A2-A572-4E062D223E09|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?&Action=DescribeSnapshotMonitorData
&RegionId=cn-hangzhou
&StartTime=2019-05-10T00:00:00Z
&EndTime=2019-05-10T03:00:00Z
&Period=60
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSnapshotMonitorDataResponse>
     <MonitorData>
          <DataPoint>
               <element>
                    <Size>243036848128</Size>
                    <TimeStamp>2019-05-10T01:00:00Z</TimeStamp>
               </element>
               <element>
                    <Size>243036848128</Size>
                    <TimeStamp>2019-05-10T02:00:00Z</TimeStamp>
               </element>
               <element>
                    <Size>243036848128</Size>
                    <TimeStamp>2019-05-10T03:00:00Z</TimeStamp>
               </element>
          </DataPoint>
     </MonitorData>
     <RequestId>9F8163A8-F5DE-47A2-A572-4E062D223E09</RequestId>
</DescribeSnapshotMonitorDataResponse>
```

`JSON` format

```
{
    "RequestId": "9F8163A8-F5DE-47A2-A572-4E062D223E09",
    "MonitorData": {
        "DataPoint": [
            {
                "TimeStamp": "2019-05-10T01:00:00Z",
                "Size": 243036848128
            },
            {
                "TimeStamp": "2019-05-10T02:00:00Z",
                "Size": 243036848128
            },
            {
                "TimeStamp": "2019-05-10T03:00:00Z",
                "Size": 243036848128
            }
        ]}
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidStartTime.Malformed|The specified parameter "StartTime" is not valid.|The error message returned because the specified StartTime parameter is invalid.|
|400|InvalidEndTime.Malformed|The specified parameter "EndTime" is not valid.|The error message returned because the specified EndTime parameter is invalid.|
|400|InvalidPeriod.ValueNotSupported|The specified parameter "Period" is not valid.|The error message returned because the specified Period parameter is invalid.|
|400|InvalidStartTime.TooEarly|The specified parameter "StartTime" is too early.|The error message returned because the specified StartTime parameter is more than 30 days earlier than the current time.|
|400|InvalidParameter.TooManyDataQueried|Too many data queried.|The error message returned because the amount of queried monitoring data has reached the upper limit.|
|400|Throttling|Request was denied due to request throttling.|The error message returned because the request is denied due to throttling. Try again later.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

