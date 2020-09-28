# ModifyDiskAttribute

You can call this operation to modify the attributes of one or more Elastic Block Storage devices, including their names, descriptions, and whether they are released along with their attached instances.

## Description

-   If you set DeleteWithInstance to false and the instance to which the disk is attached is locked for security reasons \(the OperationLocks parameter is set to `"LockReason": "security"`\), the DeleteWithInstance parameter will be ignored and the disk will be released with the instance.
-   You can call the `DiskIds.N` operation to modify the attributes of multiple Elastic Block Storage devices at a time, including their names, descriptions, and whether they are released along with their attached instances.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyDiskAttribute&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyDiskAttribute|The operation that you want to perform. Set the value to ModifyDiskAttribute. |
|DiskId|String|No|d-bp1famypsnar20bv\*\*\*\*|The ID of the disk to be modified.

**Note:** You can specify `DiskId` or `DiskIds.N` but you cannot specify both of them. |
|DiskIds.N|RepeatList|No|d-bp1famypsnar20bv\*\*\*\*|The IDs of disk N to be modified. Valid values of N: 0 to 100.

**Note:** You can specify `DiskId` or `DiskIds.N` but you cannot specify both of them. |
|DiskName|String|No|MyDiskName|The name of the disk. The name must be 2 to 128 characters in length, and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://. |
|Description|String|No|TestDescription|The description of the disk. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DeleteWithInstance|Boolean|No|false|Specifies whether the disk is released with the instance. This parameter is empty by default, which indicates that the current value remains unchanged.

An error will be returned if you set this parameter to false in the following cases:

-   When Category is set to ephemeral.
-   When Category is set to cloud and Portable is set to false. |
|DeleteAutoSnapshot|Boolean|No|false|Specifies whether automatic snapshots are deleted when the disk is released. This parameter is empty by default, which indicates that the current value remains unchanged. |
|EnableAutoSnapshot|Boolean|No|true|Specifies whether to apply an existing automatic snapshot policy to the disk. This parameter is empty by default, which indicates that the current value remains unchanged. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyDiskAttribute
&DiskId=d-bp1famypsnar20bv****
&DiskName=MyDiskName
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyDiskAttributeResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyDiskAttributeResponse>
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
|404|InvalidDiskId.NotFound|The specified disk does not exist.|The error message returned because the specified disk ID does not exist. Check whether the disk ID is correct.|
|400|InvalidDiskName.Malformed|The specified disk name is wrongly formed.|The error message returned because the specified DiskName parameter is invalid. The name must be 2 to 128 characters in length and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.|
|404|InvalidDescription.Malformed|The specified description is wrongly formed.|The error message returned because the specified description is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|NoAttributeToModify|No attribute to be modified in this request.|The error message returned because no attributes of the specified snapshot are modified.|
|403|QuotaExceed.Snapshot|The snapshot quota exceeds.|The error message returned because the maximum number of snapshots has been reached. To create new snapshots, delete unnecessary snapshots without affecting your business.|
|403|DiskNotPortable|The specified disk is not a portable disk.|The error message returned because the specified disk is not removable.|
|403|IncorrectDiskStatus|The operation is not supported in this status.|The error message returned because the operation is not supported while the disk is in the current state. Make sure that the disk is available and you have no overdue payment for it.|
|400|IncompleteParamter|Some fields can not be null in this request.|The error message returned because the required parameters are not specified.|
|403|UserNotInTheWhiteList|The user is not in disk white list.|The error message returned because you are not in the whitelist to manage the disk. Try again when you are in the whitelist.|
|400|InvalidRegionId.MalFormed|The specified RegionId is not valid|The error message returned because the specified RegionId parameter is invalid.|
|404|InvalidInstanceId.NotFound|Specified attached instance does not exist.|The error message returned because the specified InstanceId parameter does not exist. Check whether the instance ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

