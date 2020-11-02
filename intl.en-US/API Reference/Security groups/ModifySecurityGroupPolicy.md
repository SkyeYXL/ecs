# ModifySecurityGroupPolicy

You can call this operation to modify the internal access policy of a basic security group. The internal access policy of an advanced security group cannot be modified.

## Description

When you call this operation, take note of the following items:

-   When InnerAccessPolicy is set to Accept, instances within the security group can communicate with each other. In this case, the Accept policy has the highest priority of all rules, and all other user-defined rules are ignored.
-   When InnerAccessPolicy is set to Drop, instances within the security group are isolated from each other. In this case, user-defined security group rules have a higher priority and can be used to change the internal access policy. For example, you can call the [AuthorizeSecurityGroup](~~25554~~) operation to allow ECS instances in the security group to communicate with each other.
-   You can call the [DescribeSecurityGroupAttribute](~~25555~~) operation to query the internal access policy of the current security group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifySecurityGroupPolicy&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifySecurityGroupPolicy|The operation that you want to perform. Set the value to ModifySecurityGroupPolicy. |
|InnerAccessPolicy|String|Yes|Drop|The internal access policy of the security group. Valid values:

-   Accept: All instances in the security group can communicate with each other.
-   Drop: All instances in the security group are isolated from each other.

The values are case-insensitive. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the security group. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|SecurityGroupId|String|Yes|sg-bp67acfmxazb4ph\*\*\*\*|The ID of the security group. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value must contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifySecurityGroupPolicy
&RegionId=cn-hangzhou
&SecurityGroupId=sg-bp67acfmxazb4ph****
&InnerAccessPolicy=Drop
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifySecurityGroupPolicyResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</ModifySecurityGroupPolicyResponse>
```

`JSON` format

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidSecurityGroupId.Malformed|The SecurityGroupId is invalid. Only letters, numbers and underscores are supported. Maximum length is 100 characters.|The error message returned because the specified SecurityGroupId parameter is invalid. The security group ID can be up to 100 characters in length and can contain only letters, digits, and underscores \(\_\).|
|400|InvalidPolicy.Malformed|The Policy is invalid. Only 'Accept' and 'Drop' are supported. Ignore case.|The error message returned because the specified InnerAccessPolicy parameter is invalid. Valid values of this parameter are Accept and Drop, and these values are case-insensitive.|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

