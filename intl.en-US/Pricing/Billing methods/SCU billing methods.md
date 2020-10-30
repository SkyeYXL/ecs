---
keyword: [Alibaba Cloud, SCU, storage package, storage cost, capacity package, pay-as-you-go]
---

# SCU billing methods

You can use Storage Capacity Units \(SCUs\) to offset the bills of storage resources such as disks, Object Storage Service \(OSS\), Apsara File Storage NAS \(NAS\), and snapshots. SCUs use the subscription billing method. The all-upfront payment option is supported.

## Billing methods

SCUs use the subscription billing method, and are billed based on their capacity and validity period. For more information about pricing, see the Pricing tab on the [Storage Capacity Unit](https://www.alibabacloud.com/product/scu/pricing) page.

-   SCU capacity: For the capacity specifications that SCUs support, see [Overview](/intl.en-US/Block Storage/Storage capacity units/Overview.md).
-   Subscription period: You can subscribe to an SCU for a period of 1 month, 2 months, 3 months, 6 months, 12 months, 3 years, or 5 years. If you use an annual or multi-year subscription, you can receive certain discounts.

When you purchase an SCU, if you select the All Upfront payment option, full payment is required upfront at purchase.

Sum = Subscription period × SCU capacity × SCU unit price.Unit: dollar.

## Usage rules

After you purchase an SCU, the SCU automatically matches all qualified pay-as-you-go storage services within the region and is used to offset your bills before the SUC expires. When the used capacity exceeds the SCU capacity, the excess capacity is billed on a pay-as-you-go basis.

The amount of storage capacity that an SCU can offset varies depending on the types of resources to which the SCU is applied. For more information, see [Usage rules](/intl.en-US/Block Storage/Storage capacity units/Usage rules.md).

## Expiration

After an SCU expires, you cannot use it to offset the bills of pay-as-you-go storage resources. If you have no other SCUs within the same region, those pay-as-you-go resources are billed on a pay-as-you-go basis.

