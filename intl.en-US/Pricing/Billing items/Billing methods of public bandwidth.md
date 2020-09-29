---
keyword: [subscription, pay-as-you-go, pay-by-bandwidth, pay-by-traffic, public IP address, outbound bandwidth, inbound bandwidth]
---

# Billing methods of public bandwidth

This topic describes public bandwidth types, billing methods, and examples on how to calculate bandwidth fees.

## Types of public IP addresses

An ECS instance can access the Internet by using the following types of public IP addresses:

-   Fixed public IP address

    To use an allocated public IP address to access the Internet, select **Assign Public IP Address** when you configure the public bandwidth during instance creation. For more information, see [Create an instance by using the provided wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the provided wizard.md).

-   Elastic IP address \(EIP\)

    An EIP is a public IP address resource that you can purchase and use independently. It provides higher flexibility for Internet access. For more information about the differences between EIPs and fixed public IP addresses and the billing methods of EIPs, see [What is an EIP?](/intl.en-US/.md).

    To use an EIP to access the Internet, attach the purchased EIP to an ECS instance. When you configure the public bandwidth, you do not need to select **Assign Public IP Address** to purchase public bandwidth.


## Public bandwidth types

After an ECS instance is assigned a fixed public IP address, you can use the instance to access the Internet and process requests from the Internet. Two types of public bandwidth are used.

|Public bandwidth type|Charged|Description|Example|
|---------------------|-------|-----------|-------|
|Outbound bandwidth|Yes|Bandwidth for outbound traffic from ECS instances|The FTP client downloads resources from ECS instances through public IP addresses.|
|Inbound bandwidth|No|Bandwidth for inbound traffic to ECS instances|The FTP client uploads resources to ECS instances through public IP addresses.|

For more information about the limits on the public bandwidth of ECS instances, see [Limits](/intl.en-US/Product Introduction/Limits.md).

**Note:** Alibaba Cloud does not charge any fees for internal bandwidth usage. Within the same region, no fees are charged for traffic between ECS instances or between ECS instances and other Alibaba Cloud services. For example, communication between Alibaba Cloud services that belong to the same VPC is free. If an ECS instance communicates with other Alibaba Cloud services through the Internet, the outbound bandwidth will be billed. For example, you will be billed for communication between an instance from China \(Hangzhou\) and an instance from China \(Shanghai\).

## Billing methods

Billing methods of public bandwidth include pay-by-bandwidth and pay-by-traffic. Pricing of bandwidth varies among regions. For more information, see [Pricing](https://www.aliyun.com/price/product#/ecs/detail). The following table describes the billing methods of public bandwidth and their relationship with billing methods of ECS instances.

|Bandwidth billing method|Description|Instance billing method|Billing rule|Pricing unit|
|------------------------|-----------|-----------------------|------------|------------|
|Pay-by-bandwidth|Fees are charged based on the bandwidth that you specify. Your actual outbound bandwidth will not exceed the specified bandwidth.|Subscription|You must pay for the bandwidth you purchased in advance. **Note:** The unit price for ECS resources with the weekly subscription will be prorated based on the monthly unit price. For more information, see the buy page.

|-   Equal to or less than 5 Mbit/s: CNY/\(n Mbit/s per month\). The value of n is an integer from 1 to 5.
-   Greater than or equal to 6 Mbit/s: CNY/\(Mbit/s per month\). |
|Pay-as-you-go|Bandwidth bills are accurate to the second. The bills are generated every hour.|CNY/\(Mbit/s per hour\). You can divide this price by 3600 to obtain the price per second. |
|Pay-by-traffic|Fees are charged based on your actual traffic usage. You can configure a bandwidth limit for outbound traffic to avoid unmanageable fees incurred by outbound traffic bursts.|Subscription|The bills are generated every hour.|CNY/GB.|
|Pay-as-you-go|The bills are generated every hour.|CNY/GB.|

**Note:** Bandwidth price for 6 Mbit/s or higher = \(Unit price for 5 Mbit/s\) + \(n - 5\) × \(Unit price for 6 Mbit/s or higher\). The value of n is an integer from 5 to ∞.

## Billing methods

Billing methods of public bandwidth include pay-by-bandwidth and pay-by-traffic. Pricing of network bandwidth varies among regions. For more information, see [Pricing](https://www.alibabacloud.com/zh/product/ecs#pricing).

**Note:** You can also purchase a data transfer plan to offset the network traffic. For more information, see [Purchase a data transfer plan with one click](https://www.alibabacloud.com/starter-packages/general).

Billing methods of public bandwidth include pay-by-bandwidth and pay-by-traffic. Pricing of network bandwidth varies among regions. For more information, see Pricing.

-   Pay-by-bandwidth: Fees are charged based on the bandwidth that you specify. Your actual outbound bandwidth will not exceed the specified bandwidth.
-   Pay-by-traffic: Fees are charged based on your actual traffic usage in the unit of USD/GB. You can configure a bandwidth limit for outbound traffic to avoid unmanageable fees incurred by outbound traffic bursts.

## Billing examples

The following table describes how public bandwidth is billed. This example uses the China \(Hangzhou\) region.

**Note:** Prices in the following table are for reference only. Visit the Pricing page for more price details.

|Bandwidth billing method|Instance billing method|Billing example|Fee \(CNY\)|
|:-----------------------|-----------------------|---------------|-----------|
|Pay-by-bandwidth|Subscription|-   Usage period: 1 month.
-   Bandwidth: 2 Mbit/s.
-   Unit price for 2 Mbit/s: CNY 46.00/\(2 Mbit/s per month\).

|1 × 46.00 = 46.00|
|-   Usage period: 1 month.
-   Bandwidth: 7 Mbit/s.
-   Unit price for 5 Mbit/s: CNY 125.00/\(5 Mbit/s per month\).
-   Unit price for 6 Mbit/s or higher: CNY 80.00/\(Mbit/s per month\).

|1 × \[125.00 + \(7 - 5\) × 80.00\] = 285.00|
|Pay-as-you-go|-   Usage period: 1 hour.
-   Bandwidth: 2 Mbit/s.
-   Unit price for 1 to 5 Mbit/s: CNY 0.063/\(Mbit/s per hour\).

|1 × \(2 × 0.063\) = 0.126|
|-   Usage period: 1 hour.
-   Bandwidth: 7 Mbit/s.
-   Unit price for 1 to 5 Mbit/s: CNY 0.063/\(Mbit/s per hour\).
-   Unit price for 6 Mbit/s or higher: CNY 0.248/\(Mbit/s per hour\).

|1 × \[\(0.063 × 5\) + \(7 - 5\) × 0.248\] = 0.811|
|Pay-by-traffic|Subscription and pay-as-you-go|-   Consumed traffic: 1 GB.
-   Unit price: CNY 0.80/GB.
-   Usage period: N/A. You are billed by the traffic that you actually use.

|1 × 0.80 = 0.80|

## View billing details

To view the volume of outbound Internet traffic for a pay-as-you-go ECS instance, take note of the instance ID, go to the [Billing Management](https://expense.console.aliyun.com/) console, and then choose **All Menus** \> **Bill** \> **Bill**. On the **Details** tab, view the volume of **Outgoing traffic** for the corresponding instance ID with **Elastic Compute Service \(ECS\) - Pay by quantity** as the product detail.

![View billing details](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6091909951/p61589.png)

## Billing examples

The following table describes how public bandwidth is billed on a pay-by-traffic basis. This example uses the China \(Hangzhou\) region.

**Note:** The unit price here is for reference only. Visit the Pricing page for price details.

|Bandwidth billing method|Billing example|Fee \(USD\)|
|------------------------|---------------|-----------|
|Pay-by-traffic|This example assumes that the bandwidth is 0.5 Mbit/s.

 -   Usage period: 1 hour
-   Average bandwidth: 0.5 Mbit/s
-   Unit price: USD 0.1/GB

|The volume of the outbound traffic is \(0.5 × 60 × 60\)/1024/8 GB = 0.22 GB.

**Note:** In this formula, 1024 is used to convert Mbit into Gbit, and 8 is used to convert Gbit into GB.

 You must pay the following amount for the hourly traffic: 0.22 GB × 0.1 USD/GB = USD 0.022.|

## View billing details

To view the volume of outbound Internet traffic for a pay-as-you-go ECS instance, you can go to the Billing Management console and click Usage Records to download the usage history of **Elastic Compute Service \(ECS\) - Pay-As-You-Go**.

To view the volume of outbound Internet traffic for a pay-as-you-go ECS instance, you can go to the [Billing Management](https://billing.console.aliyun.com/) console and click Usage Records to download the usage history of **Elastic Compute Service \(ECS\) - Pay-As-You-Go**.

![Elastic Compute Service (ECS) - Pay-As-You-Go](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7091909951/p61575.png)

## Change billing methods

You must use different methods to change the billing method of public bandwidth based on how an ECS instance is billed.

|Instance billing method|Conversion of the billing method|Method|Effective time|
|-----------------------|--------------------------------|------|--------------|
|Subscription|From pay-by-traffic to pay-by-bandwidth|[Upgrade configurations of subscription instances](/intl.en-US/Instance/Change configurations/Upgrade configurations/Upgrade configurations of subscription instances.md)|Immediately|
|From pay-by-bandwidth to pay-by-traffic|[Downgrade the public bandwidths of subscription instances](/intl.en-US/Instance/Change configurations/Downgrade configurations/Downgrade the public bandwidths of subscription instances.md)|Immediately|
|[Downgrade an instance during renewal](/intl.en-US/Pricing/Renew instances/Downgrade instance configurations during renewal.md)|From the next billing cycle|
|Pay-as-you-go|From pay-by-traffic to pay-by-bandwidth|[Change Internet bandwidth](/intl.en-US/Instance/Change configurations/Change configurations of Pay-As-You-Go instances/Change the Internet bandwidth of a pay-as-you-go instance.md)|Immediately|
|From pay-by-bandwidth to pay-by-traffic|[Change Internet bandwidth](/intl.en-US/Instance/Change configurations/Change configurations of Pay-As-You-Go instances/Change the Internet bandwidth of a pay-as-you-go instance.md)|Immediately|

