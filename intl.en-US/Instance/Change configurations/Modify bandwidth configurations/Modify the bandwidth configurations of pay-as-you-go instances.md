---
keyword: [Alibaba Cloud, ECS, upgrade and downgrade, pay-as-you-go, modify bandwidth configurations, pay-by-traffic, pay-by-bandwidth]
---

# Modify the bandwidth configurations of pay-as-you-go instances

If the bandwidth configurations of a pay-as-you-go instance that uses a public IP address are not suitable for your business requirements, you can modify the bandwidth configurations.

You can perform the following operations to modify the bandwidth configurations of pay-as-you-go instances. You can modify the bandwidth configurations of instances multiple times, but you must wait at least five minutes between two consecutive operations.

-   Change the billing method for network usage. You can select **Pay-By-Bandwidth** or **Pay-By-Traffic**.
-   Modify the public bandwidth or peak traffic bandwidth based on the billing method for network usage.

    **Note:** If you change the public bandwidth of a classic network-type instance to 0 Mbit/s, the public IP address of the instance is retained. If you change the public bandwidth of a VPC-type instance to 0 Mbit/s, the public IP address of the instance is released.


This topic describes how to modify the bandwidth configurations of pay-as-you-go instances that use public IP addresses. For more information about how to modify the bandwidth configurations of a pay-as-you-go instance that uses an elastic IP address \(EIP\), see [Modify the bandwidth of an EIP](/intl.en-US/Instance/Change configurations/Modify bandwidth configurations/Modify the bandwidth of an Elastic IP address.md).

## Modify the bandwidth configurations of a single instance

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Find the pay-as-you-go instance for which you want to modify the bandwidth configurations. Choose **More** \> **Configuration Change** \> **Change Pay-as-you-go Instance Bandwidth** in the corresponding **Actions** column.

5.  On the Change Bandwidth page, find the Bandwidth section and modify the peak bandwidth.

    1.  Select **Pay-By-Bandwidth** or **Pay-By-Traffic** as the billing method for network usage.

    2.  Specify the corresponding public bandwidth or peak traffic bandwidth.

6.  Read the notes and terms of service. If you do not have any questions, select *ECS Terms of Service*.

7.  Confirm the configuration costs, click **Confirm**, and then perform the subsequent operations as instructed on the page.

    **Note:** The new bandwidth configurations take effect immediately after you modify the bandwidth. If you change the public bandwidth of a classic network-type instance from 0 Mbit/s to a non-zero value for the first time, you must restart the instance by using the console or by calling the RebootInstance operation to make the new configurations take effect.


## Modify the bandwidth configurations of multiple instances

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the top navigation bar, select a region.

4.  Select the pay-as-you-go instances for which you want to modify the bandwidth configurations. In the lower part of the page, choose **More** \> **Configuration Change** \> **Change Pay-as-you-go Instance Bandwidth**.

5.  On the Change Bandwidth page, find the Bandwidth section and modify the peak traffic bandwidth.

    1.  Select **Pay-By-Bandwidth** or **Pay-By-Traffic** as the billing method for network usage.

    2.  Specify the corresponding public bandwidth or peak traffic bandwidth.

    When you modify the bandwidth configurations of multiple instances, instances are filtered out if they are not associated with a public IP address. You can continue to perform operations only on the qualified instances, as shown in the following figure.

    ![Modify the bandwidth configurations of multiple instances](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6259443061/p139288.png)

6.  Read the notes and terms of service. If you do not have any questions, select *ECS Terms of Service*.

7.  Confirm the configuration costs, click **Confirm**, and then perform the subsequent operations as instructed on the page.

    **Note:** The new bandwidth configurations take effect immediately after you modify the bandwidth. If you change the public bandwidth of a classic network-type instance from 0 Mbit/s to a non-zero value for the first time, you must restart the instance by using the console or by calling the RebootInstance operation to make the new configurations take effect.


**Related topics**  


[DescribeResourcesModification](/intl.en-US/API Reference/Regions/DescribeResourcesModification.md)

[ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md)

