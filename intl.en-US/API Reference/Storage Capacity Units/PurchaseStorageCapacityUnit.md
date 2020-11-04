# PurchaseStorageCapacityUnit

You can call this operation to purchase one or more storage capacity units \(SCUs\). SCUs are subscription storage resource plans that can be used to offset bills of pay-as-you-go disks located within the same regions as the SCUs.

## Description

Before you call this operation, take note of the billing methods and pricing of SCUs. For more information, see [SCU billing](~~137897~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=PurchaseStorageCapacityUnit&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|PurchaseStorageCapacityUnit|The operation that you want to perform. Set the value to PurchaseStorageCapacityUnit. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SCU. After the region is specified, SCUs can only offset bills of pay-as-you-go disks located within this region. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Capacity|Integer|Yes|20|The capacity of the SCU. Unit: GiB. Valid values: 20, 40, 100, 200, 500, 1024, 2048, 5120, 10240, 20480, and 51200. |
|Name|String|No|ScuPurchaseDemo|The name of the SCU. It must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter but cannot start with http:// or https://.

This parameter is empty by default. |
|Description|String|No|ScuPurchaseDemo|The description of the SCU. It must be 2 to 256 characters in length and cannot start with http:// or https://.

This parameter is empty by default. |
|PeriodUnit|String|No|Month|The unit of the validity period. Valid values:

-   Month. Valid values of the Period parameter: 1, 2, 3, and 6.
-   Year. Valid values of the Period parameter: 1, 3, and 5.

Default value: Month |
|Period|Integer|No|1|The validity period of the SCU. Valid values: 1, 2, 3, 5, and 6.

Default value: 1. |
|StartTime|String|No|2020-09-09T02:00:00Z|The time when the SCU takes effect. It cannot be earlier than or six months later than the create time. Specify the time in the ISO 8601 standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

This parameter is empty by default. The SCU takes effect immediately after it is created. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The `ClientToken` value can only contain ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|Amount|Integer|No|1|The number of SCUs to be purchased. Valid values: 1 to 20.

Default value: 1. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|OrderId|String|204135153880\*\*\*\*|The ID of the order. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|StorageCapacityUnitIds|List|scu-bp67acfmxazb4p\*\*\*\*|The ID of the SCU. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=PurchaseStorageCapacityUnit
&Capacity=20
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<PurchaseStorageCapacityUnitResponse>
      <OrderId>204135153880***</OrderId>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <StorageCapacityUnitIds>
            <StorageCapacityUnitId>scu-bp67acfmxazb4p****</StorageCapacityUnitId>
      </StorageCapacityUnitIds>
</PurchaseStorageCapacityUnitResponse>
```

`JSON` format

```
{
    "OrderId": "204135153880****",
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
    "StorageCapacityUnitIds": {
        "StorageCapacityUnitId": "scu-bp67acfmxazb4p****"
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter.Period|The specified Period is not valid.|The error message returned because the specified Period parameter is invalid.|
|400|MissingParameter.RegionId|The specified RegionId should not be null.|The error message returned because the RegionId parameter is not specified.|
|400|InvalidParameter.Name|The specified Name is invalid.|The error message returned because the specified Name parameter is invalid.|
|400|InvalidParameter.Capacity|The specified Capacity is invalid.|The error message returned because the specified Capacity parameter is invalid.|
|400|MissingParameter.Capacity|The specified Capacity should be not null.|The error message returned because the Capacity parameter is not specified.|
|400|InvalidParameter.PeriodUnit|The specified PeriodUnit is not supported.|The error message returned because the specified PeriodUnit parameter is invalid.|
|400|InvalidParameter.CapacityExceed|The specified Capacity exceeds the limitation of quota.|The error message returned because the specified Capacity parameter exceeds the upper limit.|
|400|InvalidStartTime.NotSupported|The specified StartTime should be within 180 calendar days from the current date, and you must specify a precision to hour.|The error message returned because the specified StartTime parameter is invalid.|
|400|InvalidStartTime.MalFormed|The specified StartTime is out of the permitted range.|The error message returned because the specified StartTime parameter exceeds the upper limit.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

