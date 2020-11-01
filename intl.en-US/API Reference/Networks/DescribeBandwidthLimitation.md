# DescribeBandwidthLimitation

You can call this operation to query the maximum public bandwidth that can be purchased, upgraded, or downgraded for various instance types.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeBandwidthLimitation&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeBandwidthLimitation|The operation that you want to perform. Set the value to DescribeBandwidthLimitation. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|InstanceType|String|No|ecs.g5.large|The instance type. For more information about the values, see [Instance families](~~25378~~).

**Note:** This parameter is required. |
|InstanceChargeType|String|No|PrePaid|The billing method of the instance. For more information, see [Billing overview](~~25398~~). Valid values:

-   PrePaid: subscription
-   PostPaid: pay-as-you-go

Default value: PostPaid. |
|SpotStrategy|String|No|NoSpot|The preemption policy for the preemptible or pay-as-you-go instance. Valid values:

-   NoSpot: The instance is a regular pay-as-you-go instance.
-   SpotWithPriceLimit: The instance is a preemptible instance with user-defined maximum hourly prices.
-   SpotAsPriceGo: The system automatically offers a bid, which is not higher than the pay-as-you-go price for the same instance type.

Default value: NoSpot.

**Note:** This parameter takes effect only when the InstanceChargeType parameter is set to PostPaid. |
|ResourceId|String|No|i-bp67acfmxazb4ph\*\*\*|The ID of the resource.

**Note:** This parameter is required when the OperationType parameter is set to Upgrade or Downgrade. |
|OperationType|String|No|Upgrade|Specifies the operation for which to query the maximum public bandwidth. Valid values:

-   Upgrade: upgrades the public bandwidth.
-   Downgrade: downgrades the public bandwidth.
-   Create: creates an ECS instance.

Default value: Create. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Bandwidths|Array of Bandwidth| |Details about the maximum public bandwidth. |
|Bandwidth| | | |
|InternetChargeType|String|PayByTraffic|The billing method for network usage. Valid values:

-   PayByBandwidth
-   PayByTraffic |
|Max|Integer|100|The maximum public bandwidth. |
|Min|Integer|0|The minimum public bandwidth. |
|Unit|String|Mbps|The unit of the public bandwidth. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeBandwidthLimitation
&RegionId=cn-hangzhou
&InstanceType=ecs.g5.large
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeBandwidthLimitationResponse>
      <Bandwidths>
            <Bandwidth>
                  <Max>100</Max>
                  <InternetChargeType>PayByBandwidth</InternetChargeType>
                  <Unit>Mbps</Unit>
                  <Min>0</Min>
            </Bandwidth>
            <Bandwidth>
                  <Max>100</Max>
                  <InternetChargeType>PayByTraffic</InternetChargeType>
                  <Unit>Mbps</Unit>
                  <Min>0</Min>
            </Bandwidth>
      </Bandwidths>
      <RequestId>226CB38E-29E3-423E-85DD-DCD1C99832B0</RequestId>
</DescribeBandwidthLimitationResponse>
```

`JSON` format

```
{
    "Bandwidths": {
        "Bandwidth": [
            {
                "Max": 100,
                "InternetChargeType": "PayByBandwidth",
                "Unit": "Mbps",
                "Min": 0
            },
            {
                "Max": 100,
                "InternetChargeType": "PayByTraffic",
                "Unit": "Mbps",
                "Min": 0
            }
        ]
    },
    "RequestId": "226CB38E-29E3-423E-85DD-DCD1C99832B0"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Invalid.InstanceChargeType|The specified InstanceChargeType is not valid.|The error message returned because the specified InstanceChargeType parameter is invalid.|
|404|Invalid.NetworkCategory|The specified NetworkCategory is not valid.|The error message returned because the specified NetworkCategory parameter is invalid.|
|404|Invalid.SpotStrategy|The specified SpotStrategy is not valid.|The error message returned because the specified SpotStrategy parameter is invalid.|
|404|Invalid.IoOptimized|The specified IoOptimized is not valid.|The error message returned because the specified IoOptimized parameter is invalid.|
|404|Invalid.ResourceId|The specified ResourceId is not valid.|The error message returned because the specified ResourceId parameter is invalid.|
|404|Invalid.InstancePayType|The specified InstancePayType is not valid.|The error message returned because the specified InstanceChargeType parameter is invalid.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType beyond the permitted range.|The error message returned because the specified InstanceType parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

