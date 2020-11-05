# ModifyAutoProvisioningGroup

You can call this operation to modify the configurations of an auto provisioning group.

## Description

Before you call this operation, take note of the following items:

-   If you modify the capacity or capacity-related settings of an auto provisioning group, the group executes scheduling tasks once after it is modified.
-   You cannot modify an auto provisioning group when the group is being deleted.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyAutoProvisioningGroup&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyAutoProvisioningGroup|The operation that you want to perform. Set the value to ModifyAutoProvisioningGroup. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the auto provisioning group to be modified. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|AutoProvisioningGroupId|String|No|apg-bp67acfmxazb4ph\*\*\*\*|The ID of the auto provisioning group. |
|ExcessCapacityTerminationPolicy|String|No|no-termination|Specifies whether to stop excess preemptible instances when the target capacity of the specified auto provisioning group is exceeded. Valid values:

-   no-termination: The system continues to run excess preemptible instances.
-   termination: stops excess preemptible instances. The action to be performed on these stopped instances is specified by the SpotInstanceInterruptionBehavior parameter.

**Note:** The SpotInstanceInterruptionBehavior parameter is set when the auto provisioning group is created, and cannot be modified. |
|DefaultTargetCapacityType|String|No|Spot|Specifies the billing method of the capacity difference when the sum of the values of the PayAsYouGoTargetCapacity and SpotTargetCapacity parameters is less than the value of the TotalTargetCapacity parameter. Valid values:

-   PayAsYouGo: pay-as-you-go
-   Spot: preemptible instance |
|TerminateInstancesWithExpiration|Boolean|No|false|Specifies whether the preemptible instances are stopped when the auto provisioning group expires. Valid values:

-   true: The preemptible instances are stopped. The action to be performed on these stopped instances is specified by the SpotInstanceInterruptionBehavior parameter.
-   false: The preemptible instances continue to run.

**Note:** The SpotInstanceInterruptionBehavior parameter is set when the auto provisioning group is created, and cannot be modified. |
|MaxSpotPrice|Float|No|0.5|The maximum price of preemptible instances in the auto provisioning group.

**Note:** If both the MaxSpotPrice and LaunchTemplateConfig.N.MaxPrice parameters are specified, the maximum price is the lower value of the two parameters. The LaunchTemplateConfig.N.MaxPrice parameter is set when the auto provisioning group is created, and cannot be modified. |
|TotalTargetCapacity|String|No|70|The target capacity of the auto provisioning group. The parameter value is a positive integer.

The target capacity of the auto provisioning group must be at least the sum of the capacity of pay-as-you-go instances specified by the PayAsYouGoTargetCapacity parameter and the capacity of preemptible instances specified by the SpotTargetCapacity parameter. |
|PayAsYouGoTargetCapacity|String|No|30|The target capacity of pay-as-you-go instances in the auto provisioning group. Valid values: Set this parameter to a value smaller than that of the TotalTargetCapacity parameter. |
|SpotTargetCapacity|String|No|30|The target capacity of preemptible instances in the auto provisioning group. Valid values: Set this parameter to a value smaller than that of the TotalTargetCapacity parameter. |
|AutoProvisioningGroupName|String|No|apg-test|The name of the auto provisioning group. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|B48A12CD-1295-4A38-A8F0-0E92C937\*\*\*\*|The ID of the request. |

## Examples

Sample requests

```
http(s)://ecs.aliyuncs.com/?Action=ModifyAutoProvisioningGroup
&RegionId=cn-hangzhou
&AutoProvisioningGroupId=apg-bp67acfmxazb4ph****
&TotalTargetCapacity=70
&MaxSpotPrice=0.5
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyAutoProvisioningGroupResponse>
    <RequestId>928E2273-5715-46B9-A730-238DC996****</RequestId>
</ModifyAutoProvisioningGroupResponse>
```

`JSON` format

```
{
    "RequestId": "B48A12CD-1295-4A38-A8F0-0E92C937****"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbidden.RAM|User not authorized to operate on the specified resource, or this API doesn't support RAM.|The error message returned because you are not authorized to manage this resource, or this API operation does not support RAM roles.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

