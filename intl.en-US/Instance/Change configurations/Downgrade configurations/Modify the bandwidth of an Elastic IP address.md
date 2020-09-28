# Modify the bandwidth of an Elastic IP address

ECS instances in VPCs are associated with Elastic IP addresses to have access to the Internet. You can modify the peak bandwidths of the Elastic IP addresses that are associated to subscription or pay-as-you-go ECS instances.

The ECS instance is associated with an Elastic IP address.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the target ECS instance and click **Upgrade/Downgrade** in the **Actions** column.

5.  In the Upgrade/Downgrade Wizard dialog box, select **Bandwidth Adjustment** and click **Continue**.

6.  Select a new peak bandwidth.

    For more information, see [Modify the peak bandwidth of an EIP](/intl.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Upgrade or downgrade the bandwidth of a pay-as-you-go EIP.md).

7.  Select *Elastic IP Agreement of Service* and click **Activate**.


The changes take effect immediately without the need to restart the instance.

