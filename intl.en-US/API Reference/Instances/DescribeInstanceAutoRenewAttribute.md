# DescribeInstanceAutoRenewAttribute

You can call this operation to query the auto-renewal status of one or more subscription ECS instances.

## Description

-   Before you configure auto-renewal or manual renewal for subscription instances, you can query the auto-renewal status of the instances.
-   This operation is applicable only to subscription instances. An error is returned if you call this operation on pay-as-you-go instances.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceAutoRenewAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceAutoRenewAttribute|The operation that you want to perform. Set the value to DescribeInstanceAutoRenewAttribute. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InstanceId|String|No|i-bp18x3z4hc7bixhx\*\*\*\*,i-bp1g6zv0ce8oghu7\*\*\*\*|The IDs of the instances. You can specify a maximum of 100 subscription instance IDs at a time. Separate multiple instance IDs with commas \(,\).

**Note:** The `InstanceId` and `RenewalStatus` parameters cannot be empty at the same time. |
|RenewalStatus|String|No|AutoRenewal|The auto-renewal status of the instance. Valid values:

-   AutoRenewal: Auto-renewal is enabled for the instance.
-   Normal: Auto-renewal is disabled for the instance.
-   NotRenewal: The instance is not to be renewed. The system sends no more expiration reminders, but sends only a non-renewal reminder three days before the expiration date. For an instance that is not to be renewed, you can call the [ModifyInstanceAutoRenewAttribute](~~52843~~) operation to change its auto-renewal status to `Normal`. Then you can manually renew the instance or enable auto-renewal for the instance. |
|PageSize|String|No|10|The number of entries to return on each page.

Valid values: 1 to 100.

Default value: 10. |
|PageNumber|String|No|1|The number of the page to return.

Pages start from page 1.

Default value: 1. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceRenewAttributes|Array of InstanceRenewAttribute| |Details about the renewal attributes of instances. |
|InstanceRenewAttribute| | | |
|AutoRenewEnabled|Boolean|false|Indicates whether auto-renewal was enabled. |
|Duration|Integer|1|The auto-renewal period. |
|InstanceId|String|i-bp18x3z4hc7bixhx\*\*\*\*|The ID of the instance. |
|PeriodUnit|String|week|The unit of the auto-renewal period. |
|RenewalStatus|String|Normal|The auto-renewal status of the instance. Valid values:

-   AutoRenewal: Auto-renewal is enabled for the instance.
-   Normal: Auto-renewal is disabled for the instance.
-   NotRenewal: The instance is not to be renewed. The system sends no more expiration reminders, but sends only a non-renewal reminder three days before the expiration date. For an instance that is not to be renewed, you can call the [ModifyInstanceAutoRenewAttribute](~~52843~~) operation to change its auto-renewal status to `Normal`. Then you can manually renew the instance or enable auto-renewal for the instance. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|6|The total number of instances. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceAutoRenewAttribute
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=1
&RenewalStatus=AutoRenewal
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceAutoRenewAttributeResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <InstanceRenewAttributes>
            <InstanceRenewAttribute>
                  <RenewalStatus>AutoRenewal</RenewalStatus>
                  <Duration>1</Duration>
                  <InstanceId>i-bp18x3z4hc7bixhx****</InstanceId>
                  <AutoRenewEnabled>true</AutoRenewEnabled>
                  <PeriodUnit>Week</PeriodUnit>
            </InstanceRenewAttribute>
      </InstanceRenewAttributes>
      <PageSize>1</PageSize>
      <RequestId>DAE023B4-A78F-4B39-8860-96F17B54F772</RequestId>
</DescribeInstanceAutoRenewAttributeResponse>
```

`JSON` format

```
{
    "PageNumber": 1,
    "TotalCount": 1,
    "InstanceRenewAttributes": {
        "InstanceRenewAttribute": [
            {
                "RenewalStatus": "AutoRenewal",
                "Duration": 1,
                "InstanceId": "i-bp18x3z4hc7bixhx****",
                "AutoRenewEnabled": true,
                "PeriodUnit": "Week"
            }
        ]
    },
    "PageSize": 1,
    "RequestId": "DAE023B4-A78F-4B39-8860-96F17B54F772"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|MissingParameter.InstanceId|InstanceId should not be null.|The error message returned because the required InstanceId parameter is not specified.|
|403|InvalidParameter.ToManyInstanceIds|InstanceId should be less than 100.|The error message returned because more than 100 instances are specified.|
|403|InvalidParameter.InvalidInstanceId|%s|The error message returned because the specified InstanceId parameter is invalid.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the instance is in the current state.|
|403|ChargeTypeViolation|Pay-As-You-Go instances do not support this operation.|The error message returned because the operation is not supported by pay-as-you-go instances. Check the billing method of your instance.|
|403|InvalidParameter.RenewalStatus|The specified parameter RenewalStatus is not valid.|The error message returned because the specified RenewalStatus parameter is invalid.|
|403|InvalidParameter.RenewalStatusInstanceId|The parameter RenewalStatus and InstanceId can not be both empty.|The error message returned because neither of the RenewalStatus and InstanceId parameters is specified.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

