# Anti-DDoS Basic

Anti-DDoS Basic is a service that protects ECS instances from distributed denial-of-service \(DDoS\) attacks to ensure system stability. If the inbound traffic to an instance exceeds the maximum traffic allowed by the instance type, Alibaba Cloud Security limits the inbound traffic.

Anti-DDoS Basic is a free service included in Alibaba Cloud Security. It offers up to 5 Git/s of mitigation capacity against common DDoS attacks. The ECS instance type determines the free-tier mitigation capacity, and you can log on to the Anti-DDoS Basic console to check the actual mitigation capacity threshold. For more information, see [View black hole triggering thresholds in Anit-DDoS Origin Basic](/intl.en-US/DDoS Protection Guide/Product Introduction/View black hole triggering thresholds in Anit-DDoS Origin Basic.md).

## How Anti-DDoS Basic works

After the Anti-DDoS Basic feature is enabled, Alibaba Cloud Security monitors inbound traffic to ECS instances in real time. When large amounts of traffic or unusual traffic involving DDoS attacks is detected, Alibaba Cloud Security redirects the traffic and removes malicious traffic. After the traffic is cleaned, the traffic is passed back to ECS instances. This process is called traffic scrubbing. For more information, see [How Anti-DDoS Basic works]().

**Note:** If Anti-DDoS Basic is enabled for an ECS instance, Alibaba Cloud Security triggers a blackhole when the inbound traffic from the Internet is greater than 5 Gbit/s. All inbound traffic is routed to the blackhole and the Internet access is blocked to secure the cluster. For more information, see [Blackhole filtering policy of Alibaba Cloud](/intl.en-US/DDoS Protection Guide/Product Introduction/Blackhole filtering policy of Alibaba Cloud.md) in DDoS Protection.

Triggering conditions:

-   Attack types. When specified attacks are identified in the inbound traffic, traffic scrubbing is triggered.
-   Traffic size. Generally, traffic involving DDoS attacks is measured in Gbit/s. When the inbound traffic into an ECS instance exceeds the specified threshold, traffic scrubbing is triggered no matter whether the traffic is normal.

The methods of traffic scrubbing include filtering attack packets, limiting the bit rate, and limiting the packet forwarding rate.

Therefore, you must configure the following thresholds when you use Anti-DDoS Basic:

-   BPS threshold: When the inbound traffic exceeds this value, traffic scrubbing is triggered.
-   PPS threshold: When the inbound packet forwarding rate exceeds this value, traffic scrubbing is triggered.

## Traffic scrubbing thresholds of ECS instances

The traffic scrubbing threshold of an ECS instance is determined by its instance type.

-   **Maximum BPS threshold \(Gbit/s\)**: For more information, see the **Bandwidth \(Gbit/s\)** specifications in [Instance families](/intl.en-US/Instance/Instance families.md) and [Phased-out instance types](/intl.en-US/Instance/Phased-out instance types.md).
-   **Maximum PPS threshold \(Kpps\)**: For more information, see the **Packet forwarding rate \(Kpps\)** specifications in [Instance families](/intl.en-US/Instance/Instance families.md) and [Phased-out instance types](/intl.en-US/Instance/Phased-out instance types.md).

The following table describes the scrubbing threshold of ecs.g5.16xlarge.

|Instance type|Maximum BPS threshold \(Gbit/s\)|Maximum PPS threshold \(Kpps\)|
|:------------|:-------------------------------|:-----------------------------|
|ecs.g5.16xlarge|20|400|

## Operations

By default, Anti-DDoS Basic is enabled for ECS. You can perform the following operations after you create an ECS instance:

-   Configure the scrubbing threshold: After an ECS instance is created, the maximum threshold of Anti-DDoS Basic for the instance type is used. However, the maximum BPS threshold for some instance types may be too high to be safe. Therefore, you must set a threshold based on your business needs. For more information, see [Configure a cleaning threshold](/intl.en-US/Anti-DDoS Origin User Guide/Cleaning settings/Configure a cleaning threshold.md) in Anti-DDoS Basic User Guide.
-   Disable traffic scrubbing: not recommended. When the inbound traffic reaches the configured threshold, the entire traffic \(including normal traffic\) is cleaned. This may affect or interrupt normal business. Therefore, you can manually disable traffic scrubbing. For more information, see [Cancel traffic cleaning](/intl.en-US/Anti-DDoS Origin User Guide/Cleaning settings/Cancel traffic cleaning.md) in Anti-DDoS Basic User Guide.

    **Warning:** After traffic scrubbing is disabled, when the inbound traffic is greater than 5 Gbit/s, all traffic is routed to a blackhole. Proceed with caution.


