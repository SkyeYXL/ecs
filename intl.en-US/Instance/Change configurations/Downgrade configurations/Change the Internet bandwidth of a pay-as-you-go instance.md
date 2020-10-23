---
keyword: [Alibaba Cloud, ECS, downgrade, pay-as-you-go]
---

# Change the Internet bandwidth of a pay-as-you-go instance

You can change the Internet bandwidth of your pay-as-you-go instance if it does not meet or exceeds your business requirements.

You can change the Internet bandwidth of a pay-as-you-go instance based on the network type and the public IP category of the instance, as listed in the following table.

|Network type|Public IP category|Available feature|
|:-----------|:-----------------|:----------------|
|VPC|Elastic IP address \(EIP\)|Change the bandwidth of the EIP|
|Allocated public IP address|Change the bandwidth of the pay-as-you-go instance|
|Classic network|Allocated public IP address|Change the bandwidth of the pay-as-you-go instance|

After you change the bandwidth of a pay-as-you-go instance, you cannot change it again in the next 5 minutes. When you change the bandwidth of a pay-as-you-go instance, you can perform the following operations:

-   Change the billing method of Internet bandwidth: Select **Pay-By-Bandwidth** or **Pay-By-Traffic**.
-   Set a new Internet bandwidth value. After the Internet bandwidth is set to 0 Mbit/s,
    -   For a VPC-type instance, its public IP address is released immediately.
    -   The public IP addresses of classic network-type instances are retained, but do not provide public access.

## Change the bandwidth of an EIP

For a VPC-type instance to which an EIP is attached, perform the following steps to change the Internet bandwidth of the EIP:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).

3.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

4.  In the top navigation bar, select a region.

5.  Find the pay-as-you-go instance that is bound to an EIP, and click **Upgrade/Downgrade** in the **Actions** column.

6.  In the Upgrade/Downgrade Wizard dialog box, select **Bandwidth Adjustment**, and click **Continue**.

7.  On the Update page, select the new peak bandwidth and billing method for network traffic.

    For more information, see [Modify the peak bandwidth of an EIP](/intl.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Upgrade or downgrade the bandwidth of a pay-as-you-go EIP.md).

8.  Select the new peak bandwidth.

    For more information, see [Modify the peak bandwidth of an EIP](/intl.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Upgrade or downgrade the bandwidth of a pay-as-you-go EIP.md).

9.  Select *Elastic IP Agreement of Service,* and click **Activate**.

10. Complete the configuration as instructed.


## Change the bandwidth of a pay-as-you-go instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).

3.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

4.  In the top navigation bar, select a region.

5.  Different methods are required to change the Internet bandwidth based on the number of target pay-as-you-go instances.

    -   For one instance: Find the pay-as-you-go instance, and choose **More** \> **Configuration Change** \> **Change Bandwidth** from the **Actions** column.
    -   For multiple instances: Select the pay-as-you-go instances. At the bottom of the instance list, choose **More** \> **Configuration Change** \> **Change Bandwidth**.
6.  Click **Batch Change**.

7.  Modify the bandwidth settings, and click **OK**.

8.  Select *ECS Terms of Service,* and click **OK**.

    After the change is completed, the new Internet bandwidth setting takes effect immediately.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md)

