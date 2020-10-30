# DescribeSecurityGroups

You can call this operation to query basic information of security groups.

## Description

Basic information of security groups includes their IDs and descriptions. Security groups are displayed in descending order of their IDs.

When you call an API operation by using Alibaba Cloud CLI, you must specify request parameter values of different data types in required formats. For more information, see [Parameter format overview](~~110340~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSecurityGroups&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSecurityGroups|The operation that you want to perform. Set the value to DescribeSecurityGroups. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the security group. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|VpcId|String|No|vpc-bp67acfmxazb4p\*\*\*\*|The ID of the VPC to which the security group belongs. |
|PageNumber|Integer|No|1|The number of the page to return.

Pages start from page 1.

Default: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page.

Valid values: 1 to 50.

Default value: 10 |
|SecurityGroupIds|String|No|\["sg-bp67acfmxazb4p\*\*\*\*", "sg-bp67acfmxazb4p\*\*\*\*", "sg-bp67acfmxazb4p\*\*\*\*",....\]|The IDs of security groups. The value is a JSON array that consists of up to 100 security group IDs. Separate multiple security group IDs with commas \(,\). |
|Tag.N.value|String|No|testvalue|The value of tag N of the security group.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Value parameter to ensure future compatibility. |
|Tag.N.key|String|No|testkey|The key of tag N of the security group.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Key parameter to ensure future compatibility. |
|Tag.N.Key|String|No|TestKey|The key of tag N of the security group. Valid values of N: 1 to 20.

If a single tag is specified to query resources, up to 1,000 resources that are bound with this tag can be displayed in the response. If multiple tags are specified to query resources, up to 1,000 resources that are bound with all these tags can be displayed in the response. To query more than 1,000 resources that are bound with specified tags, call the [ListTagResources](~~110425~~) operation. |
|Tag.N.Value|String|No|TestValue|The value of tag N of the security group. Valid values of N: 1 to 20. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the security group belongs. When this parameter is specified to query resources, up to 1,000 resources that belong to the specified resource group can be displayed in the response. |
|NetworkType|String|No|vpc|The network type of the security group. Valid values:

-   vpc
-   classic |
|SecurityGroupId|String|No|sg-bp67acfmxazb4p\*\*\*\*|The ID of the security group. |
|SecurityGroupName|String|No|SGTestName|The name of the security group. |
|SecurityGroupType|String|No|normal|The type of the security group. Valid values:

-   normal: basic security group
-   enterprise: advanced security group

**Note:** If you do not specify this parameter, both basic and advanced security groups are queried. |
|DryRun|Boolean|No|false|Specifies whether to check the validity of the request without actually making the request. Valid values:

-   true: The validity of the request is checked but the request is not made. Check items include whether your AccessKey pair is valid, whether RAM users are authorized, and whether the required parameters are set. If the check fails, the corresponding error message is returned. If the check succeeds, the DryRunOperation error code is returned.
-   false: The validity of the request is checked. If the check succeeds, a 2XX HTTP status code is returned and the request is made.

Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|1|The number of entries returned per page. |
|RegionId|String|cn-hangzhou|The region ID of the security group. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|SecurityGroups|Array of SecurityGroup| |Details about the security groups. |
|SecurityGroup| | | |
|AvailableInstanceAmount|Integer|0| |
|CreationTime|String|2017-12-05T22:40:00Z|The time when the security group was created. [The time follows the ISO 8601](~~25696~~) standard in the yyyy-MM-ddThh:mmZ format. The time is displayed in UTC. |
|Description|String|TestDescription|The description of the security group. |
|EcsCount|Integer|0| |
|ResourceGroupId|String|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the security group belongs. |
|SecurityGroupId|String|sg-bp67acfmxazb4p\*\*\*\*|The ID of the security group. |
|SecurityGroupName|String|SGTestName|The name of the security group. |
|SecurityGroupType|String|normal|The type of the security group. Valid values:

-   normal: basic security group
-   enterprise: advanced security group |
|ServiceID|Long|12345678910|The ID of the distributor to which the security group belongs. |
|ServiceManaged|Boolean|true|Indicates whether the user is an Alibaba Cloud service or a distributor. |
|Tags|Array of Tag| |The tags of the security groups. |
|Tag| | | |
|TagKey|String|TestKey|The tag key of the security group. |
|TagValue|String|TestValue|The tag value of the security group. |
|VpcId|String|vpc-bp67acfmxazb4p\*\*\*\*|The ID of the VPC to which the security group belongs. |
|TotalCount|Integer|49|The total number of security groups. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroups
&RegionId=cn-hangzhou
&PageSize=1
&PageNumber=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSecurityGroupsResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>49</TotalCount>
      <PageSize>1</PageSize>
      <RegionId>cn-hangzhou</RegionId>
      <RequestId>A1707FC0-430C-423A-B624-284046B20399</RequestId>
      <SecurityGroups>
            <SecurityGroup>
                  <CreationTime>2019-11-01T06:08:46Z</CreationTime>
                  <SecurityGroupId>sg-bp67acfmxazb4p****</SecurityGroupId>
                  <Description></Description>
                  <SecurityGroupName>SGTestName</SecurityGroupName>
                  <ResourceGroupId></ResourceGroupId>
                  <SecurityGroupType>normal</SecurityGroupType>
                  <VpcId>vpc-bp67acfmxazb4p****</VpcId>
            </SecurityGroup>
      </SecurityGroups>
</DescribeSecurityGroupsResponse>
```

`JSON` format

```
{
    "PageNumber": 1,
    "TotalCount": 49,
    "PageSize": 1,
    "RegionId": "cn-hangzhou",
    "RequestId": "A1707FC0-430C-423A-B624-284046B20399",
    "SecurityGroups": {
        "SecurityGroup": [
            {
                "CreationTime": "2019-11-01T06:08:46Z",
                "Tags": {
                    "Tag": []
                },
                "SecurityGroupId": "sg-bp67acfmxazb4p****",
                "Description": "",
                "SecurityGroupName": "SGTestName",
                "ResourceGroupId": "",
                "SecurityGroupType": "normal",
                "VpcId": "vpc-bp67acfmxazb4p****"
            }
        ]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

