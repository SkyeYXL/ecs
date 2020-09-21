# DescribeSecurityGroupReferences

You can call this operation to query whether a specified security group is authorized by other security groups.

## Description

When you call this operation, take note of the following items:

-   Security group authorization includes authorization for inbound and outbound traffic rules.
-   A maximum of 100 authorization entries can be returned each time.
-   When you fail to delete a security group \([DeleteSecurityGroup](~~25558~~)\), you can call the DescribeSecurityGroupReferences operation to query whether the specified security group is authorized by other security groups. If the security group is authorized by other security groups, you must revoke the authorization before the security group can be deleted.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeSecurityGroupReferences&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSecurityGroupReferences|The operation that you want to perform. Set the value to DescribeSecurityGroupReferences. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the security group. |
|SecurityGroupId.N|RepeatList|Yes|sg-bp14vtedjtobkvi\*\*\*\*|The ID of security group N to be queried. Valid values of N: 1 to 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|SecurityGroupReferences|Array| |An array consisting of SecurityGroupReference data. |
|SecurityGroupReference| | | |
|ReferencingSecurityGroups|Array| |An array consisting of ReferencingSecurityGroup data. |
|ReferencingSecurityGroup| | | |
|AliUid|String|1234567890|The ID of the Alibaba Cloud account to which the security group belongs. |
|SecurityGroupId|String|sg-bp67acfmxazb4j\*\*\*\*|The ID of the security group. |
|SecurityGroupId|String|sg-bp67acfmxazb4p\*\*\*\*|The ID of the queried security group. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroupReferences
&RegionId=cn-hangzhou
&SecurityGroupId.1=sg-bp14vtedjtobkvi****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSecurityGroupReferencesResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
      <SecurityGroupReferences>
          <SecurityGroupReference>
              <SecurityGroupId>sg-bp67acfmxazb4ph****</SecurityGroupId>
              <ReferencingSecurityGroups>
                  <ReferencingSecurityGroup>
                      <SecurityGroupId>sg-bp67acfmxazb4pi****</SecurityGroupId>
                      <AliUid>1234567890</AliUid>
                  </ReferencingSecurityGroup>
                  <ReferencingSecurityGroup>
                      <SecurityGroupId>sg-bp67acfmxazb4pj****</SecurityGroupId>
                      <AliUid>1234567890</AliUid>
                  </ReferencingSecurityGroup>
              </ReferencingSecurityGroups>
          </SecurityGroupReference>
      </SecurityGroupReferences>
</DescribeSecurityGroupReferencesResponse>
```

`JSON` format

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
    "SecurityGroupReferences": [
        {
            "SecurityGroupId": "sg-bp67acfmxazb4ph****",
            "SecurityReferencingGroups": [
                {
                    "AliUid": "1234567890",
                    "SecurityGroupId": "sg-bp67acfmxazb4pi****"
                },
                {
                    "AliUid": "1234567890",
                    "SecurityGroupId": "sg-bp67acfmxazb4pj****"
                }
            ]
        }
    ]
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidSecurityGroupId.Malformed|The specified parameter SecurityGroupId is essential and size should less than 10|The error message returned because the specified SecurityGroupId.N parameter must be specified and the value of N cannot exceed 10.|
|404|InvalidSecurityGroupId.NotFound|The SecurityGroupId provided does not exist in our records.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

