# CreateImage

You can call this operation to create a custom image. The created custom image can be used to create ECS instances \(RunInstances\) and replace system disks \(ReplaceSystemDisk\).

## Description

When you call this operation, take note of the following items:

-   The created custom image can be used only when it is in the Available \(Available\) state.
-   If the response message contains `{"OperationLocks": {"LockReason" : "security"}}` when you query information of an instance, the instance is locked for security reasons and all operations are prohibited on it.

You can call the CreateImage operation to create a custom image by using one of the following methods. The following request parameters are sorted by priority: `InstanceId` \> `DiskDeviceMapping` \> `SnapshotId`. If your request contains two or more parameters, the custom image is created based on the parameter with a higher priority by default.

-   **Method 1**: Create a custom image from an instance. You only need to specify the instance ID \(`InstanceId`\). The instance must be in the Running \(`Running`\) or Stopped \(`Stopped`\) state. After the CreateImage operation is called, a new snapshot is created for each disk of the instance.
-   **Method 2**: Create a custom image from the system disk snapshot of an instance. You only need to specify the ID of the system disk snapshot \(`SnapshotId`\). The specified snapshot cannot be created on or before July 15, 2013.
-   **Method 3**: Create a custom image from multiple disk snapshots. You must specify the data mapping between the disks corresponding to the snapshots \(`DiskDeviceMapping`\).

When you use Method 3 to create a custom image, take note of the following items:

-   You can specify only one system disk snapshot. The device name of the system disk must be /dev/xvda.
-   You can specify multiple data disk snapshots. The device names of the data disks are unique and ascend from /dev/xvdb to /dev/xvdz.
-   `SnapshotId` may not be specified. In this case, an empty data disk with a specific size is created.
-   The specified snapshot cannot be created on or before July 15, 2013.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CreateImage&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateImage|The operation that you want to perform. Set the value to CreateImage. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region in which to create the custom image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|DiskDeviceMapping.N.SnapshotId|String|No|s-bp17441ohwkdca0\*\*\*\*|The ID of snapshot N that is used to create disk N specified by DiskDeviceMapping.N.Size in the custom image. |
|DiskDeviceMapping.N.Size|Integer|No|2000|The size of disk N in the custom image. Unit: GiB. The valid values and default value of DiskDeviceMapping.N.Size depend on DiskDeviceMapping.N.SnapshotId.

-   If no corresponding snapshot IDs are specified in the DiskDeviceMapping.N.SnapshotId value, the following valid values and default value are available for DiskDeviceMapping.N.Size:
    -   For basic disks, the valid values are 5 to 2000, and the default value is 5.
    -   For other disk categories, the valid values are 20 to 32768, and the default value is 20.
-   If a corresponding snapshot ID is specified in the DiskDeviceMapping.N.SnapshotId value, the value of DiskDeviceMapping.N.Size must be greater than or equal to the size of the specified snapshot. The default value of DiskDeviceMapping.N.Size is the size of the specified snapshot. |
|DiskDeviceMapping.N.Device|String|No|/dev/vdb|The device name of disk N in the custom image. Valid values:

-   For disk categories other than basic disks, such as standard SSDs, ultra disks, and enhanced SSDs: /dev/vda to /dev/vdz
-   For basic disks: /dev/xvda to /dev/xvdz |
|DiskDeviceMapping.N.DiskType|String|No|system|The type of disk N in the custom image. You can set this parameter to create the system disk of the custom image from a data disk snapshot. If you do not set this parameter, the disk type is determined by the corresponding snapshot. Valid values:

-   system: system disk
-   data: data disk |
|SnapshotId|String|No|s-bp17441ohwkdca0\*\*\*\*|The ID of the snapshot that is used to create the custom image. |
|InstanceId|String|No|i-bp1g6zv0ce8oghu7\*\*\*\*|The ID of the instance. |
|ImageName|String|No|TestCentOS|The name of the image. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

This parameter is empty by default. |
|Description|String|No|ImageTestDescription|The description of the image. The description must be 2 to 256 characters in length and cannot start with http:// or https://.

This parameter is empty by default. |
|Platform|String|No|CentOS|The distribution of the operating system for the system disk in the custom image. If you specify a data disk snapshot to create the system disk of the custom image, you must use the Platform parameter to determine the distribution of the operating system for the system disk. Default value: Others Linux. Valid values:

-   CentOS
-   Ubuntu
-   SUSE
-   OpenSUSE
-   RedHat
-   Debian
-   CoreOS
-   Aliyun
-   Windows Server 2012
-   Windows 7
-   Customized Linux
-   Others Linux |
|Architecture|String|No|x86\_64|The system architecture of the system disk. If you specify a data disk snapshot to create the system disk of the custom image, you must use the Architecture parameter to determine the system architecture of the system disk. Default value: x86\_64. Valid values:

-   i386
-   x86\_64 |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** value can only contain ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|Tag.N.value|String|No|null|The value of tag N of the custom image.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Value parameter to ensure future compatibility. |
|Tag.N.key|String|No|null|The key of tag N of the custom image.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Key parameter to ensure future compatibility. |
|Tag.N.Key|String|No|KeyTest|The key of tag N of the custom image. Valid values of N: 1 to 20. The tag key cannot be an empty string. It can be up to 128 characters in length and cannot contain http:// or https://. It cannot start with acs: or aliyun. |
|Tag.N.Value|String|No|ValueTest|The value of tag N of the custom image. Valid values of N: 1 to 20. The tag value can be an empty string. It can be up to 128 characters in length. It cannot start with acs: or contain http:// or https://. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which to assign the custom image. |
|ImageFamily|String|No|hangzhou-daily-update|The name of the image family of the custom image. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It cannot contain http:// or https://. It must start with a letter and cannot start with acs: or aliyun.

This parameter is empty by default. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ImageId|String|m-bp146shijn7hujku\*\*\*\*|The ID of the image. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=CreateImage
&RegionId=cn-hangzhou
&DiskDeviceMapping.1.Size=2000
&DiskDeviceMapping.1.SnapshotId=s-bp17441ohwkdca0****
&DiskDeviceMapping.1.DiskType=system
&SnapshotId=s-bp17441ohwkdca0****
&InstanceId=i-bp1g6zv0ce8oghu7****
&ImageName=TestCentOS
&ImageVersion=2017011017
&Description=ImageTestDescription
&Platform=CentOS
&Architecture=x86_64
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&Tag.1.Key=KeyTest
&Tag.1.Value=ValueTest
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateImageResponse>
      <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
      <ImageId>m-bp146shijn7hujku****</ImageId>
</CreateImageResponse>
```

`JSON` format

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9",
    "ImageId": "m-bp146shijn7hujku****"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidSnapshotId.NotFound|The specified SnapshotId does not exist.|The error message returned because the specified SnapshotId parameter does not exist. Check whether the snapshot ID is correct.|
|400|InvalidImageName.Malformed|The specified Image name is wrongly formed.|The error message returned because the specified ImageName parameter is invalid. The name must be 2 to 128 characters in length and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.|
|400|InvalidImageName.Duplicated|The specified Image name has already bean used.|The error message returned because the specified image name already exists.|
|400|InvalidDescription.Malformed|The specified description is wrongly formed.|The error message returned because the specified Description parameter is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|InvalidImageVersion.Malformed|The specified ImageVersion is wrongly formed.|The error message returned because the specified image version is invalid or you are not authorized to use the snapshot.|
|403|InvalidSnapshotId.NotReady|The current status of the DiskDeviceMapping.n.SnapshotId or SnapshotId does not support this operation.|The error message returned because the operation is not supported while the specified snapshot is in the current state.|
|403|InvalidSnapshot.TooOld|This operation is denied because the specified snapshot by DiskDeviceMapping.n.SnapshotId or SnapshotId is created before 2013-07-15.|The error message returned because the operation is not supported while the snapshot specified by the DiskDeviceMapping.N.SnapshotId or SnapshotId parameter was created before July 15, 2013.|
|403|OperationDenied|The specified snapshot is not allowed to create image.|The error message returned because the specified snapshot cannot be used to create images.|
|403|QuotaExceed.Image|The Image Quota exceeds.|The error message returned because the maximum number of custom images has been reached.|
|403|OperationDenied|The specified snapshot is not from system disk.|The error message returned because the specified snapshot was not created from a system disk.|
|403|InvalidParamter.Conflict|The specified same token is trying to make requests with different parameters.|The error message returned because the same token is used to make requests that have different parameters.|
|404|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|The error message returned because the specified InstanceId parameter does not exist.|
|400|IncorrectInstanceStatus|The current status of the instance does not support this operation.|The error message returned because the operation is not supported while the instance is in the current state.|
|400|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|The error message returned because the operation is not supported while the instance is locked for security reasons.|
|400|InvalidDevice.Malformed|The specified parameter DiskDeviceMapping.n.Device is not valid.|The error message returned because the specified DiskDeviceMapping.N.Device parameter is invalid.|
|400|MissingParameter|The input parameter SnapshotId or InstanceId or DiskDeviceMapping that is mandatory for processing this request is not supplied.|The error message returned because none of SnapshotId, InstanceId, and parameters that start with DiskDeviceMapping is specified.|
|400|InvalidSize.ValueNotSupported|The specified parameter DiskDeviceMapping.n.Size beyond the permitted range.|The error message returned because the specified DiskDeviceMapping.N.Size parameter is not within the permitted range.|
|400|InvalidDevice.InUse|The specified parameter DiskDeviceMapping.n.Device has been occupied.|The error message returned because device names specified in the DiskDeviceMapping.N.Device value already exist.|
|400|OperationDenied|The specified parameter DiskDeviceMapping.n.SnapshotId does not contain system disk snapshot.|The error message returned because the specified DiskDeviceMapping.N.SnapshotID parameter does not contain a system disk snapshot ID.|
|400|OperationDenied|The specified parameter DiskDeviceMapping.n.SnapshotId contains two or more system disk snapshots.|The error message returned because the specified DiskDeviceMapping.N.SnapshotID parameter already contains a system disk snapshot ID.|
|400|InvalidDiskCategory.CreateImage|The specified diskCategory is not allowed to create image.|The error message returned because the operation is not supported by the specified disk category.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account balance is insufficient. Add funds to your account and try again.|
|403|InvalidAccountStatus.SnapshotServiceUnavailable|Snapshot service has not been opened yet.|The error message returned because the operation is not supported while the snapshot service is not activated.|
|403|UserNotInTheWhiteList|The user is not in the white list of create image by data disk snapshot.|The error message returned because you are not authorized to create an image from data disk snapshots. Try again when you are authorized to do so.|
|400|InvalidArchitecture.Malformed|The specified Architecture is wrongly formed.|The error message returned because the specified Architecture parameter is invalid.|
|400|InvalidPlatform.Malformed|The specified Platform is wrongly formed.|The error message returned because the specified Platform parameter is invalid.|
|400|OperationDenied|Not support creating system image from an encrypted snapshot/disk.|The error message returned because an encrypted disk or snapshot cannot be used to create custom images.|
|400|InvalidParameter.AllEmpty|%s|The error message returned because no parameters are specified. Specify required parameters.|
|403|IncorrectDiskStatus.Invalid|Device status is invalid, please restart instance and try again.|The error message returned because the device status is invalid. Restart the instance and try again.|
|403|OperationDenied.InvalidSnapshotCategory|%s|The error message returned because the operation is not supported by the snapshot type.|
|403|QuotaExceed.Snapshot|The snapshot quota exceeds.|The error message returned because the maximum number of snapshots has been reached. To store new snapshots, delete snapshots that are no longer needed.|
|403|IncorrectDiskStatus.Transferring|The specified device is transferring, you can retry after the process is finished.|The error message returned because the specified disk is being migrated. Wait until the disk is migrated and try again.|
|403|IncorrectDiskStatus|The current disk status does not support this operation.|The error message returned because the operation is not supported while the disk is in the current state. Make sure that the disk is available and your account has no overdue payment for it.|
|403|InvalidSystemSnapshot.Missing|? s|The error message returned because the specified SnapshotId parameter is invalid. Check whether the snapshot exists.|
|403|IncorrectDiskStatus.CreatingSnapshot|A previous snapshot creation is in process.|The error message returned because another snapshot is being created. Wait until the snapshot is created and try again.|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|The error message returned because the specified ResourceGroupId parameter does not exist.|
|500|InternalError|The process of creating snapshot has failed due to some unknown error.|The error message returned because the snapshot has failed to be created.|
|403|InvalidParameter.KMSKeyId.KMSUnauthorized|ECS service have no right to access your KMS.|The error message returned because ECS is not authorized to access your KMS resources.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|The error message returned because the specified tag key already exists. Tag keys must be unique.|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|The error message returned because the specified Tag.N.Key parameter is invalid.|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|The error message returned because the specified Tag.N.Value parameter is invalid.|
|403|QuotaExceed.Tags|%s|The error message returned because the number of specified tags exceeds the upper limit.|
|400|InvalidDiskType.ValueNotSupported|The specified disk type is not supported.|The error message returned because the specified disk type is not supported.|
|400|IdempotenceParamNotMatch|Request uses a client token in a previous request but is not identical to that request.|The error message returned because this request and the previous request contain the same client token but different parameters.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

