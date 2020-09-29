# DescribeInstanceTypes

You can call this operation to query the instance types provided by ECS.

## Description

The DescribeInstanceTypes operation is only used to query the configurations and performance of instance types. To query instance types that are available in a region, call the [DescribeAvailableResource](~~66186~~) operation.

To use more instance types, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to contact Alibaba Cloud.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceTypes&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeInstanceTypes|The operation that you want to perform. Set the value to DescribeInstanceTypes. |
|InstanceTypeFamily|String|No|ecs.g6|The instance family to which the instance type belongs. For more information about valid values, see [DescribeInstanceTypeFamilies](~~25621~~).

For more information, see [Instance families](~~25378~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceTypes|Array of InstanceType| |The collection of details about instance types. |
|InstanceType| | | |
|BaselineCredit|Integer|4|The baseline vCPU computing performance \(overall performance of all vCPUs\) of the t5 or t6 burstable instance family. |
|CpuCoreCount|Integer|8|The number of vCPUs. |
|EniIpv6AddressQuantity|Integer|1|The maximum number of IPv6 addresses for a single Elastic Network Interface \(ENI\). |
|EniPrivateIpAddressQuantity|Integer|6|The maximum number of private IP addresses for a single ENI. |
|EniQuantity|Integer|2|The maximum number of ENIs that can be attached to an instance. |
|EniTotalQuantity|Integer|0|**Note:** This parameter is in invitational preview and not available. |
|EniTrunkSupported|Boolean|false|**Note:** This parameter is in invitational preview and not available. |
|GPUAmount|Integer|2|The number of GPUs. |
|GPUSpec|String|NVIDIA V100|The GPU type. |
|InitialCredit|Integer|120|The initial vCPU credit value of the t5 or t6 burstable instance family. |
|InstanceBandwidthRx|Integer|1024000|The maximum inbound bandwidth of the internal network for the instance. Unit: Kbit/s. |
|InstanceBandwidthTx|Integer|1024000|The maximum outbound bandwidth of the internal network for the instance. Unit: Kbit/s. |
|InstanceFamilyLevel|String|EnterpriseLevel|The level of the instance family. Valid values:

-   EntryLevel
-   EnterpriseLevel
-   CreditEntryLevel. For more information, see [Burstable instance families](~~59977~~). |
|InstancePpsRx|Long|300000|The inbound packet forwarding rate of the internal network. Unit: pps |
|InstancePpsTx|Long|300000|The outbound packet forwarding rate of the internal network. Unit: pps |
|InstanceTypeFamily|String|ecs.g5|The instance family. |
|InstanceTypeId|String|ecs.g5.large|The ID of the instance type. |
|LocalStorageAmount|Integer|1|The number of local disks attached to the instance. |
|LocalStorageCapacity|Long|5000|The capacity of the local disk attached to the instance. Unit: GiB. |
|LocalStorageCategory|String|local\_ssd\_pro|The category of the local disk. For more information, see [Local disks](~~63138~~). Valid values:

-   local\_hdd\_pro: local SATA HDDs attached to instances of the d1ne and d1 instance families.
-   local\_ssd\_pro: local NVMe SSDs attached to instances of the i2, i2g, i1, ga1, and gn5 instance families. |
|MaximumQueueNumberPerEni|Integer|8|The maximum queue number per ENI. |
|MemorySize|Float|8.0|The memory size. Unit: GiB. |
|PrimaryEniQueueNumber|Integer|4|The default queue number of the primary ENI. |
|SecondaryEniQueueNumber|Integer|4|The default queue number of the secondary ENI. |
|TotalEniQueueQuantity|Integer|128|The maximum ENI queue number that the instance type supports. |
|RequestId|String|00827261-20B7-4562-83F2-4DF39876A45A|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceTypes
&InstanceTypeFamily=ecs.g6
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeInstanceTypesResponse>
      <RequestId>CEC8A6BA-6805-4807-AB93-EB2E4B59EAF3</RequestId>
      <InstanceTypes>
            <InstanceType>
                  <MemorySize>256</MemorySize>
                  <InstancePpsTx>4000000</InstancePpsTx>
                  <EniIpv6AddressQuantity>1</EniIpv6AddressQuantity>
                  <PrimaryEniQueueNumber>32</PrimaryEniQueueNumber>
                  <CpuCoreCount>64</CpuCoreCount>
                  <TotalEniQueueQuantity>256</TotalEniQueueQuantity>
                  <EniTotalQuantity>60</EniTotalQuantity>
                  <EniTrunkSupported>true</EniTrunkSupported>
                  <InstanceTypeFamily>ecs.g6</InstanceTypeFamily>
                  <InstancePpsRx>4000000</InstancePpsRx>
                  <EniQuantity>8</EniQuantity>
                  <InstanceBandwidthRx>20480000</InstanceBandwidthRx>
                  <GPUAmount>0</GPUAmount>
                  <InstanceBandwidthTx>20480000</InstanceBandwidthTx>
                  <SecondaryEniQueueNumber>32</SecondaryEniQueueNumber>
                  <LocalStorageCategory></LocalStorageCategory>
                  <GPUSpec></GPUSpec>
                  <InstanceFamilyLevel>EnterpriseLevel</InstanceFamilyLevel>
                  <InstanceTypeId>ecs.g6.16xlarge</InstanceTypeId>
                  <EniPrivateIpAddressQuantity>20</EniPrivateIpAddressQuantity>
            </InstanceType>
            <InstanceType>
                  <MemorySize>128</MemorySize>
                  <InstancePpsTx>2000000</InstancePpsTx>
                  <EniIpv6AddressQuantity>1</EniIpv6AddressQuantity>
                  <PrimaryEniQueueNumber>16</PrimaryEniQueueNumber>
                  <CpuCoreCount>32</CpuCoreCount>
                  <TotalEniQueueQuantity>128</TotalEniQueueQuantity>
                  <EniTotalQuantity>8</EniTotalQuantity>
                  <EniTrunkSupported>false</EniTrunkSupported>
                  <InstanceTypeFamily>ecs.g6</InstanceTypeFamily>
                  <InstancePpsRx>2000000</InstancePpsRx>
                  <EniQuantity>8</EniQuantity>
                  <InstanceBandwidthRx>10240000</InstanceBandwidthRx>
                  <GPUAmount>0</GPUAmount>
                  <InstanceBandwidthTx>10240000</InstanceBandwidthTx>
                  <SecondaryEniQueueNumber>16</SecondaryEniQueueNumber>
                  <LocalStorageCategory></LocalStorageCategory>
                  <GPUSpec></GPUSpec>
                  <InstanceFamilyLevel>EnterpriseLevel</InstanceFamilyLevel>
                  <InstanceTypeId>ecs.g6nv.8xlarge</InstanceTypeId>
                  <EniPrivateIpAddressQuantity>20</EniPrivateIpAddressQuantity>
            </InstanceType>
      </InstanceTypes>
</DescribeInstanceTypesResponse>
```

`JSON` format

```
{
    "RequestId": "CEC8A6BA-6805-4807-AB93-EB2E4B59EAF3",
    "InstanceTypes": {
        "InstanceType": [
            {
                "MemorySize": 256,
                "InstancePpsTx": 4000000,
                "EniIpv6AddressQuantity": 1,
                "PrimaryEniQueueNumber": 32,
                "CpuCoreCount": 64,
                "TotalEniQueueQuantity": 256,
                "EniTotalQuantity": 60,
                "EniTrunkSupported": true,
                "InstanceTypeFamily": "ecs.g6",
                "InstancePpsRx": 4000000,
                "EniQuantity": 8,
                "InstanceBandwidthRx": 20480000,
                "GPUAmount": 0,
                "InstanceBandwidthTx": 20480000,
                "SecondaryEniQueueNumber": 32,
                "LocalStorageCategory": "",
                "GPUSpec": "",
                "InstanceFamilyLevel": "EnterpriseLevel",
                "InstanceTypeId": "ecs.g6.16xlarge",
                "EniPrivateIpAddressQuantity": 20
            },
            {
                "MemorySize": 128,
                "InstancePpsTx": 2000000,
                "EniIpv6AddressQuantity": 1,
                "PrimaryEniQueueNumber": 16,
                "CpuCoreCount": 32,
                "TotalEniQueueQuantity": 128,
                "EniTotalQuantity": 8,
                "EniTrunkSupported": false,
                "InstanceTypeFamily": "ecs.g6",
                "InstancePpsRx": 2000000,
                "EniQuantity": 8,
                "InstanceBandwidthRx": 10240000,
                "GPUAmount": 0,
                "InstanceBandwidthTx": 10240000,
                "SecondaryEniQueueNumber": 16,
                "LocalStorageCategory": "",
                "GPUSpec": "",
                "InstanceFamilyLevel": "EnterpriseLevel",
                "InstanceTypeId": "ecs.g6nv.8xlarge",
                "EniPrivateIpAddressQuantity": 20
            }
        ]
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

