---
keyword: [ECS instance family, instance family]
---

# Instance families

An ECS instance is the smallest unit that can provide compute capabilities and services for your business. Compute capabilities vary based on instance types. This topic describes available ECS instance families and the features, specifications, and application scenarios of each instance family.

ECS instances are categorized into different instance families based on their usage scenarios. Each instance family is divided into different instance types based on their CPU and memory specifications. ECS instance type defines the basic properties of an ECS instance, such as CPU, clock speed, and memory. In addition to the instance type, you must also configure the Elastic Block Storage \(EBS\) devices, image, and network type when you create an ECS instance.

**Note:** The available instance families and types vary based on regions. You can go to the [ECS Instance Types Available for Each Region](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) page to view the available instance types in each region.

Enterprise scenarios have high requirements for business stability. Alibaba Cloud ECS instance families are divided into enterprise-level and shared instance families based on whether the instance families are suitable for enterprise scenarios. Enterprise-level instance families offer consistent performance and dedicated resources. In enterprise-level instance families, each vCPU corresponds to a hyperthread of the Intel ® Xeon ® core. For more information about the differences between enterprise-level and shared instance families, see [ECS instance FAQ](/intl.en-US/Instance/ECS instance FAQ.md).

You can upgrade or downgrade instance types within an instance family or across instance families. For more information, see [Change instance types of instances](/intl.en-US/Instance/Change configurations/Change instance types of instances.md).

For information about how to choose instance families based on scenarios, see [Best practices for instance type selection](/intl.en-US/Best Practices/Best practices for instance type selection.md).

Alibaba Cloud ECS instances are categorized into the following instance families:

|Enterprise-level computing instance families based on the x86 architecture:|
|---------------------------------------------------------------------------|
|Recommended intance families|Other available instance families|
|-   [g6, general purpose instance family](#g6)
-   [g6a, general purpose instance family](#g6a)
-   [g6t, security-enhanced general purpose instance family](#g6t)
-   [g6e, general purpose instance family with enhanced performance](#g6e)
-   [g5, general purpose instance family](#g5)
-   [g5se, storage enhanced instance family](#g5se)
-   [g5ne, network enhanced instance family](#g5ne)
-   [ic5, compute intensive instance family](#ic5)
-   [c6, compute optimized instance family](#c6)
-   [c6a, compute optimized instance family](#c6a)
-   [c6t, security-enhanced compute optimized instance family](#c6t)
-   [c6e, compute optimized instance family with enhanced performance](#c6e)
-   [c5, compute optimized instance family](#c5)
-   [r6, memory optimized instance family](#r6)
-   [r6a, memory optimized instance family](#r6a)
-   [r6e, memory optimized instance family with enhanced performance](#r6e)
-   [re6, high memory instance family](#re6)
-   [r5, memory optimized instance family](#r5)
-   [d2c, compute intensive big data instance family](#d2c)
-   [d2s, storage intensive big data instance family](#d2s)
-   [d1ne, big data instance family with enhanced network performance](#d1ne)
-   [i2, instance family with local SSDs](#i2)
-   [i2g, instance family with local SSDs](#i2g)
-   [i2ne, instance family with local SSDs](#i2ne)
-   [i2gne, instance family with local SSDs](#i2gne)
-   [hfc7, compute optimized instance family with high clock speed](#hfc7)
-   [hfc6, compute optimized instance family with high clock speed](#hfc6)
-   [hfg7, general purpose instance family with high clock speed](#hfg7)
-   [hfg6, general purpose instance family with high clock speed](#hfg6)
-   [hfr7, memory optimized instance family with high clock speed](#hfr7)
-   [hfr6, memory optimized instance family with high clock speed](#hfr6)

|-   [sn2ne, general purpose instance family with enhanced network performance](#sn2ne)
-   [sn1ne, compute optimized instance family with enhanced network performance](#sn1ne)
-   [re4, high memory instance family](#re4)
-   [re4e, high memory instance family](#re4e)
-   [se1ne, memory optimized instance family with enhanced network performance](#se1ne)
-   [se1, memory optimized instance family](#se1)
-   [d1, big data instance family](#d1)
-   [i1, instance family with local SSDs](#i1)
-   [hfc5, compute optimized instance family with high clock speed](#hfc5)
-   [hfg5, general purpose instance family with high clock speed](#hfg5) |

|Enterprise-level heterogeneous computing instance families:|
|-----------------------------------------------------------|
|Recommended intance families|Other available instance families|
|-   [vgn6i, lightweight GPU-accelerated compute optimized instance family](#vgn6i)
-   [gn6i, GPU-accelerated compute optimized instance family](#gn6i)
-   [gn6e, GPU-accelerated compute optimized instance family](#gn6e)
-   [gn6v, GPU-accelerated compute optimized instance family](#gn6v)
-   [f3, FPGA-accelerated compute optimized instance family](#f3)

|-   [vgn5i, lightweight GPU-accelerated compute optimized instance family](#vgn5i)
-   [gn5, GPU-accelerated compute optimized instance family](#gn5)
-   [gn5i, GPU-accelerated compute optimized instance family](#gn5i)
-   [gn4, GPU-accelerated compute optimized instance family](#gn4)
-   [f1, FPGA-accelerated compute optimized instance family](#f1) |

|ECS Bare Metal Instance families and Super Computing Cluster \(SCC\) instance families:|
|---------------------------------------------------------------------------------------|
|Recommended intance families|Other available instance families|
|-   [ebmgn6e, GPU-accelerated compute optimized ECS Bare Metal Instance family](#ebmgn6e)
-   [ebmgn6v, GPU-accelerated compute optimized ECS Bare Metal Instance family](#ebmgn6v)
-   [ebmgn6i, GPU-accelerated compute optimized ECS Bare Metal Instance family](#ebmgn6i)
-   [ebmc6a, compute optimized ECS Bare Metal Instance family](#ebmc6a)
-   [ebmc6e, compute optimized ECS Bare Metal Instance family with enhanced performance](#ebmc6e)
-   [ebmc6, compute optimized ECS Bare Metal Instance family](#ebmc6)
-   [ebmg6a, general purpose ECS Bare Metal Instance family](#ebmg6a)
-   [ebmg6e, general purpose ECS Bare Metal Instance family with enhanced performance](#ebmg6e)
-   [ebmg6, general purpose ECS Bare Metal Instance family](#ebmg6)
-   [ebmr6a, memory optimized ECS Bare Metal Instance family](#ebmr6a)
-   [ebmr6e, memory optimized ECS Bare Metal Instance family with enhanced performance](#ebmr6e)
-   [ebmr6, memory optimized ECS Bare Metal Instance family](#ebmr6)
-   [ebmhfc6, compute optimized ECS Bare Metal Instance family with high clock speed](#ebmhfc6)
-   [ebmhfg6, general purpose ECS Bare Metal Instance family with high clock speed](#ebmhfg6)
-   [ebmhfr6, memory optimized ECS Bare Metal Instance family with high clock speed](#ebmhfr6)
-   [ebmre6p, non-volatile memory optimized ECS Bare Metal Instance family with enhanced performance](#ebmre6p)
-   [ebmre6-6t, memory optimized ECS Bare Metal Instance family with enhanced performance](#ebmre6-6t)
-   [scchfc6, compute optimized SCC instance family with high clock speed](#scchfc6)
-   [scchfg6, general purpose SCC instance family with high clock speed](#scchfg6)
-   [scchfr6, memory optimized SCC instance family with high clock speed](#scchfr6)
-   [scch5, SCC instance family with high clock speed](#scch5)
-   [sccg5, general purpose SCC instance family](#sccg5)
-   [sccgn6, GPU-accelerated compute optimized SCC instance family](#sccgn6)

|-   [ebmc5s, compute optimized ECS Bare Metal Instance family with enhanced network performance](#ebmc5s)
-   [ebmg5s, general purpose ECS Bare Metal Instance family with enhanced network performance](#ebmg5s)
-   [ebmr5s, memory optimized ECS Bare Metal Instance family with enhanced network performance](#ebmr5s)
-   [ebmg5, general purpose ECS Bare Metal Instance family](#ebmg5)
-   [ebmhfg5, ECS Bare Metal Instance family with high clock speed](#ebmhfg5)
-   [ebmc4, compute optimized ECS Bare Metal Instance family](#ebmc4) |

|Shared computing instance families based on the x86 architecture:|
|-----------------------------------------------------------------|
|Recommended intance families|Other available instance families|
|-   [t6, burstable instance family](#t6)
-   [s6, shared standard instance family](#s6)

|-   [t5, burstable instance family](#t5)
-   [v5, CPU overprovisioned instance family](#v5)
-   [xn4, n4, mn4, and e4, previous-generation shared instance families](#xn4-n4-mn4-e4) |

For information about retired instance families, see [Phased-out instance types](/intl.en-US/Instance/Phased-out instance types.md).

## g6, general purpose instance family

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies based on instance families. A single g6 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see [g5se, memory optimized instance family with enhanced performance](/intl.en-US/Instance/Instance families.md).

-   Provides high storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides an ultra-high packet forwarding rate.

    **Note:** The maximum network performance varies based on instance families. For higher concurrent connection capabilities, we recommend that you use g5ne. For more information, see [g5ne, network enhanced instance family](/intl.en-US/Instance/Instance families.md).

-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Supports instance type changes to c6 or r6.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Websites and application servers
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.g6.large|2|8.0|None|1.0|3.0|300|Yes|Up to 250|2|2|6|10.0|1|
|ecs.g6.xlarge|4|16.0|None|1.5|5.0|500|Yes|Up to 250|4|3|10|20.0|1.5|
|ecs.g6.2xlarge|8|32.0|None|2.5|8.0|800|Yes|Up to 250|8|4|10|25.0|2|
|ecs.g6.3xlarge|12|48.0|None|4.0|10.0|900|Yes|Up to 250|8|6|10|30.0|2.5|
|ecs.g6.4xlarge|16|64.0|None|5.0|10.0|1,000|Yes|300|8|8|20|40.0|3|
|ecs.g6.6xlarge|24|96.0|None|7.5|10.0|1,500|Yes|450|12|8|20|50.0|4|
|ecs.g6.8xlarge|32|128.0|None|10.0|None|2,000|Yes|600|16|8|20|60.0|5|
|ecs.g6.13xlarge|52|192.0|None|12.5|None|3,000|Yes|900|32|7|20|100.0|8|
|ecs.g6.26xlarge|104|384.0|None|25.0|None|6,000|Yes|1,800|32|15|20|200.0|16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## g6a, general purpose instance family

g6a is in invitational preview. To use g6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   Compute:
    -   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
    -   Offers a CPU-to-memory ratio of 1:4.
    -   Allows you to enable or disable Hyper-Threading.

        **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Storage:
    -   I/O optimized.
    -   Supports enhanced SSDs \(ESSDs\), standard SSDs, and ultra disks.
    -   Provides high storage I/O performance based on large computing capacity.

        **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Network:
    -   Provides an ultra-high packet forwarding rate.
    -   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Video encoding and decoding
    -   Scenarios where large volumes of packets are received and transmitted
    -   Websites and application servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Game servers
    -   Test and development, such as DevOps
    -   Other general purpose enterprise-level applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|-------------------------|------------------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.g6a.large|2|8.0|None|1.0|10.0|900|Yes|2|12.5|1.0|
|ecs.g6a.xlarge|4|16.0|None|1.5|10.0|1,000|Yes|3|20.0|1.5|
|ecs.g6a.2xlarge|8|32.0|None|2.5|10.0|1,600|Yes|4|30.0|2.0|
|ecs.g6a.4xlarge|16|64.0|None|5.0|10.0|2,000|Yes|8|60.0|3.0|
|ecs.g6a.8xlarge|32|128.0|None|8.0|10.0|3,000|Yes|7|75.0|4,0|
|ecs.g6a.16xlarge|64|256.0|None|16.0|None|6,000|Yes|8|150.0|8.0|
|ecs.g6a.32xlarge|128|512.0|None|32.0|None|12,000|Yes|15|300.0|16.0|
|ecs.g6a.64xlarge|256|1,024.0|None|64.0|None|24,000|Yes|15|600.0|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## g6t, security-enhanced general purpose instance family

g6t is in invitational preview.

Features

-   Implements trusted boot based on the Trusted Platform Module \(TPM\) chip. During a trusted boot, each module in the boot chain from the underlying hardware to the guest OS is measured and verified.
-   Supports comprehensive monitoring on the IaaS layer and provides trusted capabilities of the whole IaaS layer.
-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture. g6t improves storage performance, network performance, and computing stability by an order of magnitude through fast path acceleration of X-Dragon chips.
-   Compute:
    -   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
    -   Offers a CPU-to-memory ratio of 1:4.
    -   Allows you to enable or disable Hyper-Threading.

        **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Storage:
    -   I/O optimized.
    -   Supports ESSDs only.
    -   Provides high storage I/O performance based on large computing capacity.

        **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Network:
    -   Provides an ultra-high packet forwarding rate.
    -   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios that require high security and enhanced trust, such as financial services, government affairs, and enterprise services
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Websites and application servers
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|TPM support|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|-----------|------------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.g6t.large|2|8.0|None|A burstable bandwidth of up to 10.0|900|Yes|Yes|Up to 250|2|3|6|20.0|1.0|
|ecs.g6t.xlarge|4|16.0|None|A burstable bandwidth of up to 10.0|1,000|Yes|Yes|Up to 250|4|4|15|40.0|1.5|
|ecs.g6t.2xlarge|8|32.0|None|A burstable bandwidth of up to 10.0|1,600|Yes|Yes|Up to 250|8|4|15|50.0|2.0|
|ecs.g6t.4xlarge|16|64.0|None|A burstable bandwidth of up to 10.0|3,000|Yes|Yes|300|8|8|30|80.0|3.0|
|ecs.g6t.8xlarge|32|128.0|None|10.0|6,000|Yes|Yes|600|16|8|30|150.0|5.0|
|ecs.g6t.13xlarge|52|192.0|None|16.0|9,000|Yes|Yes|900|32|7|30|240.0|8.0|
|ecs.g6t.26xlarge|104|384.0|None|32.0|24,000|Yes|Yes|1,800|32|15|30|480.0|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   The results for network capabilities are the maximum values obtained from single item tests. For example, when network bandwidth is tested, no stress tests are performed on the packet forwarding rate or other metrics of the network.

## g6e, general purpose instance family with enhanced performance

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture. g6e improves storage performance, network performance, and computing stability by an order of magnitude through fast path acceleration of X-Dragon chips.
-   I/O optimized.
-   Supports ESSDs only.
-   Provides high network and storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Provides an ultra-high packet forwarding rate.

    **Note:** The maximum network performance varies based on instance families. For higher concurrent connection capabilities, we recommend that you use g5ne. For more information, see [g5ne, network enhanced instance family](/intl.en-US/Instance/Instance families.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 \(Cascade\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Websites and application servers
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|--------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.g6e.large|2|8.0|None|A burstable bandwidth of up to 10.0|900|Yes|Up to 250|2|3|6|20.0|1.0|
|ecs.g6e.xlarge|4|16.0|None|A burstable bandwidth of up to 10.0|1,000|Yes|Up to 250|4|4|15|40.0|1.5|
|ecs.g6e.2xlarge|8|32.0|None|A burstable bandwidth of up to 10.0|1,600|Yes|Up to 250|8|4|15|50.0|2.0|
|ecs.g6e.4xlarge|16|64.0|None|A burstable bandwidth of up to 10.0|3,000|Yes|300|8|8|30|80.0|3.0|
|ecs.g6e.8xlarge|32|128.0|None|10.0|6,000|Yes|600|16|8|30|150.0|5,0|
|ecs.g6e.13xlarge|52|192.0|None|16.0|9,000|Yes|900|32|7|30|240.0|8.0|
|ecs.g6e.26xlarge|104|384.0|None|32.0|24,000|Yes|1,800|32|15|30|480.0|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   The results for network capabilities are the maximum values obtained from single item tests. For example, when network bandwidth is tested, no stress tests are performed on the packet forwarding rate or other metrics of the network.

## g5, general purpose instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies based on instance families. A single g5 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see [g5se, memory optimized instance family with enhanced performance](/intl.en-US/Instance/Instance families.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Provides an ultra-high packet forwarding rate.

    **Note:** The maximum network performance varies based on instance families. For higher concurrent connection capabilities, we recommend that you use g5ne. For more information, see [g5ne, network enhanced instance family](/intl.en-US/Instance/Instance families.md).

-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) or 8269CY \(Cascade Lake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.g5.large|2|8.0|None|1.0|300|Yes|2|2|6|
|ecs.g5.xlarge|4|16.0|None|1.5|500|Yes|2|3|10|
|ecs.g5.2xlarge|8|32.0|None|2.5|800|Yes|2|4|10|
|ecs.g5.3xlarge|12|48.0|None|4.0|900|Yes|4|6|10|
|ecs.g5.4xlarge|16|64.0|None|5.0|1,000|Yes|4|8|20|
|ecs.g5.6xlarge|24|96.0|None|7.5|1,500|Yes|6|8|20|
|ecs.g5.8xlarge|32|128.0|None|10.0|2,000|Yes|8|8|20|
|ecs.g5.16xlarge|64|256.0|None|20.0|4,000|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## g5se, memory optimized instance family with enhanced performance

g5se is currently under invitational preview. To use g5se, you must [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features:

-   A single g5se instance attached with enhanced SSDs \(ESSDs\) can deliver a random read/write IOPS of up to 1,000,000 and a throughput of up to 32 Gbit/s.
-   You can create g5se instances only on dedicated hosts.

    **Note:** For information about other types of instances that can be created on dedicated hosts, see [Dedicated host types](/intl.en-US/Product Introduction/Dedicated host types.md).

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides strong storage I/O performance with a large compute capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Suitable for the following scenarios:
    -   I/O-intensive scenarios, such as medium and large OLTP core databases
    -   Medium and large NoSQL databases
    -   Search and real-time log analytics
    -   Traditional large enterprise-level commercial software, such as SAP

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.g5se.large|2|8.0|None|1.0|300|2|2|6|30|1|
|ecs.g5se.xlarge|4|16.0|None|1.5|500|2|3|6|60|2|
|ecs.g5se.2xlarge|8|32.0|None|2.5|800|2|3|8|120|4|
|ecs.g5se.4xlarge|16|64.0|None|5.0|1,000|4|8|10|230|8|
|ecs.g5se.6xlarge|24|96.0|None|7.5|1,500|6|8|10|340|12|
|ecs.g5se.8xlarge|32|128.0|None|10.0|2,000|8|8|10|450|15|
|ecs.g5se.16xlarge|64|256.0|None|14.0|3,000|16|8|10|900|30|
|ecs.g5se.18xlarge|70|336.0|None|16.0|4,000|16|8|10|1,000|32|

**Note:** For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## g5ne, network enhanced instance family

Features

-   Instances of the g5ne instance family significantly improve network throughput and packet forwarding rate. A single g5ne instance can deliver up to 10,000 Kpps.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) or 8269CY \(Cascade Lake\) processors for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:4.
-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Provides high network performance based on large computing capacity.

    **Note:** We recommend that you select instance types of the g5ne instance family to deploy Data Plane Development Kit \(DPDK\) applications.

-   Suitable for the following scenarios:
    -   DPDK applications
    -   Network intensive scenarios such as NFV or SD-WAN, mobile Internet, on-screen video comments, and telecom data forwarding
    -   Small and medium-sized database systems, caches, and search clusters
    -   Enterprise-level applications of various types and sizes
    -   Big data analysis and machine learning

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|------------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.g5ne.large|2|8.0|None|1.0|400|Yes|450|2|3|10|10.0|1|
|ecs.g5ne.xlarge|4|16.0|None|2.0|750|Yes|900|4|4|15|15.0|1|
|ecs.g5ne.2xlarge|8|32.0|None|3.5|1,500|Yes|1,750|8|6|15|30.0|1|
|ecs.g5ne.4xlarge|16|64.0|None|7.0|3,000|Yes|3,500|16|8|30|60.0|2|
|ecs.g5ne.8xlarge|32|128.0|None|15.0|6,000|Yes|7,000|32|8|30|120.0|4|
|ecs.g5ne.16xlarge|64|256.0|None|30.0|12,000|Yes|14,000|32|8|30|240.0|8|
|ecs.g5ne.18xlarge|72|288.0|None|33.0|13,500|Yes|16,000|32|15|50|270.0|9|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ic5, compute intensive instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:1.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) or 8269CY \(Cascade Lake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Web frontend servers
    -   Data analysis, batch processing, and video encoding
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Frontend servers of MMO games

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ic5.large|2|2.0|None|1.0|300|No|2|2|6|
|ecs.ic5.xlarge|4|4.0|None|1.5|500|No|2|3|10|
|ecs.ic5.2xlarge|8|8.0|None|2.5|800|No|2|4|10|
|ecs.ic5.3xlarge|12|12.0|None|4.0|900|No|4|6|10|
|ecs.ic5.4xlarge|16|16.0|None|5.0|1,000|No|4|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## c6, compute optimized instance family

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies based on instance families. A single c6 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see [g5se, memory optimized instance family with enhanced performance](/intl.en-US/Instance/Instance families.md).

-   Provides high storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Offers a CPU-to-memory ratio of 1:2.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Supports instance type changes to g6 or r6.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.c6.large|2|4.0|None|1.0|3.0|300|Yes|Up to 250|2|2|6|10.0|1|
|ecs.c6.xlarge|4|8.0|None|1.5|5.0|500|Yes|Up to 250|4|3|10|20.0|1.5|
|ecs.c6.2xlarge|8|16.0|None|2.5|8.0|800|Yes|Up to 250|8|4|10|25.0|2|
|ecs.c6.3xlarge|12|24.0|None|4.0|10.0|900|Yes|Up to 250|8|6|10|30.0|2.5|
|ecs.c6.4xlarge|16|32.0|None|5.0|10.0|1,000|Yes|300|8|8|20|40.0|3|
|ecs.c6.6xlarge|24|48.0|None|7.5|10.0|1,500|Yes|450|12|8|20|50.0|4|
|ecs.c6.8xlarge|32|64.0|None|10.0|None|2,000|Yes|600|16|8|20|60.0|5|
|ecs.c6.13xlarge|52|96.0|None|12.5|None|3,000|Yes|900|32|7|20|100.0|8|
|ecs.c6.26xlarge|104|192.0|None|25.0|None|6,000|Yes|1,800|32|15|20|200.0|16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## c6a, compute optimized instance family

c6a is in invitational preview. To use c6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   Compute:
    -   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
    -   Offers a CPU-to-memory ratio of 1:2.
    -   Allows you to enable or disable Hyper-Threading.

        **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Storage:
    -   I/O optimized.
    -   Supports enhanced SSDs \(ESSDs\), standard SSDs, and ultra disks.
    -   Provides high storage I/O performance based on large computing capacity.

        **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Network:
    -   Provides an ultra-high packet forwarding rate.
    -   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Video encoding and decoding
    -   Scenarios where large volumes of packets are received and transmitted
    -   Web frontend servers
    -   Frontend servers of massively multiplayer online \(MMO\) games
    -   Test and development, such as DevOps

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|-------------------------|------------------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.c6a.large|2|4.0|None|1.0|10.0|900|Yes|2|12.5|1.0|
|ecs.c6a.xlarge|4|8.0|None|1.5|10.0|1,000|Yes|3|20.0|1.5|
|ecs.c6a.2xlarge|8|16.0|None|2.5|10.0|1,600|Yes|4|30.0|2.0|
|ecs.c6a.4xlarge|16|32.0|None|5.0|10.0|2,000|Yes|8|60.0|3.0|
|ecs.c6a.8xlarge|32|64.0|None|8.0|10.0|3,000|Yes|7|75.0|4,0|
|ecs.c6a.16xlarge|64|128.0|None|16.0|None|6,000|Yes|8|150.0|8.0|
|ecs.c6a.32xlarge|128|256.0|None|32.0|None|12,000|Yes|15|300.0|16.0|
|ecs.c6a.64xlarge|256|512.0|None|64.0|None|24,000|Yes|15|600.0|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## c6t, security-enhanced compute optimized instance family

c6t is in invitational preview.

Features

-   Implements trusted boot based on the Trusted Platform Module \(TPM\) chip. During a trusted boot, each module in the boot chain from the underlying hardware to the guest OS is measured and verified.
-   Supports comprehensive monitoring on the IaaS layer and ensures trusted capabilities of the whole IaaS layer.
-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture. c6t improves storage performance, network performance, and computing stability by an order of magnitude through fast path acceleration of X-Dragon chips.
-   Compute:
    -   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
    -   Offers a CPU-to-memory ratio of 1:2.
    -   Allows you to enable or disable Hyper-Threading.

        **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Storage:
    -   I/O optimized.
    -   Supports ESSDs only.
    -   Provides high storage I/O performance based on large computing capacity.

        **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Network:
    -   Provides an ultra-high packet forwarding rate.
    -   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios that require high security and enhanced trust, such as financial services, government affairs, and enterprise services
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|TPM support|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|--------------------|:------------------------------|-----------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.c6t.large|2|4.0|None|A burstable bandwidth of up to 10.0|900|Yes|Yes|Up to 250|2|3|6|20.0|1.0|
|ecs.c6t.xlarge|4|8.0|None|A burstable bandwidth of up to 10.0|1,000|Yes|Yes|Up to 250|4|4|15|40.0|1.5|
|ecs.c6t.2xlarge|8|16.0|None|A burstable bandwidth of up to 10.0|1,600|Yes|Yes|Up to 250|8|4|15|50.0|2.0|
|ecs.c6t.4xlarge|16|32.0|None|A burstable bandwidth of up to 10.0|3,000|Yes|Yes|300|8|8|30|80.0|3.0|
|ecs.c6t.8xlarge|32|64.0|None|10.0|6,000|Yes|Yes|600|16|8|30|150.0|5.0|
|ecs.c6t.13xlarge|52|96.0|None|16.0|9,000|Yes|Yes|900|32|7|30|240.0|8.0|
|ecs.c6t.26xlarge|104|192.0|None|32.0|24,000|Yes|Yes|1,800|32|15|30|480.0|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   The results for network capabilities are the maximum values obtained from single item tests. For example, when network bandwidth is tested, no stress tests are performed on the packet forwarding rate or other metrics of the network.

## c6e, compute optimized instance family with enhanced performance

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture. c6e improves storage performance, network performance, and computing stability by an order of magnitude through fast path acceleration of X-Dragon chips.
-   I/O optimized.
-   Supports ESSDs only.
-   Provides high network and storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Provides an ultra-high packet forwarding rate.

    **Note:** The maximum network performance varies based on instance families. For higher concurrent connection capabilities, we recommend that you use g5ne. For more information, see [g5ne, network enhanced instance family](/intl.en-US/Instance/Instance families.md).

-   Offers a CPU-to-memory ratio of 1:2.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 \(Cascade\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|--------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.c6e.large|2|4.0|None|A burstable bandwidth of up to 10.0|900|Yes|Up to 250|2|3|6|20.0|1.0|
|ecs.c6e.xlarge|4|8.0|None|A burstable bandwidth of up to 10.0|1,000|Yes|Up to 250|4|4|15|40.0|1.5|
|ecs.c6e.2xlarge|8|16.0|None|A burstable bandwidth of up to 10.0|1,600|Yes|Up to 250|8|4|15|50.0|2.0|
|ecs.c6e.4xlarge|16|32.0|None|A burstable bandwidth of up to 10.0|3,000|Yes|300|8|8|30|80.0|3.0|
|ecs.c6e.8xlarge|32|64.0|None|10.0|6,000|Yes|600|16|8|30|150.0|5.0|
|ecs.c6e.13xlarge|52|96.0|None|16.0|9,000|Yes|900|32|7|30|240.0|8.0|
|ecs.c6e.26xlarge|104|192.0|None|32.0|24,000|Yes|1,800|32|15|30|480.0|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   The results for network capabilities are the maximum values obtained from single item tests. For example, when network bandwidth is tested, no stress tests are performed on the packet forwarding rate or other metrics of the network.

## c5, compute optimized instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies based on instance families. A single c5 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see [g5se, memory optimized instance family with enhanced performance](/intl.en-US/Instance/Instance families.md).

-   Offers a CPU-to-memory ratio of 1:2.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) or 8269CY \(Cascade Lake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.c5.large|2|4.0|None|1.0|300|Yes|2|2|6|
|ecs.c5.xlarge|4|8.0|None|1.5|500|Yes|2|3|10|
|ecs.c5.2xlarge|8|16.0|None|2.5|800|Yes|2|4|10|
|ecs.c5.3xlarge|12|24.0|None|4.0|900|Yes|4|6|10|
|ecs.c5.4xlarge|16|32.0|None|5.0|1,000|Yes|4|8|20|
|ecs.c5.6xlarge|24|48.0|None|7.5|1,500|Yes|6|8|20|
|ecs.c5.8xlarge|32|64.0|None|10.0|2,000|Yes|8|8|20|
|ecs.c5.16xlarge|64|128.0|None|20.0|4,000|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## r6, memory optimized instance family

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies with instance families. A single r6 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see the "g5se, storage optimized instance family with enhanced performance" section in [Instance families](/intl.en-US/Instance/Instance families.md).

-   Provides high storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:8.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Supports changes to g6 or c6 instance families.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.r6.large|2|16.0|None|1.0|3.0|300|Yes|Up to 250|2|2|6|10|1|
|ecs.r6.xlarge|4|32.0|None|1.5|5.0|500|Yes|Up to 250|4|3|10|20|1.5|
|ecs.r6.2xlarge|8|64.0|None|2.5|8.0|800|Yes|Up to 250|8|4|10|25|2|
|ecs.r6.3xlarge|12|96.0|None|4.0|10.0|900|Yes|Up to 250|8|6|10|30|2.5|
|ecs.r6.4xlarge|16|128.0|None|5.0|10.0|1,000|Yes|300|8|8|20|40|3|
|ecs.r6.6xlarge|24|192.0|None|7.5|10.0|1,500|Yes|450|12|8|20|50|4|
|ecs.r6.8xlarge|32|256.0|None|10.0|None|2,000|Yes|600|16|8|20|60|5|
|ecs.r6.13xlarge|52|384.0|None|12.5|None|3,000|Yes|900|32|7|20|100|8|
|ecs.r6.26xlarge|104|768.0|None|25.0|None|6,000|Yes|1,800|32|15|20|200|16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## r6a, memory optimized instance family

r6a is in invitational preview. To use r6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   Compute:
    -   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
    -   Offers a CPU-to-memory ratio of 1:8.
    -   Allows you to enable or disable Hyper-Threading.

        **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Storage:
    -   I/O optimized.
    -   Supports enhanced SSDs \(ESSDs\), standard SSDs, and ultra disks.
    -   Provides high storage I/O performance based on large computing capacity.

        **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Network:
    -   Provides an ultra high packet forwarding rate.
    -   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Video encoding and decoding
    -   Scenarios where large volumes of packets are received and transmitted
    -   In-memory databases
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications
    -   Test and development, such as DevOps

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|-------------------------|------------------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.r6a.large|2|16.0|None|1.0|10.0|900|Yes|2|12.5|1.0|
|ecs.r6a.xlarge|4|32.0|None|1.5|10.0|1,000|Yes|3|20|1.5|
|ecs.r6a.2xlarge|8|64.0|None|2.5|10.0|1,600|Yes|4|30|2.0|
|ecs.r6a.4xlarge|16|128.0|None|5.0|10.0|2,000|Yes|8|60|3.0|
|ecs.r6a.8xlarge|32|256.0|None|8.0|10.0|3,000|Yes|7|75|4,0|
|ecs.r6a.16xlarge|64|512.0|None|16.0|None|6,000|Yes|8|150|8.0|
|ecs.r6a.32xlarge|128|1024.0|None|32.0|None|12,000|Yes|15|300|16.0|
|ecs.r6a.64xlarge|256|2048.0|None|64.0|None|24,000|Yes|15|600|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## r6e, memory optimized instance family with enhanced performance

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture. In addition, improves storage performance, network performance, and computing stability by an order of magnitude through fast path acceleration of X-Dragon chips.
-   I/O optimized.
-   Supports ESSDs.
-   Provides high network and storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Provides an ultra high packet forwarding rate.

    **Note:** The maximum network performance varies depending on instance families. For more concurrent connections, we recommend that you use g5ne. For more information, see the "g5ne, general purpose instance family with enhanced network performance" section in [Instance families](/intl.en-US/Instance/Instance families.md).

-   Offers a CPU-to-memory ratio of 1:8.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|--------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.r6e.large|2|16.0|None|A burstable bandwidth of up to 10.0|900|Yes|Up to 250|2|3|6|20|1.0|
|ecs.r6e.xlarge|4|32.0|None|A burstable bandwidth of up to 10.0|1,000|Yes|Up to 250|4|4|15|40|1.5|
|ecs.r6e.2xlarge|8|64.0|None|A burstable bandwidth of up to 10.0|1,600|Yes|Up to 250|8|4|15|50|2.0|
|ecs.r6e.4xlarge|16|128.0|None|A burstable bandwidth of up to 10.0|3,000|Yes|300|8|8|30|80|3.0|
|ecs.r6e.8xlarge|32|256.0|None|10.0|6,000|Yes|600|16|8|30|150|5.0|
|ecs.r6e.13xlarge|52|384.0|None|16.0|9,000|Yes|900|32|7|30|240|8.0|
|ecs.r6e.26xlarge|104|768.0|None|32.0|24,000|Yes|1,800|32|15|30|480|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   The results for network capabilities are the maximum values obtained from single item tests. For example, when network bandwidth is tested, no stress tests are performed on the packet forwarding rate or other metrics of the network.

## re6, high memory instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Optimized for high-performance databases, in-memory databases, and other memory intensive enterprise applications.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:15 and up to 3 TiB memory.
-   Suitable for the following scenarios:
    -   High-performance databases and in-memory databases such as SAP HANA
    -   Memory intensive applications
    -   Big data processing engines such as Apache Spark and Presto

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.re6.13xlarge|52|768.0|None|10.0|1,800|Yes|16|7|20|50|4|
|ecs.re6.26xlarge|104|1536.0|None|16.0|3,000|Yes|32|7|20|100|8|
|ecs.re6.52xlarge|208|3072.0|None|32.0|6,000|Yes|32|15|20|200|16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## r5, memory optimized instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.

    **Note:** The maximum performance of disks varies with instance families. A single r5 instance can deliver up to 200,000 IOPS. For higher storage I/O performance, we recommend that you use g5se. For more information, see the "g5se, storage optimized instance family with enhanced performance" section in [Instance families](/intl.en-US/Instance/Instance families.md).

-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) or Intel ® Xeon ® Paltinum 8269CY \(Cascade Lake\) processors for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:8.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.r5.large|2|16.0|None|1.0|300|Yes|2|2|6|
|ecs.r5.xlarge|4|32.0|None|1.5|500|Yes|2|3|10|
|ecs.r5.2xlarge|8|64.0|None|2.5|800|Yes|2|4|10|
|ecs.r5.3xlarge|12|96.0|None|4.0|900|Yes|4|6|10|
|ecs.r5.4xlarge|16|128.0|None|5.0|1,000|Yes|4|8|20|
|ecs.r5.6xlarge|24|192.0|None|7.5|1,500|Yes|6|8|20|
|ecs.r5.8xlarge|32|256.0|None|10.0|2,000|Yes|8|8|20|
|ecs.r5.16xlarge|64|512.0|None|20.0|4,000|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## d2c, compute intensive big data instance family

d2c is under invitational preview. To use d2c, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features:

-   I/O optimized.
-   Supports enhanced SSDs, standard SSDs, and ultra disks.
-   High-capacity local SATA HDDs with high throughput and a maximum of 35 Gbit/s bandwidth among instances.
-   Supports online replacement and hot swapping of damaged disks to avoid instance shutdown.

    If a local disk fails, you will receive a notification about the system event. You can respond to the system event by initiating the process to fix the damaged disk. For more information, see [Overview of system events on ECS instances equipped with local disks](/intl.en-US/Deployment & Maintenance/System events/System events on ECS instances equipped with local disks/Overview of system events on ECS instances equipped with local disks.md).

    -   If a backup disk is available on the physical machine, Alibaba Cloud will replace the damaged disk with the backup disk online.
    -   If no backup disk is available on the physical machine, the disk hardware must be replaced manually before Alibaba Cloud can replace the damaged disk.
    **Note:** After you have started the process to fix the damaged disk, data in the damaged disk cannot be recovered.

-   Equipped with 2.5 GHz Intel® Xeon ® Platinum 8269CY \(Cascade Lake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Big data computing and storage business scenarios that use Hadoop MapReduce, HDFS, Hive, and HBase
    -   Scenarios in which EMR JindoFS and OOS are used to store hot and cold data separately and decouple storage and computing
    -   Machine learning scenarios such as in-memory computing with Spark and scalable machine learning with MLlib
    -   Search and log data processing scenarios that use solutions such as Elasticsearch and Kafka

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.d2c.6xlarge|24|88.0|3 × 4,000|12.0|1,600|Yes|8|8|20|
|ecs.d2c.12xlarge|48|176.0|6 × 4000|20.0|2,000|Yes|16|8|20|
|ecs.d2c.24xlarge|96|352.0|12 × 4000|35.0|4,500|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## d2s, storage intensive big data instance family

Features:

-   I/O-optimized.
-   Supports enhanced SSDs, standard SSDs, and ultra disks.
-   High-capacity local SATA HDDs with high throughput and a maximum of 35 Gbit/s bandwidth among instances.
-   Supports online replacement and hot swapping of damaged disks to avoid instance shutdown.

    If a local disk fails, you will receive a notification about the system event. You can respond to the system event by initiating the process to fix the damaged disk. For more information, see [Overview of system events on ECS instances equipped with local disks](/intl.en-US/Deployment & Maintenance/System events/System events on ECS instances equipped with local disks/Overview of system events on ECS instances equipped with local disks.md).

    -   If a backup disk is available on the physical machine, Alibaba Cloud will replace the damaged disk with the backup disk online.
    -   If no backup disk is available on the physical machine, the disk hardware must be replaced manually before Alibaba Cloud can replace the damaged disk.
    **Note:** After you have started the process to fix the damaged disk, data in the damaged disk cannot be recovered.

-   Equipped with 2.5 GHz Intel ® Xeon® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Big data computing and storage business scenarios that use Hadoop MapReduce, HDFS, Hive, and HBase
    -   Machine learning scenarios such as in-memory computing with Spark and scalable machine learning with MLlib
    -   Search and log data processing scenarios that use solutions such as Elasticsearch and Kafka

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.d2s.5xlarge|20|88.0|8 × 7,300|12.0|1,600|Yes|8|8|20|
|ecs.d2s.10xlarge|40|176.0|15 × 7,300|20.0|2,000|Yes|16|8|20|
|ecs.d2s.20xlarge|80|352.0|30 × 7,300|35.0|4,500|Yes|32|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## d1ne, big data instance family with enhanced network performance

Features:

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   High-capacity local SATA HDDs with high throughput and a maximum of 35 Gbit/s bandwidth among instances.
-   Offers a CPU-to-memory ratio of 1:4, which is designed for big data scenarios.
-   Equipped with 2.5 GHz Intel® Xeon® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios that use Hadoop MapReduce, HDFS, Hive, and HBase
    -   Machine learning scenarios such as in-memory computing with Spark and scalable machine learning with MLlib
    -   Use of solutions such as Elasticsearch for log data processing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.d1ne.2xlarge|8|32.0|4 × 5,500|6.0|1,000|Yes|4|4|10|
|ecs.d1ne.4xlarge|16|64.0|8 × 5,500|12.0|1,600|Yes|4|8|20|
|ecs.d1ne.6xlarge|24|96.0|12 × 5,500|16.0|2,000|Yes|6|8|20|
|ecs.d1ne-c8d3.8xlarge|32|128.0|12 × 5,500|20.0|2,000|Yes|6|8|20|
|ecs.d1ne.8xlarge|32|128.0|16 × 5,500|20.0|2,500|Yes|8|8|20|
|ecs.d1ne-c14d3.14xlarge|56|160.0|12 × 5,500|35.0|4,500|Yes|14|8|20|
|ecs.d1ne.14xlarge|56|224.0|28 × 5,500|35.0|4,500|Yes|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## i2, instance family with local SSDs

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Attached with high-performance local NVMe SSDs that feature high IOPS, high I/O throughput, and low latency.
-   Offers a CPU-to-memory ratio of 1:8, which is designed for high-performance databases.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Scenarios:
    -   Online transaction processing \(OLTP\) and high-performance relational databases
    -   NoSQL databases such as Cassandra, MongoDB, and HBase
    -   Search scenarios that use solutions such as Elasticsearch

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|-------------------------|
|ecs.i2.xlarge|4|32.0|1 × 894|1.0|500|Yes|2|3|10|Up to 16|
|ecs.i2.2xlarge|8|64.0|1 × 1,788|2.0|1,000|Yes|2|4|10|Up to 16|
|ecs.i2.4xlarge|16|128.0|2 × 1,788|3.0|1,500|Yes|4|8|20|Up to 16|
|ecs.i2.8xlarge|32|256.0|4 × 1,788|6.0|2,000|Yes|8|8|20|Up to 16|
|ecs.i2.16xlarge|64|512.0|8 × 1,788|10.0|4,000|Yes|16|8|20|Up to 16|
|ecs.i2d.21xlarge|84|712.0|4 × 3,570|25.0|4,000|Yes|32|16|20|Up to 16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   For more information about the performance metrics of SSDs, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).

## i2g, instance family with local SSDs

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Attached with high-performance local NVMe SSDs that feature high IOPS, high I/O throughput, and low latency.
-   Offers a CPU-to-memory ratio of 1:4, which is designed for high-performance databases.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Scenarios:
    -   OLTP and high-performance relational databases
    -   NoSQL databases such as Cassandra, MongoDB, and HBase
    -   Search scenarios that use solutions such as Elasticsearch

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.i2g.2xlarge|8|32.0|1 × 894|2.0|1,000|No|2|4|10|
|ecs.i2g.4xlarge|16|64.0|1 × 1,788|3.0|1,500|No|4|8|20|
|ecs.i2g.8xlarge|32|128.0|2 × 1,788|6.0|2,000|No|8|8|20|
|ecs.i2g.16xlarge|64|256.0|4 × 1,788|10.0|4,000|No|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   For more information about the performance metrics of SSDs, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).

## i2ne, instance family with local SSDs

i2ne is in invitational preview. To use i2ne, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Attached with high-performance local NVMe SSDs that feature high IOPS, high I/O throughput, and low latency.
-   Provides a bandwidth of up to 20 Gbit/s.
-   Offers a CPU-to-memory ratio of 1:8, which is designed for high-performance databases.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Scenarios:
    -   OLTP and high-performance relational databases
    -   NoSQL databases such as Cassandra, MongoDB, and HBase
    -   Search scenarios that use solutions such as Elasticsearch

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk bandwidth \(Gbit/s\)|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|-------------------------|
|ecs.i2ne.xlarge|4|32.0|1 × 894|1.5|500|Yes|2|3|10|Up to 16|
|ecs.i2ne.2xlarge|8|64.0|1 × 1,788|2.5|1,000|Yes|2|4|10|Up to 16|
|ecs.i2ne.4xlarge|16|128.0|2 × 1,788|5.0|1,500|Yes|4|8|20|Up to 16|
|ecs.i2ne.8xlarge|32|256.0|4 × 1,788|10.0|2,000|Yes|8|8|20|Up to 16|
|ecs.i2ne.16xlarge|64|512.0|8 × 1,788|20.0|4,000|Yes|16|8|20|Up to 16|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   For more information about the performance metrics of SSDs, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).

## i2gne, instance family with local SSDs

i2gne is in invitational preview. To use i2gne, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Attached with high-performance local NVMe SSDs that feature high IOPS, high I/O throughput, and low latency.
-   Provides a bandwidth of up to 20 Gbit/s.
-   Offers a CPU-to-memory ratio of 1:4, which is designed for high-performance databases.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Scenarios:
    -   OLTP and high-performance relational databases
    -   NoSQL databases such as Cassandra, MongoDB, and HBase
    -   Search scenarios that use solutions such as Elasticsearch

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.i2gne.2xlarge|8|32.0|1 × 894|2.5|1,000|No|2|4|10|
|ecs.i2gne.4xlarge|16|64.0|1 × 1,788|5.0|1,500|No|4|8|20|
|ecs.i2gne.8xlarge|32|128.0|2 × 1,788|10.0|2,000|No|8|8|20|
|ecs.i2gne.16xlarge|64|256.0|4 × 1,788|20.0|4,000|No|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   For more information about the performance metrics of SSDs, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).

## hfc7, compute optimized instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture.
-   I/O optimized.
-   Supports enhanced SSDs \(ESSDs\) and provides ultra-high I/O performance.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:2.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.3 GHz Intel ® Xeon ® Platinum 8369HC \(Cooper Lake\) processors with a maximum turbo frequency of 3.8 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance frontend server clusters
    -   Frontend servers of massively multiplayer online \(MMO\) games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfc7.large|2|4.0|None|1.2|10.0|900|Yes|2|2|6|20|1.0|
|ecs.hfc7.xlarge|4|8.0|None|2.0|10.0|1,000|Yes|4|3|15|30|1.5|
|ecs.hfc7.2xlarge|8|16.0|None|3.0|10.0|1,600|Yes|8|4|15|45|2.0|
|ecs.hfc7.3xlarge|12|24.0|None|4.5|10.0|2,000|Yes|8|6|15|60|2.5|
|ecs.hfc7.4xlarge|16|32.0|None|6.0|10.0|2,500|Yes|8|8|30|75|3.0|
|ecs.hfc7.6xlarge|24|48.0|None|8.0|10.0|3,000|Yes|12|8|30|90|4.0|
|ecs.hfc7.8xlarge|32|64.0|None|10.0|None|4,000|Yes|16|8|30|105|5.0|
|ecs.hfc7.12xlarge|48|96.0|None|16.0|None|6,000|Yes|24|8|30|150|8.0|
|ecs.hfc7.24xlarge|96|192.0|None|32.0|None|12,000|Yes|32|15|30|300|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfc6, compute optimized instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:2.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz for consistent computing performance.

    **Note:** The CPU of this instance family provides a 3.1 GHz clock speed. The Intel System Studio \(ISS\) feature may cause a lower clock speed to be displayed. Alibaba Cloud is trying to fix the display problem. The problem does not affect the actual clock speed of your instances.

    You can run the following commands separately and use the turbostat tool to view the actual clock speed.

    ```
    yum install kernel-tools
    ```

    ```
    turbostat
    ```

-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfc6.large|2|4.0|None|1.0|3.0|300|Yes|2|2|6|10|1.0|
|ecs.hfc6.xlarge|4|8.0|None|1.5|5.0|500|Yes|4|3|10|20|1.5|
|ecs.hfc6.2xlarge|8|16.0|None|2.5|8.0|800|Yes|8|4|10|25|2.0|
|ecs.hfc6.3xlarge|12|24.0|None|4.0|10.0|900|Yes|8|6|10|30|2.5|
|ecs.hfc6.4xlarge|16|32.0|None|5.0|10.0|1,000|Yes|8|8|20|40|3.0|
|ecs.hfc6.6xlarge|24|48.0|None|7.5|10.0|1,500|Yes|12|8|20|50|4.0|
|ecs.hfc6.8xlarge|32|64.0|None|10.0|None|2,000|Yes|16|8|20|60|5.0|
|ecs.hfc6.10xlarge|40|96.0|None|12.5|None|3,000|Yes|32|7|20|100|8.0|
|ecs.hfc6.16xlarge|64|128.0|None|20.0|None|4,000|Yes|32|8|20|120|10.0|
|ecs.hfc6.20xlarge|80|192.0|None|25.0|None|6,000|Yes|32|15|20|200|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfg7, general purpose instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs and provides ultra-high I/O performance.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.3 GHz Intel ® Xeon ® Platinum 8369HC \(Cooper Lake\) processors with a maximum turbo frequency of 3.8 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   High-performance scientific computing
    -   Video encoding applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfg7.large|2|8.0|None|1.2|10.0|900|Yes|2|2|6|20|1.0|
|ecs.hfg7.xlarge|4|16.0|None|2.0|10.0|1,000|Yes|4|3|15|30|1.5|
|ecs.hfg7.2xlarge|8|32.0|None|3.0|10.0|1,600|Yes|8|4|15|45|2.0|
|ecs.hfg7.3xlarge|12|48.0|None|4.5|10.0|2,000|Yes|8|6|15|60|2.5|
|ecs.hfg7.4xlarge|16|64.0|None|6.0|10.0|2,500|Yes|8|8|30|75|3.0|
|ecs.hfg7.6xlarge|24|96.0|None|8.0|10.0|3,000|Yes|12|8|30|90|4.0|
|ecs.hfg7.8xlarge|32|128.0|None|10.0|None|4,000|Yes|16|8|30|105|5.0|
|ecs.hfg7.12xlarge|48|192.0|None|16.0|None|6,000|Yes|24|8|30|150|8.0|
|ecs.hfg7.24xlarge|96|384.0|None|32.0|None|12.000|Yes|32|15|30|300|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfg6, general purpose instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:4.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz for consistent computing performance.

    **Note:** The CPU of this instance family provides a 3.1 GHz clock speed. The Intel System Studio \(ISS\) feature may cause a lower clock speed to be displayed. Alibaba Cloud is trying to fix the display problem. The problem does not affect the actual clock speed of your instances.

    You can run the following commands separately and use the turbostat tool to view the actual clock speed.

    ```
    yum install kernel-tools
    ```

    ```
    turbostat
    ```

-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Websites and application servers
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfg6.large|2|8.0|None|1.0|3.0|300|Yes|2|2|6|10|1.0|
|ecs.hfg6.xlarge|4|16.0|None|1.5|5.0|500|Yes|4|3|10|20|1.5|
|ecs.hfg6.2xlarge|8|32.0|None|2.5|8.0|800|Yes|8|4|10|25|2.0|
|ecs.hfg6.3xlarge|12|48.0|None|4.0|10.0|900|Yes|8|6|10|30|2.5|
|ecs.hfg6.4xlarge|16|64.0|None|5.0|10.0|1,000|Yes|8|8|20|40|3.0|
|ecs.hfg6.6xlarge|24|96.0|None|7.5|10.0|1,500|Yes|12|8|20|50|4.0|
|ecs.hfg6.8xlarge|32|128.0|None|10.0|None|2,000|Yes|16|8|20|60|5.0|
|ecs.hfg6.10xlarge|40|192.0|None|12.5|None|3,000|Yes|32|7|20|100|8.0|
|ecs.hfg6.16xlarge|64|256.0|None|20.0|None|4,000|Yes|32|8|20|120|10.0|
|ecs.hfg6.20xlarge|80|384.0|None|25.0|None|6,000|Yes|32|15|20|200|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfr7, memory optimized instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the third-generation X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs and provides ultra-high I/O performance.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:8.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.3 GHz Intel ® Xeon ® Platinum 8369HC \(Cooper Lake\) processors with a maximum turbo frequency of 3.8 GHz for consistent computing performance.
-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfr7.large|2|16.0|None|1.2|10.0|900|Yes|2|2|6|20|1.0|
|ecs.hfr7.xlarge|4|32.0|None|2.0|10.0|1,000|Yes|4|3|15|30|1.5|
|ecs.hfr7.2xlarge|8|64.0|None|3.0|10.0|1,600|Yes|8|4|15|45|2.0|
|ecs.hfr7.3xlarge|12|96.0|None|4.5|10.0|2,000|Yes|8|6|15|60|2.5|
|ecs.hfr7.4xlarge|16|128.0|None|6.0|10.0|2,500|Yes|8|8|30|75|3.0|
|ecs.hfr7.6xlarge|24|192.0|None|8.0|10.0|3,000|Yes|12|8|30|90|4.0|
|ecs.hfr7.8xlarge|32|256.0|None|10.0|None|4,000|Yes|16|8|30|105|5.0|
|ecs.hfr7.12xlarge|48|384.0|None|16.0|None|6,000|Yes|24|8|30|150|8.0|
|ecs.hfr7.24xlarge|96|768.0|None|32.0|None|12,000|Yes|32|15|30|300|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfr6, memory optimized instance family with high clock speed

Features

-   Provides predictable and consistent high performance and reduces virtualization overheads with the use of the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides strong storage I/O performance based on large computing capacity.

    **Note:** For more information about the storage I/O performance of the new generation of enterprise-level instance families, see [Storage I/O performance](/intl.en-US/Block Storage/Performance/Storage I/O performance.md).

-   Offers a CPU-to-memory ratio of 1:8.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz for consistent computing performance.

    **Note:** The CPU of this instance family provides a 3.1 GHz clock speed. The Intel System Studio \(ISS\) feature may cause a lower clock speed to be displayed. Alibaba Cloud is trying to fix the display problem. The problem does not affect the actual clock speed of your instances.

    You can run the following commands separately and use the turbostat tool to view the actual clock speed.

    ```
    yum install kernel-tools
    ```

    ```
    turbostat
    ```

-   Allows you to enable or disable Hyper-Threading.

    **Note:** By default, Hyper-Threading is enabled on ECS instances. For more information, see [Customize CPU options](/intl.en-US/Instance/Manage instances/Customize CPU options.md).

-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Burstable bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:------------------------|------------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.hfr6.large|2|16.0|None|1.0|3.0|300|Yes|2|2|6|10|1.0|
|ecs.hfr6.xlarge|4|32.0|None|1.5|5.0|500|Yes|4|3|10|20|1.5|
|ecs.hfr6.2xlarge|8|64.0|None|2.5|8.0|800|Yes|8|4|10|25|2.0|
|ecs.hfr6.3xlarge|12|96.0|None|4.0|10.0|900|Yes|8|6|10|30|2.5|
|ecs.hfr6.4xlarge|16|128.0|None|5.0|10.0|1,000|Yes|8|8|20|40|3.0|
|ecs.hfr6.6xlarge|24|192.0|None|7.5|10.0|1,500|Yes|12|8|20|50|4.0|
|ecs.hfr6.8xlarge|32|256.0|None|10.0|None|2,000|Yes|16|8|20|60|5.0|
|ecs.hfr6.10xlarge|40|384.0|None|12.5|None|3,000|Yes|32|7|20|100|8.0|
|ecs.hfr6.16xlarge|64|512.0|None|20.0|None|4,000|Yes|32|8|20|120|10.0|
|ecs.hfr6.20xlarge|80|768.0|None|25.0|None|6,000|Yes|32|15|20|200|16.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## sn2ne, general purpose instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks only.
-   Offers a CPU-to-memory ratio of 1:4.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) or Platinum 8163 \(Skylake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.sn2ne.large|2|8.0|None|1.0|300|Yes|2|2|6|
|ecs.sn2ne.xlarge|4|16.0|None|1.5|500|Yes|2|3|10|
|ecs.sn2ne.2xlarge|8|32.0|None|2.0|1,000|Yes|4|4|10|
|ecs.sn2ne.3xlarge|12|48.0|None|2.5|1,300|Yes|4|6|10|
|ecs.sn2ne.4xlarge|16|64.0|None|3.0|1,600|Yes|4|8|20|
|ecs.sn2ne.6xlarge|24|96.0|None|4.5|2,000|Yes|6|8|20|
|ecs.sn2ne.8xlarge|32|128.0|None|6.0|2,500|Yes|8|8|20|
|ecs.sn2ne.14xlarge|56|224.0|None|10.0|4,500|Yes|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## sn1ne, compute optimized instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks only.
-   Offers a CPU-to-memory ratio of 1:2.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) or Platinum 8163 \(Skylake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of MMO games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.sn1ne.large|2|4.0|None|1.0|300|Yes|2|2|6|
|ecs.sn1ne.xlarge|4|8.0|None|1.5|500|Yes|2|3|10|
|ecs.sn1ne.2xlarge|8|16.0|None|2.0|1,000|Yes|4|4|10|
|ecs.sn1ne.3xlarge|12|24.0|None|2.5|1,300|Yes|4|6|10|
|ecs.sn1ne.4xlarge|16|32.0|None|3.0|1,600|Yes|4|8|20|
|ecs.sn1ne.6xlarge|24|48.0|None|4.5|2,000|Yes|6|8|20|
|ecs.sn1ne.8xlarge|32|64.0|None|6.0|2,500|Yes|8|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## re4, high memory instance family

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Optimized for high-performance databases, in-memory databases, and other memory intensive enterprise applications.
-   Equipped with 2.2 GHz Intel ® Xeon ® E7 8880 v4\(Broadwell\) processors with a maximum turbo frequency of 2.4 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:12 and up to 1,920 GiB memory.
-   The ecs.re4.20xlarge and ecs.re4.40xlarge instance types are SAP HANA-certified.
-   Suitable for the following scenarios:
    -   High-performance databases and in-memory databases such as SAP HANA
    -   Memory intensive applications
    -   Big data processing engines such as Apache Spark and Presto

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.re4.20xlarge|80|960.0|None|15.0|2,000|Yes|16|8|20|
|ecs.re4.40xlarge|160|1920.0|None|30.0|4,500|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## re4e, high memory instance family

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Optimized for high-performance databases, in-memory databases, and other memory intensive enterprise applications.
-   Equipped with 2.2 GHz Intel ® Xeon ® E7 8880 v4\(Broadwell\) processors with a maximum turbo frequency of 2.4 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:24 and up to 3,840 GiB memory.
-   Suitable for the following scenarios:
    -   High-performance databases and in-memory databases such as SAP HANA
    -   Memory intensive applications
    -   Big data processing engines such as Apache Spark and Presto

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.re4e.40xlarge|160|3840.0|None|30.0|4,500|Yes|16|15|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## se1ne, memory optimized instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Offers a CPU-to-memory ratio of 1:8.
-   Provides an ultra-high packet forwarding rate.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) or Intel ® Xeon ® Platinum 8163 \(Skylake\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.se1ne.large|2|16.0|None|1.0|300|Yes|2|2|6|
|ecs.se1ne.xlarge|4|32.0|None|1.5|500|Yes|2|3|10|
|ecs.se1ne.2xlarge|8|64.0|None|2.0|1,000|Yes|4|4|10|
|ecs.se1ne.3xlarge|12|96.0|None|2.5|1,300|Yes|4|6|10|
|ecs.se1ne.4xlarge|16|128.0|None|3.0|1,600|Yes|4|8|20|
|ecs.se1ne.6xlarge|24|192.0|None|4.5|2,000|Yes|6|8|20|
|ecs.se1ne.8xlarge|32|256.0|None|6.0|2,500|Yes|8|8|20|
|ecs.se1ne.14xlarge|56|480.0|None|10.0|4,500|Yes|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## se1, memory optimized instance family

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Offers a CPU-to-memory ratio of 1:8.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors for consistent computing performance.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.se1.large|2|16.0|None|0.5|100|No|1|2|6|
|ecs.se1.xlarge|4|32.0|None|0.8|200|No|1|3|10|
|ecs.se1.2xlarge|8|64.0|None|1.5|400|No|1|4|10|
|ecs.se1.4xlarge|16|128.0|None|3.0|500|No|2|8|20|
|ecs.se1.8xlarge|32|256.0|None|6.0|800|No|3|8|20|
|ecs.se1.14xlarge|56|480.0|None|10.0|1,200|No|4|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## d1, big data instance family

Features:

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   High-capacity local SATA HDDs with high throughput and up to 17 Gbit/s of bandwidth among instances.
-   Offers a CPU-to-memory ratio of 1:4, which is designed for big data scenarios.
-   Equipped with 2.5 GHz Intel® Xeon® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Scenarios that use Hadoop MapReduce, HDFS, Hive, and HBase
    -   Machine learning scenarios such as in-memory computing with Spark and scalable machine learning with MLlib
    -   Suitable for customers in Internet, finance, and other industries that need to compute, store, and analyze big data
    -   Use of solutions such as Elasticsearch for log data processing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.d1.2xlarge|8|32.0|4 × 5,500|3.0|300|No|1|4|10|
|ecs.d1.3xlarge|12|48.0|6 × 5,500|4.0|400|No|1|6|10|
|ecs.d1.4xlarge|16|64.0|8 × 5,500|6.0|600|No|2|8|20|
|ecs.d1.6xlarge|24|96.0|12 × 5,500|8.0|800|No|2|8|20|
|ecs.d1-c8d3.8xlarge|32|128.0|12 × 5,500|10.0|1,000|No|4|8|20|
|ecs.d1.8xlarge|32|128.0|16 × 5,500|10.0|1,000|No|4|8|20|
|ecs.d1-c14d3.14xlarge|56|160.0|12 × 5,500|17.0|1,800|No|6|8|20|
|ecs.d1.14xlarge|56|224.0|28 × 5,500|17.0|1,800|No|6|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## i1, instance family with local SSDs

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Attached with high-performance local NVMe SSDs that feature high IOPS, high I/O throughput, and low latency.
-   Offers a CPU-to-memory ratio of 1:4, which is designed for high-performance databases.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Scenarios:
    -   OLTP and high-performance relational databases
    -   NoSQL databases such as Cassandra and MongoDB
    -   Search scenarios that use solutions such as Elasticsearch

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.i1.xlarge|4|16.0|2 × 104|0.8|200|No|1|3|10|
|ecs.i1.2xlarge|8|32.0|2 × 208|1.5|400|No|1|4|10|
|ecs.i1.3xlarge|12|48.0|2 × 312|2.0|400|No|1|6|10|
|ecs.i1.4xlarge|16|64.0|2 × 416|3.0|500|No|2|8|20|
|ecs.i1-c5d1.4xlarge|16|64.0|2 × 1,456|3.0|400|No|2|8|20|
|ecs.i1.6xlarge|24|96.0|2 × 624|4.5|600|No|2|8|20|
|ecs.i1.8xlarge|32|128.0|2 × 832|6.0|800|No|3|8|20|
|ecs.i1-c10d1.8xlarge|32|128.0|2 × 1,456|6.0|800|No|3|8|20|
|ecs.i1.14xlarge|56|224.0|2 × 1,456|10.0|1,200|No|4|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).
-   For more information about the performance metrics of SSDs, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).

## hfc5, compute optimized instance family with high clock speed

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Provides consistent computing performance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Gold 6149 \(Skylake\) processors.
-   Offers a CPU-to-memory ratio of 1:2.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   High-performance web frontend servers
    -   High-performance scientific and engineering applications
    -   MMO gaming and video coding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.hfc5.large|2|4.0|None|1.0|300|No|2|2|6|
|ecs.hfc5.xlarge|4|8.0|None|1.5|500|No|2|3|10|
|ecs.hfc5.2xlarge|8|16.0|None|2.0|1,000|No|2|4|10|
|ecs.hfc5.3xlarge|12|24.0|None|2.5|1,300|No|4|6|10|
|ecs.hfc5.4xlarge|16|32.0|None|3.0|1,600|No|4|8|20|
|ecs.hfc5.6xlarge|24|48.0|None|4.5|2,000|No|6|8|20|
|ecs.hfc5.8xlarge|32|64.0|None|6.0|2,500|No|8|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## hfg5, general purpose instance family with high clock speed.

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Provides consistent computing performance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Gold 6149 \(Skylake\) processors.
-   Offers a CPU-to-memory ratio of 1:4 \(excluding the instance type with 56 vCPUs\).
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   High-performance web frontend servers
    -   High-performance scientific and engineering applications
    -   MMO gaming and video coding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.hfg5.large|2|8.0|None|1.0|300|No|2|2|6|
|ecs.hfg5.xlarge|4|16.0|None|1.5|500|No|2|3|10|
|ecs.hfg5.2xlarge|8|32.0|None|2.0|1,000|No|2|4|10|
|ecs.hfg5.3xlarge|12|48.0|None|2.5|1,300|No|4|6|10|
|ecs.hfg5.4xlarge|16|64.0|None|3.0|1,600|No|4|8|20|
|ecs.hfg5.6xlarge|24|96.0|None|4.5|2,000|No|6|8|20|
|ecs.hfg5.8xlarge|32|128.0|None|6.0|2,500|No|8|8|20|
|ecs.hfg5.14xlarge|56|160.0|None|10.0|4,000|No|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## vgn6i, lightweight compute optimized instance family with GPU capabilities

vgn6i is under invitational preview. To use vgn6i, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses NVIDIA T4 GPU computing accelerators.
-   Contains virtual GPUs \(vGPUs\), which are the result of GPU virtualization with mediated pass-through.
    -   Supports the 1/8, 1/4, and 1/2 computing capacity of NVIDIA® Tesla® T4 GPUs.
    -   Supports 2, 4, and 8 GB of GPU memory.
-   Offers a CPU-to-memory ratio of 1:5.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   AI \(deep learning and machine learning\) inference for the elastic deployment of Internet services
    -   Educational environment of deep learning
    -   Modeling experiment environment of deep learning

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.vgn6i-m4.xlarge|4|23.0|None|1/4 × T4|4|3.0|500|Yes|2|4|10|
|ecs.vgn6i-m8.2xlarge|10|46.0|None|1/2 × T4|8|4.0|800|Yes|4|5|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn6i, compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Supports enhanced SSDs \(ESSDs\) that deliver millions of IOPS, standard SSDs, and ultra disks.
-   Uses NVIDIA T4 GPU computing accelerators.
    -   Powered by the new NVIDIA Turing architecture.
    -   16 GB GPU memory \(320 GB/s bandwidth\).
    -   2,560 CUDA cores per GPU.
    -   Up to 320 Turing Tensor cores.
    -   Mixed-precision Tensor cores support 65 FP16 TFLOPS, 130 INT8 TOPS, and 260 INT4 TOPS.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   AI \(deep learning and machine learning\) inference for computer vision, speech recognition, speech synthesis, natural language processing \(NLP\), machine translation, and recommendation systems
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   Graphics workstations or overloaded graphics computing
    -   GPU-accelerated databases
    -   High-performance computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|--------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn6i-c4g1.xlarge|4|15.0|None|1 × T4|16|4.0|500|Yes|2|2|10|
|ecs.gn6i-c8g1.2xlarge|8|31.0|None|1 × T4|16|5.0|800|Yes|2|2|10|
|ecs.gn6i-c16g1.4xlarge|16|62.0|None|1 × T4|16|6.0|1,000|Yes|4|3|10|
|ecs.gn6i-c24g1.6xlarge|24|93.0|None|1 × T4|16|7.5|1,200|Yes|6|4|10|
|ecs.gn6i-c24g1.12xlarge|48|186.0|None|2 × T4|32|15.0|2,400|Yes|12|6|10|
|ecs.gn6i-c24g1.24xlarge|96|372.0|None|4 × T4|64|30.0|4,800|Yes|24|8|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn6e, compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Uses NVIDIA V100 \(32 GB NVLink\) GPU processors.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Uses NVIDIA V100 GPU computing accelerators that have the SXM2 module.
    -   Powered by the new NVIDIA Volta architecture.
    -   32 GB HBM2 GPU memory \(900 GB/s bandwidth\).
    -   5,120 CUDA cores per GPU.
    -   640 Tensor cores per GPU.
    -   Supports up to six NVLink connections and a total bandwidth of 300 GB/s \(25 GB/s per connection\).
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning applications such as training and inference applications of AI algorithms used in image classification, autonomous vehicles, and speech recognition
    -   Scientific computing applications, such as fluid dynamics, finance, molecular dynamics, and environmental analysis

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn6e-c12g1.3xlarge|12|92.0|None|1 × V100|32|5.0|800|Yes|8|6|10|
|ecs.gn6e-c12g1.12xlarge|48|368.0|None|4 × V100|128|16.0|2,400|Yes|8|8|20|
|ecs.gn6e-c12g1.24xlarge|96|736.0|None|8 × V100|256|32.0|4,800|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn6v, compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Uses NVIDIA V100 GPU processors.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Uses NVIDIA V100 GPU computing accelerators that have the SXM2 module.
    -   Powered by the new NVIDIA Volta architecture.
    -   16 GB HBM2 GPU memory \(900 GB/s bandwidth\).
    -   5,120 CUDA cores per GPU.
    -   640 Tensor cores per GPU.
    -   Supports up to six NVLink connections and a total bandwidth of 300 GB/s \(25 GB/s per connection\).
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning applications such as training and inference applications of AI algorithms used in image classification, autonomous vehicles, and speech recognition
    -   Scientific computing applications, such as fluid dynamics, finance, molecular dynamics, and environmental analysis

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn6v-c8g1.2xlarge|8|32.0|None|1 × NVIDIA V100|1 × 16|2.5|800|Yes|4|4|10|
|ecs.gn6v-c8g1.8xlarge|32|128.0|None|4 × NVIDIA V100|4 × 16|10.0|2,000|Yes|8|8|20|
|ecs.gn6v-c8g1.16xlarge|64|256.0|None|8 × NVIDIA V100|8 × 16|20.0|2,500|Yes|16|8|20|
|ecs.gn6v-c10g1.20xlarge|82|336.0|None|8 × NVIDIA V100|8 × 16|32.0|4,500|Yes|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## f3, compute optimized instance family with FPGAs

Features:

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses Xilinx 16nm Virtex UltraScale+ VU9P FPGAs.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel® Xeon® Platinum 8163 \(Skylake\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning and inference
    -   Genomics research
    -   Database acceleration
    -   Image transcoding such as conversion of JPEG images to WebP images
    -   Real-time video processing such as H.265 video compression

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|FPGAs|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:----|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.f3-c4f1.xlarge|4|16.0|None|1 × Xilinx VU9P|1.5|300|No|2|3|10|
|ecs.f3-c8f1.2xlarge|8|32.0|None|1 × Xilinx VU9P|2.5|500|No|4|4|10|
|ecs.f3-c16f1.4xlarge|16|64.0|None|1 × Xilinx VU9P|5.0|1,000|No|4|8|20|
|ecs.f3-c16f1.8xlarge|32|128.0|None|2 × Xilinx VU9P|10.0|2,000|No|8|8|20|
|ecs.f3-c16f1.16xlarge|64|256.0|None|4 × Xilinx VU9P|20.0|2,500|No|16|8|20|
|ecs.f3-c22f1.22xlarge|88|336.0|None|4 × Xilinx VU9P|30.0|4,500|No|16|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## vgn5i, lightweight compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses NVIDIA P4 GPU computing accelerators.
-   Contains virtual GPUs \(vGPUs\), which are the result of GPU virtualization with mediated pass-through.
    -   Supports the 1/8, 1/4, 1/2, and 1/1 computing capacity of NVIDIA® Tesla® P4 GPUs.
    -   Supports 1, 2, 4, and 8 GB of GPU memory.
-   Offers a CPU-to-memory ratio of 1:3.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   AI \(deep learning and machine learning\) inference for the elastic deployment of Internet services
    -   Educational environment of deep learning
    -   Modeling experiment environment of deep learning

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.vgn5i-m1.large|2|6.0|None|1/8 × P4|1|1.0|300|Yes|2|2|6|
|ecs.vgn5i-m2.xlarge|4|12.0|None|1/4 × P4|2|2.0|500|Yes|2|3|10|
|ecs.vgn5i-m4.2xlarge|8|24.0|None|1/2 × P4|4|3.0|800|Yes|2|4|10|
|ecs.vgn5i-m8.4xlarge|16|48.0|None|1 × P4|8|5.0|1,000|Yes|4|5|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn5, compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses NVIDIA P100 GPU processors.
-   Offers multiple CPU-to-memory ratios.
-   Attached with high-performance local NVMe SSDs.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing applications, such as fluid dynamics, finance, genomics, and environmental analysis
    -   Server-side GPU compute workloads such as high-performance computation, rendering, and multi-media coding and decoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn5-c4g1.xlarge|4|30.0|440|1 × NVIDIA P100|1 × 16|3.0|300|No|1|3|10|
|ecs.gn5-c8g1.2xlarge|8|60.0|440|1 × NVIDIA P100|1 × 16|3.0|400|No|1|4|10|
|ecs.gn5-c4g1.2xlarge|8|60.0|880|2 × NVIDIA P100|2 × 16|5.0|1,000|No|2|4|10|
|ecs.gn5-c8g1.4xlarge|16|120.0|880|2 × NVIDIA P100|2 × 16|5.0|1,000|No|4|8|20|
|ecs.gn5-c28g1.7xlarge|28|112.0|440|1 × NVIDIA P100|1 × 16|5.0|1,000|No|8|8|20|
|ecs.gn5-c8g1.8xlarge|32|240.0|1,760|4 × NVIDIA P100|4 × 16|10.0|2,000|No|8|8|20|
|ecs.gn5-c28g1.14xlarge|56|224.0|880|2 × NVIDIA P100|2 × 16|10.0|2,000|No|14|8|20|
|ecs.gn5-c8g1.14xlarge|54|480.0|3,520|8 × NVIDIA P100|8 × 16|25.0|4,000|No|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn5i, compute optimized instance family with GPU capabilities

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses NVIDIA P4 GPU processors.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning and inference
    -   Server-side GPU compute workloads such as multimedia encoding and decoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn5i-c2g1.large|2|8.0|None|1 × NVIDIA P4|1 × 8|1.0|100|Yes|2|2|6|
|ecs.gn5i-c4g1.xlarge|4|16.0|None|1 × NVIDIA P4|1 × 8|1.5|200|Yes|2|3|10|
|ecs.gn5i-c8g1.2xlarge|8|32.0|None|1 × NVIDIA P4|1 × 8|2.0|400|Yes|4|4|10|
|ecs.gn5i-c16g1.4xlarge|16|64.0|None|1 × NVIDIA P4|1 × 8|3.0|800|Yes|4|8|20|
|ecs.gn5i-c16g1.8xlarge|32|128.0|None|2 × NVIDIA P4|2 × 8|6.0|1,200|Yes|8|8|20|
|ecs.gn5i-c28g1.14xlarge|56|224.0|None|2 × NVIDIA P4|2 × 8|10.0|2,000|Yes|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## gn4, compute optimized family with GPU capabilities

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses NVIDIA M40 GPU processors.
-   Offers multiple CPU-to-memory ratios.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing applications, such as fluid dynamics, finance, genomics, and environmental analysis
    -   Server-side GPU compute workloads such as high-performance computation, rendering, and multi-media coding and decoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:---|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.gn4-c4g1.xlarge|4|30.0|None|1 × NVIDIA M40|1 × 12|3.0|300|No|1|3|10|
|ecs.gn4-c8g1.2xlarge|8|30.0|None|1 × NVIDIA M40|1 × 12|3.0|400|No|1|4|10|
|ecs.gn4.8xlarge|32|48.0|None|1 × NVIDIA M40|1 × 12|6.0|800|No|3|8|20|
|ecs.gn4-c4g1.2xlarge|8|60.0|None|2 × NVIDIA M40|2 × 12|5.0|500|No|1|4|10|
|ecs.gn4-c8g1.4xlarge|16|60.0|None|2 × NVIDIA M40|2 × 12|5.0|500|No|1|8|20|
|ecs.gn4.14xlarge|56|96.0|None|2 × NVIDIA M40|2 × 12|10.0|1,200|No|4|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## f1, compute optimized instance family with FPGAs

Features:

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Uses Intel® Arria® 10 GX 1150 FPGAs.
-   Offers a CPU-to-memory ratio of 1:7.5.
-   Equipped with 2.5 GHz Intel® Xeon® E5-2682 v4 \(Broadwell\) processors.
-   Provides a fast and reliable network based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning and inference
    -   Genomics research
    -   Financial analysis
    -   Image transcoding
    -   Computational workloads such as real-time video processing and security management

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|FPGAs|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:----|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.f1-c8f1.2xlarge|8|60.0|None|Intel Arria 10 GX 1150|3.0|400|Yes|4|4|10|
|ecs.f1-c8f1.4xlarge|16|120.0|None|2 × Intel Arria 10 GX 1150|5.0|1,000|Yes|4|8|20|
|ecs.f1-c28f1.7xlarge|28|112.0|None|Intel Arria 10 GX 1150|5.0|2,000|Yes|8|8|20|
|ecs.f1-c28f1.14xlarge|56|224.0|None|2 × Intel Arria 10 GX 1150|10.0|2,000|Yes|14|8|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmgn6e, GPU-accelerated compute optimized ECS Bare Metal Instance family

ebmgn6e is in invitational preview. To use ebmgn6e, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides flexible and powerful software-defined compute based on the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Uses NVIDIA V100 \(32 GB NVLink\) GPU processors.
-   Offers a CPU-to-memory ratio of 1:8.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Uses NVIDIA V100 GPU computing accelerators \(SXM2-based\).
    -   Powered by the new NVIDIA Volta architecture.
    -   Equipped with 32 GB HBM2 GPU memory \(900 GB/s bandwidth\) per GPU.
    -   Equipped with 5,120 CUDA cores per GPU.
    -   Equipped with 640 Tensor cores per GPU.
    -   Supports up to six NVLink connections for a total bandwidth of 300 GB/s \(25 GB/s per connection\).
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning applications such as training and inference applications of AI algorithms used in image classification, autonomous vehicles, and speech recognition
    -   Scientific computing applications such as computational fluid dynamics, computational finance, molecular dynamics, and environmental analysis

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|----|-----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmgn6e.24xlarge|96|768.0|None|V100\*8|256|32.0|4,800|Yes|16|15|20|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmgn6v, GPU-accelerated compute optimized ECS Bare Metal Instance family

Features

-   Provides flexible and powerful software-defined compute based on the X-Dragon architecture.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Uses NVIDIA V100 GPU processors.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Uses NVIDIA V100 GPU computing accelerators \(SXM2-based\).
    -   Powered by the new NVIDIA Volta architecture.
    -   Equipped with 16 GB HBM2 GPU memory \(900 GB/s bandwidth\) per GPU.
    -   Equipped with 5,120 CUDA cores per GPU.
    -   Equipped with 640 Tensor cores per GPU.
    -   Supports up to six NVLink connections for a total bandwidth of 300 GB/s \(25 GB/s per connection\).
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   Deep learning applications such as training and inference applications of AI algorithms used in image classification, autonomous vehicles, and speech recognition
    -   Scientific computing applications such as computational fluid dynamics, computational finance, molecular dynamics, and environmental analysis

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|----|-----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmgn6v.24xlarge|96|384.0|None|V100\*8|128|30.0|4,500|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmgn6i, GPU-accelerated compute optimized ECS Bare Metal Instance family

Features

-   Provides flexible and powerful software-defined compute based on the X-Dragon architecture.
-   I/O optimized.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Supports ESSDs that deliver millions of IOPS, standard SSDs, and ultra disks.
-   Uses NVIDIA T4 GPU computing accelerators.
    -   Powered by the new NVIDIA Turing architecture.
    -   Equipped with 16 GB memory \(320 GB/s bandwidth\) per GPU.
    -   Equipped with 2,560 CUDA cores per GPU.
    -   Euipped with up to 320 Turing Tensor cores per GPU.
    -   Mixed-precision Tensor cores support 65 FP16 TFLOPS, 130 INT8 TOPS, and 260 INT4 TOPS.
-   Provides high network performance based on large computing capacity.
-   Suitable for the following scenarios:
    -   AI \(deep learning and machine learning\) inference for computer vision, speech recognition, speech synthesis, natural language processing \(NLP\), machine translation, and recommendation systems
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   Graphics workstations or overloaded graphics computing
    -   GPU-accelerated databases
    -   High-performance computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPUs|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|----|-----------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmgn6i.24xlarge|96|384.0|None|T4\*4|64|30.0|4,500|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmc6a, compute optimized ECS Bare Metal Instance family

ebmc6a is in invitational preview. To use ebmc6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:2.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering
    -   Data analysis and computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|--------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.ebmc6a.64xlarge|256|512.0|None|64.0|24,000|Yes|31|480|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmc6e, compute optimized ECS Bare Metal Instance family with enhanced performance

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   I/O optimized.
-   Supports ESSDs.
-   Offers a CPU-to-memory ratio of 1:2.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Scenarios that have high security and regulatory requirements, such as deploying core database services
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Web frontend servers
    -   Frontend servers of massively multiplayer online \(MMO\) games
    -   Data analysis, batch processing, and video encoding
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.ebmc6e.26xlarge|104|192.0|None|30.0|24,000|Yes|1,800|16|31|10|480|20.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmc6, compute optimized ECS Bare Metal Instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:1.8.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering
    -   Frontend servers of MMO games
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmc6.26xlarge|104|192.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmg6a, general purpose ECS Bare Metal Instance family

ebmg6a is in invitational preview. To use ebmg6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:4.
-   I/O optimized.
-   Supports enhanced SSDs \(ESSDs\), standard SSDs, and ultra disks.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering
    -   Computing clusters and memory intensive data processing
    -   Data analysis and computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|--------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.ebmg6a.64xlarge|256|1024.0|None|64.0|24,000|Yes|31|480|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmg6e, general purpose ECS Bare Metal Instance family with enhanced performance

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   I/O optimized.
-   Supports ESSDs.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Scenarios that have high security and regulatory requirements, such as deploying core database services
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Enterprise-level applications of various types and sizes
    -   Websites and application servers
    -   Game servers
    -   Small and medium-sized database systems, caches, and search clusters
    -   Data analysis and computing
    -   Compute clusters and memory intensive data processing
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.ebmg6e.26xlarge|104|384.0|None|30.0|24,000|Yes|1,800|16|31|10|480|20.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmg6, general purpose ECS Bare Metal Instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:3.7.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering
    -   Enterprise-level applications such as large and medium-sized databases
    -   Computing clusters and memory intensive data processing
    -   Data analysis and computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmg6.26xlarge|104|384.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmr6a, memory optimized ECS Bare Metal Instance family

ebmr6a is in invitational preview. To use ebmr6a, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   Equipped with 2.6 GHz AMD EPYC TM ROME processors with a maximum turbo frequency of 3.3 GHz for consistent computing performance.
-   Offers a CPU-to-memory ratio of 1:8.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   In-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|ENIs \(including one primary ENI\)|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|--------------------|:------------------------------|:-----------|:---------------------------------|---------------|-------------------------|
|ecs.ebmr6a.64xlarge|256|2048.0|None|64.0|24,000|Yes|31|480|32.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmr6e, memory optimized ECS Bare Metal Instance family with enhanced performance

Features

-   Provides predictable and consistent ultra-high computing, storage, and network performance with the use of the fast path acceleration based on the third-generation X-Dragon architecture.
-   Provides dedicated hardware resources and physical isolation.
-   I/O optimized.
-   Supports ESSDs.
-   Offers a CPU-to-memory ratio of 1:8.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides ultra-high network performance with a packet forwarding rate of 24,000 Kpps.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Scenarios that have high security and regulatory requirements, such as deploying core database services
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications
    -   High-performance scientific and engineering applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|Connections \(K\)|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|Disk IOPS \(K\)|Disk bandwidth \(Gbit/s\)|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|-----------------|:---------|:---------------------------------|----------------------------|---------------|-------------------------|
|ecs.ebmr6e.26xlarge|104|768.0|None|30.0|24,000|Yes|1,800|16|31|10|480|20.0|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmr6, memory optimized ECS Bare Metal Instance family

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:7.4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmr6.26xlarge|104|768.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmhfc6, compute optimized ECS Bare Metal Instance family with high clock speed

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:2.4.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmhfc6.20xlarge|80|192.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmhfg6, general purpose ECS Bare Metal Instance family with high clock speed

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:4.8.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Enterprise-level applications such as large and medium-sized databases
    -   Video encoding, decoding, and rendering

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmhfg6.20xlarge|80|384.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmhfr6, memory optimized ECS Bare Metal Instance family with high clock speed

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:9.6.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmhfr6.20xlarge|80|768.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmre6p, non-volatile memory optimized ECS Bare Metal Instance family with enhanced performance

To use ebmre6p, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   Uses Intel ® Optane TM non-volatile memory.
-   Cost-effective due to end-to-end optimization for ApsaraDB for Redis scenarios.
-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Supports a maximum of 1,920 GiB memory \(384 GiB DRAM memory + 1,536 GiB Intel ® Optane TM non-volatile memory\), offers a CPU-to-memory ratio of about 1:20, and can meet the needs of memory intensive applications.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   In-memory databases such as ApsaraDB for Redis
    -   High-performance databases such as SAP HANA
    -   Other memory intensive applications such as AI applications and smart search applications

Instance types

|Instance type|vCPUs|DRAM \(GiB\)|AEP memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-----------|------------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmre6p.26xlarge|104|384.0|1536.0|None|30.0|6,000|Yes|16|31|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmre6-6t, memory optimized ECS Bare Metal Instance family with enhanced performance

To use ebmre6-6t, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:30.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz.
-   Provides high network performance with a packet forwarding rate of 6,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   High-performance databases and in-memory databases such as SAP HANA
    -   Memory intensive applications
    -   Big data processing engines such as Apache Spark and Presto

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmre6-6t.52xlarge|208|6144.0|None|30.0|6,000|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## scchfc6, compute optimized SCC instance family with high clock speed

To use this instance family, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports enhanced SSDs \(ESSDs\), standard SSDs, and ultra disks.
-   Supports both RoCE and VPCs, of which RoCE is dedicated to RDMA communication.
-   Provides all the features of ECS Bare Metal Instance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Offers a CPU-to-memory ratio of 1:2.4.
-   Scenarios:
    -   Large-scale machine learning training
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Physical cores|Memory \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|--------------|:--|:-------------------|:------------------------------|:--------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.scchfc6.20xlarge|80|40|192.0|None|30.0|6,000|50|Yes|8|32|10|

**Note:**

-   ecs.scchfc6.20xlarge provides 80 logical processors on 40 physical cores.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## scchfg6, general purpose SCC instance family with high clock speed

To use this instance family, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports enhanced SSDs, standard SSDs, and ultra disks.
-   Supports both RoCE and VPCs, of which RoCE is dedicated to RDMA communication.
-   Provides all the features of ECS Bare Metal Instance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Offers a CPU-to-memory ratio of 1:4.8.
-   Scenarios:
    -   Large-scale machine learning training
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Physical cores|Memory \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|--------------|:--|:-------------------|:------------------------------|:--------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.scchfg6.20xlarge|80|40|384.0|None|30.0|6,000|50|Yes|8|32|10|

**Note:**

-   ecs.scchfg6.20xlarge provides 80 logical processors on 40 physical cores.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## scchfr6, memory optimized SCC instance family with high clock speed

To use this instance family, [submit a ticket](https://workorder-intl.console.aliyun.com/console.htm).

Features

-   I/O optimized.
-   Supports enhanced SSDs, standard SSDs, and ultra disks.
-   Supports both RoCE and VPCs, of which RoCE is dedicated to RDMA communication.
-   Provides all the features of ECS Bare Metal Instance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Platinum 8269 \(Cascade Lake\) processors with a maximum turbo frequency of 3.5 GHz.
-   Offers a CPU-to-memory ratio of 1:9.6.
-   Scenarios:
    -   Large-scale machine learning training
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Physical cores|Memory \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|--------------|:--|:-------------------|:------------------------------|:--------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.scchfr6.20xlarge|80|40|768.0|None|30.0|6,000|50|Yes|8|32|10|

**Note:**

-   ecs.scchfr6.20xlarge provides 80 logical processors on 40 physical cores.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## scch5, SCC instance family with high clock speed

Features

-   I/O optimized.
-   Supports only standard SSDs and ultra disks.
-   Supports both RoCE and VPCs, of which RoCE is dedicated to RDMA communication.
-   Provides all the features of ECS Bare Metal Instance.
-   Equipped with 3.1 GHz Intel ® Xeon ® Gold 6149 \(Skylake\) processors.
-   Offers a CPU-to-memory ratio of 1:3.
-   Scenarios:
    -   Large-scale machine learning training
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Physical cores|Memory \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|--------------|:--|:-------------------|:------------------------------|:--------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.scch5.16xlarge|64|32|192.0|None|10.0|4,500|25 × 2|No|8|32|10|

**Note:**

-   ecs.scch5.16xlarge provides 64 logical processors on 32 physical cores.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## sccg5, general purpose SCC instance family

Features

-   I/O optimized.
-   Supports only standard SSDs and ultra disks.
-   Supports both RoCE and VPCs, of which RoCE is dedicated to RDMA communication.
-   Provides all the features of ECS Bare Metal Instance.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Offers a CPU-to-memory ratio of 1:4.
-   Scenarios:
    -   Large-scale machine learning training
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Physical cores|Memory \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|--------------|:--|:-------------------|:------------------------------|:--------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.sccg5.24xlarge|96|48|384.0|None|10.0|4,500|25 × 2|No|8|32|10|

**Note:**

-   ecs.sccg5.24xlarge provides 96 logical processors on 48 physical cores.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## sccgn6, compute optimized SCC instance family with GPU capabilities

Features

-   I/O optimized.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Provides all the features of ECS Bare Metal Instance.
-   Storage:
    -   Supports enhanced SSDs, standard SSDs, and ultra disks
    -   Supports a high performance CPFS
-   Networking:
    -   Supports VPCs
    -   Supports the RoCE v2 network, which is dedicated to low-latency RDMA communication
-   Uses NVIDIA V100 GPU processors that have the SXM2 module:
    -   Powered by the new NVIDIA Volta architecture
    -   Offers a 16 GB HBM2 GPU memory
    -   CUDA Cores 5120
    -   Tensor Cores 640
    -   Offers a GPU memory bandwidth of up to 900 GB/s
    -   Supports up to six NVLink connections and total bandwidth of 300 GB/s \(25 GB/s per connection\)
-   Scenarios:
    -   Ultra-large-scale machine learning training on a distributed GPU cluster
    -   Large-scale high performance scientific computing and simulations
    -   Large-scale data analysis, batch processing, and video encoding

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|GPU|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|RoCE \(Gbit/s\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:--|:-------------------|:------------------------------|---------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.sccgn6.24xlarge|96|384.0|None|V100\*8|30|4,500|25 × 2|Yes|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmc5s, compute optimized ECS Bare Metal Instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:2.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors with a maximum turbo frequency of 2.7 GHz.
-   Provides high network performance with a packet forwarding rate of 4,500 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Scenarios where large volumes of packets are received and transmitted, such as on-screen video comments and telecom data forwarding
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Video encoding, decoding, and rendering

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmc5s.24xlarge|96|192.0|None|30.0|4,500|No|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmg5s, general purpose ECS Bare Metal Instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors with a maximum turbo frequency of 2.7 GHz.
-   Provides high network performance with a packet forwarding rate of 4,500 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Enterprise-level applications such as large and medium-sized databases
    -   Video encoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmg5s.24xlarge|96|384.0|None|30.0|4,500|No|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmr5s, memory optimized ECS Bare Metal Instance family with enhanced network performance

Features

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Offers a CPU-to-memory ratio of 1:8.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors with a maximum turbo frequency of 2.7 GHz.
-   Provides high network performance with a packet forwarding rate of 4,500 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   High-performance databases and in-memory databases
    -   Data analysis, data mining, and distributed memory caching
    -   Hadoop clusters, Spark clusters, and other memory intensive enterprise applications

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmr5s.24xlarge|96|768.0|None|30.0|4,500|No|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmg5, general purpose ECS Bare Metal Instance family

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors with a maximum turbo frequency of 2.7 GHz.
-   Provides high network performance with a packet forwarding rate of 4,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Enterprise-level applications such as large and medium-sized databases
    -   Video encoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmg5.24xlarge|96|384.0|None|10.0|4,000|No|8|32|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmhfg5, ECS Bare Metal Instance family with high clock speed

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Offers a CPU-to-memory ratio of 1:4.
-   Equipped with 3.7 GHz Intel ® Xeon ® E3-1240v6 \(Skylake\) processors with a maximum turbo frequency of 4.1 GHz.
-   Provides high network performance with a packet forwarding rate of 2,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Disabled failover by default.

    You can call the [ModifyInstanceMaintenanceAttributes](/intl.en-US/API Reference/Operations and monitoring/ModifyInstanceMaintenanceAttributes.md) operation to modify the maintenance action. Set ActionOnMaintenance to AutoRedeploy to enable failover.

-   Supports Intel ® SGX.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Gaming and finance applications that require high performance
    -   High-performance web servers
    -   Enterprise-level applications such as high-performance databases

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmhfg5.2xlarge|8|32.0|None|6.0|2,000|No|8|6|8|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## ebmc4, compute optimized ECS Bare Metal Instance family

Features

-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Offers a CPU-to-memory ratio of 1:2.
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors with a maximum turbo frequency of 2.9 GHz.
-   Provides high network performance with a packet forwarding rate of 4,000 Kpps.
-   Supports VPCs only.
-   Provides dedicated hardware resources and physical isolation.
-   Suitable for the following scenarios:
    -   Workloads that require direct access to physical resources or scenarios that require a license to be bound to the hardware
    -   Third-party virtualization including Xen and KVM, and AnyStack including OpenStack and ZStack
    -   Containers including Docker, Clear Containers, and Pouch
    -   Enterprise-level applications such as large and medium-sized databases
    -   Video encoding

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:----|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.ebmc4.8xlarge|32|64.0|None|10.0|4,000|No|8|12|10|

**Note:**

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## t6, burstable instance family

Features:

-   Equipped with 2.5 GHz Intel® Xeon® Cascade Lake processors with a maximum turbo frequency of 3.2 GHz.
-   More cost-effective when compared with the t5 burstable instance family.
-   Delivers a bandwidth of up to 6 Gbit/s.
-   Paired with the DDR4 memory.
-   Provides baseline CPU performance and is burstable, but limited by accumulated CPU credits.
-   Supports VPCs only.
-   Scenarios:
    -   Web application servers
    -   Lightweight applications and microservices
    -   Development and testing environments

Instance types

|Instance type|vCPU|Memory \(GiB\)|Baseline CPU computing performance|CPU credits per hour|Max CPU credit balance|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|--------------|:---------------------------------|:-------------------|:---------------------|---------------------|-------------------------|-------------------------------|:-----------|----------|:---------------------------------|----------------------------|
|ecs.t6-c4m1.large|2|0.5|5%|6|144|None|0.08|40|Yes|1|2|2|
|ecs.t6-c2m1.large|2|1.0|10%|12|288|None|0.08|60|Yes|1|2|2|
|ecs.t6-c1m1.large|2|2.0|20%|24|576|None|0.08|100|Yes|1|2|2|
|ecs.t6-c1m2.large|2|4.0|20%|24|576|None|0.08|100|Yes|1|2|2|
|ecs.t6-c1m4.large|2|8.0|30%|36|864|None|0.08|100|Yes|1|2|2|
|ecs.t6-c1m4.xlarge|4|16.0|40%|96|2304|None|0.16|200|Yes|1|2|6|
|ecs.t6-c1m4.2xlarge|8|32.0|40%|192|4608|None|0.32|400|Yes|1|2|6|

**Note:**

-   When you bind or unbind an ENI, instances of the following instance types must be in the Stopped state: ecs.t6-c1m1.large, ecs.t6-c1m2.large, ecs.t6-c1m4.large, ecs.t6-c2m1.large, and ecs.t6-c4m1.large.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## t5, burstable instance family

Features:

-   Equipped with 2.5 GHz Intel® Xeon® processors.
-   Paired with the DDR4 memory.
-   Offers multiple CPU-to-memory ratios.
-   Provides baseline CPU performance and is burstable, but limited by accumulated CPU credits.
-   Offers a balance of compute, memory, and network resources.
-   Supports VPCs only.
-   Scenarios:
    -   Web application servers
    -   Lightweight applications and microservices
    -   Development and testing environments

Instance types

|Instance type|vCPU|Memory \(GiB\)|Baseline CPU computing performance|CPU credits per hour|Max CPU credit balance|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|--------------|:---------------------------------|:-------------------|:---------------------|---------------------|--------------------|-------------------------------|:-----------|----------|:---------------------------------|----------------------------|
|ecs.t5-lc2m1.nano|1|0.5|20%|12|288|None|0.1|40|Yes|1|2|2|
|ecs.t5-lc1m1.small|1|1.0|20%|12|288|None|0.2|60|Yes|1|2|2|
|ecs.t5-lc1m2.small|1|2.0|20%|12|288|None|0.2|60|Yes|1|2|2|
|ecs.t5-lc1m2.large|2|4.0|20%|24|576|None|0.4|100|Yes|1|2|2|
|ecs.t5-lc1m4.large|2|8.0|20%|24|576|None|0.4|100|Yes|1|2|2|
|ecs.t5-c1m1.large|2|2.0|25%|30|720|None|0.5|100|Yes|1|2|2|
|ecs.t5-c1m2.large|2|4.0|25%|30|720|None|0.5|100|Yes|1|2|2|
|ecs.t5-c1m4.large|2|8.0|25%|30|720|None|0.5|100|Yes|1|2|2|
|ecs.t5-c1m1.xlarge|4|4.0|25%|60|1440|None|0.8|200|Yes|1|2|6|
|ecs.t5-c1m2.xlarge|4|8.0|25%|60|1440|None|0.8|200|Yes|1|2|6|
|ecs.t5-c1m4.xlarge|4|16.0|25%|60|1440|None|0.8|200|Yes|1|2|6|
|ecs.t5-c1m1.2xlarge|8|8.0|25%|120|2880|None|1.2|400|Yes|1|2|6|
|ecs.t5-c1m2.2xlarge|8|16.0|25%|120|2880|None|1.2|400|Yes|1|2|6|
|ecs.t5-c1m4.2xlarge|8|32.0|25%|120|2880|None|1.2|400|Yes|1|2|6|
|ecs.t5-c1m1.4xlarge|16|16.0|25%|240|5760|None|1.2|600|Yes|1|2|6|
|ecs.t5-c1m2.4xlarge|16|32.0|25%|240|5760|None|1.2|600|Yes|1|2|6|

**Note:**

-   When you bind or unbind an ENI, instances of the following instance types must be in the Stopped state: ecs.t5-lc2m1.nano, ecs.t5-c1m1.large, ecs.t5-c1m2.large, ecs.t5-c1m4.large, ecs.t5-lc1m1.small, ecs.t5-lc1m2.large, ecs.t5-lc1m2.small, and ecs.t5-lc1m4.large.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## v5, CPU overprovisioned instance family

Features:

-   Supports a range of CPU-to-memory ratios, such as 1:1, 1:2, 1:4, and 1:8.
-   You can create v5 instances only on dedicated hosts.

    **Note:** For information about other types of instances that can be created on dedicated hosts, see [Dedicated host types](/intl.en-US/Product Introduction/Dedicated host types.md).

-   I/O optimized.
-   Supports ESSDs, standard SSDs, and ultra disks.
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors.
-   Suitable for the following scenarios:
    -   Migration from offline virtualization environments to Alibaba Cloud
    -   Services that generate low, medium, or burstable CPU loads

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|-------------|-----|--------------|--------------------|-------------------------------|------------|----------|----------------------------------|----------------------------|
|ecs.v5-c1m1.large|2|2.0|2.0|300|Yes|2|2|2|
|ecs.v5-c1m1.xlarge|4|4.0|2.0|300|Yes|2|2|6|
|ecs.v5-c1m1.2xlarge|8|8.0|3.0|400|Yes|2|3|6|
|ecs.v5-c1m1.3xlarge|12|12.0|3.0|400|Yes|4|3|6|
|ecs.v5-c1m1.4xlarge|16|16.0|4.0|500|Yes|4|4|6|
|ecs.v5-c1m1.8xlarge|32|32.0|4.0|500|Yes|8|4|6|
|ecs.v5-c1m2.large|2|4.0|2.0|300|Yes|2|2|2|
|ecs.v5-c1m2.xlarge|4|8.0|2.0|300|Yes|2|2|6|
|ecs.v5-c1m2.2xlarge|8|16.0|3.0|400|Yes|2|3|6|
|ecs.v5-c1m2.3xlarge|12|24.0|3.0|400|Yes|4|3|6|
|ecs.v5-c1m2.4xlarge|16|32.0|4.0|500|Yes|4|4|6|
|ecs.v5-c1m2.8xlarge|32|64.0|4.0|500|Yes|8|4|6|
|ecs.v5-c1m4.large|2|8.0|2.0|300|Yes|2|2|2|
|ecs.v5-c1m4.xlarge|4|16.0|2.0|300|Yes|2|2|6|
|ecs.v5-c1m4.2xlarge|8|32.0|3.0|400|Yes|2|3|6|
|ecs.v5-c1m4.3xlarge|12|48.0|3.0|400|Yes|4|3|6|
|ecs.v5-c1m4.4xlarge|16|64.0|4.0|500|Yes|4|4|6|
|ecs.v5-c1m4.8xlarge|32|128.0|4.0|500|Yes|8|4|6|
|ecs.v5-c1m8.large|2|16.0|2.0|300|Yes|2|2|2|
|ecs.v5-c1m8.xlarge|4|32.0|2.0|300|Yes|2|2|6|
|ecs.v5-c1m8.2xlarge|8|64.0|3.0|400|Yes|2|3|6|
|ecs.v5-c1m8.3xlarge|12|96.0|3.0|400|Yes|4|3|6|
|ecs.v5-c1m8.4xlarge|16|128.0|4.0|500|Yes|4|4|6|
|ecs.v5-c1m8.8xlarge|32|256.0|4.0|500|Yes|8|4|6|

**Note:** For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## s6, shared standard instance family

Features:

-   More cost-effective than the previous-generation shared instance families \(xn4, n4, mn4, and e4\).
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8269CY \(Cascade Lake\) processors with a maximum turbo frequency of 3.2 GHz for consistent computing performance.
-   Paired with DDR4 memory.
-   Offers multiple CPU-to-memory ratios, such as 1:1, 1:2, and 1:4.
-   I/O optimized.
-   Supports standard SSDs and ultra disks.
-   Supports VPCs only.
-   Suitable for the following scenarios:
    -   Small and medium-sized websites, and web applications
    -   Development environments, servers, code repositories, microservices, and testing and staging environments
    -   Lightweight databases and caches
    -   Lightweight enterprise applications and integrated application services

Instance types

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Base bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|-------------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.s6-c1m1.small|1|1.0|None|0.1|150|Yes|1|2|2|
|ecs.s6-c1m2.small|1|2.0|None|0.1|150|Yes|1|2|2|
|ecs.s6-c1m4.small|1|4.0|None|0.1|150|Yes|1|2|2|
|ecs.s6-c1m2.large|2|4.0|None|0.2|200|Yes|1|2|2|
|ecs.s6-c1m4.large|2|8.0|None|0.4|200|Yes|1|2|2|
|ecs.s6-c1m2.xlarge|4|8.0|None|0.4|300|Yes|1|2|6|
|ecs.s6-c1m4.xlarge|4|16.0|None|0.8|300|Yes|1|2|6|
|ecs.s6-c1m2.2xlarge|8|16.0|None|0.8|600|Yes|1|2|6|
|ecs.s6-c1m4.2xlarge|8|32.0|None|1.2|600|Yes|1|2|6|

**Note:**

-   To bind or unbind an Elastic Network Interface \(ENI\), instances of the following instance types must be in the stopped state: ecs.s6-c1m1.small, ecs.s6-c1m2.large, ecs.s6-c1m2.small, ecs.s6-c1m4.large, and ecs.s6-c1m4.small.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## Previous-generation shared instance families xn4, n4, mn4, and e4

Features:

-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors.
-   Paired with DDR4 memory.
-   Offers multiple CPU-to-memory ratios.

|Instance family|Description|vCPU-to-memory ratio|Scenario|
|:--------------|:----------|:-------------------|:-------|
|xn4|Shared compact type|1:1|-   Frontend web applications
-   Lightweight applications and microservices
-   Applications for development or testing applications |
|n4|Shared compute optimized type|1:2|-   Websites and web applications
-   Development environments, servers, code repositories, microservices, and testing and staging environments
-   Lightweight enterprise applications |
|mn4|Shared general purpose type|1:4|-   Websites and web applications
-   Lightweight databases and caches
-   Integrated applications and lightweight enterprise services |
|e4|Shared memory optimized type|1:8|-   Applications that require a large amount of memory
-   Lightweight databases and caches |

Instance types of xn4

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.xn4.small|1|1.0|None|0.5|50|No|1|2|2|

**Note:**

-   To bind or unbind an ENI, instances of the ecs.xn4.small instance type must be in the stopped state.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

Instance types of n4

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.n4.small|1|2.0|None|0.5|50|No|1|2|2|
|ecs.n4.large|2|4.0|None|0.5|100|No|1|2|2|
|ecs.n4.xlarge|4|8.0|None|0.8|150|No|1|2|6|
|ecs.n4.2xlarge|8|16.0|None|1.2|300|No|1|2|6|
|ecs.n4.4xlarge|16|32.0|None|2.5|400|No|1|2|6|
|ecs.n4.8xlarge|32|64.0|None|5.0|500|No|1|2|6|

**Note:**

-   To bind or unbind an ENI, instances of the ecs.n4.small and ecs.n4.large instance types must be in the stopped state.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

Instance types of mn4

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.mn4.small|1|4.0|None|0.5|50|No|1|2|2|
|ecs.mn4.large|2|8.0|None|0.5|100|No|1|2|2|
|ecs.mn4.xlarge|4|16.0|None|0.8|150|No|1|2|6|
|ecs.mn4.2xlarge|8|32.0|None|1.2|300|No|1|2|6|
|ecs.mn4.4xlarge|16|64.0|None|2.5|400|No|1|2|6|
|ecs.mn4.8xlarge|32|128.0|None|5|500|No|2|8|6|

**Note:**

-   To bind or unbind an ENI, instances of the ecs.mn4.small and ecs.mn4.large instance types must be in the stopped state.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

Instance types of e4

|Instance type|vCPU|Memory \(GiB\)|Local storage \(GiB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs \(including one primary ENI\)|Private IP addresses per ENI|
|:------------|:---|:-------------|:--------------------|:-------------------|:------------------------------|:-----------|:---------|:---------------------------------|----------------------------|
|ecs.e4.small|1|8.0|None|0.5|50|No|1|2|2|
|ecs.e4.large|2|16.0|None|0.5|100|No|1|2|2|
|ecs.e4.xlarge|4|32.0|None|0.8|150|No|1|2|6|
|ecs.e4.2xlarge|8|64.0|None|1.2|300|No|1|3|6|
|ecs.e4.4xlarge|16|128.0|None|2.5|400|No|1|8|6|

**Note:**

-   To bind or unbind an ENI, instances of the ecs.e4.small and ecs.e4.large instance types must be in the stopped state.
-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Description of instance specifications](/intl.en-US/Instance/Instance families.md).

## Description of instance specifications

|Specification|Descripition|
|-------------|------------|
|Local storage|Local storage, also called cache disks or local disks, refers to the disks attached to the physical servers where ECS instances are hosted. Local storage provides temporary block storage for instances. Local storage capacity is measured in GiB. Data stored on local disks may be lost when the compute resources \(vCPUs and memory\) of an instance are released or when an instance is failed over to a normal physical server upon a physical server failure. For more information, see [Local disks](/intl.en-US/Block Storage/Block Storage overview/Local disks.md).|
|Bandwidth|The maximum bandwidth in one direction. Inbound bandwidth and outbound bandwidth are calculated separately. **Note:** Each instance specification is obtained through verification in a test environment. In actual scenarios, the performance of an instance may vary depending on other factors such as instance load. We recommend that you perform business stress tests on instances to choose appropriate instance types. |
|Packet forwarding rate|The maximum sum of inbound and outbound packet forwarding rates. For more information about how to test the packet forwarding rate, see [Test network performance](https://www.alibabacloud.com/help/faq-detail/55757.htm). **Note:** Each instance specification is obtained through verification in a test environment. In actual scenarios, the performance of an instance may vary depending on other factors such as instance load. We recommend that you perform business stress tests on instances to choose appropriate instance types. |
|Connections|Connections, also called sessions, are the process of establishing connections and transferring data between a client and a server. A connection is uniquely defined by the network communication quintuple that consists of a source IP address, a destination IP address, a source port, a destination port, and a protocol. Connections of an ECS instance include TCP, UDP, and ICMP connections.|
|NIC queues|The maximum number of NIC queues that the primary NIC of an instance supports. If your instance type is not a member of an ECS Bare Metal Instance family, the maximum number of NIC queues supported by the secondary NIC is the same as that supported by the primary NIC.|

