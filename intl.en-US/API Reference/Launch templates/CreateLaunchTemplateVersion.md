# CreateLaunchTemplateVersion

You can call this operation to create a version for a specific launch template.

## Description

To modify the parameters of a specific launch template version, you can create a new version. You can create a maximum of 30 versions for each launch template.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CreateLaunchTemplateVersion&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLaunchTemplateVersion|The operation that you want to perform. Set the value to CreateLaunchTemplateVersion. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the launch template for which you want to create a new version. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|LaunchTemplateId|String|No|lt-m5eiaupmvm2op9dxxxxx|The ID of the launch template. For more information, call the [DescribeLaunchTemplates](~~73759~~) operation to query the ID of the launch template. You must set `LaunchTemplateId` or `LaunchTemplateName` to specify the launch template. |
|LaunchTemplateName|String|No|JoshuaWinPrePaid|The name of the launch template. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). |
|VersionDescription|String|No|LTFinanceJoshua|The description of the launch template version. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|ImageId|String|No|win2008r2\_64\_ent\_sp1\_en-us\_40G\_alibase\_20170915.vhd|The ID of the image used to create an instance. You can call the [DescribeImages](~~25534~~) operation to query the available images. |
|ImageOwnerAlias|String|No|system|The source of the image.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|InstanceType|String|No|ecs.g5.large|The instance type of the instance to be created. For more information, see [Instance families](~~25378~~). Alternatively, you can call the [DescribeInstanceTypes](~~25620~~) operation to query the most recent instance type list. |
|SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7\*\*\*|The ID of the security group to which the instance to be created belongs. Instances within the same security group can access each other. |
|VpcId|String|No|vpc-bp12433upq1y5sceni\*\*\*|The ID of the VPC to which the instance to be created belongs. |
|VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*|The ID of the VSwitch. You must specify this parameter after you specify the VpcId parameter. |
|InstanceName|String|No|JoshuaHost|The name of the instance to be created. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). |
|Description|String|No|FinaceDept|The description of the instance to be created. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|InternetMaxBandwidthIn|Integer|No|50|The maximum inbound public bandwidth. Unit: Mbit/s. Valid values:

-   When the purchased outbound public bandwidth is less than 10 Mbit/s: 1 to 10. Default value: 10.
-   When the purchased outbound public bandwidth is greater than 10 Mbit/s: 1 to the value of `InternetMaxBandwidthOut`. The `InternetMaxBandwidthOut` value is used by default. |
|InternetMaxBandwidthOut|Integer|No|5|The maximum outbound public bandwidth. Unit: Mbit/s. Valid values: 0 to 100. |
|HostName|String|No|JoshuaHost|The hostname of the instance to be created.

-   The hostname cannot start or end with a period \(.\) or a hyphen \(-\). It cannot contain consecutive periods \(.\) or hyphens \(-\).
-   For Windows instances, the hostname must be 2 to 15 characters in length, and can contain letters, digits, and hyphens \(-\). The hostname cannot contain periods \(.\) or only contain digits.
-   For instances running other operating systems such as Linux, the hostname must be 2 to 64 characters in length. You can use periods \(.\) to separate a name into multiple segments. Each segment can contain letters, digits, and hyphens \(-\). |
|ZoneId|String|No|cn-hangzhou-g|The zone ID of the instance to be created. |
|SystemDisk.Category|String|No|cloud\_ssd|The category of the system disk. Valid values:

-   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   cloud\_essd: enhanced SSD |
|SystemDisk.Size|Integer|No|40|The size of the system disk. Unit: GiB. Valid values: 20 to 500.

The value of this parameter must be at least 20 and greater than or equal to the size of the image. |
|SystemDisk.DiskName|String|No|cloud\_ssdSystem|The name of the system disk. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). |
|SystemDisk.Description|String|No|FinanceDept|The description of the system disk. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DataDisk.N.Size|Integer|No|2000|The size of data disk N. Valid values of N: 1 to 16. Unit: GiB. Valid values:

-   For basic disks: 5 to 2000
-   For ultra disks: 20 to 32768
-   For standard SSDs: 20 to 32768
-   For enhanced SSDs: 20 to 32768

The value of this parameter must be greater than or equal to the size of the snapshot specified by the `SnapshotId`parameter. |
|DataDisk.N.SnapshotId|String|No|s-bp17441ohwka0yuhx\*\*\*|The ID of the snapshot used to create data disk N. Valid values of N: 1 to 16. If the `DataDisk.N.SnapshotId` parameter is specified, the `DataDisk.N.Size` parameter will be ignored, and the size of the created disk will be the specified snapshot size.

Use snapshots created after July 15, 2013. Otherwise, an error message will be returned and your request will be rejected. |
|DataDisk.N.Category|String|No|cloud\_ssd|The category of data disk N. Valid values:

-   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   cloud\_essd: enhanced SSD |
|DataDisk.N.Encrypted|String|No|false|Specifies whether to encrypt data disk N. |
|DataDisk.N.DiskName|String|No|cloud\_ssdData|The name of data disk N. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). |
|DataDisk.N.Description|String|No|FinanceDept|The description of data disk N. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DataDisk.N.DeleteWithInstance|Boolean|No|true|Specifies whether to release data disk N along with the instance to be created. |
|IoOptimized|String|No|optimized|Specifies whether the instance to be created is I/O optimized. Valid values:

-   none: The instance to be created is not I/O optimized.
-   optimized: The instance to be created is I/O optimized. |
|NetworkInterface.N.PrimaryIpAddress|String|No|192.168.2.XXX|The primary private IP address of ENI N.

**Note:** The value of N in this parameter cannot be greater than 1. |
|NetworkInterface.N.VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*|The ID of the VSwitch to which ENI N is connected. The instance to be created and ENI N must be in the same zone of the same VPC, but they can be connected to different VSwitches.

**Note:** The value of N in this parameter cannot be greater than 1. |
|NetworkInterface.N.SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7\*\*\*|The ID of the security group to which ENI N is connected. The security group of ENI N must belong to the same VPC as that of the instance to be created.

**Note:** The value of N in this parameter cannot be greater than 1. |
|NetworkInterface.N.NetworkInterfaceName|String|No|FinnanceJoshua|The name of ENI N.

**Note:** The value of N in this parameter cannot be greater than 1. |
|NetworkInterface.N.Description|String|No|FinnanceDept|The description of ENI N. The description must be 2 to 256 characters in length and cannot start with http:// or https://.

**Note:** The value of N in this parameter cannot be greater than 1. |
|InstanceChargeType|String|No|PrePaid|The billing method of the instance to be created. Valid values:

-   PrePaid: subscription. If you set the value of this parameter to PrePaid, make sure that you have sufficient balance or credit in your payment account. Otherwise, the `InvalidPayMethod` error message is returned.
-   PostPaid: pay-as-you-go. |
|Period|Integer|No|1|The subscription period of the instance to be created. Unit: months. This parameter takes effect and is required only when the `InstanceChargeType` parameter is set to `PrePaid`. If the DedicatedHostId parameter is specified, the value of the Period parameter must fall within the subscription period of the dedicated host. Valid values:

-   Valid values in the case of `PeriodUnit=Week`: 1, 2, 3, and 4
-   Valid values in the case of `PeriodUnit=Month`: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60 |
|InternetChargeType|String|No|PayByTraffic|The billing method for outbound Internet usage. Valid values:

-   PayByBandwidth
-   PayByTraffic

**Note:** The bandwidth that you specify when the pay-by-traffic billing method is used is the peak outbound bandwidth. In the event of resource contention, this bandwidth cannot be guaranteed. If you want a guaranteed bandwidth for your instance, use the pay-by-bandwidth billing method. |
|EnableVmOsConfig|Boolean|No|false|Specifies whether to enable the operating system configuration of the instance to be created. |
|NetworkType|String|No|vpc|The network type of the instance to be created. Valid values:

-   classic
-   vpc |
|UserData|String|No|ZWNobyBoZWxsbyBlY\*\*\*|The user data of the instance to be created. It must be encoded in Base64. The maximum size of the raw data is 16 KB. |
|KeyPairName|String|No|Instancetest|The name of the SSH key pair.

-   For Windows instances, this parameter is ignored. The `Password` parameter still takes effect even if the KeyPairName parameter is specified.
-   For Linux instances, the username and password authentication method is disabled by default. |
|RamRoleName|String|No|FinanceDept|The RAM role name of the instance to be created. You can call the [ListRoles](~~28713~~) operation provided by RAM to query the RAM roles that you have created. |
|AutoReleaseTime|String|No|2018-01-01T12:05:00Z|The time scheduled for the instance to be automatically released. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

-   If the value of `ss` is not `00`, the time will be automatically set to the start of the current minute \(`mm`\).
-   It must be at least 30 minutes later than the current time.
-   It must be at most three years from the current time. |
|SpotStrategy|String|No|NoSpot|The preemption policy for a preemptible or pay-as-you-go instance. This parameter takes effect when the `InstanceChargeType` parameter is set to `PostPaid`. Valid values:

-   NoSpot: The instance to be created is a regular pay-as-you-go instance.
-   SpotWithPriceLimit: The instance to be created is a preemptible instance with a user-defined maximum hourly price.
-   SpotAsPriceGo: The instance to be created is a preemptible instance whose price is based on the market price at the time of purchase. |
|SpotPriceLimit|Float|No|0.97|The maximum hourly price of the instance to be created. This parameter supports up to three decimal places. |
|SpotDuration|Integer|No|1|The protection period of the instance to be created.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*|The ID of the resource group to which the instance to be created belongs. |
|SecurityEnhancementStrategy|String|No|Active|Specifies whether to enable security hardening for the operating system. Valid values:

-   Active: enables security hardening for public images.
-   Deactive: disables security hardening for all image types. |
|Tag.N.Key|String|No|FinanceDept|The key of tag N of the instance, Block Storage device, or primary NIC. Valid values of N: 1 to 5. The tag key cannot be an empty string. It can be up to 64 characters in length, cannot start with acs: or aliyun, and cannot contain http:// or https://. |
|Tag.N.Value|String|No|FinanceDept.Joshua|The value of tag N of the instance, Block Storage device, or primary NIC. Valid values of N: 1 to 5. The tag value can be an empty string. It can be up to 128 characters in length, cannot start with acs: or aliyun, and cannot contain http:// or https://. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|LaunchTemplateVersionNumber|Long|2|The version number of the launch template. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=CreateLaunchTemplateVersion
&RegionId=cn-hangzhou
&LaunchTemplateId=lt-m5eiaupmvm2op9d*****
&LaunchTemplateName=JoshuaWinPrePaid
&VersionDescription=LTFinanceJoshua
&ImageId=win2008r2_64_ent_sp1_en-us_40G_alibase_20170915.vhd
&InstanceType=ecs.g5.large
&SecurityGroupId=sg-bp15ed6xe1yxeycg7***
&VpcId=vpc-bp12433upq1y5sceni07X
&VSwitchId=vsw-bp1s5fnvk4gn2tws03***
&InstanceName=JoshuaHost
&Description=FinaceDept
&InternetMaxBandwidthIn=50
&InternetMaxBandwidthOut=5
&HostName=JoshuaHost
&ZoneId=cn-hangzhou-g
&SystemDisk.Category=cloud_ssd
&SystemDisk.Size=40
&SystemDisk.DiskName=cloud_ssdSystem
&SystemDisk.Description=FinanceDept
&DataDisk.1.Size=2000
&DataDisk.1.SnapshotId=s-bp17441ohwka0yuhx***
&DataDisk.1.Category=cloud_ssd
&DataDisk.1.Encrypted=false
&DataDisk.1.DiskName=cloud_ssdData
&DataDisk.1.Description=FinanceDept
&DataDisk.1.DeleteWithInstance=true
&IoOptimized=optimized
&NetworkInterface.1.PrimaryIpAddress=192.168.2. ***
&NetworkInterface.1.VSwitchId=vsw-bp1s5fnvk4gn2tws03***
&NetworkInterface.1.SecurityGroupId=sg-bp15ed6xe1yxeycg7***
&NetworkInterface.1.NetworkInterfaceName=FinnanceJoshua
&NetworkInterface.1.Description=FinnanceDept
&InstanceChargeType=PrePaid
&Period=1
&InternetChargeType=PayByTraffic
&NetworkType=vpc
&UserData=ZWNobyBoZWxsbyBlY3Mh
&RamRoleName=FinanceDept
&AutoReleaseTime=2020-02-02T12:05:00Z
&SpotStrategy=NoSpot
&SpotPriceLimit=0.97
&SecurityEnhancementStrategy=Active
&Tag.1.Key=FinanceDept
&Tag.1.Value=FinanceDept.Joshua
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLaunchTemplateVersionResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
      <LaunchTemplateVersionNumber>2</LaunchTemplateVersionNumber>
</CreateLaunchTemplateVersionResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "LaunchTemplateVersionNumber": 2
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidRegion.NotExist|%s|The error message returned because the specified RegionId parameter does not exist. Check whether the region ID is correct.|
|403|LaunchTemplateVersionLimitExceed|%s|The error message returned because the maximum number of launch template versions has been reached.|
|404|InvalidLaunchTemplate.NotFound|%s|The error message returned because the specified launch template does not exist. Check whether the specified value of the LaunchTemplateId or LaunchTemplateName parameter is correct.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|400|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|400|InvalidDescription.Malformed|The specified parameter "Description" is not valid.|The error message returned because the specified Description parameter is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|403|InnerServiceFailed|%s|The error message returned because an internal service failed to be called.|
|400|InvalidUserData.SizeExceeded|%s|The error message returned because the size of the specified user data exceeds the upper limit.|
|400|InvalidUserData.Base64FormatInvalid|%s|The error message returned because the format you specified for the user data is invalid. Select a valid data format.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

