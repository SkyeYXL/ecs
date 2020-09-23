---
keyword: [subscription, expiration of ECS resources, data retention, subscription, refund, weekly subscription, billable resources]
---

# Subscription

Subscription is a billing method that allows you to use resources only after you pay for them. By using the subscription billing method, you can reserve resources in advance and reduce costs with discounted rates. This topic describes the billing rules for subscription ECS resources.

## Overview

Before you use subscription resources, you must create a subscription ECS instance. The following figure shows the subscription duration options that you can choose for your ECS instance.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9790359951/p54963.png)

During instance creation, resources are billed separately to generate the total price. You can use subscription resources only after you pay the total price. For more information about how prices are calculated, see [Billing](#section_oqg_bdk_0r1).

After a subscription ECS instance is created, you can change its configurations or resize subscription cloud disks attached to the instance. For more information, see [Overview of instance upgrade and downgrade](/intl.en-US/Instance/Change configurations/Overview of instance upgrade and downgrade.md) and [Overview](/intl.en-US/Block Storage/Resize cloud disks/Overview.md).

After a subscription period expires, you can renew your ECS instance to continue to use it. For more information, see [t9590.md\#](/intl.en-US/Pricing/Renew instances/Overview.md).

## Applicable resources

When you create an ECS instance, you must configure Elastic Block Storage \(EBS\), the image, and the network type. The following table describes the ECS resources that support the subscription billing method.

|Resource|Description|
|--------|-----------|
|ECS instance|When you create an ECS instance, you must specify whether to use the subscription billing method.|
|Image|The image that you selected when create a subscription instance also uses the subscription billing method.|
|Cloud disk|Cloud disks created along with subscription ECS instances also use the subscription billing method. After a subscription ECS instance is created, you can create subscription disks for the instance or attach pay-as-you-go disks that are separately created to the instance. For more information, see [Create a subscription disk]() and [Attach a data disk](/intl.en-US/Block Storage/Cloud disks/Attach a data disk.md). |
|Public bandwidth \(pay-by-bandwidth\)|If you select pay-by-bandwidth as the billing method for network usage when you create a subscription ECS instance, the bandwidth is also billed on a subscription basis. For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md).|

You can view the total price of the preceding resources in the lower-left part of the instance buy page, as shown in the following figure.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9790359951/p54970.png)

-   **Total** price is the price of the following resources:
    -   ECS instance
    -   Cloud disk
    -   Public bandwidth \(pay-by-bandwidth\)

        **Note:** If you select pay-by-traffic as the billing method for network usage, the total price does not include the price for public bandwidth. For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md).

-   **Marketplace Image Fees** indicates that you selected a paid image.

You can use the ECS [TCO Calculator](https://cart.alibabacloud.com/calculator) to analyze your cloud migration costs.

## Billing

The billing cycle of a subscription instance is the time commitment you made when you purchased the instance \(based on UTC+8:00\). The cycle starts from the time when the purchased subscription resource is activated or renewed \(accurate to the second\) and ends at 00:00:00 the next day after the expiration date.

Assume that you created a subscription ECS instance at 13:00:00 on August 9, 2019. Related resources include the ECS instance, image, and cloud disk \(system disk\). You select a subscription duration of one month and manually renew the instance with another one-month commitment. The following billing cycles apply:

-   The first billing cycle is from 13:00:00 on August 9, 2019 to 00:00:00 on September 10, 2019.
-   The second billing cycle is from 00:00:00 on September 10, 2019 to 00:00:00 on October 10, 2019.

ECS resources are billed separately. You must pay these fees before you can use the resources. You can calculate the total price based on the configurations that you choose. The following table describes the formulas used to calculate the fee of each ECS resource.

|Resource|Formula|Unit price|
|:-------|-------|----------|
|ECS instance|Unit price of an instance type × Subscription duration|For more information, see the **Instance** tab on the [ECS Pricing](https://www.alibabacloud.com/product/ecs) page. **Note:** Local disks are tied to specific instance types. The prices of local disks are contained in the price of corresponding instance types. |
|Image|Unit price of an image × Subscription duration|You can obtain the price on the buy page or in Alibaba Cloud Marketplace.|
|Cloud disk \(system disk\)|Unit price of a disk × Disk capacity × Subscription duration|For more information, see the **System Cloud Disk Fee** section on the **Storage** tab of the [ECS Pricing](https://www.alibabacloud.com/product/ecs) page.**Note:** The price for a pay-as-you-go disk on the page is displayed in the USD/100 GiB/hour format. Divide it by 100 to obtain the unit price per GiB. |
|Cloud disk \(data disk\)|Unit price of a disk × Disk capacity × Subscription duration|For more information, see the **Data Cloud Disk Fee** section on the **Storage** tab of the [ECS Pricing](https://www.alibabacloud.com/product/ecs) page.**Note:** The price for a pay-as-you-go disk on the page is displayed in the USD/100 GiB/hour format. Divide it by 100 to obtain the unit price per GiB. |
|Public bandwidth \(pay-by-bandwidth\)|Unit price of bandwidth × Bandwidth value × Subscription duration For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md).

|A tiered billing model is used for bandwidth. You can select a bandwidth value on the buy page to view the changes in fees.|

Assume that you created a subscription ECS instance in China \(Qingdao\) with a subscription duration of three months. The following figure shows the process for calculating the price of the subscription ECS instance.

**Note:** The price is only for reference. For more information about the actual price, see the links in the preceding table.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9790359951/p54971.png)

## Changes in resource status after expiration

**Note:** After an ECS instance expires, the instance may be stopped. The system may send you notifications for renewing the instance. In this case, renew your instance to ensure service availability. If you still have problems, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

If the auto-renewal feature is not enabled for a subscription ECS instance, the instance stops providing services at some point from 00:00:00 on the expiration date to 00:00:00 on the next day.

**Note:** You cannot enable the auto-renewal feature for an expired subscription ECS instance.

The following table describes the resource status of an ECS instance after expiration.

|Resource|Within 15 days after expiration|More than 15 days after expiration|
|--------|-------------------------------|----------------------------------|
|ECS instance|The ECS instance is retained but it cannot be used. **Note:** After an ECS instance is stopped, you cannot connect to the instance or access websites deployed on the instance, and service errors may occur.

|The ECS instance is released.|
|Image|The image is unavailable.|The image is unavailable.|
|EBS|-   Cloud disks and data on them are retained, but the cloud disks cannot be used.
-   Local disks and data on them are retained, but the local disks cannot be used.

|-   Subscription disks are released and data on them cannot be restored.

**Note:** If you manually attach a pay-as-you-go cloud disk to a subscription instance and do not set the release mode to Release with Instance, the pay-as-you-go cloud disk stops to work.

-   Local disks are released and data on them cannot be restored. |
|Public IP address|-   In the classic network: The public IP address is retained.
-   In a VPC:
    -   The public IP address is retained.
    -   The EIP associated with the instance remains unchanged.

|-   In the classic network: The public IP address is released.
-   In a VPC:
    -   The public IP address is released.
    -   The EIP is disassociated from the instance. |

If the auto-renewal feature is enabled for a subscription ECS instance but the renewal fails, the instance automatically stops providing services at some point from 00:00:00 on the 15th day after expiration to 00:00:00 on the 16th day after expiration.

The following table describes the resource status of an ECS instance after expiration.

|Resource|Within 15 days after expiration|More than 15 days after expiration|More than 30 days after expiration|
|--------|-------------------------------|----------------------------------|----------------------------------|
|ECS instance|The ECS instance is retained and works properly. **Note:** When an ECS instance works properly, you can start or stop the instance, and connect to the instance by using management terminals or other connection methods.

|The ECS instance is retained but it cannot be used. **Note:** After an ECS instance is stopped, you cannot connect to the instance or access websites deployed on the instance, and service errors may occur.

|The ECS instance is released.|
|Image|The image is available.|The image is unavailable.|The image is unavailable.|
|EBS|-   Cloud disks and data on them are retained. The cloud disks can work properly.
-   Local disks and data on them are retained. The local disks can work properly.

|-   Cloud disks and data on them are retained, but the cloud disks cannot be used.
-   Local disks and data on them are retained, but the local disks cannot be used.

|-   Subscription disks are released and data on them cannot be restored.

**Note:** If you manually attach a pay-as-you-go cloud disk to a subscription instance and do not set the release mode to Release with Instance, the pay-as-you-go cloud disk stops to work.

-   Local disks are released and data on them cannot be restored. |
|Public IP address|-   In the classic network: The public IP address is retained.
-   In a VPC:
    -   The public IP address is retained.
    -   The EIP associated with the instance remains unchanged.

|-   In the classic network: The public IP address is retained.
-   In a VPC:
    -   The public IP address is retained.
    -   The EIP associated with the instance remains unchanged.

|-   In the classic network: The public IP address is released.
-   In a VPC:
    -   The public IP address is released.
    -   The EIP is disassociated from the instance. |

After the instance expires, a **Data Storage** button is displayed in the **Actions** column of the **Instances** page. Before the instance is released, you can create a custom image from the instance or create snapshots to back up the data stored on the disks.

![Data Storage](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5959480061/p141155.png)

## Overdue payments

If you have overdue payments in your account, subscription ECS resources can be used properly, but you cannot purchase, renew, or upgrade instances.

