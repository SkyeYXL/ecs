# DescribeImageFromFamily

You can call this operation to query available custom images that are newly created in a specific image family.

## Description

-   This API operation only returns the available custom images that are newly created in the specified image family. Public images, Alibaba Cloud Marketplace images, community images, or shared images are not queried.
-   If no available custom images exist in the specified image family, the response is empty.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeImageFromFamily&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeImageFromFamily|The operation that you want to perform. Set the value to DescribeImageFromFamily. |
|ImageFamily|String|Yes|hangzhou-daily-update|The name of the image family. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http://, https://, acs:, or aliyun. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the image. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Image|Struct| |The image information. |
|Architecture|String|x86\_64|The image architecture. Valid values:

-   i386
-   x86\_64 |
|CreationTime|String|2018-01-10T01:01:10Z|The time when the image was created. |
|Description|String|testDescription|The description of the image. |
|DiskDeviceMappings|Array of DiskDeviceMapping| |The mappings between the disks and snapshots under the image. |
|DiskDeviceMapping| | | |
|Device|String|/dev/xvdb|The device name of the disk. Example: /dev/xvdb.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|Format|String|qcow2|The format of the image. |
|ImportOSSBucket|String|testEcsImport|The OSS bucket that contains the imported image file. |
|ImportOSSObject|String|imageImport|The OSS object corresponding to the imported image file. |
|Size|String|80|The size of the disk. Unit: GiB. |
|SnapshotId|String|s-bp17ot2q7x72ggtw\*\*\*\*|The ID of the snapshot. |
|Type|String|custom|The type of the image. |
|ImageFamily|String|testImageFamily|The name of the image family. |
|ImageId|String|m-bp1g7004ksh0oeuc\*\*\*\*|The ID of the image. |
|ImageName|String|testImageName|The name of the image. |
|ImageOwnerAlias|String|self|The alias of the image owner. Valid values:

-   system: public images provided by Alibaba Cloud
-   self: your custom images
-   others: shared images from other Alibaba Cloud accounts
-   marketplace: Alibaba Cloud Marketplace images |
|ImageVersion|String|2|The version of the image. |
|IsCopied|Boolean|false|Indicates whether the image is a copy of another image. |
|IsSelfShared|String|true|Indicates whether the image has been shared to other Alibaba Cloud accounts. |
|IsSubscribed|Boolean|false|Indicates whether you have subscribed to the image corresponding to the specified product code. |
|IsSupportCloudinit|Boolean|true|Indicates whether the image supports cloud-init. |
|IsSupportIoOptimized|Boolean|true|Indicates whether the image can be used on I/O optimized instances. |
|OSName|String|Alibaba Cloud Linux 2.1903|The name of the operating system. |
|OSType|String|linux|The type of the operating system. Valid values:

-   windows
-   linux |
|Platform|String|Aliyun|The platform of the operating system. |
|ProductCode|String|jxsc00\*\*\*\*|The product code of the Alibaba Cloud Marketplace image. |
|Progress|String|100|The image creation progress. Unit: percent \(%\). |
|Size|Integer|80|The size of the image. Unit: GiB. |
|Status|String|Available|The status of the image. Valid values:

-   UnAvailable: The image is unavailable.
-   Available: The image is available.
-   Creating: The image is being created.
-   CreateFailed: The image failed to be created. |
|Tags|Array of Tag| |An array that consists of Tag data. |
|Tag| | | |
|TagKey|String|TestKey|The tag key of the image. |
|TagValue|String|TestValue|The tag value of the image. |
|Usage|String|none|Indicates whether the image has been used to create ECS instances. Valid values:

-   instance: The image has been used to create one or more ECS instances.
-   none: The image has not been used to create ECS instances. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeImageFromFamily
&RegionId=cn-hangzhou
&ImageFamily=as-hangzhou-game-01
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeImageFromFamilyResponse>
      <RequestId>E39053A7-C3E6-41FA-8F8D-F5BD8063E61C</RequestId>
      <Image>
            <ImageOwnerAlias>self</ImageOwnerAlias>
            <Status>Available</Status>
            <Progress></Progress>
            <Usage></Usage>
            <Description>testDescription</Description>
            <IsSelfShared></IsSelfShared>
            <Architecture>x86_64</Architecture>
            <Platform>CentOS</Platform>
            <ProductCode></ProductCode>
            <Size>40</Size>
            <IsSubscribed>false</IsSubscribed>
            <IsCopied>false</IsCopied>
            <ImageFamily>testImageFamily</ImageFamily>
            <OSName>CentOS 8.0 64-bit</OSName>
            <IsSupportIoOptimized>true</IsSupportIoOptimized>
            <IsSupportCloudinit>true</IsSupportCloudinit>
            <ImageName>testImageName</ImageName>
            <DiskDeviceMappings>
                  <DiskDeviceMapping>
                        <SnapshotId>s-bp1ejhb4r1lyu55t****</SnapshotId>
                        <Type>system</Type>
                        <Format></Format>
                        <Size>40</Size>
                        <Device>/dev/xvda</Device>
                        <ImportOSSBucket></ImportOSSBucket>
                        <ImportOSSObject></ImportOSSObject>
                  </DiskDeviceMapping>
            </DiskDeviceMappings>
            <ImageVersion></ImageVersion>
            <OSType>linux</OSType>
            <ImageId>m-bp1ejhb4r1lyu55t****</ImageId>
            <CreationTime>2020-03-17T06:19:19Z</CreationTime>
            <Tags>
        </Tags>
      </Image>
</DescribeImageFromFamilyResponse>
```

`JSON` format

```
{
    "RequestId": "E39053A7-C3E6-41FA-8F8D-F5BD8063E61C",
    "Image": {
        "ImageOwnerAlias": "self",
        "Status": "Available",
        "Progress": "",
        "Usage": "",
        "Description": "testDescription",
        "IsSelfShared": "",
        "Architecture": "x86_64",
        "Platform": "CentOS",
        "ProductCode": "",
        "Size": 40,
        "IsSubscribed": false,
        "IsCopied": false,
        "ImageFamily": "testImageFamily",
        "OSName": "CentOS 8.0 64-bit",
        "IsSupportIoOptimized": true,
        "IsSupportCloudinit": true,
        "ImageName": "testImageName",
        "DiskDeviceMappings": {
            "DiskDeviceMapping": [
                {
                    "SnapshotId": "s-bp1ejhb4r1lyu55t****",
                    "Type": "system",
                    "Format": "",
                    "Size": "40",
                    "Device": "/dev/xvda",
                    "ImportOSSBucket": "",
                    "ImportOSSObject": ""
                }
            ]
        },
        "ImageVersion": "",
        "OSType": "linux",
        "ImageId": "m-bp1ejhb4r1lyu55t****",
        "CreationTime": "2020-03-17T06:19:19Z",
        "Tags": {
            "Tag": []
        }
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The RegionId provided does not exist.|The error message returned because the specified RegionId parameter does not exist. Check whether the region ID is correct.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

