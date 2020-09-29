---
keyword: [pay-as-you-go, No Fees for Stopped Instances \(VPC-Connected\), computing resource, public IP address, retain and bill, stop mode]
---

# No Fees for Stopped Instances \(VPC-Connected\)

The No Fees for Stopped Instances \(VPC-Connected\) feature allows some ECS resources to be recycled while retaining ECS instances, reducing upkeep costs. It does not stop consumed resources from being billed.

## Prerequisites

The No Fees for Stopped Instances \(VPC-Connected\) feature is applicable to ECS instances that meet the following requirements:

-   The network type of the instances is VPC.
-   The instances are pay-as-you-go instances.

    You can change the billing method of an instance from subscription to pay-as-you-go. For more information, see [Change the billing method of instances from subscription to pay-as-you-go](/intl.en-US/Pricing/Change the billing method/Change the billing method of instances from subscription to pay-as-you-go.md).

-   The instance family is not attached with local disks.

    Instance families attached with local disks do not support No Fees for Stopped Instances \(VPC-Connected\). These instance families include d1, d1ne, i1, i2, i2g, and gn5. For more information, see the Local storage \(GiB\) column in [Instance families](/intl.en-US/Instance/Instance families.md).


The No Fees for Stopped Instances \(VPC-Connected\) feature is disabled by default. For information about how to enable this feature, see the [Enable the No Fees for Stopped Instances \(VPC-Connected\) feature](#default) section.

## Applicable resources

This feature recycles some resources while retaining ECS instances to reduce the overall costs.

-   The No Fees for Stopped Instances \(VPC-Connected\) feature is applicable to the following resources:
    -   ECS instances \(including vCPUs and memory\)
    -   Public IP addresses and bandwidth
-   The No Fees for Stopped Instances \(VPC-Connected\) feature is not applicable to some ECS resources. The following list provides some examples of these resources:
    -   System disks
    -   Data disks attached to ECS instances
    -   Elastic IP addresses \(EIPs\) and bandwidth
    -   Images
    -   Snapshots

## Trigger conditions

After the No Fees for Stopped Instances \(VPC-Connected\) feature is enabled, it is triggered only when the instance is stopped due to one of the following reasons:

-   Operations in the ECS console. For more information, see [Stop an instance](/intl.en-US/Instance/Manage instances/Stop an instance.md).
-   API requests initiated by using Alibaba Cloud CLI or SDKs. For more information, see [StopInstance](/intl.en-US/API Reference/Instances/StopInstance.md).
-   Overdue payments.

**Note:** If you stop an ECS instance from within the operating system, the No Fees for Stopped Instances \(VPC-Connected\) feature is not triggered.

If an ECS instance is in the start period, the No Fees for Stopped Instances \(VPC-Connected\) feature cannot be triggered. The start period is the time it takes for a new instance that is started for the first time to enter the Running state from the Stopped state. For more information, see [ECS instance lifecycle](/intl.en-US/Instance/ECS instance lifecycle.md).

## Impacts

After the No Fees for Stopped Instances \(VPC-Connected\) feature is triggered for an ECS instance, the ECS instance \(including vCPUs and memory\) and its public IP address are recycled. You are no longer charged for these resources. However, the following risks exist:

-   The stopped resources are recycled and the instance may fail to restart due to insufficient resources. In this case, you can try again later or switch to another instance type. For more information, see [Change the instance type of a pay-as-you-go instance](/intl.en-US/Instance/Change configurations/Change configurations of Pay-As-You-Go instances/Change the instance type of a pay-as-you-go instance.md).

    **Note:** We recommend that you restart the instance in advance to ensure that resources are sufficient for the instance to start, avoiding service interruptions caused by instance start failures.

-   Because the public IP address has been recycled, the public IP address may change after the instance is restarted. However, the private IP address remains unchanged.

    **Note:** If your application depends on a specific public IP address, we recommend that you disable the No Fees for Stopped Instances \(VPC-Connected\) feature or convert the public IP address to an EIP. For more information, see [Disable the No Fees for Stopped Instances \(VPC-Connected\) feature](#section_4h6_utd_2yr) or [Convert the public IP address of a VPC-type instance to an Elastic IP address](/intl.en-US/Network/Change IPv4 addresses/Convert the public IP address of a VPC-type instance to an Elastic IP address.md).

-   For burstable instances, the current CPU credit balance is cleared and the instances stop earning CPU credits. After you restart the burstable instances, they begin to earn CPU credits again. For more information about CPU credits of burstable instances, see [CPU credits](/intl.en-US/Instance/Instance type families/Burstable performance instances/Overview.md).

In some cases, you may need to restart your instances multiple times within a short amount of time. We recommend that you disable the No Fees for Stopped Instances \(VPC-Connected\) feature to ensure that the instances can be started and run normally. You can disable this feature in the following scenarios:

-   [Replace the system disk](/intl.en-US/Block Storage/Cloud disks/Change the operating system/Replace the system disk (public images).md) \([ReplaceSystemDisk](/intl.en-US/API Reference/Disk/ReplaceSystemDisk.md)\)
-   [Roll back a disk](/intl.en-US/Block Storage/Cloud disks/Roll back a disk.md) \([ResetDisk](/intl.en-US/API Reference/Disk/ResetDisk.md)\)
-   [Reinitialize a system disk](/intl.en-US/Block Storage/Cloud disks/Reinitialize a cloud disk/Reinitialize a system disk.md) \([ReInitDisk](/intl.en-US/API Reference/Disk/ReInitDisk.md)\)

For an instance that is stopped due to an overdue payment, if you clear the overdue payment within the specified time and reactivate the ECS instance, the retention of the public IP address is determined by the status of the No Fees for Stopped Instances \(VPC-Connected\) feature:

-   When the feature is enabled: After the instance is stopped due to an overdue payment, it enters the No Fees for Stopped Instances state. Its vCPUs, memory, and public IP address are automatically released and the public IP address may change after the instance is reactivated.
-   When the feature is disabled: After the instance is stopped due to an overdue payment, the billing of the instance is stopped. Its vCPUs and memory are automatically released. However, the public IP address is retained and does not change after the instance is reactivated.

**Note:** ECS instances do not remain in the Stopped state after a payment becomes overdue in your account. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Billing methods/Pay-as-you-go.md).

## Enable the No Fees for Stopped Instances \(VPC-Connected\) feature

The No Fees for Stopped Instances \(VPC-Connected\) feature is disabled by default to avoid unexpected impacts on your applications. Enable the No Fees for Stopped Instances \(VPC-Connected\) feature after you make sure that it is suitable for your applications. For more information, see [Impacts](/intl.en-US/Pricing/Billing methods/No Fees for Stopped Instances (VPC-Connected).md).

This section describes how to enable the No Fees for Stopped Instances \(VPC-Connected\) feature for all applicable instances in your account. The instances will enter the No Fees for Stopped Instances state when they are stopped. For more information, see [Prerequisites](/intl.en-US/Pricing/Billing methods/No Fees for Stopped Instances (VPC-Connected).md).

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the **Common Settings** section of the **Overview** page, click **Custom Settings**.

    ![No Fees for Stopped Instances (VPC-Connected)](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5091909951/p87545.png)

3.  Turn on the **No Fees for Stopped Instances \(VPC-Connected\)** switch.

4.  In the message that appears, read the note and click **OK**.

5.  In the Custom Settings dialog box, click **OK**.


## Disable the No Fees for Stopped Instances \(VPC-Connected\) feature

This section describes how to disable the No Fees for Stopped Instances \(VPC-Connected\) feature for all applicable instances in your account. The instances will not enter the No Fees for Stopped Instances state when they are stopped.

If an ECS instance is in the No Fees for Stopped Instances state, its vCPUs, memory, and public IP address are already recycled. Therefore, after the No Fees for Stopped Instances \(VPC-Connected\) feature is disabled, no fees are charged for the vCPUs and memory until these resources are reassigned after the instance is restarted. The status of the IP address is subject to the type of the IP address.

-   If the instance uses a public IP address before it is stopped, a new public IP address is assigned to the instance.
-   If the ECS instance is associated with an EIP before it is stopped, the EIP remains unchanged.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the **Common Settings** section of the **Overview** page, click **Custom Settings**.

    ![No Fees for Stopped Instances (VPC-Connected)](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5091909951/p87545.png)

3.  Turn off the **No Fees for Stopped Instances \(VPC-Connected\)** switch.

4.  In the message that appears, read the note and click **OK**.

5.  In the Custom Settings dialog box, click **OK**.


## Configure a single instance to enter the No Fees for Stopped Instances \(VPC-Connected\) state when it is stopped

Regardless of whether the No Fees for Stopped Instances \(VPC-Connected\) feature is enabled, you can still configure the Stop mode when you stop a single instance. For more information, see [Stop an instance](/intl.en-US/Instance/Manage instances/Stop an instance.md).

-   If you select **Retain Instance and Continue Charging After Instance Is Stopped**, the instance enters the Keep Stopped Instances and Continue Billing state.
-   If you select **No Charges After Instance Is Stopped**, the instance enters the No Fees for Stopped Instances state.

![No Charges After Instance Is Stopped](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6091909951/p52884.png)

## References

You can also use the scheduled startup and shutdown feature of Operation Orchestration Service \(OOS\) to automatically manage the startup and shutdown time of multiple ECS instances. You can combine this feature with the No Fees for Stopped Instances \(VPC-Connected\) feature to reduce costs. For more information, see [Scheduled startup and shutdown]().

