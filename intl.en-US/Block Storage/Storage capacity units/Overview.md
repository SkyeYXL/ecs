---
keyword: [Alibaba Cloud, SCU, storage plan, budget, cost-effectiveness]
---

# Overview

Storage capacity units \(SCUs\) are subscription storage resource plans that can be used to offset the bills of various storage resources located within the same regions as the SCUs. Compared with disks purchased together with subscription ECS instances or resource plans of a specific resource, SCUs offer a better combination of cost-effectiveness and flexibility together with pay-as-you-go resources.

## Scenarios

SCUs are suitable for scenarios that require low storage costs and high flexibility in disk creation, such as:

-   Scenarios where frequent interactions and adjustments are required in different runtime environments including development, test, and production environments. Examples: DevOps or microservice scenarios.
-   Scenarios where multiple projects are incubated at the same time and applications are delivered or released on a frequent basis. Examples: container cloud-native or mobile game scenarios.

You can use SCUs in one of the following patterns:

-   Pattern 1: You have created multiple pay-as-you-go disks. The historical bills of these disks show that the average monthly disk space consumption is consistent. You can purchase SCUs to reduce monthly storage costs.
-   Pattern 2: The cost budget for a quarter or fiscal year has been planned in advance and requires a centralized purchase or advanced payment. You can first estimate the required storage capacity based on historical data and your budget, and then purchase SCUs and pay-as-you-go disks to fulfill your storage requirements.

## Comparison between different purchase methods of disks

The following table compares the purchase methods of disks.

|Purchase method|Purpose|Form|Scenario|
|---------------|-------|----|--------|
|SCU|Offsets the hourly bills of pay-as-you-go disks.|A subscription storage resource plan that requires an all-upfront payment. It is used to offset fees incurred by pay-as-you-go disks but does not provide storage capacity.|See the [Scenarios](#section_l5q_vv0_dan) section.|
|Pay-as-you-go disk|Can be resized, encrypted, attached to or detached from an ECS instance, and have snapshots.|A disk that provides storage capacity and uses the pay-as-you-go billing method.|Applications or services with burst traffic such as temporary scale-out, temporary testing, and scientific computing.|
|Subscription disk|Can be resized, encrypted, attached to a subscription ECS instance, and have snapshots.|A disk that provides storage capacity and is purchased together with a subscription ECS instance.|Web services that have 24/7 support, or data disks that store data for subscription ECS instances for an extended period of time.|

## Specifications

SCUs are measured by their capacity. An SCU can have a capacity of 20 GiB, 40 GiB, 100 GiB, 500 GiB, 1 TiB, 2 TiB, 5 TiB, 10 TiB, 20 TiB, or 50 TiB. Different capacities are suited for different scenarios from daily use by developers to enterprise-level applications.

-   Individual developers can purchase SCUs of 20 GiB to 500 GiB for daily use to have long-time cost-effectiveness and flexibility in the use of disks.
-   SCUs of 1 TiB to 50 TiB are suitable for enterprise-level applications, meeting the requirements that cloud-native scenarios \(such as DevOps, microservice, and containerization\) have for flexibility in the use of Block Storage.

The following content lists the offset rules of SCUs:

-   SCUs can be used to offset bills of enhanced SSDs \(ESSDs\), standard SSDs, ultra disks, and basic disks. SCUs cannot be used to offset the bills of local SSDs.
-   SCUs can be used to offset bills of Capacity NAS and Performance NAS. SCUs cannot be used to offset the bills of Extreme NAS or Infrequent Access NAS.
-   SCUs can be used to offset bills of normal snapshots. SCUs cannot be used to offset the bills of local snapshots.
-   SCUs can be used to offset bills of OSS Standard, Infrequent Access, and Archive storage classes.

## Billing methods

SCUs use the subscription billing method. For more information, see [SCU billing methods]().

## Limits

SCUs have the following limits:

-   SCUs can only be used to offset bills of pay-as-you-go resources. SCUs cannot be used to offset pay-as-you-go bills of disks for preemptible instances.
-   You can configure an effective time for each SCU. The configured time must fall within six months of the SCU creation.
-   You cannot call API operations to create or manage SCUs.
-   The capacity limits of SCUs depend on the capacity of your Block Storage devices. For more information about the capacity limits of SCUs that you can purchase in a region, see [Limits](/intl.en-US/Product Introduction/Limits.md).

## Lifecycle

-   If you set SCU Effective Time to Now when you purchase an SCU:

    The SCU will take effect and be applied to pay-as-you-go storage resources at the top of the hour that your purchase the SCU. It will expire at 00:00:00 of the day after its validity period end date. It will offset the bills of pay-as-you-go disks starting from the time it takes effect until it expires.

    Assume that you purchase a 10 TiB SCU with a validity period of one year at 09:10:00 on August 20, 2019. The SCU will take effect starting at 09:00:00 on August 20, 2019 and expire at 24:00:00 on August 21, 2020.

    ![Lifecycle of an SCU](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7533594951/p60644.png)

-   If you specify an effective time when you purchase an SCU:

    The SCU will take effect at the specified time and expire at 00:00:00 of the day after its validity period end date. It will offset the bills of pay-as-you-go disks starting from the time it takes effect until it expires.

    Assume that you purchase a 10 TiB SCU with a validity period of one year at 09:15:00 on August 20, 2019 and set the effective time of the SCU to 01:00:00 of November 19, 2019. The SCU will take effect at 01:00:00 on November 19, 2019 and expire at 24:00:00 on November 20, 2020.

    ![Lifecycle of an SCU with a specified effective time](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7533594951/p67971.png)


