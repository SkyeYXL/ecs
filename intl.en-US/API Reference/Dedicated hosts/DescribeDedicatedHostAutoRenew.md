# DescribeDedicatedHostAutoRenew

You can call this operation to query the auto-renewal status of one or more subscription dedicated hosts.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeDedicatedHostAutoRenew&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDedicatedHostAutoRenew|The operation that you want to perform. Set the value to DescribeDedicatedHostAutoRenew. |
|DedicatedHostIds|String|Yes|dh-bp165p6xk2tlw61e\*\*\*\*,dh-bp1f9vxmno\*\*\*\*|The IDs of the dedicated hosts. You can enter up to 100 subscription dedicated host IDs in the list. Separate multiple IDs with commas \(,\). |
|RegionId|String|Yes|cn-hangzhou|The region ID of the dedicated host. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DedicatedHostRenewAttributes|Array of DedicatedHostRenewAttribute| |Details about the auto-renewal attributes of the dedicated hosts. |
|DedicatedHostRenewAttribute| | | |
|AutoRenewEnabled|Boolean|true|Indicates whether auto-renewal is enabled. |
|DedicatedHostId|String|dh-bp165p6xk2tlw61e\*\*\*\*|The ID of the dedicated host. |
|Duration|Integer|0|The auto-renewal period. |
|PeriodUnit|String|Month|The unit of the auto-renewal period. Valid values:

-   Week
-   Month |
|RenewalStatus|String|Normal|Indicates whether the subscription dedicated host is automatically renewed. Valid values:

-   AutoRenewal: The dedicated host is automatically renewed.
-   Normal: The dedicated host is not automatically renewed but you still receive notifications for renewals.
-   NotRenewal: Auto-renewal is disabled and no expiration notification is sent. You receive notifications for renewal three days before the expiration time of the subscription dedicated host. You can change the value of this parameter from NotRenewal to Normal for a dedicated host and manually renew it by calling the [RenewDedicatedHosts](~~93287~~) operation. Alternatively, you can renew it by setting this parameter to AutoRenewal. |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeDedicatedHostAutoRenew
&RegionId=cn-hangzhou
&DedicatedHostIds=dh-bp165p6xk2tlw61e****,dh-bp1f9vxmno****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDedicatedHostAutoRenewResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <DedicatedHostRenewAttributes>
            <DedicatedHostRenewAttribute>
                  <DedicatedHostId>dh-bp165p6xk2tlw61e****</DedicatedHostId>
                  <Duration>0</Duration>
                  <AutoRenewEnalbed>false</AutoRenewEnalbed>
                  <PeriodUnit>Month</PeriodUnit>
                  <RenewalStatus>Normal</RenewalStatus>
            </DedicatedHostRenewAttribute>
             <DedicatedHostRenewAttribute>
                  <DedicatedHostId>dh-bp1f9vxmno****</DedicatedHostId>
                  <Duration>1</Duration>
                  <PeriodUnit>Month</PeriodUnit>
                  <AutoRenewEnalbed>true</AutoRenewEnalbed>
                  <RenewalStatus>AutoRenewal</RenewalStatus>
            </DedicatedHostRenewAttribute>
      </DedicatedHostRenewAttributes>
</DescribeDedicatedHostAutoRenewResponse>
```

`JSON` format

```
{
    "DedicatedHostIdRenewAttributes": {
        "DedicatedHostIdRenewAttribute": [
            {
                "Duration": 0,
                "DedicatedHostId": "dh-bp165p6xk2tlw61e****",
                "AutoRenewEnabled": false,
                "RenewalStatus": "Normal",
                "PeriodUnit": "Month"
            },
            {
                "Duration": 1,
                "DedicatedHostId": "dh-bp1f9vxmno****",
                "AutoRenewEnabled": true,
                "RenewalStatus": "AutoRenewal",
                "PeriodUnit": "Month"
            }
        ]
    },
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|MissingParameter.DedicatedHostId|DedicatedHostId should not be null.|The error message returned because the DedicatedHostIds parameter is not specified.|
|403|InvalidParameter.ToManyDedicatedHostIds|DedicatedHostId should be less than 100.|The error message returned because more than 100 dedicated host IDs are specified in the DedicatedHostIds parameter.|
|403|InvalidParameter.InvalidDedicatedHostId|%s|The error message returned because the specified DedicatedHostIds parameter is invalid.|
|403|IncorrectDedicatedHostStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|ChargeTypeViolation|Pay-As-You-Go dedicated host do not support this operation.|The error message returned because the current operation is not supported for pay-as-you-go dedicated hosts.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

