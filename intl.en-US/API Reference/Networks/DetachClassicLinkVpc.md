# DetachClassicLinkVpc

You can call this operation to unlink a classic network-type instance from a virtual private cloud \(VPC\) by removing the ClassicLink connection between them. After the instance is unlinked from the VPC, it can no longer communicate with instances in the VPC.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DetachClassicLinkVpc&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DetachClassicLinkVpc|The operation that you want to perform. Set the value to DetachClassicLinkVpc. |
|InstanceId|String|Yes|i-bp67acfmxazb4p\*\*\*\*|The ID of the classic network-type instance. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the classic network-type instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|VpcId|String|Yes|vpc-bp67acfmxazb4p\*\*\*\*|The ID of the VPC to which the instance is linked. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DetachClassicLinkVpc
&RegionId=cn-hangzhou
&VpcId=vpc-bp67acfmxazb4p****
&InstanceId=i-bp67acfmxazb4p****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DetachClassicLinkVpcResponse>
      <RequestId>C0003E8B-B930-4F59-ADC0-0E209A9012A8</RequestId>
</DetachClassicLinkVpcResponse>
```

`JSON` format

```
{
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E209A9012A8"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidInstanceId.NotFound|The InstanceId provided does not exist in our records.|The error message returned because the specified InstanceId parameter does not exist.|
|403|InvalidRegionId.Malformed|The specified parameter ? RegionId? is not valid.|The error message returned because the specified RegionId parameter is invalid.|
|403|InvalidVpcId.Malformed|The specified parameter ? VpcId? is not valid.|The error message returned because the specified VpcId parameter is invalid.|
|403|InvalidInstanceId.MalFormed|The specified instance is not a classic network instance.|The error returned because the specified instance is not in the classic network.|
|403|OperationDenied|The instances are not allowed to detach from the linked vpc.|The error message returned because the instance cannot be unlinked from the VPC.|
|403|InvalidParameter.InvalidInstanceIdAndVpcId|The parameter InstanceId and VpcId are not allowed to be empty at the same time.|The error message returned because neither InstanceId nor VpcId is specified.|
|403|InvalidInstanceId.NotFound|The specified instance does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|403|InvalidStatus.InstanceStatus|The specified instance status is not support this operation ,expect status is running or shutted.|The error message returned because the operation is not supported while the instance is in the current state. The instance must be in the Running or Stopped state.|
|403|InvalidInstanceId.NotBelong|The specified instance is not belong to you.|The error message returned because the specified instance does not exist in your account.|
|403|Forbidden.SubUser|User not authorized to operate on the specified resource.|The error message returned because the RAM user is not authorized to manage the specified resource.|
|403|InvalidStatus.InstanceStatus|The specified instance status does not support this operation, expected status is Running or Stopped.|The error message returned because the operation is not supported while the instance is in the current state. The instance must be in the Running or Stopped state.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

