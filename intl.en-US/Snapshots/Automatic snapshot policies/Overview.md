---
keyword: [regular backup, data backup, fault tolerance, rollback]
---

# Overview

Automatic snapshot policies allow ECS to create normal snapshots and back up data for a disk on a regular basis. These policies can be applied to both system disks and data disks. Automatic snapshot policies improve data security and tolerance against operation faults.

## Scenarios

Automatic snapshot policies allow ECS to create snapshots on a regular basis at the scheduled time. These policies can protect disk data and improve system security and tolerance against operation faults. When applications such as websites or databases deployed on an ECS instance are exposed to attacks due to system vulnerabilities, you may not be able to create snapshots in time. In these cases, you can use the most recent automatic snapshot to roll back the affected disk and reduce losses.

You can also specify an automatic snapshot policy to create snapshots before you perform regular system maintenance tasks. This can also prevent losses due to unexpected problems during system maintenance.

## Limits

When you use automatic snapshot policies, take note of the following items:

-   For information about the quota of automatic snapshot policies for an Alibaba Cloud account in a region and the maximum number of automatic snapshots that can be retained for a disk, see the "Snapshot limits" section of the [Limits](/intl.en-US/Product Introduction/Limits.md) topic.
-   When the quota of automatic snapshots for a disk is reached, the earliest automatic snapshot is deleted.
-   If you modify the retention duration of automatic snapshots in an automatic snapshot policy, the modification applies only to subsequent snapshots, but not to existing snapshots.
-   You cannot create manual snapshots for a disk when an automatic snapshot is being created. You must wait until the automatic snapshot has been created.
-   You can create automatic snapshots only for disks that are in the **In Use** state.
-   Automatic snapshot policies cannot be applied to local disks.
-   Automatic snapshot policies can create only normal snapshots. They cannot create local snapshots.

## References

-   [Create an automatic snapshot policy](/intl.en-US/Snapshots/Automatic snapshot policies/Create an automatic snapshot policy.md)
-   [Apply or disable an automatic snapshot policy](/intl.en-US/Snapshots/Automatic snapshot policies/Apply or disable an automatic snapshot policy.md)
-   [Delete automatic snapshots while releasing a disk](/intl.en-US/Snapshots/Automatic snapshot policies/Delete automatic snapshots while releasing a disk.md)
-   [Modify an automatic snapshot policy](/intl.en-US/Snapshots/Automatic snapshot policies/Modify an automatic snapshot policy.md)
-   [Delete an automatic snapshot policy](/intl.en-US/Snapshots/Automatic snapshot policies/Delete an automatic snapshot policy.md)

## Related operations

-   [CreateAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md)
-   [ApplyAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/ApplyAutoSnapshotPolicy.md)
-   [CancelAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/CancelAutoSnapshotPolicy.md)
-   [DeleteAutoSnapshotPolicy](/intl.en-US/API Reference/Snapshots/DeleteAutoSnapshotPolicy.md)
-   [DescribeAutoSnapshotPolicyEX](/intl.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEX.md)
-   [ModifyAutoSnapshotPolicyEx](/intl.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md)

