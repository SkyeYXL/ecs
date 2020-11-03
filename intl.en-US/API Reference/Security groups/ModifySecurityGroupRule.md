# ModifySecurityGroupRule

You can call this operation to modify the description of inbound rules of a security group. You can modify only the description by calling this operation. If you want to modify the policies, port ranges, and authorization objects of security group rules, log on to the ECS console.

## Description

In the security group-related API documents, inbound traffic refers to the traffic that is sent by the source device and received at the destination device.

You can determine an inbound rule by specifying one of the following groups of parameters. You cannot determine a security group rule by specifying only one parameter.

-   Parameters used to specify an inbound security group rule that controls access from a specified CIDR block: IpProtocol, PortRange, SourcePortRange \(optional\), NicType, Policy, DestCidrIp, and SourceCidrIp \(optional\).
-   Parameters used to specify an inbound security group rule that controls access from a specified security group: IpProtocol, PortRange, SourcePortRange \(optional\), NicType, Policy, DestCidrIp \(optional\), DestGroupOwnerAccount, and DestGroupId.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifySecurityGroupRule&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifySecurityGroupRule|The operation that you want to perform. Set the value to ModifySecurityGroupEgressRule. |
|IpProtocol|String|Yes|all|The transport layer protocol. The value is case-insensitive. Valid values:

-   icmp
-   gre
-   tcp
-   udp
-   all |
|PortRange|String|Yes|80/80|The range of destination ports relevant to the transport layer protocol. Valid values:

-   When the IpProtocol parameter is set to tcp or udp, the port number range is 1 to 65535. Separate the start port and the end port with a forward slash \(/\). Example: 1/200.
-   When the IpProtocol parameter is set to icmp, the port number range is -1/-1, which indicates all ports.
-   When the IpProtocol parameter is set to gre, the port number range is -1/-1, which indicates all ports.
-   When IpProtocol is set to all, the port number range is -1/-1, which indicates all ports. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the destination security group. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|SecurityGroupId|String|Yes|sg-bp67acfmxazb4p\*\*\*\*|The ID of the destination security group. |
|SourceGroupId|String|No|sg-bp67acfmxazb4p\*\*\*\*|The ID of the source security group for which you want to configure access control. You must specify at least one of the SourceGroupId and SourceCidrIp parameters.

If SourceGroupId is specified but SourceCidrIp is not, the NicType parameter must be set to intranet. If both SourceGroupId and SourceCidrIp are specified, SourceCidrIp takes precedence. |
|SourceGroupOwnerId|Long|No|12345678910|The ID of the Alibaba Cloud account that manages the source security group when you set a security group rule across accounts.

-   If both SourceGroupOwnerId and SourceGroupOwnerAccount are empty, access permissions are configured for another security group managed by your account.
-   If SourceCidrIp is specified, SourceGroupOwnerId is ignored. |
|SourceGroupOwnerAccount|String|No|EcsforCloud@Alibaba.com|The Alibaba Cloud account that manages the source security group when you set a security group rule across accounts.

-   If both SourceGroupOwnerId and SourceGroupOwnerAccount are empty, access permissions are configured for another security group managed by your account.
-   If SourceCidrIp is specified, SourceGroupOwnerAccount is ignored. |
|SourceCidrIp|String|No|10.0.0.0/8|The range of source IP addresses. CIDR blocks and IPv4 addresses are supported.

This parameter is empty by default. |
|Ipv6SourceCidrIp|String|No|2001:db8:1233:1a00::\*\*\*|The range of source IPv6 addresses. CIDR blocks and IPv6 addresses are supported.

**Note:** You can specify only the IP addresses of instances in VPCs.

This parameter is empty by default. |
|SourcePortRange|String|No|80/80|The range of source ports relevant to the transport layer protocol. Valid values:

-   When the IpProtocol parameter is set to tcp or udp, the port number range is 1 to 65535. Separate the start port and the end port with a forward slash \(/\). Example: 1/200.
-   When the IpProtocol parameter is set to icmp, the port number range is -1/-1, which indicates all ports.
-   When the IpProtocol parameter is set to gre, the port number range is -1/-1, which indicates all ports.
-   When IpProtocol is set to all, the port number range is -1/-1, which indicates all ports. |
|DestCidrIp|String|No|10.0.0.0/8|The range of destination IP addresses. CIDR blocks and IPv4 addresses are supported.

This parameter is empty by default. |
|Ipv6DestCidrIp|String|No|2001:db8:1234:1a00::\*\*\*|The range of destination IPv6 addresses. CIDR blocks and IPv6 addresses are supported.

**Note:** You can specify only the IP addresses of instances in VPCs.

This parameter is empty by default. |
|Policy|String|No|accept|The access control policy. Valid values:

-   accept: grants access.
-   drop: denies access without returning a rejection response.

Default value: accept. |
|Priority|String|No|1|The priority of the security group rule. Valid values: 1 to 100.

Default: 1. |
|NicType|String|No|intranet|The NIC type of the rule when the security group is in the classic network. Valid values:

-   internet
-   intranet

Default value: internet.

The NicType parameter can be set to only intranet in the following cases:

-   If the security group is in a VPC, this parameter is required and must be set to intranet.
-   If DestGroupId is specified but DestCidrIp is not, NicType must be set to intranet. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value must contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|Description|String|No|This is a new security group rule.|The description of the security group rule. The description must be 1 to 512 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifySecurityGroupRule
&SecurityGroupId=sg-bp67acfmxazb4p****
&SourceGroupId=sg-bp67acfmxazb4p****
&SourceGroupOwnerAccount=EcsforCloud@Alibaba.com
&IpProtocol=all
&PortRange=80/80
&Policy=accept
&Description=This is a new security group rule.
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifySecurityGroupRuleResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</ModifySecurityGroupRuleResponse>
```

`JSON` format

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist in this account. Check whether the security group ID is correct.|
|404|InvalidSourceGroupId.NotFound|The SourceGroupId provided does not exist in our records.|The error message returned because the specified SourceGroupId parameter does not exist.|
|400|OperationDenied|The specified IpProtocol does not exist or IpProtocol and PortRange do not match.|The error message returned because the specified IpProtocol parameter does not exist or does not match the specified PortRange parameter.|
|400|InvalidIpProtocol.Malformed|The specified parameter "PortRange" is not valid.|The error message returned because the specified IpProtocol or PortRange parameter is invalid.|
|403|InvalidSourceGroupId.Mismatch|NicType is required or NicType expects intrnet.|The error message returned because the NicType parameter is not specified or is not set to intranet.|
|400|InvalidSourceCidrIp.Malformed|The specified parameter "SourceCidrIp" is not valid.|The error message returned because the specified SourceCidrIp parameter is invalid.|
|403|MissingParameter|The input parameter "SourceGroupId" or "SourceCidrIp" cannot be both blank.|The error message returned because the SourceGroupId and SourceCidrIp parameters cannot be empty at the same time.|
|400|InvalidPolicy.Malformed|The specified parameter "Policy" is not valid.|The error message returned because the specified Policy parameter is invalid.|
|400|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|The error message returned because the specified NicType parameter does not exist.|
|400|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|The error message returned because the specified NIC type conflicts with the authorization record.|
|403|AuthorizationLimitExceed|The limit of authorization records in the security group reaches.|The error message returned because the maximum number of authorized security group rules has been reached. Check whether your authorization policy is valid.|
|403|InvalidParamter.Conflict|The specified SecurityGroupId should be different from the SourceGroupId.|The error message returned because the specified security group is the same as the source security group.|
|400|InvalidSourceGroupId.Mismatch|Specified security group and source group are not in the same VPC.|The error message returned because the specified security group and the source security group do not belong to the same VPC.|
|400|InvalidSourceGroup.NotFound|Specified source security group does not exist.|The error message returned because the specified SourceGroupId parameter does not exist.|
|400|VPCDisabled|Can't use the SecurityGroup in VPC.|The error message returned because the current VPC does not support security groups.|
|400|InvalidPriority.Malformed|The parameter Priority is invalid.|The error message returned because the specified Priority parameter is invalid.|
|400|InvalidPriority.ValueNotSupported|The parameter Priority is invalid.|The error message returned because the specified Priority parameter is invalid.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|InvalidNetworkType.Mismatch|The specified SecurityGroup network type should be same with SourceGroup network type \(vpc or classic\).|The error message returned because the network type of the specified security group is different from that of the source security group.|
|400|InvalidSecurityGroupDiscription.Malformed|The specified security group rule description is not valid.|The error message returned because the specified Description parameter is invalid.|
|404|SecurityGroupRule.NotFound|The target security group rule not exist.|The error message returned because the specified security group rule does not exist.|
|400|MissingParameter.Source|Either SourceCidrIp or SourceGroupId must be specified.|The error message returned because the SourceCidrIp and SourceGroupId parameters cannot be empty at the same time.|
|400|InvalidIpProtocol.ValueNotSupported|The parameter IpProtocol must be specified with case insensitive TCP, UDP, ICMP, GRE or All.|The error message returned because the IpProtocol parameter is not set to tcp, udp, icmp, gre, or all.|
|400|InvalidParam.SourceIp|%s|The error message returned because the specified SourceCidrIp parameter is invalid.|
|400|InvalidParam.DestIp|%s|The error message returned because the specified DestCidrIp parameter is invalid.|
|400|InvalidParam.Ipv6DestCidrIp|%s|The error message returned because the specified Ipv6DestCidrIp parameter is invalid.|
|400|InvalidParam.Ipv6SourceCidrIp|%s|The error message returned because the specified Ipv6SourceCidrIp parameter is invalid.|
|400|InvalidParam.Ipv4ProtocolConflictWithIpv6Address|%s|The error message returned because the specified parameter is invalid. Check whether you have entered an IPv6 address under an IPv4 protocol by mistake.|
|400|InvalidParam.Ipv6ProtocolConflictWithIpv4Address|%s|The error message returned because the specified parameter is invalid. Check whether you have entered an IPv4 address under an IPv6 protocol by mistake.|
|400|ILLEGAL\_IPV6\_CIDR|%s|The error message returned because the specified IPv6 address is invalid.|
|400|InvalidSourcePortRange.Malformed|The specified parameter "SourcePortRange" is not valid.|The error message returned because the specified SourcePortRange parameter is invalid.|
|400|InvalidSecurityGroupId.Malformed|The specified parameter "SecurityGroupId" is not valid.|The error message returned because the specified SecurityGroupId parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

