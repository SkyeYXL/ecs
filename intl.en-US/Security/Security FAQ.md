---
keyword: [cannot access TCP port 25, cannot set Internet security group rules, ping failed, the maximum number of rules has been reached, network isolation, maximum number of security groups, quota of security group rules, quota of security groups]
---

# Security FAQ

-   FAQ on security groups
    -   [What is a security group?](#section_kvb_jxz_lgb)
    -   [Why do I need to select a security group when I create an ECS instance?](#section_jym_lxz_lgb)
    -   [What can I do if I create an ECS instance before I create a security group?](#section_mkc_wxz_lgb)
    -   [Why am I being prompted that the maximum number of rules has been reached when I try to add an instance to a security group?](#section_vgd_1zz_lgb)
    -   [If I adjust the maximum number of security groups that a VPC-type ECS instance can belong to, does this adjustment only take effect on security groups created after the limit is adjusted?](#section_ftt_wyz_lgb)
    -   [In what scenarios do security groups use the default security group rules?](#section_a9i_vt4_bmz)
-   FAQ on security group rules
    -   [In what scenarios do I need to add a security group rule?](#section_rg8_hk4_oph)
    -   [Why can't I configure Internet security group rules for my ECS instance in a VPC?](#section_rff_5xz_lgb)
    -   [Why can't I access TCP port 25?](#section_kmc_yxz_lgb)
    -   [Why can't I access port 80?](#section_avg_cyz_lgb)
    -   [Why have several internal security group rules been automatically added to my security group?](#section_fxk_zxz_lgb)
    -   [What happens when a security group rule is configured incorrectly?](#section_qrf_nxz_lgb)
    -   [Are the inbound and outbound rules in a security group counted separately?](#section_bll_vyz_lgb)
    -   [Can I adjust the maximum number of rules that can be added to a security group?](#section_qnp_ryz_lgb)
-   FAQ on host penalty and unblocking
    -   [What can I do if I receive a notification that my website has been blocked due to illegal activities and needs to be rectified?](#section_kw5_58g_li3)
    -   [What can I do if I receive a notification that my website has been penalized for committing external attacks?](#section_owz_g37_ea9)
-   FAQ on quotas
    -   [How do I view resource quotas?](#section_til_tmr_0wh)

## What is a security group?

A security group is a virtual firewall that implements access control for one or more ECS instances. Security groups logically isolate security domains in the cloud.

Each ECS instance must belong to at least one security group. When you create an ECS instance, you must specify a security group to add it to the instance. By default, instances within the same security group can communicate with each other but instances in different security groups are isolated from each other. You can configure a security group rule to authorize mutual access between two security groups. For more information, see [Security group overview](/intl.en-US/Security/Security groups/Overview.md).

## Why do I need to select a security group when I create an ECS instance?

When you create ECS instances, you must select security groups to divide the security domains within your application environment and configure security group rules for proper network security isolation.

If you create an ECS instance in the ECS console in a region where you have not created security groups, the instance will be assigned to the default security group. We recommend that you remove the instance from the default security group and add it to a new security group.

## What can I do if I create an ECS instance before I create a security group?

If you have not created any security groups before you create an ECS instance, you can use the default security group. The default security group allows access to common ports such as TCP port 22 and port 3389.

## Why am I being prompted that the maximum number of rules has been reached when I try to add an instance to a security group?

Maximum number of security group rules that can be associated with an ECS instance \(primary ENI\) = Maximum number of security groups to which the instance can be added × Maximum number of rules in each security group.

If you are prompted that **Failed to join the security group. The number of security group rules that have acted on the instance has reached the upper limit**, we recommend that you select another security group.

## If I adjust the maximum number of security groups that a VPC-type ECS instance can belong to, does this adjustment only take effect on security groups created after the limit is adjusted?

No, the adjustment will take effect on all security groups that the VPC-type ECS instance belongs regardless of when these security groups were created.

## In what scenarios do security groups use the default security group rules?

The default security group rules are used in the following scenarios:

-   If you have not created a security group when you create an ECS instance in a region in the ECS console for the first time, you can select a default security group automatically created by the system. The default security group is a basic security group. The default security group uses the default security rules. The default security rule has the priority of 100. It specifies that inbound traffic is allowed over ICMP, SSH port 22, and RDP port 3389 and that the authorization object is all CIDR blocks \(0.0.0.0/0\). You can also choose to allow inbound traffic over HTTP port 80 and HTTPS port 443. All outbound traffic is allowed.
-   You have selected a security group template when you created a security group in the ECS console. The security group template applies to both basic security groups and advanced security groups. Alibaba Cloud provides Web Server Linux templates \(inbound traffic is allowed over port 80, port 443, port 22, and ICMP\), Web Server Windows templates \(inbound traffic is allowed over port 80, port 443, port 3389, and ICMP\), and custom templates \(all inbound access requests are denied\).

## In what scenarios do I need to add a security group rule?

In the following scenarios, you must add a security group rule to ensure that your ECS instances can be accessed:

-   No custom security group rules or default security group rules have been added to the security group to which the ECS instance belongs. When your ECS instance needs to access the Internet or an ECS instance in another security group within the current region, you must add a security rule.
-   The created application uses a specified port or port range instead of the default port. In this case, you must allow the specified port or port range before you can check whether the application is connected. For example, assume you have deployed an NGINX service and need to set the listener port to TCP 8000 but only port 80 is allowed in your security group. In this case, you must add a security rule to ensure that the NGINX service is accessible.
-   For other scenarios, see [Scenarios for security groups](/intl.en-US/Security/Security groups/Scenarios for security groups.md).

## Why can't I configure Internet security group rules for my ECS instance in a VPC?

It is because VPC-type instances can only access the Internet through internal NIC mapping, which makes Internet NICs invisible to the instances. As a result, you can only configure internal network rules in the security groups that your instance belongs to. The security group rules you configure apply to both the internal network and the Internet.

## Why can't I access TCP port 25?

TCP port 25 is the default email service port. For security reasons, port 25 of ECS instances is disabled by default. We recommend that you use port 465 to send emails. For more application scenarios, see [Scenarios](/intl.en-US/Security/Security groups/Scenarios for security groups.md).

## Why can't I access port 80?

See [Check whether TCP port 80 is working properly](https://www.alibabacloud.com/help/faq-detail/59367.htm).

## Why have several internal security group rules been automatically added to my security group?

Rules may be automatically added to your security group in either of the following situations:

-   You have accessed Data Management Service \(DMS\).
-   You have migrated data by using Alibaba Cloud Data Transmission Service \(DTS\). The rules associated with the DTS IP address are automatically added to your security group.

## What happens when a security group rule is configured incorrectly?

If a security group rule is configured incorrectly, the ECS instances associated with this rule cannot communicate with other devices through the internal network or the Internet. These are examples of the effects:

-   You cannot access Linux ECS instances remotely by using SSH or access Windows ECS instances by using the Remote Desktop Protocol \(RDP\).
-   The public IP addresses of ECS instances cannot be `pinged`.
-   The web services provided by the ECS instances cannot be accessed through HTTP or HTTPS.
-   The ECS instances associated with this rule cannot communicate with other ECS instances through the internal network.

## Are the inbound and outbound rules in a security group counted separately?

No, the inbound rules and outbound rules of a security group are counted together. The total number of inbound rules and outbound rules for each security group cannot exceed 200. For more information, see [Limits](/intl.en-US/Product Introduction/Limits.md).

## Can I adjust the maximum number of rules that can be added to a security group?

No, each security group can contain a maximum of 200 security group rules. Each ENI of an ECS instance can be added to up to five security groups, allowing each ENI of an ECS instance to be associated with up to 1,000 security group rules.

If the maximum number of rules in each security group has been reached but you need to add more security group rules, perform the following steps:

1.  Check whether redundant rules exist. You can also [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to ask Alibaba Cloud technical support personnel to check for you.
2.  If any redundant rules exist, delete them and then add new security group rules. If no redundant rules exist, create more security groups and add new security group rules.

## What can I do if I receive a notification that my website has been blocked due to illegal activities and needs to be rectified?

You can check the records of harmful Internet information to view domain names or URLs with harmful information, penalty actions, reasons, and duration. After you are sure that the harmful information from your domain name or URL has been cleared or does not exist, you can apply to unblock the domain name or URL. For more information, see [Harmful Internet information](https://www.alibabacloud.com/help/doc-detail/84438.htm).

## What can I do if I receive a notification that my website has been penalized for committing external attacks?

You can check the penalty records to view the details about penalty actions, reasons, and duration. If you do not agree with the penalty measure, provide your feedback and file an appeal. After receiving your feedback on the penalty records, Alibaba Cloud will verify the penalty again, check whether the penalty is correct and effective, and determine whether to maintain or immediately terminate the penalty. For more information, see [View the penalty list](https://www.alibabacloud.com/help/doc-detail/84434.htm).

## How can I view the resource quota?

For more information about how to view the limits and quotas of resources, see [Limits](/intl.en-US/Product Introduction/Limits.md).

