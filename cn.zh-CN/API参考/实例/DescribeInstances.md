# DescribeInstances

调用DescribeInstances查询一台或多台ECS实例的详细信息。

## 接口说明

-   请求参数的作用类似于一个过滤器，过滤器为逻辑与（AND）关系。如果某一参数为空，则过滤器不起作用。但是参数InstanceIds如果是一个空JSON数组，则视为该过滤器有效，且返回空。
-   如果您使用的是RAM用户账号或者RAM角色，当用户或者角色缺乏接口权限时，将会返回空列表。您可以在请求中加入`DryRun`参数，判断是否因权限问题导致的空列表现象。
-   通过阿里云CLI调用API时，不同数据类型的请求参数取值必须遵循格式要求，详情请参见[CLI参数格式说明](~~110340~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeInstances&type=RPC&version=2014-05-26)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeInstances|系统规定参数。取值：DescribeInstances |
|RegionId|String|是|cn-hangzhou|实例所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|VpcId|String|否|v-bp67acfmxazb4p\*\*\*\*|专有网络VPC ID。 |
|VSwitchId|String|否|vsw-bp67acfmxazb4p\*\*\*\*|交换机ID。 |
|ZoneId|String|否|cn-hangzhou-g|可用区ID。 |
|InstanceNetworkType|String|否|vpc|实例网络类型。取值范围：

 -   classic：经典网络
-   vpc：专有网络VPC |
|SecurityGroupId|String|否|sg-bp67acfmxazb4p\*\*\*\*|实例所属的安全组。 |
|InstanceIds|String|否|\["i-bp67acfmxazb4p\*\*\*\*", "i-bp67acfmxazb4p\*\*\*\*", … "i-bp67acfmxazb4p\*\*\*\*"\]|实例ID。取值可以由多个实例ID组成一个JSON数组，最多支持100个ID，ID之间用半角逗号（,）隔开。 |
|PageNumber|Integer|否|1|实例状态列表的页码。

 起始值：1

 默认值：1 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。

 最大值：100

 默认值：10 |
|InnerIpAddresses|String|否|\["10.1.1.1", "10.1.2.1", … "10.1.10.1"\]|经典网络类型实例的内网IP列表。当InstanceNetworkType=classic时生效，取值可以由多个IP组成一个JSON数组，最多支持100个IP，IP之间用半角逗号（,）隔开。 |
|PrivateIpAddresses|String|否|\["172.16.1.1", "172.16.2.1", … "172.16.10.1"\]|VPC网络类型实例的私有IP。当InstanceNetworkType=vpc时生效，取值可以由多个IP组成一个JSON数组，最多支持100个IP，IP之间用半角逗号（,）隔开。 |
|PublicIpAddresses|String|否|\["42.1.1.\*\*", "42.1.2.\*\*", … "42.1.10.\*\*"\]|实例的公网IP列表。取值可以由多个IP组成一个JSON数组，最多支持100个IP，IP之间用半角逗号（,）隔开。 |
|EipAddresses|String|否|\["42.1.1.\*\*", "42.1.2.\*\*", … "42.1.10.\*\*"\]|实例的弹性公网IP列表。当InstanceNetworkType=vpc时该参数生效，取值可以由多个IP组成一个JSON数组，最多支持100个IP，IP之间用半角逗号（,）隔开。 |
|InstanceChargeType|String|否|PostPaid|实例的计费方式。取值范围：

 -   PostPaid：按量付费
-   PrePaid：包年包月 |
|InternetChargeType|String|否|PayByTraffic|公网带宽计费方式。取值范围：

 -   PayByBandwidth：按固定带宽计费。
-   PayByTraffic：按使用流量计费。 |
|InstanceName|String|否|Test|实例名称，支持使用通配符\*进行模糊搜索。 |
|ImageId|String|否|m-bp67acfmxazb4p\*\*\*\*|镜像ID。 |
|Status|String|否|Running|实例状态。取值范围：

 -   Pending：创建中
-   Running：运行中
-   Starting：启动中
-   Stopping：停止中
-   Stopped：已停止 |
|LockReason|String|否|security|资源被锁定的原因。 |
|IoOptimized|Boolean|否|true|是否是I/O优化型实例。 |
|Tag.N.value|String|否|valueTest|标签值。

 **说明：** 为提高兼容性，建议您尽量使用Tag.N.Value参数。 |
|Tag.N.key|String|否|keyTest|标签键。

 **说明：** 为提高兼容性，建议您尽量使用Tag.N.Key参数。 |
|Tag.N.Key|String|否|TestKey|实例的标签键。N的取值范围：1~20

 使用一个标签过滤资源，查询到该标签下的资源数量不能超过1000个；使用多个标签过滤资源，查询到同时绑定了多个标签的资源数量不能超过1000个。如果资源数量超过1000个，请使用[ListTagResources](~~110425~~)接口进行查询。 |
|Tag.N.Value|String|否|TestValue|实例的标签值。N的取值范围：1~20 |
|InstanceType|String|否|ecs.g5.large|实例的规格。 |
|InstanceTypeFamily|String|否|ecs.g5|实例的规格族。 |
|KeyPairName|String|否|KeyPairNameTest|实例使用的SSH密钥对名称。 |
|ResourceGroupId|String|否|rg-bp67acfmxazb4p\*\*\*\*|实例所在的企业资源组ID。使用该参数过滤资源时，资源数量不能超过1000个。 |
|HpcClusterId|String|否|hpc-bp67acfmxazb4p\*\*\*\*|实例所在的HPC集群ID。 |
|RdmaIpAddresses|String|否|10.10.10.102|HPC实例的Rdma网络IP。 |
|DryRun|Boolean|否|false|是否只预检此次请求。取值范围：

 -   true：发送检查请求，不会查询资源状况。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码DryRunOperation。
-   false（默认值）：发送正常请求，通过检查后返回2XX HTTP状态码并直接查询资源状况。 |
|AdditionalAttributes.N|RepeatList|否|META\_OPTIONS|其他属性值。N的取值范围：1~20。取值范围：

 -   META\_OPTIONS：实例元数据。
-   DDH\_CLUSTER：专有宿主机集群。 |
|HttpEndpoint|String|否|enabled|是否启用实例元数据的访问通道。取值范围：

 -   enabled：启用
-   disabled：禁用

 默认值：enabled

 **说明：** 有关实例元数据的信息，请参见[实例元数据概述](~~49122~~)。 |
|HttpTokens|String|否|optional|访问实例元数据时是否强制使用加固模式（IMDSv2）。取值范围：

 -   optional：不强制使用。
-   required：强制使用。设置该取值后，普通模式无法访问实例元数据。

 默认值：optional

 **说明：** 有关访问实例元数据的模式，请参见[实例元数据访问模式](~~150575~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Instances|Array of Instance| |由Instances组成的数组格式，返回实例的信息。 |
|Instance| | | |
|AutoReleaseTime|String|2017-12-10T04:04Z|按量付费实例的自动释放时间。 |
|ClusterId|String|c-bp67acfmxazb4p\*\*\*\*|实例所在的集群ID。

 **说明：** 该参数即将被弃用，为提高兼容性，请尽量使用其他参数。 |
|Cpu|Integer|8|vCPU数。 |
|CpuOptions|Struct| |CPU配置详情。 |
|CoreCount|Integer|2|物理CPU核心数。 |
|Numa|String|2|分配的线程数。可能值：2 |
|ThreadsPerCore|Integer|4|CPU线程数。 |
|CreationTime|String|2017-12-10T04:04Z|实例创建时间。 |
|CreditSpecification|String|Standard|修改突发性能实例的运行模式。可能值：

 -   Standard：标准模式，实例性能请参见[什么是突发性能实例](~~59977~~)下的性能约束模式章节。
-   Unlimited：无性能约束模式，实例性能请参见[什么是突发性能实例](~~59977~~)下的无性能约束模式章节。 |
|DedicatedHostAttribute|Struct| |由专有宿主机集群ID（DedicatedHostClusterId）、专有宿主机ID（DedicatedHostId）和名称（DedicatedHostName）组成的宿主机属性数组。 |
|DedicatedHostClusterId|String|dc-bp67acfmxazb4h\*\*\*\*|专有宿主机集群ID。 |
|DedicatedHostId|String|dh-bp67acfmxazb4p\*\*\*\*|专有宿主机ID。 |
|DedicatedHostName|String|testDedicatedHostName|专有宿主机名称。 |
|DedicatedInstanceAttribute|Struct| |专有宿主机实例的属性。 |
|Affinity|String|default|专有宿主机实例是否与专有宿主机关联。可能值：

 -   default：专有宿主机实例不与专有宿主机关联。停机不收费实例重启后，可能会放置在自动资源部署池中的其它专有宿主机上。
-   host：专有宿主机实例与专有宿主机关联。停机不收费实例重启后，仍放置在原专有宿主机上。 |
|Tenancy|String|default|实例的宿主机类型是否为专有宿主机。可能值：

 -   default：实例的宿主机类型不是专有宿主机。
-   host：实例的宿主机类型为专有宿主机。 |
|DeletionProtection|Boolean|false|实例释放保护属性，指定是否支持通过控制台或API（DeleteInstance）释放实例。

 -   true：已开启实例释放保护。
-   false：未开启实例释放保护。

 **说明：** 该属性仅适用于按量付费实例，且只能限制手动释放操作，对系统释放操作不生效。 |
|DeploymentSetGroupNo|Integer|1|ECS实例绑定部署集分散部署时，实例在部署集中的分组位置。 |
|DeploymentSetId|String|ds-bp67acfmxazb4p\*\*\*\*|部署集ID。 |
|Description|String|testDescription|实例描述。 |
|DeviceAvailable|Boolean|true|实例是否可以挂载数据盘。 |
|EcsCapacityReservationAttr|Struct| |云服务器ECS的容量预留相关参数。 |
|CapacityReservationId|String|cr-bp67acfmxazb4p\*\*\*\*|容量预留ID。 |
|CapacityReservationPreference|String|cr-bp67acfmxazb4p\*\*\*\*|容量预留偏好。 |
|EipAddress|Struct| |弹性公网IP绑定信息。 |
|AllocationId|String|i-bp67acfmxazb4p\*\*\*\*|弹性公网IP绑定的实例ID。 |
|Bandwidth|Integer|5|弹性公网IP的公网带宽限速，单位为Mbit/s。 |
|InternetChargeType|String|PayByTraffic|弹性公网IP的计费方式。

 -   PayByBandwidth：按带宽计费。
-   PayByTraffic：按流量计费。 |
|IpAddress|String|42.112.17.\*\*|弹性公网IP。 |
|IsSupportUnassociate|Boolean|true|是否可以解绑弹性公网IP。 |
|ExpiredTime|String|2017-12-10T04:04Z|过期时间。按照[ISO8601](~~25696~~)标准表示，并使用UTC+0时间，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|GPUAmount|Integer|4|实例规格附带的GPU数量。 |
|GPUSpec|String|NVIDIA V100|实例规格附带的GPU类型。 |
|HostName|String|testHostName|实例主机名。 |
|HpcClusterId|String|hpc-bp67acfmxazb4p\*\*\*\*|实例所属的HPC集群ID。 |
|ImageId|String|m-bp67acfmxazb4p\*\*\*\*|实例运行的镜像ID。 |
|InnerIpAddress|List|10.170.\*\*.\*\*|实例的内网IP地址。 |
|InstanceChargeType|String|PostPaid|实例的计费方式。可能值：

 -   PrePaid：包年包月
-   PostPaid：按量付费 |
|InstanceId|String|i-bp67acfmxazb4p\*\*\*\*|实例ID。 |
|InstanceName|String|InstanceNameTest|实例名称。 |
|InstanceNetworkType|String|vpc|实例网络类型。可能值：

 -   classic
-   vpc |
|InstanceType|String|ecs.g5.large|实例规格。 |
|InstanceTypeFamily|String|ecs.g5|实例规格族。 |
|InternetChargeType|String|PayByTraffic|网络计费类型。可能值：

 -   PayByBandwidth：按固定带宽计费。
-   PayByTraffic：按使用流量计费。 |
|InternetMaxBandwidthIn|Integer|50|公网入带宽最大值，单位为Mbit/s。 |
|InternetMaxBandwidthOut|Integer|5|公网出带宽最大值，单位为Mbit/s。 |
|IoOptimized|Boolean|true|是否为I/O优化型实例。 |
|KeyPairName|String|testKeyPairName|密钥对名称。 |
|LocalStorageAmount|Integer|2|实例挂载的本地存储数量。 |
|LocalStorageCapacity|Long|1000|实例挂载的本地存储容量。 |
|Memory|Integer|1024|内存大小，单位MiB。 |
|MetadataOptions|Struct| |元数据选项集合。 |
|HttpEndpoint|String|enabled|是否启用实例元数据的访问通道。可能值：

 -   enabled：启用
-   disabled：禁用 |
|HttpPutResponseHopLimit|Integer|0|该参数暂未上线。 |
|HttpTokens|String|optional|访问实例元数据时是否强制使用加固模式（IMDSv2）。可能值：

 -   optional：不强制使用
-   required：强制使用 |
|NetworkInterfaces|Array of NetworkInterface| |实例包含的弹性网卡集合。 |
|NetworkInterface| | | |
|MacAddress|String|00:16:3e:32:b4:\*\*|弹性网卡的MAC地址。 |
|NetworkInterfaceId|String|eni-2zeh9atclduxvf1z\*\*\*\*|弹性网卡的ID。 |
|PrimaryIpAddress|String|172.17.\*\*.\*\*\*|弹性网卡主私有IP地址。 |
|OSName|String|CentOS 7.4 64 位|实例的操作系统名称。 |
|OSNameEn|String|CentOS 7.4 64 bit|实例操作系统的英文名称。 |
|OSType|String|linux|实例的操作系统类型，分为Windows Server和Linux两种。可能值：

 -   windows
-   linux |
|OperationLocks|Array of LockReason| |实例的锁定原因。 |
|LockReason| | | |
|LockMsg|String|The specified instance is locked due to financial reason.|实例被锁定的描述信息。 |
|LockReason|String|Recycling|锁定类型。可能值：

 -   financial：因欠费被锁定。
-   security：因安全原因被锁定。
-   Recycling：抢占式实例的待释放锁定状态。
-   dedicatedhostfinancial：因为专有宿主机欠费导致ECS实例被锁定。
-   refunded：因退款被锁定。 |
|PublicIpAddress|List|121.40.61.\*\*\*|实例公网IP地址。 |
|RdmaIpAddress|List|10.10.10.102|HPC实例的Rdma网络IP。 |
|Recyclable|Boolean|false|实例是否可以回收。 |
|RegionId|String|cn-hangzhou|实例所属地域ID。 |
|ResourceGroupId|String|rg-bp67acfmxazb4p\*\*\*\*|实例所属的企业资源组ID。 |
|SaleCycle|String|month|实例计费周期。 |
|SecurityGroupIds|List|sg-bp67acfmxazb4p\*\*\*\*|实例所属安全组集合。 |
|SerialNumber|String|51d1353b-22bf-4567-a176-8b3e12e4\*\*\*\*|实例序列号。 |
|SpotDuration|Integer|1|抢占式实例的保留时长，单位为小时。可能值：0~6

 -   保留时长2~6正在邀测中，如需开通请提交工单。
-   值为0，则为无保护期模式。 |
|SpotPriceLimit|Float|0.98|实例的每小时最高价格。支持最大3位小数，参数SpotStrategy=SpotWithPriceLimit时，该参数生效。 |
|SpotStrategy|String|NoSpot|抢占式实例的抢占策略。可能值：

 -   NoSpot：正常按量付费实例。
-   SpotWithPriceLimit：设置上限价格的抢占式实例。
-   SpotAsPriceGo：系统自动出价，最高按量付费价格。 |
|StartTime|String|2017-12-10T04:04Z|实例的竞价模式开始时间。 |
|Status|String|Running|实例状态。 |
|StoppedMode|String|KeepCharging|实例停机后是否继续收费。可能值：

 -   KeepCharging：停机后继续收费，为您继续保留库存资源。
-   StopCharging：停机后不收费。停机后，我们释放实例对应的资源，例如vCPU、内存和公网IP等资源。重启是否成功依赖于当前地域中是否仍有资源库存。
-   Not-applicable：本实例不支持停机不收费功能。 |
|Tags|Array of Tag| |实例的标签集合。 |
|Tag| | | |
|TagKey|String|TestKey|实例的标签键。 |
|TagValue|String|TestValue|实例的标签值。 |
|VlanId|String|10|实例的VLAN ID。

 **说明：** 该参数即将被弃用，为提高兼容性，请尽量使用其他参数。 |
|VpcAttributes|Struct| |专有网络VPC属性。 |
|NatIpAddress|String|172.17.\*\*.\*\*|云产品的IP，用于VPC云产品之间的网络互通。 |
|PrivateIpAddress|List|172.17.\*\*.\*\*|私有IP地址。 |
|VSwitchId|String|vsw-2zeh0r1pabwtg6wcs\*\*\*\*|虚拟交换机ID。 |
|VpcId|String|vpc-2zeuphj08tt7q3brd\*\*\*\*|专有网络VPC ID。 |
|ZoneId|String|cn-hangzhou-g|实例所属可用区。 |
|PageNumber|Integer|1|实例列表的页码。 |
|PageSize|Integer|1|输入时设置的每页行数。 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |
|TotalCount|Integer|58|查询到的实例总数。 |

## 示例

请求示例

```
https://ecs.aliyuncs.com/?Action=DescribeInstances
&RegionId=cn-hangzhou
&PageSize=1
PageNumber=1
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeInstancesResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>58</TotalCount>
      <PageSize>1</PageSize>
      <RequestId>97935DF1-0289-4AA2-9DD1-72377838B16B</RequestId>
      <Instances>
            <Instance>
                  <ImageId>centos_7_06_64_20G_alibase_20190711.vhd</ImageId>
                  <VlanId></VlanId>
                  <EipAddress>
                        <IpAddress></IpAddress>
                        <AllocationId></AllocationId>
                        <InternetChargeType></InternetChargeType>
                  </EipAddress>
                  <ZoneId>cn-hangzhou-f</ZoneId>
                  <IoOptimized>true</IoOptimized>
                  <SerialNumber>51d1353b-22bf-4567-a176-8b3e12e43***</SerialNumber>
                  <Cpu>2</Cpu>
                  <Memory>8192</Memory>
                  <DeviceAvailable>true</DeviceAvailable>
                  <SecurityGroupIds>
                        <SecurityGroupId>sg-bp17zljqpohu6j2i****</SecurityGroupId>
                  </SecurityGroupIds>
                  <SaleCycle></SaleCycle>
                  <AutoReleaseTime></AutoReleaseTime>
                  <ResourceGroupId></ResourceGroupId>
                  <OSType>linux</OSType>
                  <OSName>CentOS  7.6 64位</OSName>
                  <InstanceNetworkType>classic</InstanceNetworkType>
                  <HostName>iZbp1j4i2jdf3owlheb****</HostName>
                  <CreationTime>2019-11-11T08:35Z</CreationTime>
                  <Tags>
                        <Tag>
                              <TagValue>asg-bp1d8uuut40f4qc4****</TagValue>
                              <TagKey>acs:autoscaling:scalingGroupId</TagKey>
                        </Tag>
                        <Tag>
                              <TagValue>ESS</TagValue>
                              <TagKey>ESS</TagKey>
                        </Tag>
                  </Tags>
                  <EcsCapacityReservationAttr>
                        <CapacityReservationPreference>none</CapacityReservationPreference>
                        <CapacityReservationId></CapacityReservationId>
                  </EcsCapacityReservationAttr>
                  <RegionId>cn-hangzhou</RegionId>
                  <DeletionProtection>false</DeletionProtection>
                  <OperationLocks>
            </OperationLocks>
                  <ExpiredTime>2099-12-31T15:59Z</ExpiredTime>
                  <CpuOptions>
                        <Numa></Numa>
                        <ThreadsPerCore>2</ThreadsPerCore>
                        <CoreCount>1</CoreCount>
                  </CpuOptions>
                  <InnerIpAddress>
                        <IpAddress>10.80.**.**</IpAddress>
                  </InnerIpAddress>
                  <InstanceTypeFamily>ecs.mn4</InstanceTypeFamily>
                  <InstanceId>i-bp1j4i2jdf3owlhe****</InstanceId>
                  <InternetMaxBandwidthIn>50</InternetMaxBandwidthIn>
                  <CreditSpecification></CreditSpecification>
                  <InternetChargeType>PayByTraffic</InternetChargeType>
                  <SpotStrategy>NoSpot</SpotStrategy>
                  <StoppedMode>Not-applicable</StoppedMode>
                  <InternetMaxBandwidthOut>1</InternetMaxBandwidthOut>
                  <VpcAttributes>
                        <NatIpAddress></NatIpAddress>
                        <PrivateIpAddress>
                </PrivateIpAddress>
                        <VSwitchId></VSwitchId>
                        <VpcId></VpcId>
                  </VpcAttributes>
                  <SpotPriceLimit>0</SpotPriceLimit>
                  <StartTime>2019-11-11T08:35Z</StartTime>
                  <InstanceName>ECS-asg-MyFirstScalingGroup</InstanceName>
                  <Description>ECS</Description>
                  <OSNameEn>CentOS  7.6 64 bit</OSNameEn>
                  <PublicIpAddress>
                        <IpAddress>121.40.**.**</IpAddress>
                  </PublicIpAddress>
                  <InstanceType>ecs.mn4.large</InstanceType>
                  <Status>Running</Status>
                  <MetadataOptions>
                        <HttpTokens></HttpTokens>
                        <HttpEndpoint></HttpEndpoint>
                  </MetadataOptions>
                  <Recyclable>false</Recyclable>
                  <ClusterId></ClusterId>
                  <GPUSpec></GPUSpec>
                  <InstanceChargeType>PostPaid</InstanceChargeType>
                  <GPUAmount>0</GPUAmount>
                  <DedicatedHostAttribute>
                        <DedicatedHostId></DedicatedHostId>
                        <DedicatedHostName></DedicatedHostName>
                  </DedicatedHostAttribute>
                  <DedicatedInstanceAttribute>
                        <Affinity></Affinity>
                        <Tenancy></Tenancy>
                  </DedicatedInstanceAttribute>
                  <DeploymentSetId></DeploymentSetId>
            </Instance>
      </Instances>
</DescribeInstancesResponse>
```

`JSON` 格式

```
{
	"PageNumber": 1,
	"TotalCount": 58,
	"PageSize": 1,
	"RequestId": "97935DF1-0289-4AA2-9DD1-72377838B16B",
	"Instances": {
		"Instance": [
			{
				"ImageId": "centos_7_06_64_20G_alibase_20190711.vhd",
				"VlanId": "",
				"EipAddress": {
					"IpAddress": "",
					"AllocationId": "",
					"InternetChargeType": ""
				},
				"ZoneId": "cn-hangzhou-f",
				"IoOptimized": true,
				"SerialNumber": "51d1353b-22bf-4567-a176-8b3e12e43***",
				"Cpu": 2,
				"Memory": 8192,
				"DeviceAvailable": true,
				"SecurityGroupIds": {
					"SecurityGroupId": [
						"sg-bp17zljqpohu6j2i****"
					]
				},
				"SaleCycle": "",
				"AutoReleaseTime": "",
				"ResourceGroupId": "",
				"OSType": "linux",
				"OSName": "CentOS  7.6 64位",
				"InstanceNetworkType": "classic",
				"HostName": "iZbp1j4i2jdf3owlheb****",
				"CreationTime": "2019-11-11T08:35Z",
				"Tags": {
					"Tag": [
						{
							"TagValue": "asg-bp1d8uuut40f4qc4****",
							"TagKey": "acs:autoscaling:scalingGroupId"
						},
						{
							"TagValue": "ESS",
							"TagKey": "ESS"
						}
					]
				},
				"EcsCapacityReservationAttr": {
					"CapacityReservationPreference": "none",
					"CapacityReservationId": ""
				},
				"RegionId": "cn-hangzhou",
				"DeletionProtection": false,
				"OperationLocks": {
					"LockReason": []
				},
				"ExpiredTime": "2099-12-31T15:59Z",
				"CpuOptions": {
					"Numa": "",
					"ThreadsPerCore": 2,
					"CoreCount": 1
				},
				"InnerIpAddress": {
					"IpAddress": [
						"10.80.**.**"
					]
				},
				"InstanceTypeFamily": "ecs.mn4",
				"InstanceId": "i-bp1j4i2jdf3owlhe****",
				"InternetMaxBandwidthIn": 50,
				"CreditSpecification": "",
				"InternetChargeType": "PayByTraffic",
				"SpotStrategy": "NoSpot",
				"StoppedMode": "Not-applicable",
				"InternetMaxBandwidthOut": 1,
				"VpcAttributes": {
					"NatIpAddress": "",
					"PrivateIpAddress": {
						"IpAddress": []
					},
					"VSwitchId": "",
					"VpcId": ""
				},
				"SpotPriceLimit": 0,
				"StartTime": "2019-11-11T08:35Z",
				"InstanceName": "ECS-asg-MyFirstScalingGroup",
				"Description": "ECS",
				"OSNameEn": "CentOS  7.6 64 bit",
				"PublicIpAddress": {
					"IpAddress": [
						"121.40.**.**"
					]
				},
				"InstanceType": "ecs.mn4.large",
				"Status": "Running",
                "MetadataOptions": {
					"HttpTokens": "",
					"HttpEndpoint": ""
				},
				"Recyclable": false,
				"ClusterId": "",
				"GPUSpec": "",
				"InstanceChargeType": "PostPaid",
				"GPUAmount": 0,
				"DedicatedHostAttribute": {
					"DedicatedHostId": "",
					"DedicatedHostName": ""
				},
				"DedicatedInstanceAttribute": {
					"Affinity": "",
					"Tenancy": ""
				},
				"DeploymentSetId": ""
			}
		]
	}
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|指定的实例计费方式不存在。|
|404|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid|指定的网络计费方式不合法。|
|404|InvalidLockReason.NotFound|The specified LockReason is not found|指定的锁定类型不存在。|
|404|InvalidFilterKey.NotFound| |指定的起始时间或到期时间参数错误。|
|404|InvalidNetworkType.NotFound|The specified InstanceNetworkType is not found|指定的带宽类型不存在。|
|404|InvalidStatus.NotFound|The specified Status is not found|指定的资源状态不存在。|
|400|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|指定的Tag.N.Key和Tag.N.Value不匹配。|
|400|InvalidTagCount|The specified tags are beyond the permitted range.|指定的标记超出取值范围。|
|400|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found.|指定的参数HpcClusterId不存在。|
|400|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating.|指定的HPC集群正在创建中。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

