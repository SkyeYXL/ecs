---
keyword: [Alibaba Cloud, ECS, disk resizing, resizing, EBS device]
---

# Overview

You can resize disks to meet your storage requirements as your business and application data grow. This topic describes the maximum sizes that disks can be resized to and how to resize a disk in different scenarios.

## Scenarios

You can increase the storage capacity of an instance by using one of the following methods:

-   Resize an existing disk. You must resize the existing partitions of the disk or create new partitions on the disk.

    The following methods can be used to resize an existing disk.

    |Method|Limit|Procedure|
    |------|-----|---------|
    |Resize a disk online|The instance to which the disk is attached must be in the **Running** \(Running\) state. After the disk is resized, the new size takes effect automatically without the need to restart the instance.

|    -   [Resize disks online \(Linux\)](/intl.en-US/Block Storage/Resize cloud disks/Resize disks online (Linux).md)
    -   [Resize disks online \(Windows\)](/intl.en-US/Block Storage/Resize cloud disks/Resize disks online (Windows).md) |
    |Resize a disk offline|The instance to which the disk is attached must be in the **Running** \(Running\) or **Stopped** \(Stopped\) state. After the disk is resized, you must restart its attached instance by using the ECS console or by calling the RebootInstance operation for the new size to take effect.

|    -   [Resize disks offline \(Linux\)](/intl.en-US/Block Storage/Resize cloud disks/Resize disks offline (Linux).md)
    -   [Resize disks offline \(Windows\)](/intl.en-US/Block Storage/Resize cloud disks/Resize disks offline (Windows).md) |

-   Create a new disk, attach the disk to the instance, and then partition and format the disk.
-   Replace the system disk of the instance and specify a larger size for the new system disk. For more information, see [Replace the system disk \(public images\)](/intl.en-US/Block Storage/Cloud disks/Change the operating system/Replace the system disk (public images).md).

## Size ranges of resized system disks

The sizes of resized system disks must be greater than the values before resizing, but less than or equal to 500 GiB. The following table describes the size ranges of resized system disks that attached to instances using different images.

|Image|Size range of a resized system disk \(GiB\)|
|:----|:------------------------------------------|
|CoreOS and FreeBSD|\[Max\{30, the size of the system disk before resizing\}, 500\]|
|Other Linux distributions|\[Max\{20, the size of the system disk before resizing\}, 500\]|
|Windows Server|\[Max\{40, the size of the system disk before resizing\}, 500\]|

For example, the size of the system disk on a CentOS instance before resizing is 35 GiB. After the system disk is resized, the size of the new system disk must be greater than 35 GiB and less than or equal to 500 GiB.

## Maximum sizes of resized data disks

The sizes of resized data disks must be greater than the values before resizing. The following table lists the maximum sizes of resized data disks of different categories.

|Disk category|Maximum size of a resized data disks \(GiB\)|
|:------------|:-------------------------------------------|
|Basic disk|2,000|
|Enhanced SSD \(ESSD\), standard SSD, or ultra disk|32,768|

