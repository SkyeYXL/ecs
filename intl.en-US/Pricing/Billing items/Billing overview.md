---
keyword: [prepaid, subscription, weekly subscription, pay-as-you-go, billable resources]
---

# Billing overview

This topic describes items related to ECS billing, such as billable resources, billing methods, and payment methods.

The price of an ECS resource may vary by region. For more information about ECS resource prices, see [Pricing](https://www.alibabacloud.com/product/ecs).

## Billable resources

ECS comprises the following major components: instances, images, Block Storage devices, snapshots, security groups, and networks. For more information, see [What is ECS?](/intl.en-US/Product Introduction/What is ECS?.md)

The following table describes billable ECS resources.

|Resource|Description|
|--------|-----------|
|ECS instance|You are billed based on the instance type that you choose. The instance type determines the number of vCPUs and the size of memory that you can use. **Note:** If you select an instance type that is equipped with local disks, the price of the instance type includes the price of local disks. |
|Image|Images are classified into the following types: -   Public image
    -   Windows Server: The price is subject to the instance type that you choose. For more information, see the buy page.
    -   Red Hat Enterprise Linux: You are charged for these images. For more information, see the buy page.
    -   Other images: free of charge.
-   Alibaba Cloud Marketplace image: Prices are determined by the image providers.
-   Custom image
    -   If a custom image is derived from a free public image or an Alibaba Cloud Marketplace image, you are charged for the snapshot used to create the custom image. Snapshots are charged based on storage space usage.
    -   If a custom image is obtained from a paid public image or an Alibaba Cloud Marketplace image, you are charged for the snapshot used to create the custom image. Snapshots are billed based on storage space usage. If you use a custom image to create an ECS instance, you are also charged for the image.
-   Shared image
    -   If a shared image is derived from a free public image or an Alibaba Cloud Marketplace image, the shared image is free of charge.
    -   If a shared image is derived from a paid public image or an Alibaba Cloud Marketplace image, you are also charged for the shared image when you use it to create an ECS instance. If you never use the image, you are not charged. |
|Block Storage device|Alibaba Cloud provides the following types of Block Storage devices: -   Cloud disks: Cloud disks are billed based on their storage capacity. You can use cloud disks as system disks or data disks.
-   Local disks: Local disks are billed based on their storage capacity. You can use local disks only as data disks. Local disks cannot be purchased separately. Local disks created together with an ECS instance have the same billing method as the ECS instance.

Instance families that are equipped with local disks include d1ne, d1, i2, i2g, i1, and gn5. For information about instance families, see [Instance families](/intl.en-US/Instance/Instance families.md). |
|Public bandwidth|An ECS instance can access the Internet through the following methods: -   Use the public IP address allocated by the system. You are not charged to retain public IP addresses. You are charged only for public bandwidth. For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md).
-   Use the elastic IP address \(EIP\). EIP is an independent service. For more information, see [Billing overview](/intl.en-US/Pricing/Billing.md).
-   Use the NAT gateway. NAT Gateway is an independent service. For more information, see [Billing method](/intl.en-US/Pricing/Billing.md). |
|Snapshot|Snapshots are billed based on the storage space usage.|

## Billing methods

ECS instances support the following billing methods: subscription and pay-as-you-go.

-   Subscription: a billing method that allows you to pay for an instance upfront to use for the subscription period. The subscription billing method is suited for common services without traffic spikes, such as web services. For more information, see [Subscription](/intl.en-US/Pricing/Billing methods/Subscription.md).
-   Pay-as-you-go: a billing method that allows you to use an instance and pay afterwards for the resources it uses. The pay-as-you-go billing method is suited for scenarios with traffic spikes, such as temporary scaling, interim testing, and scientific computing. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Billing methods/Pay-as-you-go.md).

For more information about the difference between subscription and pay-as-you-go, see [Comparison of billing methods](/intl.en-US/Pricing/Billing methods/Comparison of billing methods.md).

|Resource|Billing method|
|--------|--------------|
|ECS instance|-   Subscription
-   Pay-as-you-go

If you plan to make a long-term commitment with pay-as-you-go ECS instances, you can purchase reserved instances to offset your bills. This method is more flexible and cost-effective. For more information, see [Reserved instance overview](/intl.en-US/Instance/Instance purchasing options/Reserved Instances/Reserved instance overview.md). For the billing details of reserved instances, see [Reserved instance billing](/intl.en-US/Pricing/Billing methods/Reserved instance billing.md).

-   Preemptible instance

Preemptible instances are a type of on-demand instances that reduce overall ECS instance costs. Preemptible instances may be reclaimed. You can use auto provisioning groups to alleviate the instability caused by preemptible instances being reclaimed. For more information, see [Auto Provisioning overview](/intl.en-US/Elasticity/Manage auto provisioning groups/Auto Provisioning overview.md). |
|Image|-   Subscription
-   Pay-as-you-go

Images can be used only along with ECS instances. Windows reserved instances can be used to offset image bills. |
|Disk|-   Subscription
-   Pay-as-you-go

The billing methods of cloud disks depend on how they are created.

-   Cloud disks created along with an ECS instance have the same billing method as the ECS instance.
-   Cloud disks created for a subscription ECS instance use the subscription billing method.
-   Cloud disks created on the Disks page of the ECS console support only pay-as-you-go.
-   Cloud disks created from snapshots support only pay-as-you-go.

You can change the billing methods of your cloud disks. For more information, see [Change billing methods of disks](/intl.en-US/Block Storage/Cloud disks/Change billing methods of disks.md). |
|Public bandwidth|If your ECS instance accesses the Internet by using a public IP address, one of the following billing methods is used: -   Pay-by-bandwidth

Fees are calculated based on the bandwidth that you specified. You can select the pay-by-bandwidth billing method for ECS instances that use the following billing methods:

    -   Subscription
    -   Pay-as-you-go
-   Pay-by-traffic

You are billed on an hourly basis based on the amount of traffic that your instance consumed.


You can enable public bandwidth when you create an ECS instance, or enable public bandwidth by using the configuration upgrade or downgrade feature after you create an ECS instance. For more information, see [Billing methods of public bandwidth](/intl.en-US/Pricing/Billing methods of public bandwidth.md). |
|Snapshot|Pay-as-you-go

For more information, see [Snapshot billing](/intl.en-US/Pricing/Snapshot billing.md). |

## Payment methods

You can use the following methods to pay for ECS resources:

-   Bank card
-   PayPal

    Alibaba Cloud pre-authorizes your PayPal account after your pay-as-you-go resources start incurring fees.

-   Paytm \(India\)

    Only for users in India. Alibaba Cloud pre-authorizes your Paytm account after your pay-as-you-go resources start incurring fees.


**Note:** Coupons are used to pay for your resource usage before bills are issued. No actual payments are involved.

Before you purchase ECS resources, you must bind a bank card, PayPal account, or Paytm \(India\) account to your Alibaba Cloud account. For more information, see [Add a payment method](https://www.alibabacloud.com/help/doc-detail/50517.htm) in *Account Management*.

If you want to purchase ECS resources in mainland China, you must complete real-name verification. For more information, see the *How can I complete real-name registration* section in [Real-name verification FAQ](https://www.alibabacloud.com/help/doc-detail/52595.htm) in *Account Management*.

