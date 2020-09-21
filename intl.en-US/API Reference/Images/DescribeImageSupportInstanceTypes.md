# DescribeImageSupportInstanceTypes

You can call this operation to query the instance types supported by a specified image.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeImageSupportInstanceTypes&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeImageSupportInstanceTypes|The operation that you want to perform. Set the value to DescribeImageSupportInstanceTypes. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|ImageId|String|No|m-o6w3gy99qf89rkga\*\*\*\*|The ID of the image. |
|ActionType|String|No|CreateEcs|The scenario in which the instance type is to be used. Default value: CreateEcs. Valid values:

 -   CreateEcs
-   Upgrade
-   Downgrade
-   RenewDowngrade |
|Filter.N.Key|String|No|imageId|The key of filter condition N. Only the image ID can be used to filter instance types. Valid values:

 -   imagid: The image ID is used as the filter condition.
-   filter: The image ID is used as the filter condition. |
|Filter.N.Value|String|No|m-o6w3gy99qf89rkga\*\*\*\*|The value of filter condition N. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ImageId|String|m-o6w3gy99qf89rkga\*\*\*\*|The ID of the image. |
|InstanceTypes|Array| |An array consisting of InstanceType data. |
|InstanceType| | | |
|CpuCoreCount|Integer|1|The number of vCPUs of the instance type. |
|InstanceTypeFamily|String|ecs.t1|The instance family. |
|InstanceTypeId|String|ecs.t1.xsmall|The ID of the instance type. |
|MemorySize|Float|1024|The memory size of the instance type. Unit: GiB. |
|RegionId|String|cn-hangzhou|The region ID of the image. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeImageSupportInstanceTypes
&RegionId=cn-hangzhou
&ImageId=m-o6w3gy99qf89rkga****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeImageSupportInstanceTypesResponse>
      <RequestId>CF661E2D-4AFE-4BCD-959A-A65E14416B44</RequestId>
      <RegionId>cn-hangzhou</RegionId>
      <ImageId>ubuntu_16_0402_64_20G_alibase_20180409.vhd</ImageId>
      <InstanceTypes>
            <InstanceType>
                  <InstanceTypeId>ecs.t1.xsmall</InstanceTypeId>
                  <CpuCoreCount>1</CpuCoreCount>
                  <MemorySize>0.5</MemorySize>
                  <InstanceTypeFamily>ecs.t1</InstanceTypeFamily>
            </InstanceType>
            <InstanceType>
                  <InstanceTypeId>ecs.t1.small</InstanceTypeId>
                  <CpuCoreCount>1</CpuCoreCount>
                  <MemorySize>1</MemorySize>
                  <InstanceTypeFamily>ecs.t1</InstanceTypeFamily>
            </InstanceType>
      </InstanceTypes>
</DescribeImageSupportInstanceTypesResponse>
```

`JSON` format

```
{
    "RequestId": "CF661E2D-4AFE-4BCD-959A-A65E14416B44",
    "RegionId": "cn-hangzhou",
    "ImageId": "ubuntu_16_0402_64_20G_alibase_20180409.vhd",
    "InstanceTypes": {
        "InstanceType": [{
            "InstanceTypeId": "ecs.t1.xsmall",
            "CpuCoreCount": 1,
            "MemorySize": 0.5,
            "InstanceTypeFamily": "ecs.t1"
        },
        {
            "InstanceTypeId": "ecs.t1.small",
            "CpuCoreCount": 1,
            "MemorySize": 1,
            "InstanceTypeFamily": "ecs.t1"
        }]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParamter|Invalid Parameter|The error message returned because the specified parameter is invalid.|
|404|InvalidUsage|The specifed Usage is not valid|The error message returned because the specified Usage parameter value \(image, disk, image\_disk, or none\) is invalid.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type does not exist or you are not authorized to manage instances of this instance type.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

