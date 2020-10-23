---
keyword: [Alibaba Cloud, ECS, change configurations, change resource configurations, change instance type, modify bandwidth, change the billing method for network usage]
---

# Overview of instance upgrade and downgrade

If the current instance configurations of an instance cannot meet your business needs, you can change its instance type \(vCPUs and memory\), bandwidth configurations, and the billing method of its data disks. This topic describes methods to change the configurations of an ECS instance.

## Change instance types

The vCPUs and memory size of instance types are predefined. To change the instance type of an instance, you must change the number of vCPUs and memory size together. You cannot modify only vCPUs or memory size.

Before you change the instance type of an instance, make sure that you know which instance types and instance families support changes in instance type. The instance types to which you can upgrade or downgrade are displayed on the configuration change page.

-   For more information about instance types, see [Instance families](/intl.en-US/Instance/Instance families.md).
-   For information about instance families that support instance type changes, see [Change instance types of instances](/intl.en-US/Instance/Change configurations/Upgrade configurations/Change instance types of instances.md).

The following table describes the change methods best suited for different billing methods applied to your instances.

|Billing method|Change time|Effective time|Operation|
|--------------|-----------|--------------|---------|
|Subscription|Before the instance expires|After you restart the instance|-   [Upgrade configurations of subscription instances](/intl.en-US/Instance/Change configurations/Upgrade configurations/Upgrade configurations of subscription instances.md)
-   [Downgrade the instance types of subscription instances](/intl.en-US/Instance/Change configurations/Upgrade configurations/Downgrade the instance types of subscription instances.md) |
|Within 15 days before the instance expires|After you restart the instance and within the first seven days of the new subscription duration|[Downgrade instance configurations during renewal](/intl.en-US/Pricing/Renew instances/Downgrade instance configurations during renewal.md)|
|Pay-as-you-go|N/A|After you restart the instance|[Change the instance type of a pay-as-you-go instance](/intl.en-US/Instance/Change configurations/Upgrade configurations/Change the instance type of a pay-as-you-go instance.md)|

## Change the billing method for network usage

You can use different methods to change the billing method for network usage based on the public IP address type. The following table lists the methods.

|Public IP address type|Effective time|Operation|
|----------------------|--------------|---------|
|Assigned public IP address|Immediately|[Change the billing method for network usage]()|
|Elastic IP address \(EIP\)|Immediately|[Modify the bandwidth of an EIP](/intl.en-US/Instance/Change configurations/Downgrade configurations/Modify the bandwidth of an Elastic IP address.md)|

## Modify public bandwidth

The methods you can use to modify the public bandwidth of an instance depend on your business needs and the billing method of the instance. The following table lists the methods.

If you set the public bandwidth to 0 Mbit/s when you modify the public bandwidth, after the modification, you can determine whether to retain the public IP address based on the network type of the instance:

-   For a VPC-type ECS instance, its public IP address is released immediately.
-   For a classic network-type instance, it cannot access the Internet but its public IP address is retained.

You can set the public bandwidth to a non-zero value when you create an instance. The system will allocate a public IP address to your instance. If you do not assign a public IP address when you create an instance, the instance has no public bandwidth. You can change the public bandwidth from 0 Mbit/s to a non-zero value by using the configuration upgrade feature to assign a public IP address to the instance.

|Public IP address type|Application scope|Effective time|Reference|
|----------------------|-----------------|--------------|---------|
|Assigned public IP address|Modify the basic public bandwidth for a subscription instance|Immediately|[Modify the bandwidth configurations of subscription instances](/intl.en-US/Instance/Change configurations/Downgrade configurations/Downgrade the public bandwidths of subscription instances.md)|
|Modify the basic public bandwidth for a subscription instance during renewal|After the new subscription duration starts|[Downgrade instance configurations during renewal](/intl.en-US/Pricing/Renew instances/Downgrade instance configurations during renewal.md)|
|Modify the basic public bandwidth of a pay-as-you-go instance|Immediately|[Modify the bandwidth configurations of pay-as-you-go instances](/intl.en-US/Instance/Change configurations/Downgrade configurations/Change the Internet bandwidth of a pay-as-you-go instance.md)|
|EIP|Modify the bandwidth of an EIP for a subscription or pay-as-you-go instance|Immediately|[Modify the bandwidth of an EIP](/intl.en-US/Instance/Change configurations/Downgrade configurations/Modify the bandwidth of an Elastic IP address.md)|

**Note:** When you upgrade the public bandwidth of a classic network-type instance from 0 Mbit/s for the first time, you must restart the instance for the new configurations to take effect. You can restart the instance by using the ECS console or by calling the RebootInstance operation.

## Change the billing methods of data disks

Only pay-as-you-go data disks can be attached to pay-as-you-go instances. Therefore, you can only change the billing methods of data disks for subscription instances.

|Operate time|Effective time|Operation|
|------------|--------------|---------|
|Before the instance expires|Immediately|[Change billing methods of disks](/intl.en-US/Pricing/Change the billing method/Change the billing method of a subscription disk.md)|
|Within the 15 days before the instance expires or after the instance expires but before it is released|Immediately|[Downgrade instance configurations during renewal](/intl.en-US/Pricing/Renew instances/Downgrade instance configurations during renewal.md)|

## FAQ

The following section provides answers to the FAQ about upgrading and downgrading the configurations of instances. For more information, see [Instance FAQ](/intl.en-US/Instance/ECS instance FAQ.md).

-   How is the cost of an instance upgrade calculated?

    When you upgrade the instance type and configurations of an instance, the cost and its calculation method are displayed in the ECS console. You can also view the billing details on the [Account Overview](https://expense.console.aliyun.com/) page.

-   Will my cloud service configurations be affected when I upgrade ECS instances?

    Pay-as-you-go instances must be stopped before they can be upgraded. After you upgrade the instance type of a subscription instance, you must restart the instance for the new configurations to take effect. The upgrade operation will interrupt services running on the instance for a short period of time. We recommend that you upgrade instances during off-peak hours. Instances can seamlessly resume services after upgrades without having to reconfigure their environment.


