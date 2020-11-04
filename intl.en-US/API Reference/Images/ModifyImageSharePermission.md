# ModifyImageSharePermission

You can call this operation to manage the share permission on a custom image. After you share a custom image to another Alibaba Cloud account, the account can use the shared image to create ECS instances \(RunInstances\) or replace system disks of ECS instances \(ReplaceSystemDisk\).

## Description

When you call this operation, take note of the following items:

-   You can share only your own custom images to other Alibaba Cloud accounts.
-   A custom image can be shared to a maximum of 10 Alibaba Cloud accounts at a time. You can specify up to 10 Alibaba Cloud account IDs in the AddAccount.N or RemoveAccount.N parameter. If you specify more than 10 account IDs, the parameter will be ignored.
-   A single custom image can be shared to a maximum of 50 Alibaba Cloud accounts. You can [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to share the image to more accounts.
-   If an instance was created \([RunInstances](~~63440~~)\) from a shared image, the instance cannot be re-initialized \([ReInitDisk](~~25519~~)\) after the image owner unshares or deletes the image \([DeleteImage](~~25537~~)\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=ModifyImageSharePermission&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyImageSharePermission|The operation that you want to perform. Set the value to ModifyImageSharePermission. |
|ImageId|String|Yes|m-bp18ygjuqnwhechc\*\*\*\*|The ID of the custom image. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the custom image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|AddAccount.N|RepeatList|No|1234567890|The ID of Alibaba Cloud account N to which to share the custom image. Valid values of N: 1 to 10. If the value of N is greater than 10, this parameter will be ignored. |
|RemoveAccount.N|RepeatList|No|1234567890|The ID of Alibaba Cloud account N to which to unshare the custom image. Valid values of N: 1 to 10. If the value of N is greater than 10, this parameter will be ignored. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=ModifyImageSharePermission
&ImageId=m-bp18ygjuqnwhechc****
&RegionId=cn-hangzhou
&AddAccount.1=1234567890
&RemoveAccount.1=1234567890
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyImageSharePermissionResponse>
      <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</ModifyImageSharePermissionResponse>
```

`JSON` format

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter|The input parameter "RegionId" that is mandatory for processing this request is not supplied.|The error message returned because the required RegionId parameter is not specified.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist in this account.|
|404|InvalidAccount.NotFound|The specified parameter "AddAccount.n" or "RemoveAccount.n" does not exist.|The error message returned because the specified AddAccount.N or RemoveAccount.N parameter does not exist.|
|404|InvalidAccount.Forbbiden|The specified Account does not yourself.|The error message returned because you are attempting to share the image to your own account.|
|403|QuotaExceed.ShareImage|The shared Image Quota exceeds.|The error message returned because the maximum number of custom images that can be shared has been reached.|
|403|QuotaExceed.ShareImageUser|The shared Image user Quota exceeds.|The error message returned because the maximum number of Alibaba Cloud accounts to which a single image can be shared has been reached.|
|400|InvalidGroup.Malformed|The specified Group is wrongly formed.|The error message returned because the specified group does not exist.|
|403|InvalidImageId.BidMismatch|Cannot share image with other bid user.|The error message returned because images cannot be shared among users of different carriers.|
|403|OperationDeined.EncryptedSnapshot|The image contains encrypted snapshots, which do not support share.|The error message returned because the specified image contains encrypted snapshots and cannot be shared.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

