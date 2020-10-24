---
keyword: [Alibaba Cloud, ECS, server, elastic computing]
---

# Create an ECS instance by using a custom image

This topic describes how to create an ECS instance by using a custom image. You can use a custom image to create an ECS instance that has the same operating system, applications, and data as those of the custom image to make the process more efficient.

A custom image is created in the account and region where you want to create an instance.

If you do not have a custom image in the account and region where you want to create an instance, you can use one of the following solutions.

|Scenario|Solution|
|--------|--------|
|You have an image on the local device.|Import the local image to Alibaba Cloud as a custom image. For more information, see [Image import procedure](/intl.en-US/Images/Custom image/Import images/Image import procedure.md).|
|You do not have custom images but have an instance as a template.|For more information, see [Create a custom image from an instance](/intl.en-US/Images/Custom image/Create custom image/Create a custom image from an instance.md).|
|You do not have custom images but have a snapshot as a template.|For more information, see [Create a custom image from a snapshot](/intl.en-US/Images/Custom image/Create custom image/Create a custom image from a snapshot.md).|
|You have a custom image in another region.|Copy the custom image to the region where you want to create an instance. For more information, see [Copy custom images](/intl.en-US/Images/Custom image/Copy custom images.md).|
|You have a custom image in another account.|Share the custom image with the account under which you want to create an instance. For more information, see [Share or unshare custom images](/intl.en-US/Images/Custom image/Share or unshare custom images.md).|

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Images**.

3.  In the top navigation bar, select a region.

4.  Based on the image source, use one of the following methods to go to the Images page:

    -   Custom image created or exported: Go to the **Custom Images** tab.
    -   Custom image obtained by copying: Go to the **Custom Images** tab.
    -   Custom image obtained by sharing: Go to the **Shared Images** tab.
5.  Find the image that you want to use. Click **Create Instance** in the **Actions** column.

6.  Configure the parameters and create the instance.

    Information of the region and image sections is automatically filled. Configure other parameters based on your needs. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

    **Note:** If the selected custom image contains one or more data disk snapshots, an equal number of data disks are automatically created from these snapshots. Each disk has the same size as the snapshot from which the disk is created. You can extend a data disk but cannot shrink it.


If you add data disks when you create the instance, you must format the partitions before you can use the data disks. For more information, see [Format a data disk for a Windows ECS instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Windows ECS instance.md) or [Format a data disk for a Linux instance](/intl.en-US/Block Storage/Cloud disks/Format a data disk/Format a data disk for a Linux instance.md).

**Related topics**  


[RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md)

