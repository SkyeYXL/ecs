# DescribeInstanceHistoryEvents

You can call this operation to query the system events of a specific instance. By default, system events that are in the Executed, Avoided, Canceled, or Failed state are queried. You can specify the InstanceEventCycleStatus parameter to query system events in the corresponding state.

## Description

-   You can query finished system events within the last 30 days. The time range for querying unfinished system events is not restricted.
-   You can also specify the InstanceEventCycleStatus parameter to query the system events that are in the Scheduled, Executing, or Inquiring state.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceHistoryEvents&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceHistoryEvents|The operation that you want to perform. Set the value to DescribeInstanceHistoryEvents. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InstanceId|String|No|i-uf678mass4zvr9n1\*\*\*\*|The ID of the instance. If this parameter is not specified, system events of all instances in the specified region are queried. |
|EventId.N|RepeatList|No|e-uf64yvznlao4jl2c\*\*\*\*|The ID of system event N. Valid values of N: 1 to 100. Specify multiple values in the repeated list form. |
|InstanceEventCycleStatus.N|RepeatList|No|Executed|The lifecycle status of system event N. Valid values of N: 1 to 7. Specify multiple values in the repeated list form. Valid values:

-   Scheduled
-   Avoided
-   Executing
-   Executed
-   Canceled
-   Failed
-   Inquiring |
|EventCycleStatus|String|No|Executed|The lifecycle status of the system event. This parameter takes effect only when the InstanceEventCycleStatus.N parameter is not specified. Valid values:

-   Scheduled
-   Avoided
-   Executing
-   Executed
-   Canceled
-   Failed
-   Inquiring |
|InstanceEventType.N|RepeatList|No|SystemMaintenance.Reboot|The type of system event N. Valid values of N: 1 to 30. Specify multiple values in the repeated list form. Valid values:

-   SystemMaintenance.Reboot: The instance is restarted due to system maintenance.
-   SystemMaintenance.Redeploy: The instance is redeployed due to system maintenance.
-   SystemFailure.Reboot: The instance is restarted due to a system failure.
-   SystemFailure.Redeploy: The instance is redeployed due to a system failure.
-   SystemFailure.Delete: The instance is released due to an instance creation failure.
-   InstanceFailure.Reboot: The instance is restarted due to an instance failure.
-   InstanceExpiration.Stop: The instance is stopped due to subscription expiration.
-   InstanceExpiration.Delete: The instance is released due to subscription expiration.
-   AccountUnbalanced.Stop: The pay-as-you-go instance is stopped due to overdue payments.
-   AccountUnbalanced.Delete: The pay-as-you-go instance is released due to overdue payments.

**Note:** For more information, see [Overview](~~66574~~). Values of this parameter are applicable only to instance system events, but not to disk system events. |
|EventType|String|No|SystemMaintenance.Reboot|The system event type. This parameter takes effect only when the InstanceEventType.N parameter is not specified. Valid values:

-   SystemMaintenance.Reboot: The instance is restarted due to system maintenance.
-   SystemMaintenance.Redeploy: The instance is redeployed due to system maintenance.
-   SystemFailure.Reboot: The instance is restarted due to a system failure.
-   SystemFailure.Redeploy: The instance is redeployed due to a system failure.
-   SystemFailure.Delete: The instance is released due to an instance creation failure.
-   InstanceFailure.Reboot: The instance is restarted due to an instance failure.
-   InstanceExpiration.Stop: The instance is stopped due to subscription expiration.
-   InstanceExpiration.Delete: The instance is released due to subscription expiration.
-   AccountUnbalanced.Stop: The pay-as-you-go instance is stopped due to overdue payments.
-   AccountUnbalanced.Delete: The pay-as-you-go instance is released due to overdue payments.

**Note:** For more information, see [Overview](~~66574~~). Values of this parameter are applicable only to instance system events, but not to disk system events. |
|NotBefore.Start|String|No|2017-11-30T06:32:31Z|The start time of the scheduled event execution period. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|NotBefore.End|String|No|2017-12-01T06:32:31Z|The end time of the scheduled event execution period. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|EventPublishTime.Start|String|No|2017-11-30T06:32:31Z|The start time of the period during which the system event is published. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|EventPublishTime.End|String|No|2017-12-01T06:32:31Z|The end time of the period during which the system event is published. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. |
|PageNumber|Integer|No|1|The number of the page to return. Pages start from page 1.

Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100.

Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceSystemEventSet|Array of InstanceSystemEventType| |Details about the history system events. |
|InstanceSystemEventType| | | |
|EventCycleStatus|Struct| |The lifecycle status of the system event. |
|Code|Integer|0|The status code of the system event. |
|Name|String|Executed|The status name of the system event. |
|EventFinishTime|String|2017-12-01T06:35:31Z|The time when the system event ended. The time follows the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|EventId|String|e-uf64yvznlao4jl2c\*\*\*\*|The ID of the system event. |
|EventPublishTime|String|2017-11-30T06:32:31Z|The time when the system event was published. The time follows the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|EventType|Struct| |The type of the system event. |
|Code|Integer|34|The code of the system event type. |
|Name|String|InstanceExpiration.Stop|The name of the system event type. |
|ExtendedAttribute|Struct| |The extended attribute of the system event. |
|Device|String|/dev/vda|The device name of the local disk. |
|DiskId|String|d-diskid1|The ID of the local disk. |
|InactiveDisks|Array of InactiveDisk| |Details about inactive cloud disks or local disks that have been released but must be removed. |
|InactiveDisk| | | |
|CreationTime|String|2018-11-30T06:32:31Z|The time when the disk was created. The time follows the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|DeviceCategory|String|cloud\_efficiency|The category of the disk. Valid values:

-   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   cloud\_essd: enhanced SSD \(ESSD\)
-   local\_ssd\_pro: I/O intensive local disk
-   local\_hdd\_pro: throughput intensive local disk
-   ephemeral: retired local disk
-   ephemeral\_ssd: retired local SSD |
|DeviceSize|String|80|The size of the disk. Unit: GiB. |
|DeviceType|String|data|The type of the disk. Valid values:

-   system: system disk
-   data: data disk |
|ReleaseTime|String|2019-11-30T06:32:31Z|The time when the disk was released. The time follows the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|ImpactLevel|String|100|The impact level of the system event. |
|InstanceId|String|i-uf678mass4zvr9n1\*\*\*\*|The ID of the instance. |
|NotBefore|String|2017-12-06T00:00:00Z|The scheduled execution time of the system event. The time follows the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|Reason|String|System maintenance is scheduled due to \*\*\*.|The reason for scheduling the system event. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|2|The total number of instances. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceHistoryEvents
&RegionId=cn-hangzhou
&InstanceId=i-uf678mass4zvr9n1****
&EventId.1=e-uf64yvznlao4jl2c****
&InstanceEventCycleStatus.1=Executed
&EventCycleStatus=Executed
&InstanceEventType.1=SystemMaintenance.Reboot
&NotBefore.Start=2017-11-30T06:32:31Z
&NotBefore.End=2017-12-01T06:32:31Z
&PageNumber=1
&PageSize=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceHistoryEventsResponse>
      <InstanceSystemEventSet>
            <InstanceSystemEventType>
                  <InstanceId>i-uf678mass4zvr9n1****</InstanceId>
                  <EventId>e-uf64yvznlao4jl2c****</EventId>
                  <EventType>
                        <Code>1</Code>
                        <Name>SystemMaintenance.Reboot</Name>
                  </EventType>
                  <EventCycleStatus>
                        <Code>0</Code>
                        <Name>Executed</Name>
                  </EventCycleStatus>
                  <EventPublishTime>2017-11-30T06:32:31Z</EventPublishTime>
                  <NotBefore>2017-12-01T06:32:31Z</NotBefore>
                  <EventFinishTime>2017-12-01T06:35:31Z</EventFinishTime>
            </InstanceSystemEventType>
            <InstanceSystemEventType>
                  <InstanceId>i-uf678mass4zvr9n1****</InstanceId>
                  <EventId>e-uf61cbvp0w8x2xfx****</EventId>
                  <EventType>
                        <Code>34</Code>
                        <Name>InstanceExpiration.Stop</Name>
                  </EventType>
                  <EventCycleStatus>
                        <Code>8</Code>
                        <Name>Avoided</Name>
                  </EventCycleStatus>
                  <EventPublishTime>2017-11-29T06:32:31Z</EventPublishTime>
                  <NotBefore>2017-12-06T00:00:00Z</NotBefore>
                  <EventFinishTime>2017-12-05T12:35:31Z</EventFinishTime>
            </InstanceSystemEventType>
      </InstanceSystemEventSet>
      <PageSize>10</PageSize>
      <PageNumber>1</PageNumber>
      <TotalCount>2</TotalCount>
      <RequestId>02EA76D3-5A2A-44EB-XXXX-8901881D8707</RequestId>
</DescribeInstanceHistoryEventsResponse>
```

`JSON` format

```
{
    "InstanceSystemEventSet": {
        "InstanceSystemEventType": [
            {
                "InstanceId": "i-uf678mass4zvr9n1****",
                "EventId": "e-uf64yvznlao4jl2c****",
                "EventType": {
                    "Code": 1,
                    "Name": "SystemMaintenance.Reboot"
                },
                "EventCycleStatus": {
                    "Code": 0,
                    "Name": "Executed"
                },
                "EventPublishTime": "2017-11-30T06:32:31Z",
                "NotBefore": "2017-12-01T06:32:31Z",
                "EventFinishTime": "2017-12-01T06:35:31Z"
            },
            {
                "InstanceId": "i-uf678mass4zvr9n1****",
                "EventId": "e-uf61cbvp0w8x2xfx****",
                "EventType": {
                    "Code": 34,
                    "Name": "InstanceExpiration.Stop"
                },
                "EventCycleStatus": {
                    "Code": 8,
                    "Name": "Avoided"
                },
                "EventPublishTime": "2017-11-29T06:32:31Z",
                "NotBefore": "2017-12-06T00:00:00Z",
                "EventFinishTime": "2017-12-05T12:35:31Z"
            }
        ]
    },
    "PageSize": 10,
    "PageNumber": 1,
    "TotalCount": 2,
    "RequestId": "02EA76D3-5A2A-44EB-XXXX-8901881D8707"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|403|EventIdLimitExceeded|%s|The error message returned because more than 100 events are specified.|
|403|InvalidParameter.TimeEndBeforeStart|%s|The error message returned because the specified parameter is invalid. Check whether the end time is earlier than the start time.|
|403|OperationDenied.NotInWhiteList|%s|The error message returned because you are not authorized to perform this operation. Try again when you are in the whitelist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

