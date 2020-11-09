---
keyword: [, unbind an ENI, secondary ENI]
---

# Unbind an ENI

This topic describes how to unbind a secondary elastic network interface \(ENI\) from your instance.

Before you unbind an ENI, make sure that the following requirements are met:

-   The ENI to be unbound is a secondary ENI. Primary ENIs cannot be unbound from instances.
-   The instance from which you want to unbind an ENI is in the **Stopped** or **Running** state.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

2.  In the left-side navigation pane, choose **Network & Security** \> **ENIs**.

3.  In the top navigation bar, select a region.

4.  Find the ENI that you want to unbind and click **Unbind** in the **Actions** column.

5.  In the Unbind message, confirm the information and click **OK**.


If the status of the ENI changes to **Available** after you refresh the ENI list, the ENI is unbound from the instance.

You can perform the following operations on an available ENI:

-   [Bind an ENI](/intl.en-US/Network/Elastic Network Interfaces/Bind an ENI.md)
-   [Delete an ENI](/intl.en-US/Network/Elastic Network Interfaces/Delete an ENI.md)
-   [Modify an ENI](/intl.en-US/Network/Elastic Network Interfaces/Modify an ENI.md)

**Related topics**  


[DetachNetworkInterface](/intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md)

