# ModifyInstanceVpcAttribute

You can call this operation to modify the VPC, private IP address, or VSwitch of a VPC-type instance.

## Description

The ECS instance must be in the **Stopped** \(`Stopped`\) state.

-   When you call this operation to modify the private IP address or VSwitch of an instance, take note of the following items:
    -   If the instance is a new instance, you must restart the instance before you call this operation on it.
    -   After the private IP address or VSwitch of an instance is modified, you must restart the instance before you can call this operation again.
-   When you call this operation to modify the VPC of an instance, take note of the following items:
    -   **Instance:**
        -   The instance cannot be associated with Server Load Balancer \(SLB\) instances.
        -   The instance cannot be in the Locked, To Be Released, Expired, Expired and Being Recycled, or Overdue and Being Recycled state. For more information, see [ECS instance lifecycle](~~25380~~).
        -   The instance cannot be used in other cloud services. For example, the instance cannot be in the process of being migrated or having its VPC changed, or the databases deployed on the instance cannot be managed by Data Transmission Service \(DTS\).
    -   **Network:**
        -   The cut-through mode or multi-EIP to ENI mode cannot be enabled for the instance.
        -   The instance cannot be associated with a high-availability virtual IP address \(HaVip\).
        -   The VSwitch of the instance cannot be associated with a custom route table.
        -   The instance cannot have Global Acceleration \(GA\) activated.
        -   The instance cannot be attached with a secondary ENI.
        -   The instance cannot be assigned an IPv6 address.
        -   The primary ENI of the instance cannot be associated with multiple IP addresses.
        -   The VSwitch must belong to the new VPC.
        -   The zones of the VSwitches before and after the modification must be the same.
        -   If the private IP address of the primary ENI is specified, the private IP address must be available and within the CIDR block of the VSwitch. If the private IP address is not specified, the system randomly assigns one. The available IP addresses in the new VSwitch CIDR block must be sufficient.
        -   If advanced features are enabled in the new VPC, see [Instance families that do not support advanced VPC features](~~163466~~) for the application scope of advanced features.
        -   The Alibaba Cloud account that owns the new VPC cannot share the VPC to other accounts.
    -   **Security group \(SecurityGroupId.N\):**
        -   All security groups must be of the same type.
        -   The valid values of N are based on the maximum number of security groups to which the instance can belong. For more information, see the "Security group limits" section in [Limits](~~25412~~).
        -   The VPC to which the security group belongs must be the new VPC.
        -   You can switch the instance to a security group of a different type.

            When you switch an ECS instance to a security group of a different type, you must understand the differences between the rule configurations of the two security group types to avoid affecting the instance network. For more information, see [Security group overview](~~25387~~).


## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceVpcAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyInstanceVpcAttribute|The operation that you want to perform. Set the value to ModifyInstanceVpcAttribute. |
|InstanceId|String|Yes|i-bp1iudwa5b1tqag1\*\*\*\*|The ID of the instance. |
|VSwitchId|String|Yes|vsw-bp1s5fnvk4gn3tw12\*\*\*\*|The ID of the VSwitch.

-   If this parameter is set to the ID of the current VSwitch, the VSwitch of the instance remains unchanged.
-   If this parameter is set to the ID of a new VSwitch and the `VpcId` parameter is not specified, the new VSwitch must belong to the same zone and VPC as the original VSwitch.
-   If the `VpcId` parameter is specified, the VSwitch ID specified by this parameter must belong to the VPC specified by the VpcId parameter and must belong to the same zone as the original VSwitch. |
|PrivateIpAddress|String|No|172.17.\*\*. \*\*|The new private IP address of the instance.

**Note:** The `PrivateIpAddress` value depends on the `VSwitchId` value . The specified IP address must be within the CIDR block of the specified VSwitch.

By default, if this parameter is not specified, a private IP address is randomly assigned from the CIDR block of the specified VSwitch. |
|VpcId|String|No|vpc-bp1vwnn14rqpyiczj\*\*\*\*|The ID of the new VPC. |
|SecurityGroupId.N|RepeatList|No|sg-o6w9l8bc8dgmkw87\*\*\*\*|The ID of security group N to which the instance belongs after the VPC is changed. This parameter is required only when the `VpcId` parameter is specified.

-   The specified security groups must be of the same type.
-   The security group list can contain one or more security groups to which the instance belongs after the modification. The valid values of N are based on the maximum number of security groups to which the instance can belong. For more information, see the "Security group limits" section in [Limits](~~25412~~).
-   The specified security groups must belong to the VPC specified by the `VpcId` parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceVpcAttribute
&InstanceId=i-bp1iudwa5b1tqag1****
&VSwitchId=vsw-bp1s5fnvk4gn3tw12****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyInstanceAttributeResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyInstanceAttributeResponse>
```

`JSON` format

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|400|InvalidPrivateIpAddress.Malformed|Specified private IP address is malformed.|The error message returned because the specified PrivateIpAddress parameter is invalid.|
|400|InvalidPrivateIpAddress.Duplicated|Specified private IP address is duplicated.|The error message returned because the specified private IP address is already in use. Change the IP address and try again.|
|400|IncorrectVSwitchStatus|The current status of virtual switch does not support this operation.|The error message returned because the specified VSwitch is in the Pending state and cannot be deleted.|
|404|InvalidVSwitchId.NotFound|Specified virtual switch does not exist.|The error message returned because the specified VSwitchId parameter does not exist.|
|400|IncorrectInstanceStatus|The current status of instance does not support this operation.|The error message returned when the operation is not supported while the instance is in the current state.|
|400|OperationDenied|Specified operation is denied as your instance is not in VPC.|The error message returned because the specified instance is not in a VPC.|
|400|InvalidVSwitchId.Mismatch|Specified instance and virtual switch are not in the same zone.|The error message returned because the specified instance and VSwitch do not belong to the same zone.|
|400|InvalidPrivateIpAddress.Mismatch|Specified private IP address is not in the CIDR block of virtual switch.|The error message returned because the specified private IP address is not in the CIDR block of the specified VSwitch.|
|404|InvalidVSwitchId.NotFound|Specified virtual switch is not found in current VPC.|The error message returned because the specified VSwitch does not exist in the current VPC.|
|400|InvalidPrivateIp.Changing|Previous action is not finished yet.|The error message returned because the private IP address is being modified.|
|404|NoSuchResource|The specified resource is not found.|The error message returned because the specified resource does not exist.|
|400|InvalidPrivateIpAddress.Duplicated|error new ip is the same with old ip|The error message returned because the new IP address is the same as the original one.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|OperationDenied|%s|The error message returned because the operation is denied.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

