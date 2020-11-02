# DetachKeyPair

You can call this operation to unbind an SSH key pair from one or more Linux instances.

## Description

When you call this operation, take note of the following items:

-   After you unbind an SSH key pair from an instance, you must call the [RebootInstance](~~25502~~) operation to restart the instance for the unbind operation to take effect.
-   By default, the username and password authentication is used for an instance after you unbind an SSH key pair from the instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DetachKeyPair&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DetachKeyPair|The operation that you want to perform. Set the value to DetachKeyPair. |
|InstanceIds|String|Yes|\["i-bp1d6tsvznfghy7y\*\*\*\*", "i-bp1ippxbaql9zet7\*\*\*\*", … "i-bp1ib7bcz07l\*\*\*\*"\]|The IDs of instances from which you want to detach the SSH key pair. The value can be a JSON array that consists of up to 50 instance IDs. Separate multiple instance IDs with commas \(,\). |
|KeyPairName|String|Yes|testKeyPairName|The name of the SSH key pair. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SSH key pair. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|FailCount|String|0|The number of instances from which the SSH key pair failed to be unbound. |
|KeyPairName|String|testKeyPairName|The name of the SSH key pair. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|Results|Array of Result| |The result set of the unbind operation. |
|Result| | | |
|Code|String|200|The operation status code returned. 200 indicates that the operation is successful. |
|InstanceId|String|i-bp1d6tsvznfghy7y\*\*\*\*|The ID of the instance. |
|Message|String|successful|The operation information returned. When the value of Code is 200, the value of Message is successful. |
|Success|String|true|Indicates whether the operation was successful. |
|TotalCount|String|2|The total number of instances from which you attempted to unbind the SSH key pair. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DetachKeyPair
&RegionId=cn-qingdao
&InstanceIds=["i-bp1d6tsvznfghy7y****", "i-bp1ippxbaql9zet7****", … "i-bp1ib7bcz07l****"]
&KeyPairName=testKeyPairName
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DetachKeyPairResponse>
      <TotalCount>2</TotalCount>
      <RequestId>834B3E6B-2D1D-482F-81A4-810C327D4735</RequestId>
      <Results>
            <Result>
                  <Message>successful</Message>
                  <InstanceId>i-m5eg7be9ndloji64****</InstanceId>
                  <Success>true</Success>
                  <Code>200</Code>
            </Result>
            <Result>
                  <Message>successful</Message>
                  <InstanceId>i-m5e25x2mwr0hk33d****</InstanceId>
                  <Success>true</Success>
                  <Code>200</Code>
            </Result>
      </Results>
      <FailCount>0</FailCount>
</DetachKeyPairResponse>
```

`JSON` format

```
{
    "TotalCount": 2,
    "RequestId": "834B3E6B-2D1D-482F-81A4-810C327D4735",
    "Results": {
        "Result": [
            {
                "Message": "successful",
                "InstanceId": "i-m5eg7be9ndloji64****",
                "Success": true,
                "Code": "200"
            },
            {
                "Message": "successful",
                "InstanceId": "i-m5e25x2mwr0hk33d****",
                "Success": true,
                "Code": "200"
            }
        ]
    },
    "FailCount": 0
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidKeyPairName.NotFound|The specified KeyPairName does not exist in our records.|The error message returned because the specified KeyPairName parameter does not exist.|
|403|DependencyViolation.WindowsInstance|The instance creating is windows, cannot use ssh key pair to login|The error message returned because the specified instance is a Windows instance and does not support logons with SSH key pairs.|
|400|InvalidInstanceIds.ValueNotSupported|The specified parameter InstanceIds is not valid.|The error message returned because the specified InstanceIds parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

