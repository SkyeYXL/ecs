---
keyword: [snapshot, storage plan, pay-as-you-go, snapshot fee, snapshot billing]
---

# Snapshot billing

This topic describes the billing methods and billing rules of ECS snapshots, and how to deal with overdue payments. An example of how to calculate the snapshot fee is also provided.

## Billing items of snapshots

A snapshot is a backup of the data on a disk at a specific point in time. snapshots are often used for disaster recovery and environment clone. The following table describes the billing items of snapshots.

|Billing item|Description|Billing method|
|------------|-----------|--------------|
|Snapshot type|Normal snapshot|Normal snapshots have strong disaster recovery capabilities and are stored in OSS buckets in the same region as the snapshots. An extended period of time is required to create a normal snapshot.|Pay-as-you-go|
|Local snapshots|Local snapshots are stored in the same storage cluster as the disks for which the snapshots are created. Local snapshots can be used to perform data backup and disk rollback within seconds. Local snapshots can be created only for enhanced SSDs \(ESSDs\).|Pay-as-you-go|
|Snapshot service|Snapshot replication|When a normal snapshot is copied from one region to another, a copy of the normal snapshot is created in another region.|Pay-as-you-go|

## Billing method

ECS snapshots are billed based on their size and storage duration and use the pay-as-you-go billing method. Billing starts when a snapshot is created and stops when the snapshot is released. The snapshot fee is calculated by billing cycle \(each hour\). A bill is generated at the end of each settlement cycle, and the corresponding fee is deducted from your account.

## Billing rules

|Billing item|Billing rule|
|------------|------------|
|Storage fees for normal and local snapshots|Snapshots are billed once an hour based on the storage capacity occupied by the snapshots.

Snapshot fee = Snapshot unit price × Snapshot size × Billing duration. The following section describes the billing rules of each item in the formula:-   Snapshot unit price: The unit is USD/GiB/month. You can obtain the price per hour after conversion. For information about snapshot prices in different regions, see the Pricing tab on the [Elastic Compute Service](https://www.alibabacloud.com/product/ecs) page.
-   Snapshot size: The unit is GiB. You have a free storage quota of 5 GiB each month.

The first snapshot of a disk is a full snapshot. Subsequent snapshots of the disk are incremental snapshots. Each incremental snapshot consists only of the data changes since the last snapshot. For more information, see [Incremental snapshots](/intl.en-US/Snapshots/Incremental snapshots.md).

-   Billing duration: The unit is hours. Billing starts when a snapshot is created and stops when the snapshot is released. A storage duration of less than one hour is calculated as one hour. |
|Replication fee for snapshots|Replication fee for snapshots = Unit price of snapshot replication × Snapshot sizeFor information about the unit prices of snapshot replication in different regions, see the Pricing tab on the [Elastic Compute Service](https://www.alibabacloud.com/product/ecs) page.

**Note:** For information about the storage fees of snapshot copies, see the "Storage fees for normal snapshots" item in this table. |

## Examples of calculating normal snapshot fees

**Note:** The following example is for reference only. You can view your actual snapshot bills on the Bills page in the User Center.

For example, assume that you have three disks in the China \(Hangzhou\) region in your account. You created a snapshot for each disk at 10:20. The snapshots are 50 GiB, 220 GiB, and 40 GiB in size. If you do not delete these snapshots on the current day, the fees of the three snapshots are calculated in the following way:

-   Billing conditions
    -   Snapshot size: 50 GiB + 220 GiB + 40 GiB = 310 GiB.

        If you have not used the 5 GiB free storage quota of this month, the billed snapshot size is 305 GiB.

    -   Snapshot unit price: Assume that the pay-as-you-go price for snapshots in the China \(Hangzhou\) region is USD 0.0200/GiB/month, which is equivalent to USD 0.0000277778/GiB/hour.
    -   Billing duration: The period from 10:20 to 11:00 is calculated as an hour. A total of 13 hours are calculated until 23:00 when a bill is generated.
-   Billing calculation

    Snapshot fee = Snapshot unit price × Snapshot size × Billing duration. That is, 305 GiB × USD 0.0000277778/GiB/hour × 13 = USD 0.008472.

    -   The actual payable amount shown on the billing page is USD 0.008.
    -   The generated bill records the amount of USD 0.0085.

## Overdue payments

If your account balance in the current billing cycle is less than the payable amount of the previous billing cycle, the system sends an SMS or email notification to you.

The snapshot service is suspended 24 hours after your account payments become overdue. After your account has overdue payments:

-   In the first 15 days, all existing snapshots are retained, and no automatic snapshots can be created. All automatic snapshots whose retention period is less than 15 days are deleted.
-   After 15 days, all snapshots are deleted, except for those that have been used to create disks or custom images. The automatic snapshot policy is also deleted.

## References

-   [Overview](/intl.en-US/Snapshots/Snapshot overview.md)
-   [Reduce snapshot fees](/intl.en-US/Snapshots/Use snapshots/Reduce snapshot fees.md)
-   [Snapshot FAQ](/intl.en-US/Snapshots/Snapshot FAQ.md)

