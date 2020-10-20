# CreateLaunchTemplate

You can call this operation to create an ECS instance launch template \(template\). An instance launch template removes the need to configure a large number of parameters every time you create an instance.

## Description

Instance launch templates contain preset configurations used to create instances, such as the region, image ID, instance type, security group ID, and public bandwidth settings. If the setting of a certain parameter is not included in the template, that parameter must be specified manually during instance creation.

After you create a template \(`CreateLaunchTemplate`\), its version number is set to 1 by default. You can create multiple versions \(`CreateLaunchTemplateVersion`\) based on this template. Version numbers start from 1 and increase sequentially. If you do not specify a template version number when you create instances \([RunInstances](~~63440~~)\), the default version is used.

When you call this operation, take note of the following points:

-   You can create up to 30 instance launch templates in each region. Each template can have up to 30 versions.
-   Most parameters of instance launch templates are optional. When you create a template, ECS does not verify the existence or validity of its parameter values. The validity of specified parameter values cannot be verified until you create instances with the template.
-   If you set a certain parameter in an instance launch template, you cannot filter out this setting when you create instances \([RunInstances](~~63440~~)\). For example, if you set `HostName=LocalHost` for a template, and then do not specify the value of `HostName` when you create instances \(`RunInstances`\), the instance hostname is still `LocalHost`. If you want to overwrite `HostName=LocalHost`, you can set `HostName=MyHost` or set the HostName parameter to other values when you create instances \(`RunInstances`\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CreateLaunchTemplate&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLaunchTemplate|The operation that you want to perform. Set the value to CreateLaunchTemplate. |
|LaunchTemplateName|String|Yes|WinPrePaid|The name of the instance launch template. The name must be 2 to 128 characters in length. The name can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with http:// or https://. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance launch template. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|TemplateTag.N.Key|String|No|LTtest|The key of tag N of the launch template. Valid values of N: 1 to 20. The tag key cannot be an empty string. The tag key can be up to 128 characters in length and cannot contain http:// or https://. It cannot start with acs: or aliyun. |
|TemplateTag.N.Value|String|No|LTtest|The value of tag N of the launch template. Valid values of N: 1 to 20. The tag value can be an empty string. The tag value can be up to 128 characters in length and cannot contain http:// or https://. It cannot start with acs: or aliyun. |
|VersionDescription|String|No|LTtest|The description of the version 1 of instance launch template. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|ImageId|String|No|win2008r2\_64\_ent\_sp1\_en-us\_40G\_alibase\_20170915.vhd|The ID of the image used to create the instance. You can call the [DescribeImages](~~25534~~) operation to query available images. |
|ImageOwnerAlias|String|No|system|The source of the image. Valid values:

-   system: public images provided by Alibaba Cloud.
-   self: your custom images.
-   others: images shared from other Alibaba Cloud accounts.
-   marketplace: available images from [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/). If Alibaba Cloud Marketplace images are returned in the response, you can directly use these images without prior subscription. You must pay attention to the billing details of Alibaba Cloud Marketplace images.

This parameter is empty by default, indicating that the results matching system, self, and others are returned. |
|PasswordInherit|Boolean|No|false|Specifies whether to use the password preset in the image.

**Note:** To use the PasswordInherit parameter, the Password parameter must be empty and you must make sure that the selected image has a password configured. |
|InstanceType|String|No|ecs.g5.large|The instance type. For more information, see [Instance families](~~25378~~) or call the [DescribeInstanceTypes](~~25620~~) operation to query the most recent instance type list. |
|SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7\*\*\*|The ID of the security group to which the instance belongs. Instances in the same security group can communicate with each other. One security group can contain a maximum of 1,000 instances. |
|VpcId|String|No|vpc-bp12433upq1y5sceni\*\*\*|The ID of the VPC to which the new instance belongs. |
|VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*|The ID of the VSwitch. If you are creating a VPC-type instance, you must specify this parameter. |
|InstanceName|String|No|EcsHost|The name of the instance. The name must be 2 to 128 characters in length. The name can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://. |
|Description|String|No|EcsHost|The description of the instance. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|InternetMaxBandwidthIn|Integer|No|10|The maximum inbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values:

-   If the purchased outbound bandwidth for Internet traffic is less than or equal to 10 Mbit/s, valid values are 1 to 10. Default value: 10.
-   If the purchased outbound bandwidth for Internet traffic is greater than 10 Mbit/s, valid values are 1 to the value of the `InternetMaxBandwidthOut` parameter. The value of the `InternetMaxBandwidthOut` parameter is used by default. |
|InternetMaxBandwidthOut|Integer|No|10|The maximum outbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values: 0 to 100. |
|HostName|String|No|EcsHost|The hostname of the instance.

-   The hostname cannot start or end with a period \(.\) or a hyphen \(-\) It cannot contain consecutive periods \(.\) or hyphens \(-\).
-   Windows instances: The hostname must be 2 to 15 characters in length, and can contain letters, digits, and hyphens \(-\). The hostname cannot contain periods \(.\) or only contain digits.
-   Non-Windows Instances: The hostname must be 2 to 64 characters in length. You can use periods \(.\) to separate a name into multiple segments. Each segment can contain letters, digits, and hyphens \(-\). |
|ZoneId|String|No|cn-hangzhou-g|The zone ID of the instance. |
|SystemDisk.Category|String|No|cloud\_ssd|The category of the system disk. Valid values:

-   cloud: basic disks
-   cloud\_efficiency: ultra disks
-   cloud\_ssd: standard SSDs
-   cloud\_essd: enhanced SSDs |
|SystemDisk.Size|Integer|No|40|The size of the system disk. Unit: GiB. Valid values: 20 to 500.

The value of the parameter must be at least 20 and greater than or equal to the size of the image. |
|SystemDisk.DiskName|String|No|cloud\_ssdSystem|The name of the system disk of the created instance. The name must be 2 to 128 characters in length. The name can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with http:// or https://. |
|SystemDisk.Description|String|No|TestDisk|The description of the system disk. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DataDisk.N.Size|Integer|No|2000|The size of data disk N. Valid values of N: 1 to 16. Unit: GiB. Valid values:

-   cloud: 5 to 2000
-   cloud\_efficiency: 20 to 32768
-   cloud\_ssd: 20 to 32768
-   cloud\_essd: 20 to 32768

The value of this parameter must be greater than or equal to the size of the snapshot specified by the `SnapshotId`parameter. |
|DataDisk.N.SnapshotId|String|No|s-bp17441ohwka0yuhx\*\*\*|The ID of the snapshot used to create data disk N. Valid values of N: 1 to 16. If the `DataDisk.N.SnapshotId` parameter is specified, the `DataDisk.N.Size` parameter will be ignored, and the size of the created disk will be the specified snapshot size.

Snapshots created on or before July 15, 2013 cannot be used here. Otherwise, an error message will be returned and your request will be rejected. |
|DataDisk.N.Category|String|No|cloud\_ssd|The category of data disk N. Valid values:

-   cloud: basic disks
-   cloud\_efficiency: ultra disks
-   cloud\_ssd: standard SSDs
-   cloud\_essd: enhanced SSDs |
|DataDisk.N.Encrypted|String|No|false|Specifies whether to encrypt data disk N. |
|DataDisk.N.DiskName|String|No|cloud\_ssdData|The disk name of data disk N. The name must be 2 to 128 characters in length. The name can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://. |
|DataDisk.N.Description|String|No|TestDisk|The description of data disk N. The description must be 2 to 256 characters in length and cannot start with http:// or https://. |
|DataDisk.N.DeleteWithInstance|Boolean|No|true|Specifies whether to release data disk N along with the instance. |
|IoOptimized|String|No|optimized|Specifies whether the instance is an I/O optimized instance. Valid values:

-   none: The instance is a non-I/O optimized instance.
-   optimized: The instance is an I/O optimized instance. |
|NetworkInterface.N.PrimaryIpAddress|String|No|192.168.2.\*\*\*|The IP address of primary elastic network interface \(ENI\) N.

**Note:** The value of N in the `NetworkInterface.N` parameter cannot be greater than 1. |
|NetworkInterface.N.VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*|The ID of the VSwitch to which ENI N belongs. The instance and ENI N must be in the same zone of the same VPC, but they can belong to different VSwitches.

**Note:** The value of N in the `NetworkInterface.N` parameter cannot be greater than 1. |
|NetworkInterface.N.SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7\*\*\*|The ID of the security group to which ENI N belongs. The security group of ENI N must belong to the same VPC as that of the instance.

**Note:** The value of N in the `NetworkInterface.N` parameter cannot be greater than 1. |
|NetworkInterface.N.NetworkInterfaceName|String|No|TestEni|The name of ENI N.

**Note:** The value of N in the `NetworkInterface.N` parameter cannot be greater than 1. |
|NetworkInterface.N.Description|String|No|TestEni|The description of ENI N. The description must be 2 to 256 characters in length and cannot start with http:// or https://.

**Note:** The value of N in the `NetworkInterface.N` parameter cannot be greater than 1. |
|InstanceChargeType|String|No|PrePaid|The billing method of the instance. Valid values:

-   PrePaid: subscription. If it is set to PrePaid, you must make sure that your payment account has sufficient credit. Otherwise, the error message `InvalidPayMethod` is returned.
-   PostPaid: pay-as-you-go. |
|Period|Integer|No|1|The subscription period of the instance. Unit: months. This parameter takes effect and is required only when the value of the `InstanceChargeType` parameter is set to `PrePaid`. If the DedicatedHostId parameter is specified, values of the Period parameter must be within the subscription period of the dedicated host. Valid values:

-   In case of `PeriodUnit=Week`, valid values of the Period parameter are 1, 2, 3, and 4.
-   In case of `PeriodUnit=Month`, valid values of the Period parameter are 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60. |
|InternetChargeType|String|No|PayByTraffic|The billing method for network usage. Valid values:

-   PayByBandwidth
-   PayByTraffic |
|EnableVmOsConfig|Boolean|No|false|Specifies whether to enable the operating system configurations of the instance.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|NetworkType|String|No|vpc|The network type of the instance. Valid values:

-   classic
-   vpc |
|UserData|String|No|ZWNobyBoZWxsbyBlY3Mh|The user data of the instance. It must be encoded in Base64. The maximum size of the raw data is 16 KB. |
|KeyPairName|String|No|Instancetest|The name of the SSH key pair.

-   For Windows instances, this parameter is ignored The `Password` parameter still takes effect even if the KeyPairName parameter is specified.
-   For Linux instances, if this parameter is set, the username and password authentication method is disabled for instance logon. |
|RamRoleName|String|No|TestRamRole|The RAM role name of the instance. You can call the [ListRoles](~~28713~~) operation provided by RAM to query the RAM roles that you have created. |
|AutoReleaseTime|String|No|2018-01-01T12:05:00Z|The time scheduled for a created ECS instance to be automatically released. Specify the time in the [ISO 8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

-   If the value of seconds \(`ss`\) is not `00`, it is automatically set to the start time of the current minute \(`mm`\).
-   It must be at least 30 minutes later than the current time.
-   The maximum release time must be at most three years from the current time. |
|SpotStrategy|String|No|NoSpot|The preemption policy for a preemptible or pay-as-you-go instance. This parameter takes effect when the `InstanceChargeType` parameter is set to `PostPaid`. Valid values:

-   NoSpot: the regular pay-as-you-go instance.
-   SpotWithPriceLimit: the preemptible instance with a user-defined upper price limit.
-   SpotAsPriceGo: the preemptible instance whose price is based on the current market price. |
|SpotPriceLimit|Float|No|0.97|The maximum hourly price of the instance. It can be accurate to three decimal places and takes effect when the `SpotStrategy` parameter is set to `SpotWithPriceLimit`. |
|SpotDuration|Integer|No|1|The protection period of the instance.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*|The ID of the resource group to which the instance, Block Storage, and ENI belong. |
|TemplateResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*|The ID of the resource group to which the launch template belongs. |
|SecurityEnhancementStrategy|String|No|Deactive|Specifies whether to enable security hardening for the operating system. Valid values:

-   Active: enables security hardening. It is applicable only to Alibaba Cloud public images.
-   Deactive: disables security hardening. It is applicable to all image types. |
|Tag.N.Key|String|No|TestTag|The key of tag N of the instance, Block Storage, or primary NIC. Valid values of N: 1 to 20. The tag key cannot be an empty string. The tag key can be up to 64 characters in length and cannot contain http:// or https://. It cannot start with acs: or aliyun. |
|Tag.N.Value|String|No|TestTag|The value of tag N of the instance, Block Storage, or primary NIC. Valid values of N: 1 to 20. The tag value can be an empty string. The tag value can be up to 128 characters in length and cannot contain http:// or https://. It cannot start with acs: or aliyun. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|LaunchTemplateId|String|lt-m5eiaupmvm2op9d\*\*\*\*\*|The ID of the instance launch template. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=CreateLaunchTemplate
&LaunchTemplateName=WinPrePaid
&RegionId=cn-hangzhou
&TemplateTag.1.Key=LTtest
&TemplateTag.1.Value=LTtest
&VersionDescription=LTtest
&ImageId=win2008r2_64_ent_sp1_en-us_40G_alibase_20170915.vhd
&InstanceType=ecs.g5.large
&SecurityGroupId=sg-bp15ed6xe1yxeycg7***
&VpcId=vpc-bp12433upq1y5sceni***
&VSwitchId=vsw-bp1s5fnvk4gn2tws03***
&InstanceName=EcsHost
&Description=EcsHost
&InternetMaxBandwidthIn=10
&InternetMaxBandwidthOut=10
&HostName=EcsHost
&ZoneId=cn-hangzhou-g
&SystemDisk.Category=cloud_ssd
&SystemDisk.Size=40
&SystemDisk.DiskName=cloud_ssdSystem
&SystemDisk.Description=TestDisk
&DataDisk.1.Size=2000
&DataDisk.1.SnapshotId=s-bp17441ohwka0yuhx***
&DataDisk.1.Category=cloud_ssd
&DataDisk.1.Encrypted=false
&DataDisk.1.DiskName=cloud_ssdData
&DataDisk.1.Description=TestDisk
&DataDisk.1.DeleteWithInstance=true
&IoOptimized=optimized
&NetworkInterface.1.PrimaryIpAddress=192.168.2. ***
&NetworkInterface.1.VSwitchId=vsw-bp1s5fnvk4gn2tws03***
&NetworkInterface.1.SecurityGroupId=sg-bp15ed6xe1yxeycg7***
&NetworkInterface.1.NetworkInterfaceName=TestEni
&NetworkInterface.1.Description=TestEni
&InstanceChargeType=PrePaid
&Period=1
&InternetChargeType=PayByTraffic
&NetworkType=vpc
&UserData=ZWNobyBoZWxsbyBlY3Mh
&RamRoleName=TestRamRole
&AutoReleaseTime=2018-01-01T12:05:00Z
&SpotStrategy=NoSpot
&SpotPriceLimit=0.97
&SecurityEnhancementStrategy=Deactive
&Tag.1.Key=TestTag
&Tag.1.Value=TestTag
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLaunchTemplateResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
      <LaunchTemplateId>lt-m5eiaupmvm2op9d*****</LaunchTemplateId>
</CreateLaunchTemplateResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "LaunchTemplateId": "lt-m5eiaupmvm2op9d*****"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidRegion.NotExist|%s|The error message returned because the specified RegionId parameter does not exist. Check whether the region ID is correct.|
|403|LaunchTemplateLimitExceed|%s|The error message returned because the maximum number of launch templates has been reached.|
|403|LaunchTemplateName.Duplicated|%s|The error message returned because the specified LaunchTemplateName parameter already exists.|
|400|MissingParameter|%s|The error message returned because a required parameter is not specified.|
|400|InvalidParameter|%s|The error message returned because the specified parameter is invalid.|
|400|InvalidLaunchTemplateName.Malformed|The specified parameter LaunchTemplateName is not valid.|The error message returned because the specified LaunchTemplateName parameter is invalid.|
|400|InvalidDescription.Malformed|The specified parameter "VersionDescription" is not valid.|The error message returned because the specified VersionDescription parameter is invalid.|
|403|InnerServiceFailed|%s|The error message returned because an internal service failed to be called.|
|400|InvalidUserData.SizeExceeded|%s|The error message returned because the size of the specified UserData parameter exceeds the upper limit.|
|400|InvalidUserData.Base64FormatInvalid|%s|The error message returned because the UserData parameter is invalid. Select valid data.|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|The error message returned because the specified Tag.N.Key parameter already exists. Tag keys must be unique.|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|The error message returned because the specified Tag.N.Key parameter is invalid.|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|The error message returned because the specified Tag.N.Value parameter is invalid.|
|403|QuotaExceed.Tags|%s|The error message returned because the maximum number of tags has been reached.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

