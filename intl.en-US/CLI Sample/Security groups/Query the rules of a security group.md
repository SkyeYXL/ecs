# Query the rules of a security group

This topic describes how to call the DescribeSecurityGroupAttribute operation by using Alibaba Cloud CLI to query the rules of a security group.

You can call the DescribeSecurityGroupAttribute operation to query the rules of a security group. Before you call the operation, we recommend that you read the description of the operation. For more information, see [DescribeSecurityGroupAttribute](/intl.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md).

When you call an API operation through Alibaba Cloud CLI, make sure that request parameter values of different data types are in required formats. For more information, see [Parameter format overview]().

## Example 1: Query the inbound rules of a security group

Query the inbound rules of the `sg-bp18viqv1vrl0fgy****` security group.

```
aliyun ecs DescribeSecurityGroupAttribute --RegionId cn-hangzhou --SecurityGroupId sg-bp18viqv1vrl0fgy**** --Direction ingress --output cols=SourceCidrIp,NicType,PortRange,Direction,IpProtocol,Policy rows=Permissions.Permission[]
```

Sample response:

```
SourceCidrIp | NicType  | PortRange | Direction | IpProtocol | Policy
------------ | -------  | --------- | --------- | ---------- | ------
0.0.0.0/0    | intranet | 22/22     | ingress   | TCP        | Accept
0.0.0.0/0    | intranet | 80/80     | ingress   | TCP        | Accept
```

## Example 2: Query the outbound rules of a security group

Query the outbound rules of the `sg-bp18viqv1vrl0fgy****` security group.

```
aliyun ecs DescribeSecurityGroupAttribute --RegionId cn-hangzhou --SecurityGroupId sg-bp18viqv1vrl0fgy**** --Direction egress --output cols=SourceCidrIp,NicType,PortRange,Direction,IpProtocol,Policy rows=Permissions.Permission[]
```

Sample response:

```
SourceCidrIp | NicType  | PortRange | Direction | IpProtocol | Policy
------------ | -------  | --------- | --------- | ---------- | ------
0.0.0.0/0    | intranet | -1/-1     | egress    | ALL        | Accept
```

## Example 3: Query the rules of a classic network-type security group by NIC type

The rules of a classic network-type security group distinguish between internal and public NICs. The `sg-bp17g9h65ajbejxv****` classic network-type security group is used in this example to query rules by NIC type.

**Note:** By default, only internal NICs are available for rules in a VPC-type security group.

-   Query the rules that have the NIC Type parameter set to Public.

    ```
    aliyun ecs DescribeSecurityGroupAttribute --RegionId cn-hangzhou --SecurityGroupId sg-bp17g9h65ajbejxv**** --NicType internet --output cols=SourceCidrIp,NicType,PortRange,Direction,IpProtocol,Policy rows=Permissions.Permission[]
    ```

    Sample response:

    ```
    SourceCidrIp    | NicType  | PortRange | Direction | IpProtocol | Policy
    ------------    | -------  | --------- | --------- | ---------- | ------
    0.0.0.0/0       | internet | 80/80     | ingress   | TCP        | Accept
    0.0.0.0/0       | internet | 22/22     | ingress   | TCP        | Accept
    0.0.0.0/0       | internet | 443/443   | ingress   | TCP        | Accept
    ```

-   Query the rules that have the NIC Type parameter set to Internal.

    ```
    aliyun ecs DescribeSecurityGroupAttribute --RegionId cn-hangzhou --SecurityGroupId sg-bp17g9h65ajbejxv**** --NicType intranet --output cols=SourceCidrIp,NicType,PortRange,Direction,IpProtocol,Policy rows=Permissions.Permission[]
    ```

    Sample response:

    ```
    SourceCidrIp      | NicType  | PortRange | Direction | IpProtocol | Policy
    ------------      | -------  | --------- | --------- | ---------- | ------
    0.0.0.0/0         | intranet | 6379/6379 | ingress   | TCP        | Accept
    ```


