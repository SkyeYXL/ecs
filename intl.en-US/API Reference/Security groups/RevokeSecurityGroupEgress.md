# RevokeSecurityGroupEgress

You can call this operation to delete an outbound security group rule. After the rule is deleted, the access control implemented by it is removed.

## Description

In the security group-related API documents, inbound traffic refers to the traffic sent by the source device and received at the destination device.

You can determine a security group rule by specifying one of the following groups of parameters. You cannot determine a security group rule by specifying only one parameter.

-   Parameters used to specify an outbound security group rule that controls access to a specified CIDR block: IpProtocol, PortRange, SourcePortRange \(optional\), NicType, Policy, DestCidrIp, and SourceCidrIp \(optional\).

    ```
    
        https://ecs.aliyuncs.com/?Action=RevokeSecurityGroupEgress
        &SecurityGroupId=sg-bp67acfmxazb4ph***
        &IpProtocol=tcp
        &DestCidrIp=10.0.0.0/8
        &PortRange=-22/22
        &NicType=intranet
        &Policy=Allow
        &<Common request parameters>
        
    ```

-   Parameters used to specify an outbound security group rule that controls access to a specified security group: IpProtocol, PortRange, SourcePortRange \(optional\), NicType, Policy, DestCidrIp \(optional\), DestGroupOwnerAccount, and DestGroupId.

    ```
    
        https://ecs.aliyuncs.com/?Action=RevokeSecurityGroupEgress
        &SecurityGroupId=sg-bp67acfmxazb4ph***
        &DestGroupId=sg-bp67acfmxazb4pi***
        &DestGroupOwnerAccount=test@aliyun.com
        &IpProtocol=tcp
        &PortRange=22/22
        &NicType=intranet
        &Policy=Drop
        &<Common request parameters>
        
    ```


If the security group rule to match does not exist, the RevokeSecurityGroupEgress operation succeeds but no rules are deleted.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=RevokeSecurityGroupEgress&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RevokeSecurityGroupEgress|The operation that you want to perform. Set the value to RevokeSecurityGroupEgress. |
|IpProtocol|String|Yes|tcp|The transport layer protocol. The value is case-insensitive. Valid values:

 -   icmp
-   gre
-   tcp
-   udp
-   all |
|PortRange|String|Yes|22/22|The range of destination ports relevant to the transport layer protocol. Valid values:

 -   When the IpProtocol parameter is set to tcp or udp, the port number range is 1 to 65535. Separate the start port and the end port with a forward slash \(/\). Example: 1/200.
-   When the IpProtocol parameter is set to icmp, the port number range is -1/-1, which indicates all ports.
-   When the IpProtocol parameter is set to gre, the port number range is -1/-1, which indicates all ports.
-   When IpProtocol is set to all, the port number range is -1/-1, which indicates all ports. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the source security group. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|SecurityGroupId|String|Yes|sg-bp67acfmxazb4p\*\*\*\*|The ID of the source security group. |
|DestGroupId|String|No|sg-bp67acfmxazb4p\*\*\*\*|The ID of the destination security group.

 -   You must specify either DestGroupId or DestCidrIp.
-   If DestGroupId is specified but DestCidrIp is not, NicType can be set only to intranet.
-   If both DestGroupId and DestCidrIp are specified, DestCidrIp takes precedence. |
|DestGroupOwnerId|Long|No|12345678910|The ID of the Alibaba Cloud account that manages the destination security group when you delete security group rules across accounts.

 -   If both DestGroupOwnerId and DestGroupOwnerAccount are empty, the access control is revoked from another security group managed by your account.
-   If DestCidrIp is specified, DestGroupOwnerId is ignored. |
|DestGroupOwnerAccount|String|No|EcsforCloud@Alibaba.com|The Alibaba Cloud account that manages the destination security group when you delete security group rules across accounts.

 -   If both DestGroupOwnerAccount and DestGroupOwnerId are empty, the access control is revoked from another security group managed by your account.
-   If DestCidrIp is specified, DestGroupOwnerAccount is ignored. |
|DestCidrIp|String|No|10.0.0.0/8|The range of destination IP addresses. CIDR blocks and IPv4 addresses are supported.

 This parameter is empty by default. |
|Ipv6DestCidrIp|String|No|2001:db8:1233:1a00::\*\*\*|The range of destination IPv6 addresses. CIDR blocks and IPv6 addresses are supported.

 This parameter is empty by default.

 **Note:** You can specify only the IP addresses of VPC-type instances. |
|SourceCidrIp|String|No|10.0.0.0/8|The range of source IP addresses. CIDR blocks and IPv4 addresses are supported.

 This parameter is empty by default. |
|Ipv6SourceCidrIp|String|No|2001:db8:1234:1a00::\*\*\*|The range of source IPv6 addresses. CIDR blocks and IPv6 addresses are supported.

 This parameter is empty by default.

 **Note:** You can specify only the IP addresses of VPC-type instances. |
|SourcePortRange|String|No|22/22|The range of source ports relevant to the transport layer protocol. Valid values:

 -   When the IpProtocol parameter is set to tcp or udp, the port number range is 1 to 65535. Separate the start port and the end port with a forward slash \(/\). Example: 1/200.
-   When the IpProtocol parameter is set to icmp, the port number range is -1/-1, which indicates all ports.
-   When the IpProtocol parameter is set to gre, the port number range is -1/-1, which indicates all ports.
-   When IpProtocol is set to all, the port number range is -1/-1, which indicates all ports. |
|Policy|String|No|accept|The access control policy. Valid values:

 -   accept: grants access.
-   drop: denies access without returning a rejection response.

 Default value: accept. |
|Priority|String|No|1|The priority of the security group rule. Valid values: 1 to 100.

 Default: 1. |
|NicType|String|No|intranet|The NIC type of the security group rule when the security group is in the classic network. Valid values:

 -   internet
-   intranet

 Default value: internet.

 The NicType parameter can be set only to intranet in the following cases:

 -   If the security group is in a VPC, this parameter is set to intranet by default and cannot be modified.
-   If DestGroupId is specified but DestCidrIp is not, NicType can be set to only intranet. |
|ClientToken|String|No|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value must contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|Description|String|No|TestDescription|The description of the security group rule. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=RevokeSecurityGroupEgress
&SecurityGroupId=sg-bp67acfmxazb4p****
&IpProtocol=tcp
&DestCidrIp=10.0.0.0/8
&PortRange=22/22
&NicType=intranet
&Policy=Allow
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RevokeSecurityGroupEgressResponse>
       <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</RevokeSecurityGroupEgressResponse>
```

`JSON` format

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is correct.|
|400|InvalidIpProtocol.ValueNotSupported|The specified IpProtocol does not exist.|The error message returned because the specified IpProtocol parameter is invalid.|
|400|InvalidIpPortRange.Malformed|The specified parameter "PortRange" is not valid.|The error message returned because the specified PortRange parameter is invalid.|
|404|InvalidDestGroupId.NotFound|The DestGroupId provided does not exist in our records.|The error message returned because the specified DestGroupId parameter does not exist.|
|403|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|The error message returned because the specified NIC type conflicts with the authorization record.|
|403|InvalidGroupAuthItem.NotFound|Specified group authorized item does not exist in our records.|The error message returned because the specified group authorization entry does not exist.|
|400|InvalidDestCidrIp.sMalformed|The specified parameter "DestCidrIp" is not valid.|The error message returned because the specified DestCidrIp parameter is invalid.|
|400|MissingParameter|The input parameter "DestGroupId" or "DestCidrIp" cannot be both blank.|The error message returned because the DestGroupId and DestCidrIp parameters cannot be empty at the same time.|
|400|InvalidPolicy.Malformed|The specified parameter "Policy" is not valid.|The error message returned because the specified Policy parameter is invalid.|
|400|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|The error message returned because the specified NicType parameter does not exist. Check whether the Nic type is correct.|
|400|InvalidDestGroupId.Mismatch|Specified security group and destination group are not in the same VPC.|The error message returned because the specified security group and the destination security group do not belong to the same VPC.|
|400|VPCDisabled|Can't use the SecurityGroup in VPC.|The error message returned because the current VPC does not support security groups.|
|403|InvalidSecurityGroup.IsSame|The authorized SecurityGroupId should be different from the DestGroupId.|The error message returned because the authorized security group is the same as the destination group.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|InvalidDestCidrIp.Malformed|The specified parameter "DestCidrIp" is not valid.|The error message returned because the specified DestCidrIp parameter is invalid.|
|400|MissingParameter.Dest|Either DestCidrIp or DestGroupId must be specified.|The error message returned because the DestCidrIp and DestGroupId parameters cannot be empty at the same time.|
|400|InvalidIpProtocol.ValueNotSupported|The parameter IpProtocol must be specified with case insensitive TCP, UDP, ICMP, GRE or All.|The error message returned because the IpProtocol parameter is not set to tcp, udp, icmp, gre, or all.|
|400|InvalidPriority.Malformed|The parameter Priority is invalid.|The error message returned because the specified Priority parameter is invalid.|
|400|InvalidPriority.ValueNotSupported|The parameter Priority is invalid.|The error message returned because the specified Priority parameter is invalid.|
|403|InvalidParamter.Conflict|The specified SecurityGroupId should be different from the SourceGroupId.|The error message returned because the specified security group is the same as the source security group.|
|400|InvalidDestCidrIp.Malformed|The specified parameter DestCidrIp is not valid.|The error message returned because the specified DestCidrIp parameter is invalid.|
|400|InvalidParam.SourceIp|%s|The error message returned because the specified SourceCidrIp parameter is invalid.|
|400|InvalidParam.DestIp|%s|The error message returned because the specified DestCidrIp parameter is invalid.|
|400|InvalidParam.Ipv6DestCidrIp|%s|The error message returned because the specified Ipv6DestCidrIp parameter is invalid.|
|400|InvalidParam.Ipv6SourceCidrIp|%s|The error message returned because the specified Ipv6SourceCidrIp parameter is invalid.|
|400|InvalidParam.Ipv4ProtocolConflictWithIpv6Address|%s|The error message returned because the specified parameter is invalid. Check whether you have entered an IPv6 address under an IPv4 protocol by mistake.|
|400|InvalidParam.Ipv6ProtocolConflictWithIpv4Address|%s|The error message returned because the specified parameter is invalid. Check whether you have entered an IPv4 address under an IPv6 protocol by mistake.|
|400|ILLEGAL\_IPV6\_CIDR|%s|The error message returned because the specified IPv6 address is invalid.|
|400|InvalidSecurityGroupId.Malformed|The specified parameter "SecurityGroupId" is not valid.|The error message returned because the specified SecurityGroupId parameter is invalid.|
|400|InvalidSourcePortRange.Malformed|The specified parameter "SourcePortRange" is not valid.|The error message returned because the specified SourcePortRange parameter is invalid.|
|400|InvalidSecurityGroupDiscription.Malformed|The specified security group rule description is not valid.|The error message returned because the specified Description parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

