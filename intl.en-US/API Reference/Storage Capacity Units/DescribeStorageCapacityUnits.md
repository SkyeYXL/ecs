# DescribeStorageCapacityUnits

You can call this operation to query one or more storage capacity units \(SCUs\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeStorageCapacityUnits&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeStorageCapacityUnits|The operation that you want to perform. Set the value to DescribeStorageCapacityUnits. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SCU. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|PageNumber|Integer|No|1|The number of the page to return.

Pages start from page 1.

Default value: 1. |
|PageSize|Integer|No|1|The number of entries to return on each page.

Maximum value: 100.

Default value: 10. |
|Name|String|No|testScuName|The name of the SCU. |
|Capacity|Integer|No|20|The capacity of the SCU. Unit: GiB. Valid values: 20, 40, 100, 200, 500, 1024, 2048, 5120, 10240, 20480, and 51200.

This parameter is empty by default. |
|StorageCapacityUnitId.N|RepeatList|No|scu-bp67acfmxazb4p\*\*\*\*|The ID of SCU N. Valid values of N: 1 to 100. |
|Status.N|RepeatList|No|Active|The status of SCU N. Valid values of N: 1 to 4. Valid values of this parameter:

-   Creating: The SCU is being created.
-   Active: The SCU is enabled.
-   Expired: The SCU has expired.
-   Pending: The SCU is waiting to take effect.

This parameter is empty by default. |
|AllocationType|String|No|Shared|The allocation type. This parameter is empty by default.

-   If you do not specify this parameter, all SCUs in the current account are queried.
-   If you set this parameter to Shared, all SCUs shared between the current account and the accounts that have a trusteeship with the current account are queried. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|1|The number of entries returned per page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|StorageCapacityUnits|Array| |An array that consists of StorageCapacityUnits data. |
|StorageCapacityUnit| | | |
|AllocationStatus|String|Allocated|Indicates the sharing status when the AllocationType parameter is set to Shared. Valid values:

-   Allocated: The SCU is shared to other accounts.
-   BeAllocated: The SCU is shared from another account. |
|Capacity|Integer|20|The capacity of the SCU. |
|CreationTime|String|2019-09-25T02:12:00Z|The time when the SCU was created. |
|Description|String|testScuDescription|The description of the SCU. |
|ExpiredTime|String|2019-09-25T02:12:00Z|The time when the SCU expires. |
|Name|String|testScuName|The name of the SCU. |
|RegionId|String|cn-hangzhou|The region ID of the SCU. |
|StartTime|String|2019-09-25T02:00:00Z|The time when the SCU took effect. |
|Status|String|Active|The status of the SCU. |
|StorageCapacityUnitId|String|scu-bp67acfmxazb4p\*\*\*\*|The ID of the SCU. |
|TotalCount|Integer|4|The total number of SCUs. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeStorageCapacityUnits
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeStorageCapacityUnitsResponse>
      <PageNumber>1</PageNumber>
      <PageSize>1</PageSize>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <StorageCapacityUnits>
            <StorageCapacityUnit>
                  <Capacity>20</Capacity>
                  <CreationTime>2019-09-25T02:12:00Z</CreationTime>
                  <Description>testScuDescription</Description>
                  <ExpiredTime>2019-09-25T02:12:00Z</ExpiredTime>
                  <Name>testScuName</Name>
                  <OfferingType>All Upfront</OfferingType>
                  <RegionId>cn-hangzhou</RegionId>
                  <StartTime>2019-09-25T02:00:00Z</StartTime>
                  <Status>Active</Status>
                  <AllocationStatus></AllocationStatus>
                  <StorageCapacityUnitId>scu-bp67acfmxazb4p****</StorageCapacityUnitId>
            </StorageCapacityUnit>
      </StorageCapacityUnits>
      <TotalCount>4</TotalCount>
</DescribeStorageCapacityUnitsResponse>
```

`JSON` format

```
{
    "PageNumber": "1",
    "PageSize": "1",
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
    "StorageCapacityUnits": {
        "StorageCapacityUnit": [{
            "Capacity": "20",
            "CreationTime": "2019-09-25T02:12:00Z",
            "Description": "testScuDescription",
            "ExpiredTime": "2019-09-25T02:12:00Z",
            "Name": "testScuName",
            "OfferingType": "All Upfront",
            "RegionId": "cn-hangzhou",
            "StartTime": "2019-09-25T02:00:00Z",
            "Status": "Active",
            "AllocationStatus": "",
            "StorageCapacityUnitId": "scu-bp67acfmxazb4p****"
    
        }] 
    },    
    "TotalCount": "4"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter.RegionId|The specified RegionId should not be null.|The error message returned because the RegionId parameter is not specified.|
|400|InvalidParameter.Name|The specified Name is invalid.|The error message returned because the specified Name parameter is invalid.|
|400|InvalidParameter.CapacityExceed|The specified Capacity exceeds the limitation of quota.|The error message returned because the specified Capacity parameter exceeds the upper limit.|
|400|InvalidAllocationType.ValueNotSupported|The specified AllocationType is not supported.|The error message returned because the specified AllocationType parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

