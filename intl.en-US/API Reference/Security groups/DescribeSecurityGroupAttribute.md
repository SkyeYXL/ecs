# DescribeSecurityGroupAttribute

You can call this operation to query the rules of a security group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSecurityGroupAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSecurityGroupAttribute|The operation that you want to perform. Set the value to DescribeSecurityGroupAttribute. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the security group. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|SecurityGroupId|String|Yes|sg-bp1gxw6bznjjvhu3\*\*\*\*|The ID of the security group. |
|NicType|String|No|intranet|The NIC type of the security group rule.

-   Default value: internet. Valid values when the security group is in the classic network:
    -   internet
    -   intranet

**Note:** By default, the parameter is set to internet. For a single call, you can query only security group rules of one NIC type. If you want to query all security group rules, call the operation twice.

-   When the security group is in a VPC, set the value to intranet. This is also the default value.

**Note:** If you set this parameter to internet or leave this parameter empty, the intranet value is automatically used. |
|Direction|String|No|all|The direction in which the security group rule is applied. Valid values:

-   egress: outbound
-   ingress: inbound
-   all: outbound and inbound

Default value: all. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Description|String|testDescription1|The description of the security group. |
|InnerAccessPolicy|String|Accept|The access control policy within the security group. Valid values:

-   Accept: All instances in the security group can communicate with each other.
-   drop: All instances within the security group are isolated from each other. |
|Permissions|Array of Permission| |Details about the security group rules. |
|Permission| | | |
|CreateTime|String|2018-12-12T07:28:38Z|The time when the security group rule was created. The time is displayed in UTC. |
|Description|String|testDescription2|The description of the security group. |
|DestCidrIp|String|0.0.0.0/0|The destination CIDR block for outbound access control. |
|DestGroupId|String|sg-bp1czdx84jd88i7v\*\*\*\*|The ID of the destination security group for outbound access control. |
|DestGroupName|String|testDestGroupName|The name of the destination security group. |
|DestGroupOwnerAccount|String|1234567890|The Alibaba Cloud account that manages the destination security group. |
|Direction|String|ingress|The direction in which the security group rule is applied. |
|IpProtocol|String|TCP|The transport layer protocol. |
|Ipv6DestCidrIp|String|2001:db8:1233:1a00::\*\*\*|The destination IPv6 CIDR block. |
|Ipv6SourceCidrIp|String|2001:db8:1234:1a00::\*\*\*|The source IPv6 CIDR block. |
|NicType|String|intranet|The NIC type of the security group rule. |
|Policy|String|Accept|The authorization policy. |
|PortRange|String|80/80|The port range. |
|Priority|String|1|The rule priority. |
|SourceCidrIp|String|0.0.0.0/0|The source CIDR block for inbound access control. |
|SourceGroupId|String|sg-bp12kc4rqohaf2js\*\*\*\*|The ID of the source security group for inbound access control. |
|SourceGroupName|String|testSourceGroupName1|The name of the source security group. |
|SourceGroupOwnerAccount|String|1234567890|The Alibaba Cloud account that manages the source security group. |
|SourcePortRange|String|80/80|The source port range. |
|RegionId|String|cn-hangzhou|The region ID of the security group. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|SecurityGroupId|String|sg-bp1gxw6bznjjvhu3\*\*\*\*|The ID of the destination security group. |
|SecurityGroupName|String|testSecurityGroupName2|The name of the security group. |
|VpcId|String|vpc-bp1opxu1zkhn00gzv\*\*\*\*|The ID of the VPC. If a VPC ID is returned, the network type of the security group is VPC. Otherwise, the network type of the security group is classic network. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?RegionId=cn-hangzhou
&SecurityGroupId=sg-bp1gxw6bznjjvhu3****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSecurityGroupAttributeResponse>
      <SecurityGroupId>sg-bp1gxw6bznjjvhu3****</SecurityGroupId>
      <InnerAccessPolicy>Accept</InnerAccessPolicy>
      <SecurityGroupName>FinanceJoshua</SecurityGroupName>
      <Description>testDescription1</Description>
      <RegionId>cn-hangzhou</RegionId>
      <RequestId>A72322C1-47C0-491E-8088-8B17E4EA859F</RequestId>
      <Permissions>
            <Permission>
                  <SourceCidrIp>10.0.0.0/8</SourceCidrIp>
                  <Description></Description>
                  <DestCidrIp></DestCidrIp>
                  <NicType>intranet</NicType>
                  <DestGroupName></DestGroupName>
                  <PortRange>22/22</PortRange>
                  <DestGroupId></DestGroupId>
                  <Ipv6DestCidrIp></Ipv6DestCidrIp>
                  <Direction>ingress</Direction>
                  <Priority>1</Priority>
                  <IpProtocol>TCP</IpProtocol>
                  <SourcePortRange></SourcePortRange>
                  <SourceGroupOwnerAccount></SourceGroupOwnerAccount>
                  <Policy>Accept</Policy>
                  <CreateTime>2018-12-12T07:28:38Z</CreateTime>
                  <SourceGroupId></SourceGroupId>
                  <DestGroupOwnerAccount></DestGroupOwnerAccount>
                  <Ipv6SourceCidrIp></Ipv6SourceCidrIp>
                  <SourceGroupName></SourceGroupName>
            </Permission>
            <Permission>
                  <SourceCidrIp>0.0.0.0/0</SourceCidrIp>
                  <Description></Description>
                  <DestCidrIp></DestCidrIp>
                  <NicType>intranet</NicType>
                  <DestGroupName></DestGroupName>
                  <PortRange>443/443</PortRange>
                  <DestGroupId></DestGroupId>
                  <Ipv6DestCidrIp></Ipv6DestCidrIp>
                  <Direction>ingress</Direction>
                  <Priority>1</Priority>
                  <IpProtocol>TCP</IpProtocol>
                  <SourcePortRange></SourcePortRange>
                  <SourceGroupOwnerAccount></SourceGroupOwnerAccount>
                  <Policy>Accept</Policy>
                  <CreateTime>2018-12-12T07:28:38Z</CreateTime>
                  <SourceGroupId></SourceGroupId>
                  <DestGroupOwnerAccount></DestGroupOwnerAccount>
                  <Ipv6SourceCidrIp></Ipv6SourceCidrIp>
                  <SourceGroupName></SourceGroupName>
            </Permission>
            <Permission>
                  <SourceCidrIp>0.0.0.0/0</SourceCidrIp>
                  <Description></Description>
                  <DestCidrIp></DestCidrIp>
                  <NicType>intranet</NicType>
                  <DestGroupName></DestGroupName>
                  <PortRange>80/80</PortRange>
                  <DestGroupId></DestGroupId>
                  <Ipv6DestCidrIp></Ipv6DestCidrIp>
                  <Direction>ingress</Direction>
                  <Priority>1</Priority>
                  <IpProtocol>TCP</IpProtocol>
                  <SourcePortRange></SourcePortRange>
                  <SourceGroupOwnerAccount></SourceGroupOwnerAccount>
                  <Policy>Accept</Policy>
                  <CreateTime>2018-12-12T07:28:38Z</CreateTime>
                  <SourceGroupId></SourceGroupId>
                  <DestGroupOwnerAccount></DestGroupOwnerAccount>
                  <Ipv6SourceCidrIp></Ipv6SourceCidrIp>
                  <SourceGroupName></SourceGroupName>
            </Permission>
            <Permission>
                  <SourceCidrIp>10.0.0.0/8</SourceCidrIp>
                  <Description></Description>
                  <DestCidrIp></DestCidrIp>
                  <NicType>intranet</NicType>
                  <DestGroupName></DestGroupName>
                  <PortRange>-1/-1</PortRange>
                  <DestGroupId></DestGroupId>
                  <Ipv6DestCidrIp></Ipv6DestCidrIp>
                  <Direction>ingress</Direction>
                  <Priority>1</Priority>
                  <IpProtocol>ICMP</IpProtocol>
                  <SourcePortRange>-1/-1</SourcePortRange>
                  <SourceGroupOwnerAccount></SourceGroupOwnerAccount>
                  <Policy>Accept</Policy>
                  <CreateTime>2018-12-12T07:28:38Z</CreateTime>
                  <SourceGroupId></SourceGroupId>
                  <DestGroupOwnerAccount></DestGroupOwnerAccount>
                  <Ipv6SourceCidrIp></Ipv6SourceCidrIp>
                  <SourceGroupName></SourceGroupName>
            </Permission>
      </Permissions>
      <VpcId>vpc-bp1opxu1zkhn00gzv****</VpcId>
</DescribeSecurityGroupAttributeResponse>
```

`JSON` format

```
{
    "SecurityGroupId": "sg-bp1gxw6bznjjvhu3****",
    "InnerAccessPolicy": "Accept",
    "SecurityGroupName": "FinanceJoshua",
    "Description": "testDescription1",
    "RegionId": "cn-hangzhou",
    "RequestId": "A72322C1-47C0-491E-8088-8B17E4EA859F",
    "Permissions": {
        "Permission": [
            {
                "SourceCidrIp": "10.0.0.0/8",
                "Description": "",
                "DestCidrIp": "",
                "NicType": "intranet",
                "DestGroupName": "",
                "PortRange": "22/22",
                "DestGroupId": "",
                "Ipv6DestCidrIp": "",
                "Direction": "ingress",
                "Priority": 1,
                "IpProtocol": "TCP",
                "SourcePortRange": "",
                "SourceGroupOwnerAccount": "",
                "Policy": "Accept",
                "CreateTime": "2018-12-12T07:28:38Z",
                "SourceGroupId": "",
                "DestGroupOwnerAccount": "",
                "Ipv6SourceCidrIp": "",
                "SourceGroupName": ""
            },
            {
                "SourceCidrIp": "0.0.0.0/0",
                "Description": "",
                "DestCidrIp": "",
                "NicType": "intranet",
                "DestGroupName": "",
                "PortRange": "443/443",
                "DestGroupId": "",
                "Ipv6DestCidrIp": "",
                "Direction": "ingress",
                "Priority": 1,
                "IpProtocol": "TCP",
                "SourcePortRange": "",
                "SourceGroupOwnerAccount": "",
                "Policy": "Accept",
                "CreateTime": "2018-12-12T07:28:38Z",
                "SourceGroupId": "",
                "DestGroupOwnerAccount": "",
                "Ipv6SourceCidrIp": "",
                "SourceGroupName": ""
            },
            {
                "SourceCidrIp": "0.0.0.0/0",
                "Description": "",
                "DestCidrIp": "",
                "NicType": "intranet",
                "DestGroupName": "",
                "PortRange": "80/80",
                "DestGroupId": "",
                "Ipv6DestCidrIp": "",
                "Direction": "ingress",
                "Priority": 1,
                "IpProtocol": "TCP",
                "SourcePortRange": "",
                "SourceGroupOwnerAccount": "",
                "Policy": "Accept",
                "CreateTime": "2018-12-12T07:28:38Z",
                "SourceGroupId": "",
                "DestGroupOwnerAccount": "",
                "Ipv6SourceCidrIp": "",
                "SourceGroupName": ""
            },
            {
                "SourceCidrIp": "10.0.0.0/8",
                "Description": "",
                "DestCidrIp": "",
                "NicType": "intranet",
                "DestGroupName": "",
                "PortRange": "-1/-1",
                "DestGroupId": "",
                "Ipv6DestCidrIp": "",
                "Direction": "ingress",
                "Priority": 1,
                "IpProtocol": "ICMP",
                "SourcePortRange": "-1/-1",
                "SourceGroupOwnerAccount": "",
                "Policy": "Accept",
                "CreateTime": "2018-12-12T07:28:38Z",
                "SourceGroupId": "",
                "DestGroupOwnerAccount": "",
                "Ipv6SourceCidrIp": "",
                "SourceGroupName": ""
            }
        ]
    },
    "VpcId": "vpc-bp1opxu1zkhn00gzv****"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned because the specified RegionId parameter does not exist.|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is correct.|
|400|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|The error message returned because the specified NicType parameter does not exist. Check whether the NIC type is correct.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|InvalidParamter|Invalid Parameter|The error message returned because a specified parameter is invalid.|
|400|InvalidSecurityGroupId.Malformed|The specified parameter "SecurityGroupId" is not valid.|The error message returned because the specified SecurityGroupId parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

