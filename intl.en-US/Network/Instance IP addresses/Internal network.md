# Internal network

If you need to transmit data between two ECS instances within the same region, we recommend that you transmit data over the internal network. ECS instances can also be connected to ApsaraDB RDS, SLB, and OSS over the internal network.

In the internal network, each non-I/O optimized instance has a shared bandwidth of 1 Gbit/s and each I/O optimized instance has a shared bandwidth of 10 or 25 Gbit/s. The internal network is a shared network and bandwidth may fluctuate.

The following rules apply to an ECS instance in the internal network:

-   The internal communication is affected by the network type, account, region, or security group of an ECS instance. The following table describes how the internal communication is affected.

    |Network type|Account|Region|Security group|Internal communication|
    |:-----------|:------|:-----|:-------------|:---------------------|
    |One VPC|One or more accounts|One region|One security group|By default, Internal communication is enabled. Instances within a security group can also be isolated from each other. For more information, see [Isolation of instances within a security group](/intl.en-US/Best Practices/Security/Isolation of instances within a security group.md).|
    |Different security groups|You can implement internal communication by authorizing mutual access between two security groups. For more information, see [Scenarios for security groups](/intl.en-US/Security/Security groups/Scenarios for security groups.md).|
    |Different VPCs|One or more accounts|One region|Different security groups|You can implement internal communication by using Express Connect. For more information, see [Scenarios](/intl.en-US/Product Introduction/Scenarios.md).|
    |Different regions|
    |Classic network|One account|One region|One security group|By default, internal communication is enabled.|
    |Different accounts|One region|Different security groups|You can implement internal communication by authorizing mutual access between two security groups. For more information, see [Scenarios for security groups](/intl.en-US/Security/Security groups/Scenarios for security groups.md).|

-   The private IP address of an ECS instance within a VPC can be modified. For more information, see [Change the private IP address of an instance](/intl.en-US/Network/Change IPv4 addresses/Change the private IP address of an instance.md). The private IP address of an ECS instance within the classic network cannot be modified.
-   You can use the ClassicLink feature of VPC to connect an ECS instance in the classic network to the cloud resources deployed in a VPC. For more information, see [ClassicLink](/intl.en-US/VPC network connections/ClassicLink/Establish a ClassicLink connection.md).

