# List of operations by function

The following tables list API operations available for use in ECS.

## Instances

|API|Description|
|---|-----------|
|[RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md)|Creates one or more pay-as-you-go or subscription ECS instances.|
|[CreateInstance](/intl.en-US/API Reference/Instances/CreateInstance.md)|Creates a pay-as-you-go or subscription ECS instance.|
|[StartInstance](/intl.en-US/API Reference/Instances/StartInstance.md)|Starts an instance.|
|[StopInstance](/intl.en-US/API Reference/Instances/StopInstance.md)|Stops an instance.|
|[RebootInstance](/intl.en-US/API Reference/Instances/RebootInstance.md)|Restarts an instance that is in the Running state.|
|[DeleteInstance](/intl.en-US/API Reference/Instances/DeleteInstance.md)|Releases a pay-as-you-go instance or an expired subscription instance.|
|[StartInstances](/intl.en-US/API Reference/Instances/StartInstances.md)|Starts one or more ECS instances that are in the Stopped state.|
|[RebootInstances](/intl.en-US/API Reference/Instances/RebootInstances.md)|Restarts one or more ECS instances that are in the Running state.|
|[StopInstances](/intl.en-US/API Reference/Instances/StopInstances.md)|Stops one or more ECS instances that are in the Running state.|
|[AttachInstanceRamRole](/intl.en-US/API Reference/Instances/AttachInstanceRamRole.md)|Attaches a RAM role to one or more ECS instances. An ECS instance can have only one RAM role. If an instance already has a RAM role, an error code is returned when you attach another RAM role to the instance.|
|[DetachInstanceRamRole](/intl.en-US/API Reference/Instances/DetachInstanceRamRole.md)|Detaches a RAM role from one or more ECS instances.|
|[DescribeInstanceStatus](/intl.en-US/API Reference/Instances/DescribeInstanceStatus.md)|Queries the status information of one or more ECS instances.|
|[DescribeInstances](/intl.en-US/API Reference/Instances/DescribeInstances.md)|Queries the detailed information of one or more instances.|
|[DescribeInstanceVncUrl](/intl.en-US/API Reference/Instances/DescribeInstanceVncUrl.md)|Queries the VNC URL of an ECS instance.|
|[DescribeUserData](/intl.en-US/API Reference/Instances/DescribeUserData.md)|Queries the user data of an ECS instance.|
|[DescribeInstanceAutoRenewAttribute](/intl.en-US/API Reference/Instances/DescribeInstanceAutoRenewAttribute.md)|Queries the auto-renewal status of one or more subscription ECS instances.|
|[DescribeInstanceRamRole](/intl.en-US/API Reference/Instances/DescribeInstanceRamRole.md)|Queries RAM roles attached to one or more ECS instances.|
|[DescribeSpotPriceHistory](/intl.en-US/API Reference/Instances/DescribeSpotPriceHistory.md)|Queries the price history of a preemptible instance within the last 30 days.|
|[DescribeInstanceTypeFamilies](/intl.en-US/API Reference/Instances/DescribeInstanceTypeFamilies.md)|Queries instance families provided by ECS.|
|[DescribeInstanceTypes](/intl.en-US/API Reference/Instances/DescribeInstanceTypes.md)|Queries instance types provided by ECS.|
|[ModifyInstanceAttribute](/intl.en-US/API Reference/Instances/ModifyInstanceAttribute.md)|Modifies information about an ECS instance, such as the password, name, description, hostname, and user data. For a burstable instance, you can also change its burst mode.|
|[ModifyInstanceVncPasswd](/intl.en-US/API Reference/Instances/ModifyInstanceVncPasswd.md)|Modifies the VNC password of an instance.|
|[ModifyInstanceAutoReleaseTime](/intl.en-US/API Reference/Instances/ModifyInstanceAutoReleaseTime.md)|Sets or cancels the automatic release time for a pay-as-you-go instance. Exercise caution when you set the automatic release time because the instance will be automatically released upon expiration.|
|[ModifyInstanceAutoRenewAttribute](/intl.en-US/API Reference/Instances/ModifyInstanceAutoRenewAttribute.md)|Configures auto-renewal for one or more subscription instances. To reduce the maintenance workload when an instance expires, you can configure auto-renewal for subscription ECS instances.|
|[ModifyInstanceChargeType](/intl.en-US/API Reference/Instances/ModifyInstanceChargeType.md)|Changes the billing method of one or more ECS instances. You can switch the billing method of instances between pay-as-you-go and subscription, or change the billing method of all data disks attached to an instance from pay-as-you-go to subscription.|
|[ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md)|Modifies the instance type and public bandwidth of a pay-as-you-go instance.|
|[ModifyPrepayInstanceSpec](/intl.en-US/API Reference/Instances/ModifyPrepayInstanceSpec.md)|Upgrades or downgrades the instance type of a subscription ECS instance. The new instance type takes effect for the entire lifecycle of the instance.|
|[ModifyInstanceMetadataOptions](/intl.en-US/API Reference/Instances/ModifyInstanceMetadataOptions.md)|Modifies the metadata of an instance.|
|[RenewInstance](/intl.en-US/API Reference/Instances/RenewInstance.md)|Renews a subscription ECS instance.|
|[ReactivateInstances](/intl.en-US/API Reference/Instances/ReActivateInstances.md)|Reactivates an expired subscription instance or a pay-as-you-go instance that is in the Overdue and Being Recycled state.|
|[DeleteInstances](/intl.en-US/API Reference/Instances/DeleteInstances.md)|Releases one or more pay-as-you-go ECS instances or expired subscription ECS instances.|

## Dedicated hosts

|API|Description|
|---|-----------|
|[AllocateDedicatedHosts](/intl.en-US/API Reference/Dedicated hosts/AllocateDedicatedHosts.md)|Creates one or more pay-as-you-go or subscription dedicated hosts. A dedicated host provides a dedicated physical server for a single tenant. You can create ECS instances on a dedicated host and view the attributes of the physical server.|
|[RenewDedicatedHosts](/intl.en-US/API Reference/Dedicated hosts/RenewDedicatedHosts.md)|Renews one or more subscription dedicated hosts.|
|[ReleaseDedicatedHost](/intl.en-US/API Reference/Dedicated hosts/ReleaseDedicatedHost.md)|Releases a pay-as-you-go dedicated host.|
|[RedeployDedicatedHost](/intl.en-US/API Reference/Dedicated hosts/RedeployDedicatedHost.md)|Migrates ECS instances from a failed dedicated host.|
|[DescribeDedicatedHosts](/intl.en-US/API Reference/Dedicated hosts/DescribeDedicatedHosts.md)|Queries the detailed information of one or more dedicated hosts, including the physical performance metrics, machine code, usage status, and list of ECS instances that have been created.|
|[DescribeDedicatedHostTypes](/intl.en-US/API Reference/Dedicated hosts/DescribeDedicatedHostTypes.md)|Queries the specifications of supported dedicated hosts in a region, or the ECS instance families that are supported by a specific type of dedicated hosts.|
|[DescribeDedicatedHostAutoRenew](/intl.en-US/API Reference/Dedicated hosts/DescribeDedicatedHostAutoRenew.md)|Queries the auto-renewal status of one or more subscription dedicated hosts.|
|[ModifyInstanceDeployment](/intl.en-US/API Reference/Dedicated hosts/ModifyInstanceDeployment.md)|Changes the dedicated host of an ECS instance. The ECS instance and the destination dedicated host must be in the same region.|
|[ModifyDedicatedHostAttribute](/intl.en-US/API Reference/Dedicated hosts/ModifyDedicatedHostAttribute.md)|Modifies some properties of a dedicated host, such as the name, description, and instance migration policy applied when the dedicated host fails.|
|[ModifyDedicatedHostAutoReleaseTime](/intl.en-US/API Reference/Dedicated hosts/ModifyDedicatedHostAutoReleaseTime.md)|Sets the automatic release time for a pay-as-you-go dedicated host or cancels the automatic release of a pay-as-you-go dedicated host.|
|[ModifyDedicatedHostAutoRenewAttribute](/intl.en-US/API Reference/Dedicated hosts/ModifyDedicatedHostAutoRenewAttribute.md)|Enables or disables automatic renewal for one or more subscription dedicated hosts.|
|[ModifyDedicatedHostsChargeType](/intl.en-US/API Reference/Dedicated hosts/ModifyDedicatedHostsChargeType.md)|Modifies the billing method of one or more dedicated hosts.|

## Launch templates

|API|Description|
|---|-----------|
|[CreateLaunchTemplate](/intl.en-US/API Reference/Launch templates/CreateLaunchTemplate.md)|Creates an instance launch template \(template\). An instance launch template eliminates the needs to configure a large number of parameters every time you create an instance.|
|[CreateLaunchTemplateVersion](/intl.en-US/API Reference/Launch templates/CreateLaunchTemplateVersion.md)|Creates a version for the specified instance launch template.|
|[DeleteLaunchTemplate](/intl.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md)|Deletes an instance launch template.|
|[DeleteLaunchTemplateVersion](/intl.en-US/API Reference/Launch templates/DeleteLaunchTemplateVersion.md)|Deletes a version of the specified instance launch template. This operation does not delete the default version. To delete the default version, you must call the DeleteLaunchTemplate operation.|
|[DescribeLaunchTemplates](/intl.en-US/API Reference/Launch templates/DescribeLaunchTemplates.md)|Queries one or more available instance launch templates.|
|[DescribeLaunchTemplateVersions](/intl.en-US/API Reference/Launch templates/DescribeLaunchTemplateVersions.md)|Queries versions of instance launch templates.|
|[ModifyLaunchTemplateDefaultVersion](/intl.en-US/API Reference/Launch templates/ModifyLaunchTemplateDefaultVersion.md)|Modifies the default version of an instance launch template. If you do not specify a template version number when you create an ECS instance \(RunInstances\), the default version is used.|

## Auto provisioning groups

|API|Description|
|---|-----------|
|[CreateAutoProvisioningGroup](/intl.en-US/API Reference/Auto provisioning group/CreateAutoProvisioningGroup.md)|Creates an auto provisioning group.|
|[ModifyAutoProvisioningGroup](/intl.en-US/API Reference/Auto provisioning group/ModifyAutoProvisioningGroup.md)|Modifies the configurations of an auto provisioning group.|
|[DeleteAutoProvisioningGroup](/intl.en-US/API Reference/Auto provisioning group/DeleteAutoProvisioningGroup.md)|Deletes an auto provisioning group.|
|[DescribeAutoProvisioningGroupInstances](/intl.en-US/API Reference/Auto provisioning group/DescribeAutoProvisioningGroupInstances.md)|Queries ECS instances in an auto provisioning group.|
|[DescribeAutoProvisioningGroups](/intl.en-US/API Reference/Auto provisioning group/DescribeAutoProvisioningGroups.md)|Queries auto provisioning groups.|
|[DescribeAutoProvisioningGroupHistory](/intl.en-US/API Reference/Auto provisioning group/DescribeAutoProvisioningGroupHistory.md)|Queries the scheduling tasks of an auto provisioning group.|

## Elastic Block Storage \(EBS\)

|API|Description|
|---|-----------|
|[CreateDisk](/intl.en-US/API Reference/Disk/CreateDisk.md)|Creates a pay-as-you-go or subscription data disk. The data disk can be a basic disk, an ultra disk, a standard SSD, or an enhanced SSD \(ESSD\).|
|[DeleteDisk](/intl.en-US/API Reference/Disk/DeleteDisk.md)|Releases a pay-as-you-go data disk. The data disk can be a basic disk, an ultra disk, a standard SSD, or an ESSD.|
|[DescribeDisks](/intl.en-US/API Reference/Disk/DescribeDisks.md)|Queries one or more cloud disks and local disks that you have created.|
|[AttachDisk](/intl.en-US/API Reference/Disk/AttachDisk.md)|Attaches a pay-as-you-go data disk to an ECS instance.|
|[DetachDisk](/intl.en-US/API Reference/Disk/DetachDisk.md)|Detaches a pay-as-you-go disk from an ECS instance. The disk to be detached can be a basic disk, an ultra disk, or a standard SSD.|
|[ModifyDiskAttribute](/intl.en-US/API Reference/Disk/ModifyDiskAttribute.md)|Modifies the properties of a disk.|
|[ReplaceSystemDisk](/intl.en-US/API Reference/Disk/ReplaceSystemDisk.md)|Replaces the system disk or operating system of an ECS instance.|
|[ReInitDisk](/intl.en-US/API Reference/Disk/ReInitDisk.md)|Re-initializes a disk to restore it to the status when it was created.|
|[ResetDisk](/intl.en-US/API Reference/Disk/ResetDisk.md)|Rolls back a disk to a specified state based on a snapshot of the disk.|
|[ResizeDisk](/intl.en-US/API Reference/Disk/ResizeDisk.md)|Resizes a system disk or data disk.|
|[ModifyDiskChargeType](/intl.en-US/API Reference/Disk/ModifyDiskChargeType.md)|Modifies the billing methods of up to 16 disks attached to an instance.|
|[ModifyDiskSpec](/intl.en-US/API Reference/Disk/ModifyDiskSpec.md)|Upgrades the performance level of an ESSD.|

## Reserved instances

|API|Description|
|---|-----------|
|[PurchaseReservedInstancesOffering](/intl.en-US/API Reference/Reserved Instances/PurchaseReservedInstancesOffering.md)|Purchases a reserved instance to automatically offset the bills of pay-as-you-go instances.|
|[DescribeReservedInstances](/intl.en-US/API Reference/Reserved Instances/DescribeReservedInstances.md)|Queries the reserved instances that you have purchased.|
|[ModifyReservedInstances](/intl.en-US/API Reference/Reserved Instances/ModifyReservedInstances.md)|Modifies reserved instances.|

## Images

|API|Description|
|---|-----------|
|[CreateImage](/intl.en-US/API Reference/Images/CreateImage.md)|Creates a custom image. You can use the created image to create ECS instances \(RunInstances\) and replace system disks \(ReplaceSystemDisk\).|
|[ImportImage](/intl.en-US/API Reference/Images/ImportImage.md)|Imports an existing image file to ECS and has the image displayed as a custom image in the corresponding region.|
|[ExportImage](/intl.en-US/API Reference/Images/ExportImage.md)|Exports a custom image to an OSS bucket in the same region as the custom image.|
|[CopyImage](/intl.en-US/API Reference/Images/CopyImage.md)|Copies a custom image from one region to another. This operation helps you deploy and copy ECS instances across regions.|
|[CancelCopyImage](/intl.en-US/API Reference/Images/CancelCopyImage.md)|Cancels an ongoing image copying \(CopyImage\) task.|
|[DescribeImages](/intl.en-US/API Reference/Images/DescribeImages.md)|Queries available images.|
|[DeleteImage](/intl.en-US/API Reference/Images/DeleteImage.md)|Deletes a custom image.|
|[DescribeImageSharePermission](/intl.en-US/API Reference/Images/DescribeImageSharePermission.md)|Queries the accounts with which a custom image is shared. The response can be displayed by page. By default, ten entries are displayed on each page.|
|[ModifyImageAttribute](/intl.en-US/API Reference/Images/ModifyImageAttribute.md)|Modifies the name and description of a custom image.|
|[ModifyImageSharePermission](/intl.en-US/API Reference/Images/ModifyImageSharePermission.md)|Manages the share permission of an image. After you share a custom image with another Alibaba Cloud account, the account owner can use the shared image to create ECS instances \(RunInstances\) or replace system disks of ECS instances \(ReplaceSystemDisk\).|
|[DescribeImageSupportInstanceTypes](/intl.en-US/API Reference/Images/DescribeImageSupportInstanceTypes.md)|Queries the instance types supported by a specific image.|

## Snapshots

|API|Description|
|---|-----------|
|[CreateSnapshot](/intl.en-US/API Reference/Snapshots/CreateSnapshot.md)|Creates a snapshot for a disk.|
|[CreateAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md)|Creates an automatic snapshot policy.|
|[ApplyAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/ApplyAutoSnapshotPolicy.md)|Applies an automatic snapshot policy to one or more disks. If the target disk has an automatic snapshot policy applied, you can call this API operation to replace the automatic snapshot policy.|
|[CopySnapshot](/intl.en-US/API Reference/Snapshots/CopySnapshot.md)|Copies a snapshot from one region to another.|
|[DeleteSnapshot](/intl.en-US/API Reference/Snapshots/DeleteSnapshot.md)|Deletes the specified snapshot. If you call this operation to delete a snapshot that is being created, the task of creating the snapshot is canceled.|
|[CancelAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/CancelAutoSnapshotPolicy.md)|Removes the automatic snapshot policy of one or more disks.|
|[DeleteAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/DeleteAutoSnapshotPolicy.md)|Deletes an automatic snapshot policy. After you delete an automatic snapshot policy, the policy will no longer be applied to the disks on which it previously took effect.|
|[DescribeAutoSnapshotPolicyEX](/intl.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEX.md)|Queries the automatic snapshot policies that you have created.|
|[DescribeSnapshots](/intl.en-US/API Reference/Snapshots/DescribeSnapshots.md)|Queries all snapshots of an ECS instance or a disk. Request parameters such as InstanceId, DiskId, and SnapshotIds act as filter conditions and have a Boolean AND relationship. These parameters are not required.|
|[DescribeSnapshotLinks](/intl.en-US/API Reference/Snapshots/DescribeSnapshotLinks.md)|Queries the snapshot chain of a disk. A snapshot chain is a chain of all the snapshots of a disk. A disk corresponds to a snapshot chain.|
|[ModifyAutoSnapshotPolicyEx](/intl.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md)|Modifies an automatic snapshot policy. After you modify an automatic snapshot policy, the new policy takes effect immediately on the disks to which the policy was applied.|
|[DescribeSnapshotsUsage](/intl.en-US/API Reference/Snapshots/DescribeSnapshotsUsage.md)|Queries the number of snapshots that are stored in a region and the total size of the snapshots.|
|[DescribeSnapshotPackage](/intl.en-US/API Reference/Snapshots/DescribeSnapshotPackage.md)|Queries the Object Storage Service \(OSS\) storage plans that you have purchased in a region. Storage plans can be used to offset the storage space of snapshots.|
|[ModifySnapshotAttribute](/intl.en-US/API Reference/Snapshots/ModifySnapshotAttribute.md)|Modifies the name and description of a snapshot.|

## Security groups

|API|Description|
|---|-----------|
|[CreateSecurityGroup](/intl.en-US/API Reference/Security groups/CreateSecurityGroup.md)|Creates a security group. For a newly created security group, only ECS instances in the security group can access each other by default. Access requests to the security group from outside are restricted. To allow access requests from resources over the Internet or from instances in other security groups, you can call the AuthorizeSecurityGroup operation to grant access permissions to those resources or instances.|
|[AuthorizeSecurityGroup](/intl.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md)|Creates an inbound security group rule. This operation allows or denies the inbound traffic from other devices to ECS instances in the security group.|
|[AuthorizeSecurityGroupEgress](/intl.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md)|Creates an outbound security group rule. This operation allows or denies the outbound traffic from the instances in the security group to other devices.|
|[RevokeSecurityGroup](/intl.en-US/API Reference/Security groups/RevokeSecurityGroup.md)|Deletes an inbound security group rule and revokes inbound permissions specified by this rule.|
|[RevokeSecurityGroupEgress](/intl.en-US/API Reference/Security groups/RevokeSecurityGroupEgress.md)|Deletes an outbound security group rule and revokes outbound permissions specified by this rule.|
|[JoinSecurityGroup](/intl.en-US/API Reference/Security groups/JoinSecurityGroup.md)|Adds an ECS instance to a specific security group.|
|[LeaveSecurityGroup](/intl.en-US/API Reference/Security groups/LeaveSecurityGroup.md)|Removes an ECS instance from a specific security group.|
|[DeleteSecurityGroup](/intl.en-US/API Reference/Security groups/DeleteSecurityGroup.md)|Deletes a security group.|
|[DescribeSecurityGroupAttribute](/intl.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md)|Queries the rules of a security group.|
|[DescribeSecurityGroups](/intl.en-US/API Reference/Security groups/DescribeSecurityGroups.md)|Queries the basic information of your security groups, such as security group IDs and descriptions. The security groups are displayed in descending order by security group ID.|
|[DescribeSecurityGroupReferences](/intl.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md)|Queries whether a specific security group and other security groups grant access permissions to each other.|
|[ModifySecurityGroupAttribute](/intl.en-US/API Reference/Security groups/ModifySecurityGroupAttribute.md)|Modifies the properties of a security group, including the name and description of the security group.|
|[ModifySecurityGroupPolicy](/intl.en-US/API Reference/Security groups/ModifySecurityGroupPolicy.md)|Modifies the access control policy of a security group.|
|[ModifySecurityGroupRule](/intl.en-US/API Reference/Security groups/ModifySecurityGroupRule.md)|Modifies the description of inbound rules of a security group. You can call the AuthorizeSecurityGroup operation to create an inbound security group rule.|
|[ModifySecurityGroupEgressRule](/intl.en-US/API Reference/Security groups/ModifySecurityGroupEgressRule.md)|Modifies the description of outbound rules of a security group. You can call the AuthorizeSecurityGroupEgress operation to create an outbound security group rule.|

## Deployment sets

|API|Description|
|---|-----------|
|[CreateDeploymentSet](/intl.en-US/API Reference/Deployment sets/CreateDeploymentSet.md)|Creates a deployment set in a specified region.|
|[DeleteDeploymentSet](/intl.en-US/API Reference/Deployment sets/DeleteDeploymentSet.md)|Deletes a deployment set.|
|[ModifyDeploymentSetAttribute](/intl.en-US/API Reference/Deployment sets/ModifyDeploymentSetAttribute.md)|Modifies the name and description of a deployment set.|
|[DescribeDeploymentSets](/intl.en-US/API Reference/Deployment sets/DescribeDeploymentSets.md)|Queries the attributes of one or more deployment sets.|

## SSH key pairs

|API|Description|
|---|-----------|
|[CreateKeyPair](/intl.en-US/API Reference/SSH key pairs/CreateKeyPair.md)|Creates an SSH key pair. The system stores the public key and returns the unencrypted private key. The private key is encoded by using PEM and is in the PKCS\#8 format. You must store the private key on your own and ensure its confidentiality.|
|[ImportKeyPair](/intl.en-US/API Reference/SSH key pairs/ImportKeyPair.md)|Imports the public key of an RSA-encrypted key pair that you created by using a third-party tool. After the key pair is imported, the public key is stored in Alibaba Cloud. You must store the private key on your own and ensure its confidentiality.|
|[AttachKeyPair](/intl.en-US/API Reference/SSH key pairs/AttachKeyPair.md)|Attaches an SSH key pair to one or more Linux instances.|
|[DetachKeyPair](/intl.en-US/API Reference/SSH key pairs/DetachKeyPair.md)|Detaches an SSH key pair from one or more Linux instances.|
|[DeleteKeyPairs](/intl.en-US/API Reference/SSH key pairs/DeleteKeyPairs.md)|Deletes one or more SSH key pairs. The entry of a deleted SSH key pair is removed from the database. However, the instance to which the SSH key pair is attached can still use the SSH key pair, and the key pair name is still displayed on the instance details page.|
|[DescribeKeyPairs](/intl.en-US/API Reference/SSH key pairs/DescribeKeyPairs.md)|Queries one or more key pairs.|

## Network

|API|Description|
|---|-----------|
|[ModifyInstanceVpcAttribute](/intl.en-US/API Reference/Networks/ModifyInstanceVpcAttribute.md)|Modifies the VPC properties of an ECS instance.|
|[AllocatePublicIpAddress](/intl.en-US/API Reference/Networks/AllocatePublicIpAddress.md)|Assigns a public IP address to an ECS instance.|
|[ConvertNatPublicIpToEip](/intl.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md)|Converts the public IP address of a VPC-type ECS instance to an elastic IP address \(EIP\).|
|[AttachClassicLinkVpc](/intl.en-US/API Reference/Networks/AttachClassicLinkVpc.md)|Connects a classic network-type instance to a VPC. This way, the instance can communicate with cloud resources in the VPC over the internal network.|
|[DetachClassicLinkVpc](/intl.en-US/API Reference/Networks/DetachClassicLinkVpc.md)|Cancels the connection between a classic network-type instance and a VPC \(ClassicLink\). After the ClassicLink is canceled, the classic network-type instance cannot communicate with the VPC.|
|[DescribeBandwidthLimitation](/intl.en-US/API Reference/Networks/DescribeBandwidthLimitation.md)|Queries available bandwidth resources.|
|[DescribeClassicLinkInstances](/intl.en-US/API Reference/Networks/DescribeClassicLinkInstances.md)|Queries one or more classic network-type instances that are connected to VPCs.|
|[ModifyInstanceNetworkSpec](/intl.en-US/API Reference/Networks/ModifyInstanceNetworkSpec.md)|Modifies the bandwidth configurations of an instance. If necessary, you can modify the network specifications of an instance to improve network performance.|

## ENIs

|API|Description|
|---|-----------|
|[CreateNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md)|Creates an elastic network interface \(ENI\).|
|[AttachNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface.md)|Binds an ENI to a VPC-type ECS instance.|
|[DetachNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md)|Unbinds an ENI from an ECS instance.|
|[DeleteNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md)|Deletes an ENI.|
|[DescribeNetworkInterfaces](/intl.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md)|Queries available ENIs.|
|[ModifyNetworkInterfaceAttribute](/intl.en-US/API Reference/Elastic network interfaces/ModifyNetworkInterfaceAttribute.md)|Modifies the properties of an ENI, such as the name, description, and security group of the ENI.|
|[AssignPrivateIpAddresses](/intl.en-US/API Reference/Elastic network interfaces/AssignPrivateIpAddresses.md)|Assigns one or more secondary private IP addresses to an ENI. You can specify private IP addresses within the CIDR block of the VSwitch that hosts the ENI. You can also specify the number of private IP addresses for ECS to assign them automatically.|
|[UnassignPrivateIpAddresses](/intl.en-US/API Reference/Elastic network interfaces/UnassignPrivateIpAddresses.md)|Deletes one or more secondary private IP addresses from an ENI.|

## System events

|API|Description|
|---|-----------|
|[DescribeDisksFullStatus](/intl.en-US/API Reference/System event/DescribeDisksFullStatus.md)|Queries the full status information of one or more EBS devices.|
|[DescribeInstancesFullStatus](/intl.en-US/API Reference/System event/DescribeInstancesFullStatus.md)|Queries the full status information of one or more ECS instances. The full status information includes the instance status and the status of instance system events. The instance status is the lifecycle status of an instance. The status of instance system events is the health status of maintenance events.|
|[DescribeInstanceHistoryEvents](/intl.en-US/API Reference/System event/DescribeInstanceHistoryEvents.md)|Queries the system events of a specific instance. Inactive historical system events are queried by default.|
|[CancelSimulatedSystemEvents](/intl.en-US/API Reference/System event/CancelSimulatedSystemEvents.md)|Cancels one or more simulated system events that are in the Scheduled or Executing state. After you cancel a simulated system event, the simulated event is in the Canceled state.|
|[CreateSimulatedSystemEvents](/intl.en-US/API Reference/System event/CreateSimulatedSystemEvents.md)|Schedules simulated system events for one or more ECS instances. The simulated system events do not occur in the actual system and the simulation does not affect ECS instances.|
|[AcceptInquiredSystemEvent](/intl.en-US/API Reference/System event/AcceptInquiredSystemEvent.md)|Accepts the default operation for a system event in the Inquiring state and authorizes the system to perform the default operation.|

## O&M and monitoring

|API|Description|
|---|-----------|
|[DescribeDiskMonitorData](/intl.en-US/API Reference/Operations and monitoring/DescribeDiskMonitorData.md)|Queries the monitoring data of a disk over the specified period of time.|
|[DescribeInstanceMonitorData](/intl.en-US/API Reference/Operations and monitoring/DescribeInstanceMonitorData.md)|Queries the monitoring data about an ECS instance. You can query the vCPU utilization, burstable instance credits, inbound data traffic, outbound data traffic, and average bandwidth of the instance.|
|[GetInstanceScreenshot](/intl.en-US/API Reference/Operations and monitoring/GetInstanceScreenshot.md)|Obtains the screenshot information of an ECS instance.|
|[GetInstanceConsoleOutput](/intl.en-US/API Reference/Operations and monitoring/GetInstanceConsoleOutput.md)|Obtains the command line output of an ECS instance. The returned command output is encoded in Base64.|
|[DescribeEniMonitorData](/intl.en-US/API Reference/Operations and monitoring/DescribeEniMonitorData.md)|Queries the traffic consumed by a secondary ENI over the specified period of time.|
|[RedeployInstance](/intl.en-US/API Reference/Operations and monitoring/RedeployInstance.md)|Redeploys an ECS instance when the instance receives an event notification.|
|[DescribeSnapshotMonitorData](/intl.en-US/API Reference/Operations and monitoring/DescribeSnapshotMonitorData.md)|Queries the monitoring data on snapshot capacity changes in a region over the past 30 days.|
|[DescribeInstanceMaintenanceAttributes](/intl.en-US/API Reference/Operations and monitoring/DescribeInstanceMaintenanceAttributes.md)|Queries the maintenance properties of an instance.|
|[ModifyInstanceMaintenanceAttributes](/intl.en-US/API Reference/Operations and monitoring/ModifyInstanceMaintenanceAttributes.md)|Modifies the maintenance properties of an instance.|

## Cloud Assistant

|API|Description|
|---|-----------|
|[CreateCommand](/intl.en-US/API Reference/Cloud assistant/CreateCommand.md)|Creates a Cloud Assistant command.|
|[InvokeCommand](/intl.en-US/API Reference/Cloud assistant/InvokeCommand.md)|Triggers a Cloud Assistant command for one or more ECS instances.|
|[StopInvocation](/intl.en-US/API Reference/Cloud assistant/StopInvocation.md)|Stops the process of a running Cloud Assistant command on one or more ECS instances.|
|[DeleteCommand](/intl.en-US/API Reference/Cloud assistant/DeleteCommand.md)|Deletes a Cloud Assistant command.|
|[DescribeCommands](/intl.en-US/API Reference/Cloud assistant/DescribeCommands.md)|Queries Cloud Assistant commands that you have created. If you specify only the Action and RegionId parameters, the system queries all available commands by default.|
|[DescribeInvocations](/intl.en-US/API Reference/Cloud assistant/DescribeInvocations.md)|Queries the execution list and status of Cloud Assistant commands in the last two weeks.|
|[DescribeInvocationResults](/intl.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md)|Queries the execution results of Cloud Assistant commands on ECS instances.|
|[DescribeCloudAssistantStatus](/intl.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md)|Queries whether the Cloud Assistant client is installed on one or more ECS instances.|
|[InstallCloudAssistant](/intl.en-US/API Reference/Cloud assistant/InstallCloudAssistant.md)|Installs the Cloud Assistant client on one or more ECS instances.|
|[RunCommand](/intl.en-US/API Reference/Cloud assistant/RunCommand.md)|Creates a Cloud Assistant command of the shell, PowerShell, or batch type, and then run the command on one or more ECS instances.|

## HPC clusters

|API|Description|
|---|-----------|
|[DeleteHpcCluster](/intl.en-US/API Reference/HPC clusters/DeleteHpcCluster.md)|Deletes an Alibaba Cloud HPC \(HPC\) cluster.|
|[CreateHpcCluster](/intl.en-US/API Reference/HPC clusters/CreateHpcCluster.md)|Creates an HPC cluster.|
|[DescribeHpcClusters](/intl.en-US/API Reference/HPC clusters/DescribeHpcClusters.md)|Queries the available HPC clusters. Specified request parameters are used as filters with logical AND \(&&\) relations. The request parameters are not dependent on each other.|
|[ModifyHpcClusterAttribute](/intl.en-US/API Reference/HPC clusters/ModifyHpcClusterAttribute.md)|Modifies the description of an HPC cluster.|

## Tags

|API|Description|
|---|-----------|
|[TagResources](/intl.en-US/API Reference/Tags/TagResources.md)|Creates and binds tags to specified ECS resources.|
|[ListTagResources](/intl.en-US/API Reference/Tags/ListTagResources.md)|Queries the tags that have been bound to one or more ECS resources.|
|[UntagResources](/intl.en-US/API Reference/Tags/UntagResources.md)|Unbinds tags from the specified ECS resources.|

## Regions

|API|Description|
|---|-----------|
|[DescribeRegions](/intl.en-US/API Reference/Regions/DescribeRegions.md)|Queries available Alibaba Cloud regions.|
|[DescribeZones](/intl.en-US/API Reference/Regions/DescribeZones.md)|Queries the zones within a specific region.|
|[DescribeAvailableResource](/intl.en-US/API Reference/Regions/DescribeAvailableResource.md)|Queries resources in a specific zone. For example, you can query resources before you create ECS instances \(RunInstances\) or modify instance specifications \(ModifyInstanceSpec\) in a specific zone.|
|[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)|Queries available resources in a specific zone when you upgrade or downgrade instance types or system disks.|

## Other operations

|API|Description|
|---|-----------|
|[CancelTask](/intl.en-US/API Reference/Others/CancelTask.md)|Cancels a running task. You can cancel the running tasks generated by calling the ImportImage and ExportImage operations.|
|[DescribeTasks](/intl.en-US/API Reference/Others/DescribeTasks.md)|Queries the progress of one or more asynchronous requests.|
|[DescribeTaskAttribute](/intl.en-US/API Reference/Others/DescribeTaskAttribute.md)|Queries the detailed information of an asynchronous task. You can query the asynchronous tasks generated by calling the ImportImage and ExportImage operations.|
|[DescribeAccountAttributes](/intl.en-US/API Reference/Others/DescribeAccountAttributes.md)|Queries the quotas of ECS resources that you can create in a region. You can query the maximum numbers of security groups, ENIs, pay-as-you-go instance vCPUs, preemptible instance vCPUs, and dedicated hosts that you can create in a region. You can also obtain the information such as network types available in the region and whether an account has passed real-name verification.|
|[JoinResourceGroup](/intl.en-US/API Reference/Others/JoinResourceGroup.md)|Adds an ECS resource or service to a resource group.|
|[DescribePrice](/intl.en-US/API Reference/Others/DescribePrice.md)|Queries the most recent prices of ECS resources. This operation is in internal preview.|
|[DescribeDemands](/intl.en-US/API Reference/Others/DescribeDemands.md)|Queries the delivery and usage status of filed resources.|

