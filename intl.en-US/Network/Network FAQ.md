---
keyword: [outbound bandwidth, website access failure, IP address query, traffic monitoring]
---

# Network FAQ

This topic provides answers to commonly asked questions about networks used by ECS instances.

-   Network performance FAQ
    -   [What is the packet loss rate when instances in different regions communicate over the Internet?](#section_t34_uni_zg6)
    -   [How is the network latency for instances within the same region that communicate over the internal network?](#section_vjv_lqq_ymq)
-   Public bandwidth FAQ
    -   [What are the inbound and outbound bandwidths of ECS instances?](#section_pv3_qbl_qgb)
    -   [I purchased a public bandwidth of 5 Mbit/s for an ECS instance. How is this bandwidth applied to the inbound and outbound bandwidths of the instance?](#section_v44_ona_zjq)
    -   [Is public bandwidth exclusive to each ECS instance, or is public bandwidth shared across multiple instances?](#section_sp8_7jn_p3g)
    -   [How is the network usage of ECS instances billed?](#section_hex_69p_rar)
    -   [Why has 200 Kbit/s of inbound traffic already been consumed on a newly created ECS instance?](#section_duq_s7w_t96)
    -   [How do I view the Internet traffic statistics of an ECS instance?](#section_r5a_u6t_chb)
    -   [Why is the bandwidth usage of my ECS instance displayed in the Cloud Monitor console different from that displayed in the ECS console?](#section_tsb_lpy_gvz)
    -   [My ECS instance has been stopped. Why am I still being charged for its outbound traffic on a pay-as-you-go basis?](#section_d7h_fs2_xu8)
-   IP addresses FAQ
    -   [How do I query IP addresses of ECS instances?](#section_vpl_qbg_qgb)
    -   [How do I disable the public NIC of an ECS instance?](#section_bxf_ywf_qgb)
-   FAQ about network access and traffic direction
    -   [Why am I unable to access a website that is hosted on an ECS instance? A message similar to "Sorry, your access has been blocked because the requested URL may pose a security threat to the website" is displayed.](#section_cwr_y3g_4gb)
    -   [An unusual logon has been detected on one of my ECS instances. What do I do?](#section_mgg_dhg_4gb)
    -   [What is traffic scrubbing?](#section_4xo_and_tfv)
    -   [How do I cancel traffic scrubbing for an ECS instance?](#section_r2g_vg8_gtv)
    -   [How do I request reverse lookup for an ECS instance?](#section_24x_y33_pml)
    -   [Can an IP address point to multiple reverse lookup domain names?](#section_0u1_fng_nzy)
-   FAQ about public IP addresses
    -   [Can I change the public IPv4 address of an instance after the instance has been created?](#section_c7c_7n5_fae)
    -   [Why am I unable to find the option to change the public IP address of an ECS instance in the ECS console?](#section_y27_eqe_lgp)
    -   [Can I change the private IP address of an instance?](#section_q67_0xd_eps)
    -   [If no public IPv4 address was assigned to an ECS instance during instance creation, how do I assign a public IP address to the instance?](#section_9rr_e3x_ks1)
-   Network basic FAQ
    -   [What is a BGP data center?](#section_hmd_spf_qgb)
    -   [What are WAN and LAN?](#section_o52_nlg_4gb)
    -   [What is CIDR?](#section_jua_0tj_q5m)
    -   [How do I express a subnet mask?](#section_nw6_q4l_pdt)
    -   [How do I plan subnets?](#section_g8p_l4s_2e8)
-   Quota FAQ
    -   [How do I view the resource quota?](#section_ubf_rd5_utp)

## What is the packet loss rate when instances in different regions communicate over the Internet?

When instances in different regions communicate through Cloud Enterprise Network \(CEN\), they use Alibaba Cloud backbone networks to transmit data. Alibaba Cloud aims to provide network services with a P99 packet loss rate of less than 0.0001% per hour.

## How is the network latency for instances within the same region that communicate over the internal network?

You can achieve minimum latency when instances within the same zone and region communicate with each other over the internal network. The P99 one-way latency for communication between instances within the same zone is less than 180 µs.

## What are the inbound and outbound bandwidths of ECS instances?

|Bandwidth type|Description|
|:-------------|:----------|
|Inbound bandwidth|The bandwidth of inbound traffic for an ECS instance, such as: -   Traffic generated when you download external resources to the ECS instance
-   Traffic generated when you upload resources to the ECS instance through an FTP client |
|Outbound bandwidth|The bandwidth of outbound traffic for an ECS instance, such as: -   Traffic generated when the ECS instance provides external access
-   Traffic generated when you download resources from the ECS instance through an FTP client |

## I purchased a public bandwidth of 5 Mbit/s for an ECS instance. How is this bandwidth applied to the inbound and outbound bandwidths of the instance?

The 5 Mbit/s that you purchased applies to the outbound bandwidth. The inbound bandwidth for this instance is capped at 10 Mbit/s.

-   Outbound bandwidth is consumed when data is sent from the ECS instance. The maximum outbound bandwidth of an ECS instance is capped at 100 Mbit/s or 200 Mbit/s regardless of whether the instance resides in a VPC or the classic network. The maximum available outbound bandwidth value depends on the billing method of the instance. For more information, see [Public bandwidth limits](/intl.en-US/Product Introduction/Limits.md)。
-   Inbound bandwidth is consumed when data is transferred to the ECS instance. The maximum inbound bandwidth is determined by the outbound bandwidth:
    -   If the outbound bandwidth is less than 10 Mbit/s, the maximum inbound bandwidth is 10 Mbit/s.
    -   If the outbound bandwidth is greater than 10 Mbit/s, the maximum inbound bandwidth is the same as the purchased outbound bandwidth.

## Is public bandwidth exclusive to each ECS instance, or is public bandwidth shared across multiple instances?

The public bandwidth of each instance is exclusive to the instance for which it is purchased.

## How is the network usage of ECS instances billed?

For more information, see [Public bandwidth](/intl.en-US/Pricing/Billing items/Public bandwidth.md).

## Why has 200 Kbit/s of inbound traffic already been consumed on a newly created ECS instance?

The traffic was generated by Address Resolution Protocol \(ARP\) broadcast packets. Each ECS instance is assigned to a large CIDR block. When the gateway receives an ARP request packet for an ECS instance, the gateway broadcasts this packet to all ECS instances within the same CIDR block. The newly created instance also receives the packet. If no requests for the IP address of your new ECS instance are sent, the instance does not need to send an ARP response packet.

## How do I view the Internet traffic statistics of an ECS instance?

To view the Internet traffic statistics of an ECS instance, perform the following steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
2.  In the top navigation bar of the ECS console, choose **Expense** \> **User Center**.
3.  In the left-side navigation pane, choose **Bill** \> **Bill**.
4.  On the Bills page, click the **Bills** tab. Specify a billing cycle, and set **Product Detail** to **Elastic Compute Service \(ECS\) - Pay by quantity** and **Subscription Type** to **Pay-As-You-Go**.
5.  Click **Export Billing Overview \(CSV\)**. In the Export Billing Overview \(CSV\) dialog box, enter the CAPTCHA verification characters and click **OK**.
6.  Open the exported CSV file to view the Internet traffic statistics of the ECS instance.

## Why is the bandwidth usage of my ECS instance displayed in the Cloud Monitor console different from that displayed in the ECS console?

ECS instances function as backend servers for Server Load Balancer \(SLB\) instances and use the Layer-7 HTTP forwarding model. In this forwarding model, SLB instances forward client requests to ECS instances, and the ECS instances use their own outbound bandwidth to return responses to the corresponding users. The bandwidth consumed by these responses is not displayed in the ECS console, but the traffic generated by the responses is counted towards the outbound traffic of the SLB instances and displayed in the Cloud Monitor console. As a result, the bandwidth usage of your ECS instance displayed in the Cloud Monitor console is different from that displayed in the ECS console.

## My ECS instance has been stopped. Why am I still being charged for its outbound traffic on a pay-as-you-go basis?

-   Problem description: Your instance is in the **Stopped** state in the ECS console, but is in the **Cleaning** state in the Anti-DDoS Basic console. You are charged for outbound traffic from the instance on a pay-as-you-go basis every hour.
-   Cause: HTTP flood protection is enabled for the ECS instance. When HTTP flood protection is enabled, the security mechanism sends probe packets to potential attack sources, generating a large volume of outbound traffic.
-   Solution: Disable HTTP flood protection for the ECS instance.

## How do I query IP addresses of ECS instances?

-   Linux instance

    Run the `ifconfig` command to view NIC information. You can view the IP addresses, subnet masks, gateways, DNS servers, and MAC addresses in the command output.

-   Windows instance

    In Command Prompt, run the `ipconfig /all` command to view NIC information. You can view the IP addresses, subnet masks, gateways, DNS servers, and MAC addresses in the command output.


## How do I disable the public NIC of an ECS instance?

-   Linux instance
    1.  Run the `ifconfig` command to view the public NIC name of the instance.
    2.  Run the `ifdown` command to disable the public NIC. For example, if the name of the public NIC is `eth1`, enter `ifdown eth1`.

        **Note:** You can run the ifup command to re-enable the NIC. For example, if the name of the public NIC is `eth1`, enter `ifup eth1`.

-   Windows instance
    1.  In Command Prompt, run the `ipconfig` command to view information about the public NIC.
    2.  Open the **Control Panel** and click View network status and tasks under Network and Internet. In the **Network and Sharing Center** window, click **Change adapter settings** in the left-side navigation pane to disable the public NIC.

## Why am I unable to access a website that is hosted on an ECS instance? A message similar to "Sorry, your access has been blocked because the requested URL may pose a security threat to the website" is displayed.

-   Problem description: When you attempt to access a website built on an ECS instance, you are prompted with a message similar to "Sorry, your access has been blocked because the requested URL may pose a security threat to the website."
-   Cause: Web Application Firewall \(WAF\) has identified your access request to the URL as an attack and blocked your access.
-   Solution: Add the source public IP address that you use to access the website to the WAF whitelist. For more information, see [Avoid Anti-DDoS Basic false positives by using a whitelist]().

## An unusual logon has been detected on one of my ECS instances. What do I do?

Perform the following operations to resolve the issue:

1.  Check the logon time to see whether the logon was performed by you or another administrator.
2.  If the logon was not performed by you or another administrator, it is an unauthorized logon. Perform the following steps:
    1.  Reset the password. For more information, see [Reset the logon password of an instance](/intl.en-US/Instance/Manage instances/Reset the logon password of an instance.md).
    2.  Check whether the ECS instance has been infected.
    3.  Configure security groups to allow access only from specific IP addresses. For more information, see [Scenarios for security groups](/intl.en-US/Security/Security groups/Scenarios for security groups.md).

## What is traffic scrubbing?

The traffic scrubbing service monitors inbound traffic to ECS instances in real time and identifies unusual traffic such as DDoS attacks. By default, Anti-DDoS Basic is enabled on ECS instances to provide traffic scrubbing. When ECS instances are under attack, the traffic scrubbing service will automatically detect the attack and scrub malicious traffic without affecting ECS instance services. When unusual traffic is detected, suspicious traffic is redirected from the destination network to a scrubbing device. The device identifies and removes malicious traffic and then returns legitimate traffic to the network to be forwarded to the ECS instances.

## How do I cancel traffic scrubbing for an ECS instance?

1.  Log on to the [Alibaba Cloud Security Anti-DDoS Basic console](https://yundun.console.aliyun.com/?p=ddosnext).
2.  Click the ECS tab. In the ECS instance list, find the IP address of an ECS instance that is in the cleaning state. Click **View Details**.
3.  Click **Cancel cleaning**.

    ![Cancel traffic scrubbing](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6357298951/p50257.png)


## How do I request reverse lookup for an ECS instance?

Reverse lookup is used in mail services to reject mail from IP addresses mapped to unregistered domain names. Most spammers use dynamic IP addresses or IP addresses mapped to unregistered domain names to send unwanted emails and avoid being tracked. When reverse lookup is enabled on a mail server, the server rejects mail sent from dynamic IP addresses or unregistered domain names to reduce the amount of spam received.

You can [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to request reverse lookup for your ECS instance. To make your ticket easier to process, we recommend that you specify the region, public IP address, and registered domain name of your ECS instance in the ticket.

After your request is approved, you can run the dig command to check whether reverse lookup has taken effect for your instance. Example:

```
dig -x 121.196.255.** +trace +nodnssec
```

If information similar to the following content is displayed in the command output, reverse lookup is enabled on your instance.

```
1.255.196.121.in-addr.arpa. 3600 IN PTR ops.alidns.com.
```

## Can an IP address point to multiple reverse lookup domain names?

No, each IP address can point only to a single reverse lookup domain name. For example, you cannot configure the IP address 121.196.255.\*\* to resolve to multiple domain names such as mail.abc.com, mail.ospf.com, and mail.zebra.com.

## Can I change the public IPv4 address of an instance after the instance has been created?

You can change the public IPv4 address of an instance within six hours after instance creation. For more information, see [Change the public IP address of an ECS instance](/intl.en-US/Network/Change IPv4 addresses/Change the public IP address of an ECS instance.md).

After six hours, whether the public IP address of the instance can be changed depends on the instance network type.

-   For an instance in a VPC, you can change the public IP address of the instance by converting the IP address into an EIP. Then, disassociate the EIP from the instance and associate a new EIP with the instance or upgrade public bandwidth of the instance to assign a new public IP address. For more information, see [Convert the public IP address of a VPC-type instance to an Elastic IP address](/intl.en-US/Network/Change IPv4 addresses/Convert the public IP address of a VPC-type instance to an Elastic IP address.md).
-   The public IP addresses of instances in the classic network cannot be changed. However, you can convert public IP addresses to EIPs when you release the instance. For more information, see [Convert a public IP address in a classic network to an Elastic IP address](/intl.en-US/Network/Change IPv4 addresses/Convert the public IP address of a classic network-type instance to an Elastic IP address.md).

## Why am I unable to find the option to change the public IP address of an ECS instance in the ECS console?

-   Within six hours after a pay-as-you-go instance is created: If No Fees for Stopped Instances \(VPC-Connected\) is enabled for your account, you must select Retain Instance and Continue Charging After Instance Is Stopped when you stop the pay-as-you-go instance. Otherwise, the option to change the public IP address will not be displayed in the ECS console after the instance is stopped.
-   If more than six hours have passed after the instance was created: You cannot change the public IP address and the option is not displayed.

## Can I change the private IP address of an instance?

-   For instances in VPCs: You can change the private IP address of an instance. For more information, see [Change the private IP address of an instance](/intl.en-US/Network/Change IPv4 addresses/Change the private IP address of an instance.md).
-   For instances in the classic network: You cannot change the private IP address of an instance.

## If no public IPv4 address was assigned to an ECS instance during instance creation, how do I assign a public IP address to the instance?

-   Apply for and bind an Elastic IP Address \(EIP\) to the ECS instance. For more information, see the following topic of *EIP documentation:* [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).
-   Modify the public bandwidth of the ECS instance to allocate a fixed public IP address. For more information about modifying the public bandwidth of a subscription ECS instance, see [Overview of instance upgrade and downgrade](/intl.en-US/Instance/Change configurations/Overview of instance upgrade and downgrade.md). For more information about modifying the public bandwidth of a pay-as-you-go ECS instance, see [Modify the bandwidth configurations of pay-as-you-go instances](/intl.en-US/Instance/Change configurations/Modify bandwidth configurations/Modify the bandwidth configurations of pay-as-you-go instances.md).

## What is a BGP data center?

Border Gateway Protocol \(BGP\) is used to interconnect autonomous systems \(AS\) over the Internet. The main function of BGP is to control route propagation and select the best routes.

China Netcom, China Telecom, China Railcom, and some large privately owned IDC service providers all have autonomous system numbers \(ASNs\). Most major network carriers in China use BGP to implement multi-line interconnections between their ASNs.

To achieve multi-line interconnection in this manner, an IDC must obtain a CIDR block and an ASN from the China Internet Network Information Center \(CNNIC\) or Asia-Pacific Network Information Center \(APNIC\), and then broadcast this CIDR block to the networks of other carriers by using BGP. After networks are interconnected through BGP, the backbone routers of the network carriers will determine the optimal routes to the CIDR block of the IDC to ensure high-speed access for users of different network carriers.

## What are WAN and LAN?

-   A wide area network \(WAN\) is also known as an external or public network. A WAN is a telecommunications network that connects smaller networks such as local area networks \(LANs\) and metro area networks \(MANs\). Each WAN extends over a large geographical area which may be as small as a city or as large as an entire continent to provide telecommunications services and form an international telecommunications network. WAN is not the same as the Internet.
-   A LAN is also known as an internal network. A LAN is a network that interconnects computers within a small area. Users can manage files, share application software and printers, schedule work for work groups, and communicate with each other such as by sending emails or faxes within a LAN. A LAN is a closed network that can be as small as two computers in an office or as large as thousands of computers in a company. In Alibaba Cloud, ECS instances within the same region can be created in the same type of networks and communicate with each other through the internal network. ECS instances in different regions are isolated from each other.

## What is CIDR?

Classless Inter-Domain Routing \(CIDR\) is a new addressing scheme for the Internet that allows for more efficient allocation of IP addresses than the old Class A, B, and C address scheme. CIDR notation is used to simplify how a range of IP addresses are represented. The CIDR notation consists of an IP address and a forward slash followed by a decimal number that denotes how many bits are in the network prefix.

-   Example 1: Convert a CIDR block to an IP address range

    For example, you can convert the CIDR block 10.0.0.0/8 to a 32-bit binary IP address of 00001010.00000.000000000000000000000000. In this CIDR block, /8 represents an 8-bit network ID. The first 8 bits of the 32-bit binary IP address are fixed, and the corresponding IP addresses are from 00001010.00000000.00000000.00000000 to 00001010.11111111.11111111.11111111. After you convert the preceding IP addresses to the decimal format, the CIDR block 10.0.0.0/8 indicates IP addresses from 10.0.0.0 to 10.255.255.255 with a subnet mask of 255.0.0.0.

-   Example 2: Convert an IP address range to a CIDR block

    For example, assume that you have a range of IP addresses from 192.168.0.0 to 192.168.31.255. You can convert the last two parts of the first and last IP addresses to binary numbers from 00000000.00000000 to 00011111.11111111. The first 19 \(8 × 2 + 3\) bits are fixed. After you convert the IP addresses to the CIDR format, the corresponding CIDR block is 192.168.0.0/19.


## How do I express a subnet mask?

You can use one of the following methods to express a subnet mask:

-   Dotted decimal notation.

    The default subnet mask of a Class A network is 255.0.0.0.

-   Append a forward slash \(/\) and a number ranging from 1 to 32 to the end of an IP address to define a subnet mask. The number indicates the length of the network identification bit in the subnet mask.

    Example: 192.168.0.3/24.


## How do I plan subnets?

For information about the best practices for planning subnets, see [Plan and design a VPC](/intl.en-US/Quick Start/Set up network connections.md).

## How can I view the resource quota?

For more information about how to view the limits and quotas of resources, see [Limits](/intl.en-US/Product Introduction/Limits.md).

