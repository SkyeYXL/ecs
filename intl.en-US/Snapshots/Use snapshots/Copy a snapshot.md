---
keyword: [snapshot backup, custom image, disk, data backup, modify key files, rollback, backup, cloud disk]
---

# Copy a snapshot

After you create a snapshot, you can copy the snapshot within the same region or across different regions. The new snapshot will be assigned a different ID from that of the source snapshot.

At least one normal snapshot is created for a disk. For more information, see [Create a normal snapshot](/intl.en-US/Snapshots/Use snapshots/Create a normal snapshot.md).

The snapshot copying feature is available in the following regions:

-   China \(Hangzhou\), China \(Shanghai\), China \(Qingdao\), China \(Beijing\), China \(Zhangjiakou\), China \(Hohhot\), China \(Ulanqab\), China \(Shenzhen\), China \(Heyuan\), and China \(Chengdu\)
-   China \(Hong Kong\), Singapore, Australia \(Sydney\), Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), Japan \(Tokyo\), Germany \(Frankfurt\), UK \(London\), US \(Silicon Valley\), US \(Virginia\), and India \(Mumbai\)

When you copy a snapshot, take note of the following items:

-   Billing:

    When you copy a snapshot across different regions, a snapshot copy is created. It will incur storage fees and snapshot replication service fees. For more information, see the **Pricing** tab on the [Elastic Compute Service](https://www.alibabacloud.com/product/ecs) page.

    **Note:** When a disk snapshot is copied for the first time, all content stored on the disk is copied. All subsequent copies of the snapshot in the same region are incremental copies. Snapshot are billed based on the snapshot size. Incremental copies can significantly reduce snapshot sizes.

-   Scenarios:
    -   DevOps: You can copy snapshots to quickly start business in new regions or migrate business systems to new regions. This helps you reduce O&M costs and achieve higher data availability.
    -   Cross-region backup: Snapshot copying meets the requirements of compliance audits and improvement of business reliability. You can restore your business system in another region by using new snapshots in the event of a disaster. This reduces recovery time objective \(RTO\) and recovery point objective \(RPO\).
-   Limits:
    -   A new snapshot that you copied from its source snapshot cannot be used to roll back the disk from which the source snapshot is created.
    -   Tags bound to source snapshots cannot be copied together with source snapshots.
    -   Encrypted snapshots cannot be copied.
    -   Local snapshots cannot be copied.

## Copy Snapshot

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Snapshots**.

3.  In the top navigation bar, select a region.

4.  Find the target snapshot and click **Copy Snapshot** in the Actions column.

5.  In the **Copy Snapshot** dialog box, set the parameters.

6.  Click **OK**.


## Cancel snapshot copying

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Snapshots**.

3.  In the top navigation bar, select a region.

4.  Find the snapshot that is being copied and click **Delete**.

5.  In the **Note** message, click **OK**.


**Related topics**  


[CopySnapshot](/intl.en-US/API Reference/Snapshots/CopySnapshot.md)

