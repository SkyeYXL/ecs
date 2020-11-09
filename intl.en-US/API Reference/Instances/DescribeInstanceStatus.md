# DescribeInstanceStatus

You can call this operation to query the status information of multiple instances.

## Description

-   For information about the lifecycle of an ECS instance, see [Instance states](~~25687~~).
-   You can also call this operation to query the list of instances.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceStatus&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceStatus|The operation that you want to perform. Set the value to DescribeInstanceStatus. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InstanceId.N|RepeatList|No|i-bp1j4i2jdf3owlhe\*\*\*\*|The ID of instance N. Valid values of N: 1 to 100. Specify multiple values in the repeated list format. |
|ZoneId|String|No|cn-hangzhou-d|The zone ID of the instance. |
|ClusterId|String|No|cls-bp67acfmxazb4p\*\*\*\*|The cluster ID of the instance. |
|PageNumber|Integer|No|1|The number of the page to return.

 Pages start from page 1.

 Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 50.

 Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceStatuses|Array| |The status information of instances. |
|InstanceStatus| | | |
|InstanceId|String|i-bp1j4i2jdf3owlhe\*\*\*\*|The ID of the instance. |
|Status|String|Running|The status of the instance. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|1|The number of entries returned per page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|58|The total number of instances. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceStatus
&RegionId=cn-hangzhou
&PageSize=1
&PageNumber=1
&InstanceId.1=i-bp1j4i2jdf3owlhe****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceStatusResponse>
      <PageNumber>1</PageNumber>
      <InstanceStatuses>
            <InstanceStatus>
                  <Status>Running</Status>
                  <InstanceId>i-bp1j4i2jdf3owlhe****</InstanceId>
            </InstanceStatus>
      </InstanceStatuses>
      <TotalCount>58</TotalCount>
      <PageSize>1</PageSize>
      <RequestId>746C3444-9A24-4D7D-B8A8-DCBF7AC8BD66</RequestId>
</DescribeInstanceStatusResponse>
```

`JSON` format

```
{
	"PageNumber": 1,
	"InstanceStatuses": {
		"InstanceStatus": [
			{
				"Status": "Running",
				"InstanceId": "i-bp1j4i2jdf3owlhe****"
			}
		]
	},
	"TotalCount": 58,
	"PageSize": 1,
	"RequestId": "746C3444-9A24-4D7D-B8A8-DCBF7AC8BD66"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

