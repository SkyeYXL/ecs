# CreateNetworkInterface

You can call this operation to create an elastic network interface \(ENI\).

## Description

-   The newly created ENI is in the Available state.
-   An ENI can be bound only to a single VPC-type instance in the same zone.
-   An ENI can be bound only to a single instance. Before you bind an ENI to another instance, you must unbind the ENI from the instance to which the ENI is bound.
-   When an ENI is bound to another instance, its attributes remain unchanged and the data traffic is redirected to the new instance.
-   By default, you can create a maximum of 100 ENIs in a region for an Alibaba Cloud account. You can [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to apply for a higher quota.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CreateNetworkInterface&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateNetworkInterface|The operation that you want to perform. Set the value to CreateNetworkInterface. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|VSwitchId|String|Yes|vsw-bp1s5fnvk4gn2tws03\*\*\*\*|The ID of the VSwitch in the specified VPC. The private IP addresses assigned to the ENI must be available IP addresses within the CIDR block of the VSwitch. |
|Tag.N.Key|String|No|TestKey|The key of tag N to be bound to the ENI. Valid values of N: 1 to 20. It cannot be an empty string. The key can be up to 128 characters in length. It cannot start with aliyun or acs:, or contain http:// or https://. |
|Tag.N.Value|String|No|TestValue|The value of tag N to be bound to the ENI. Valid values of N: 1 to 20. It can be an empty string. The value can be up to 128 characters in length and cannot start with acs: or contain http:// or https://. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group. |
|PrimaryIpAddress|String|No|172.17.\*\*. \*\*|The primary private IP address of the ENI.

The specified IP address must be available within the CIDR block of the VSwitch. If this parameter is not specified, an available IP address is assigned from the VSwitch CIDR block at random. |
|SecurityGroupId|String|No|sg-bp1fg655nh68xyz9i\*\*\*\*|The ID of the security group. The security group and the ENI must belong to the same VPC. |
|SecurityGroupIds.N|RepeatList|No|sg-bp1fg655nh68xyz9i\*\*\*\*|The ID of security group N. The security groups and the ENI must belong to the same VPC. The valid values of N are based on the maximum number of security groups to which an ENI can be added. For more information, see [Limits](~~25412~~).

**Note:** You cannot specify `SecurityGroupId` and `SecurityGroupIds.N` at the same time. |
|NetworkInterfaceName|String|No|testNetworkInterfaceName|The name of the ENI. The name must be 2 to 128 characters in length, and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

This parameter is empty by default. |
|Description|String|No|testDescription|The description of the ENI. The description must be 2 to 256 characters in length and cannot start with http:// or https://.

This parameter is empty by default. |
|PrivateIpAddress.N|RepeatList|No|172.17.\*\*. \*\*|Specifies secondary private IP address N of the ENI. This IP address must be an available IP address within the CIDR block of the VSwitch to which the ENI belongs. Valid values of N: 0 to 10.

**Note:** To assign secondary private IP addresses, you cannot specify the `PrivateIpAddress.N` and `SecondaryPrivateIpAddressCount` parameters at the same time. |
|SecondaryPrivateIpAddressCount|Integer|No|1|The number of private IP addresses that can be automatically created by ECS. |
|QueueNumber|Integer|No|1|The queue number of the ENI. Valid values: 1 to 2048.

When you bind an ENI, the value must be less than the maximum queue number of the ENI allowed for the instance type. To view the maximum queue number per ENI allowed for an instance type, you can call the [DescribeInstanceTypes](~~25620~~) operation to query the `MaximumQueueNumberPerEni` field.

This parameter is empty by default. When you bind an ENI, its default queue number is used. To view the default queue number per ENI allowed for an instance type, you can call the [DescribeInstanceTypes](~~25620~~) operation to query the `SecondaryEniQueueNumber` field. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must make sure that it is unique among different requests. The **ClientToken** value must contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Description|String|testDescription|The description of the ENI. |
|MacAddress|String|00:16:3e:12:\*\*:\*\*|The MAC address of the ENI. |
|NetworkInterfaceId|String|eni-bp14v2sdd3v8htlnm\*\*\*|The ID of the ENI. |
|NetworkInterfaceName|String|my-eni-name|The name of the ENI. |
|OwnerId|String|123456\*\*\*\*|The ID of the account that owns the ENI. |
|PrivateIpAddress|String|172.17.\*\*. \*\*|The private IP address of the ENI. |
|PrivateIpSets|Array of PrivateIpSet| |The private IP addresses of the ENI. |
|PrivateIpSet| | | |
|Primary|Boolean|true|Indicates whether the IP address is the primary private IP address. |
|PrivateIpAddress|String|172.17.\*\*. \*\*|The private IP address of the instance. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|ResourceGroupId|String|rg-2ze88m67qx5z\*\*\*\*|The ID of the resource group. |
|SecurityGroupIds|List|sg-bp18kz60mefsicfg\*\*\*\*|The IDs of security groups. |
|ServiceID|Long|12345678910|The ID of the distributor to which the ENI belongs. |
|ServiceManaged|Boolean|true|Indicates whether the user is an Alibaba Cloud service or a distributor. |
|Status|String|Available|The status of the ENI. |
|Tags|Array of Tag| |An array of Tag data. |
|Tag| | | |
|TagKey|String|TestKey|The tag key of the ENI. |
|TagValue|String|TestValue|The tag value of the ENI. |
|Type|String|Secondary|The type of the ENI. |
|VSwitchId|String|vsw-bp16usj2p27htro3\*\*\*\*|The ID of the VSwitch. |
|VpcId|String|vpc-bp1j7w3gc1cexjqd\*\*\*\*|The ID of the VPC where the ENI belongs. |
|ZoneId|String|cn-hangzhou-e|The zone ID of the ENI. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=CreateNetworkInterface
&RegionId=cn-hangzhou
&SecurityGroupIds.1=sg-bp1fg655nh68xyz9i****
&SecurityGroupIds.2=sg-bp67acfmxazb4ph****
&VSwitchId=vsw-bp1s5fnvk4gn2tws03****
&Tag.1.Key=TestKey
&Tag.1.Value=TestValue
&ResourceGroupId=rg-bp67acfmxazb4ph****
&PrimaryIpAddress=172.17. **. **
&NetworkInterfaceName=testNetworkInterfaceName
&Description=testDescription
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateNetworkInterfaceResponse>
      <Description>testDescription</Description>
      <MacAddress>00:16:3e:12:**:**</MacAddress>
      <NetworkInterfaceName>my-eni-name</NetworkInterfaceName>
      <PrivateIpAddress>172.17. **. **</PrivateIpAddress>
      <RequestId>0910A187-1002-4488-9FE5-EF770D142B73</RequestId>
      <ResourceGroupId>rg-2ze88m67qx5z****</ResourceGroupId>
      <VSwitchId>vsw-bp16usj2p27htro3****</VSwitchId>
      <VpcId>vpc-bp1j7w3gc1cexjqd****</VpcId>
      <ZoneId>cn-hangzhou-e</ZoneId>
      <NetworkInterfaceId>eni-bp1bighqoqowq73yw91r</NetworkInterfaceId>
      <Status>InUse</Status>
      <SecurityGroupIds>
            <SecurityGroupId>sg-bp18kz60mefsicfg****</SecurityGroupId>
      </SecurityGroupIds>
      <Type>Primary</Type>
      <OwnerId>123456****</OwnerId>
      <PrivateIpSets>
            <PrivateIpSet>
                  <PrivateIpAddress>192.168.0.49</PrivateIpAddress>
                  <Primary>true</Primary>
            </PrivateIpSet>
      </PrivateIpSets>
</CreateNetworkInterfaceResponse>
```

`JSON` format

```
{
    "Description": "testDescription",
    "MacAddress": "00:16:3e:12:**:**",
    "NetworkInterfaceName":"my-eni-name",
    "PrivateIpAddress": "172.17. **. **",
    "RequestId": "0910A187-1002-4488-9FE5-EF770D142B73",
    "ResourceGroupId": "rg-2ze88m67qx5z****",
    "VSwitchId": "vsw-bp16usj2p27htro3****",
    "VpcId": "vpc-bp1j7w3gc1cexjqd****",
    "ZoneId": "cn-hangzhou-e",
    "NetworkInterfaceId": "eni-bp1bighqoqowq73yw91r",
    "Status": "InUse",
    "SecurityGroupIds": {
        "SecurityGroupId": [
            "sg-bp18kz60mefsicfg****"
        ]
    },
    "Type": "Primary",
    "OwnerId": "123456****",
    "PrivateIpSets": {
        "PrivateIpSet": [
            {
                "PrivateIpAddress": "192.168.0.49",
                "Primary": true
            }
        ]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|InvalidUserType.NotSupported|%s|The error message returned because your account does not support this operation.|
|403|Abs.InvalidAccount.NotFound|%s|The error message returned because your Alibaba Cloud account does not exist or your AccessKey pair has expired.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|403|Forbidden.NotSupportRAM|%s|The error message returned because RAM users are not authorized to perform this operation.|
|400|UnsupportedParameter|%s|The error message returned because a parameter is not supported.|
|403|Forbidden.SubUser|%s|The error message returned because your account has no permission on this resource. Apply for permissions from the Alibaba Cloud account.|
|400|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|400|InvalidInstanceID.Malformed|%s|The error message returned because the specified InstanceId parameter is invalid.|
|400|InvalidOperation.InvalidEcsState|%s|The error message returned because the operation is not supported while the instance is in the current state.|
|400|InvalidOperation.InvalidEniState|%s|The error message returned because the operation is not supported while the ENI is in the current state.|
|400|InvalidOperation.DetachPrimaryEniNotAllowed|%s|The error message returned because the primary ENI cannot be unbound from the instance.|
|404|InvalidEcsId.NotFound|%s|The error message returned because the specified instance ID does not exist.|
|404|InvalidEniId.NotFound|%s|The error message returned because the specified ENI ID does not exist.|
|404|InvalidVSwitchId.NotFound|%s|The error message returned because the specified VSwitch ID does not exist.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|MaxEniCountExceeded|%s|The error message returned because the maximum number of ENIs that can be managed has been reached.|
|403|EniPerInstanceLimitExceeded|%s|The error message returned because the maximum number of ENIs that can be bound to the specified instance has been reached.|
|403|InvalidOperation.AvailabilityZoneMismatch|%s|The error message returned because the operation is invalid.|
|403|InvalidOperation.VpcMismatch|%s|The error message returned because the operation is invalid. Check whether the VPC in the operation corresponds to other parameters.|
|403|SecurityGroupInstanceLimitExceed|%s|The error message returned because the maximum number of instances in the specified security group has been reached.|
|403|InvalidSecurityGroupId.NotVpc|%s|The error message returned because the specified security group ID is invalid and the network type of the security group is not VPC.|
|403|InvalidOperation.InvalidEniType|%s|The error message returned because the ENI type does not support this operation.|
|403|InvalidVSwitchId.IpNotEnough|%s|The error message returned because available IP addresses within the CIDR block of the specified VSwitch are insufficient.|
|403|InvalidVSwitchId.IpInvalid|%s|The error message returned because the specified private IP address is invalid.|
|400|Forbidden.RegionId|%s|The error message returned because the service is unavailable in the current region.|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|The error message returned because the resource group does not exist in the records.|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|The error message returned because the specified tag key already exists. Tag keys must be unique.|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|The error message returned because the specified tag key is invalid.|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|The error message returned because the specified tag value is invalid.|
|403|QuotaExceed.Tags|%s|The error message returned because the maximum number of tags has been reached.|
|403|InvalidIp.Address|%s|The error message returned because the specified IPv6 address is invalid.|
|403|InvalidIp.IpRepeated|%s|The error message returned because the specified IP address already exists.|
|400|InvalidPrivateIpAddress.Duplicated|Specified private IP address is duplicated.|The error message returned because the specified private IP address has been used. Change the IP address and try again.|
|400|InvalidParameter.Conflict|%s|The error message returned because the specified parameters are invalid. Check whether the parameters conflict with each other.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

