# DeleteKeyPairs

You can call this operation to delete one or more SSH key pairs.

## Description

After an SSH key pair is deleted:

-   You cannot query the SSH key pair by calling the [DescribeKeyPairs](~~51773~~) operation.
-   If the SSH key pair was bound to one or more ECS instances:
    -   The key pair is no longer stored in Alibaba Cloud, but the instances can still use the key pair.
    -   When you call the [DescribeInstances](~~25506~~) operation to query information about an instance, the SSH key pair name \(KeyPairNames\) is still returned, but no other information is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DeleteKeyPairs&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Position|Type|Required|Example|Description|
|---------|--------|----|--------|-------|-----------|
|Action|Query|String|Yes|DeleteKeyPairs|The operation that you want to perform. Set the value to DeleteKeyPairs. |
|KeyPairNames|Query|String|Yes|\["skp-bp67acfmxazb41\*\*\*\*", "skp-bp67acfmxazb42\*\*\*\*", … "skp-bp67acfmxazb4p3\*\*\*"\]|The names of SSH key pairs. The value can be a JSON array that consists of up to 100 key pair names. Separate multiple key pair names with commas \(,\). |
|RegionId|Query|String|Yes|cn-hangzhou|The ID of the region. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DeleteKeyPairs
&RegionId=cn-hangzhou
&KeyPairNames=["skp-bp67acfmxazb41****", "skp-bp67acfmxazb42****", … "skp-bp67acfmxazb4p3***"]
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteKeyPairsResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteKeyPairsResponse>
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
|400|MissingParameter|The input parameter "KeyPairNames" that is mandatory for processing this request is not supplied.|The error message returned because the required KeyPairNames parameter is not specified.|
|400|InvalidKeyPairNames.ValueNotSupported|The specified parameter "KeyPairNames" is not valid.|The error message returned because the specified KeyPairNames parameter is invalid.|
|403|InstanceKeyPairLimitExceeded|Exceeding the allowed amount of instance which will be deleted.|The error message returned because the number of specified instances exceeds the upper limit.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

