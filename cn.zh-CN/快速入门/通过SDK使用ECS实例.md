# 通过SDK使用ECS实例

如果您是一位开发者，可以通过SDK的方式创建ECS实例。本文介绍如何通过Java SDK创建ECS实例。

## 准备Java SDK环境

在使用Java SDK创建ECS实例前，您需要配置好Java SDK环境，并在Maven项目的pom.xml文件中，添加阿里云核心库aliyun-java-sdk-core、云服务器aliyun-java-sdk-ecs、专有网络aliyun-java-sdk-vpc和fastjson依赖。详情请参见[安装Java SDK](/cn.zh-CN/SDK示例/Java示例/安装Java SDK.md)。

在pom.xml文件中新增专有网络aliyun-java-sdk-vpc依赖，如下所示。

```
<dependencies>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>4.4.3</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-ecs</artifactId>
            <version>4.17.1</version>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.60</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-vpc</artifactId>
            <version>3.0.9</version>
        </dependency>
    </dependencies>
```

## 获取AccessKey信息

创建AccessKey，具体请参见[创建AccessKey]()。

**说明：** 为避免主账号泄露AccessKey带来的安全风险，建议您创建RAM用户，授予RAM用户云服务器ECS相关的访问权限，再使用RAM用户的AccessKey调用SDK。详情请参见[账号访问控制](/cn.zh-CN/安全/账号访问控制.md)。

![创建ak](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9396958951/p101727.png)

![创建ak2](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9396958951/p101729.png)

## 创建ECS实例所需资源

在创建ECS实例前，您需要先创建专有网络VPC和安全组。

**说明：** 如果已经存在专有网络VPC和安全组，您也可以获取交换机ID和安全组ID后，直接购买ECS实例。具体请参见[购买ECS实例](#section_nls_s4t_eon)。

1.  创建VPC。

    在**华东1（杭州）**创建专有网络VPC，VPC网段为192.168.0.0/16。

    |API|参数|示例取值|
    |---|--|----|
    |[CreateVpc](/cn.zh-CN/API参考/专有网络（VPC）/CreateVpc.md)|RegionId|地域：cn-hangzhou|
    |CidrBlock|VPC网段：192.168.0.0/16|

    以下代码示例表示创建VPC。

    ```
    import com.aliyuncs.DefaultAcsClient;
    import com.aliyuncs.IAcsClient;
    import com.aliyuncs.exceptions.ClientException;
    import com.aliyuncs.exceptions.ServerException;
    import com.aliyuncs.profile.DefaultProfile;
    import com.google.gson.Gson;
    import com.aliyuncs.vpc.model.v20160428.*;
    
    public class CreateVpc {
    
        public static void main(String[] args) {
            DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou","<accessKeyId>", "<accessSecret>");
            IAcsClient client = new DefaultAcsClient(profile);
    
            CreateVpcRequest request = new CreateVpcRequest();
            request.setRegionId("cn-hangzhou");
            request.setCidrBlock("192.168.0.0/16");
    
            try {
                CreateVpcResponse response = client.getAcsResponse(request);
                System.out.println(new Gson().toJson(response));
            } catch (ServerException e) {
                e.printStackTrace();
            } catch (ClientException e) {
                System.out.println("ErrCode:" + e.getErrCode());
                System.out.println("ErrMsg:" + e.getErrMsg());
                System.out.println("RequestId:" + e.getRequestId());
            }
    
        }
    }
    ```

    返回结果如下所示。

    ```
    {
        "requestId":"5BE6AEA4-347F-46A9-9808-B429EF02****",
        "vpcId":"vpc-bp1h99qfh290thxml****",
        "vRouterId":"vrt-bp1cbum5ozelljyet****",
        "routeTableId":"vtb-bp1qm6p3yoww2cv10****",
        "resourceGroupId":"rg-acfmzw2jz2z****"
    }
    ```

2.  创建交换机。

    在VPC中创建交换机，交换机网段为192.168.0.0/24。

    |API|参数|示例取值|
    |---|--|----|
    |[CreateVSwitch](/cn.zh-CN/API参考/交换机/CreateVSwitch.md)|ZoneId|可用区：cn-hangzhou-i|
    |VpcId|VPC ID：使用步骤[1](#step_il8_ffp_gry)返回的结果。 示例：vpc-bp1h99qfh290thxml\*\*\*\* |
    |CidrBlock|交换机网段：192.168.0.0/24|

    以下代码示例表示创建交换机。

    ```
    import com.aliyuncs.DefaultAcsClient;
    import com.aliyuncs.IAcsClient;
    import com.aliyuncs.exceptions.ClientException;
    import com.aliyuncs.exceptions.ServerException;
    import com.aliyuncs.profile.DefaultProfile;
    import com.google.gson.Gson;
    import java.util.*;
    import com.aliyuncs.vpc.model.v20160428.*;
    
    public class CreateVSwitch {
    
        public static void main(String[] args) {
            DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
            IAcsClient client = new DefaultAcsClient(profile);
    
            CreateVSwitchRequest request = new CreateVSwitchRequest();
            request.setRegionId("cn-hangzhou");
            request.setCidrBlock("192.168.0.0/24");
            request.setVpcId("vpc-bp1h99qfh290thxml****");
            request.setZoneId("cn-hangzhou-i");
    
            try {
                CreateVSwitchResponse response = client.getAcsResponse(request);
                System.out.println(new Gson().toJson(response));
            } catch (ServerException e) {
                e.printStackTrace();
            } catch (ClientException e) {
                System.out.println("ErrCode:" + e.getErrCode());
                System.out.println("ErrMsg:" + e.getErrMsg());
                System.out.println("RequestId:" + e.getRequestId());
            }
    
        }
    }
    ```

    返回结果如下所示。

    ```
    {
        "requestId": "BAFBC8C4-3C65-427B-B470-3D257288****",
        "vSwitchId": "vsw-bp1mihse903i05oxn****"
    }
    ```

3.  创建安全组。

    |API|参数|示例取值|
    |---|--|----|
    |[CreateSecurityGroup](/cn.zh-CN/API参考/安全组/CreateSecurityGroup.md)|RegionId|地域：cn-hangzhou|
    |VpcId|VPC ID：使用步骤[1](#step_il8_ffp_gry)返回的结果。 示例：vpc-bp1h99qfh290thxml\*\*\*\* |

    以下代码示例表示创建安全组。

    ```
    import com.aliyuncs.DefaultAcsClient;
    import com.aliyuncs.IAcsClient;
    import com.aliyuncs.exceptions.ClientException;
    import com.aliyuncs.exceptions.ServerException;
    import com.aliyuncs.profile.DefaultProfile;
    import com.google.gson.Gson;
    import java.util.*;
    import com.aliyuncs.ecs.model.v20140526.*;
    
    public class CreateSecurityGroup {
    
        public static void main(String[] args) {
            DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
            IAcsClient client = new DefaultAcsClient(profile);
    
            CreateSecurityGroupRequest request = new CreateSecurityGroupRequest();
            request.setRegionId("cn-hangzhou");
            request.setVpcId("vpc-bp1h99qfh290thxml****");
    
            try {
                CreateSecurityGroupResponse response = client.getAcsResponse(request);
                System.out.println(new Gson().toJson(response));
            } catch (ServerException e) {
                e.printStackTrace();
            } catch (ClientException e) {
                System.out.println("ErrCode:" + e.getErrCode());
                System.out.println("ErrMsg:" + e.getErrMsg());
                System.out.println("RequestId:" + e.getRequestId());
            }
    
        }
    }
    ```

    返回结果如下所示。

    ```
    {
        "requestId": "718D29C6-6183-4196-AD76-A53F6A6E****",
        "securityGroupId": "sg-bp1dve08xy2c8y9g****"
    }
    ```

4.  在安全组中添加入方向放行规则。

    |API|参数|示例取值|
    |---|--|----|
    |[AuthorizeSecurityGroup](/cn.zh-CN/API参考/安全组/AuthorizeSecurityGroup.md)|RegionId|地域：cn-hangzhou|
    |SecurityGroupId|安全组ID：使用步骤[3](#step_pxb_p7m_rwb)返回的结果。 示例：sg-bp1dve08xy2c8y9g\*\*\*\* |
    |IpProtocol|协议：tcp|
    |SourceCidrIp|源CIDR：0.0.0.0/0|
    |PortRange|端口范围：     -   Linux实例：22/22
    -   Windows实例：3389/3389 |

    以下代码示例表示添加安全组规则。

    ```
    import com.aliyuncs.DefaultAcsClient;
    import com.aliyuncs.IAcsClient;
    import com.aliyuncs.exceptions.ClientException;
    import com.aliyuncs.exceptions.ServerException;
    import com.aliyuncs.profile.DefaultProfile;
    import com.google.gson.Gson;
    import java.util.*;
    import com.aliyuncs.ecs.model.v20140526.*;
    
    public class AuthorizeSecurityGroup {
    
        public static void main(String[] args) {
            DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
            IAcsClient client = new DefaultAcsClient(profile);
    
            AuthorizeSecurityGroupRequest request = new AuthorizeSecurityGroupRequest();
            request.setRegionId("cn-hangzhou");
            request.setSecurityGroupId("sg-bp1dve08xy2c8y9g****");
            request.setIpProtocol("tcp");
            request.setPortRange("22/22");
            request.setSourceCidrIp("0.0.0.0/0");
    
            try {
                AuthorizeSecurityGroupResponse response = client.getAcsResponse(request);
                System.out.println(new Gson().toJson(response));
            } catch (ServerException e) {
                e.printStackTrace();
            } catch (ClientException e) {
                System.out.println("ErrCode:" + e.getErrCode());
                System.out.println("ErrMsg:" + e.getErrMsg());
                System.out.println("RequestId:" + e.getRequestId());
            }
    
        }
    }
    ```

    返回结果如下所示。

    ```
    {
        "requestId": "7052E70F-4678-4400-81CF-E0133CCB****"
    }
    ```


## 购买ECS实例

购买一个包年包月的ECS实例。

|API|参数|示例取值|
|---|--|----|
|[RunInstances](/cn.zh-CN/API参考/实例/RunInstances.md)|RegionId|地域：cn-hangzhou|
|ImageId|镜像：推荐使用Alibaba Cloud Linux镜像aliyun\_2\_1903\_x64\_20G\_alibase\_20200324.vhd。|
|InstanceType|实例规格： -   个人应用：推荐选择1核2G的实例规格ecs.s6-c1m2.small。
-   中小企业应用：推荐选择2核4G的实例规格ecs.c5.large。 |
|SecurityGroupId|安全组ID：使用步骤[3](#step_pxb_p7m_rwb)返回的结果。 示例：sg-bp1dve08xy2c8y9g\*\*\*\* |
|VSwitchId|交换机ID：使用步骤[2](#step_024_7jm_nl1)返回的结果。 示例：vsw-bp1mihse903i05oxn\*\*\*\* |
|InstanceName|实例名称。 示例：ecs\_sdk\_demo |
|InstanceChargeType|付费方式：实例按照包年包月的付费方式PrePaid。 **说明：** 您需要确保账号余额能够完成支付。 |
|PeriodUnit|付费周期单位：Month|
|Period|付费时长：1|
|InternetMaxBandwidthOut|公网IP带宽：1|
|Password|实例登录密码：<yourPassword\>**说明：** 您需要自定义复杂密码以保护ECS实例的安全。 |

以下代码示例表示创建包年包月的ECS实例。

```
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.exceptions.ServerException;
import com.aliyuncs.profile.DefaultProfile;
import com.google.gson.Gson;
import java.util.*;
import com.aliyuncs.ecs.model.v20140526.*;

public class RunInstances {

    public static void main(String[] args) {
        DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);

        RunInstancesRequest request = new RunInstancesRequest();
        request.setRegionId("cn-hangzhou");
        request.setImageId("aliyun_2_1903_x64_20G_alibase_20200324.vhd");
        request.setInstanceType("ecs.s6-c1m2.small");
        request.setSecurityGroupId("sg-bp1dve08xy2c8y9g****");
        request.setVSwitchId("vsw-bp1mihse903i05oxn****");
        request.setInstanceName("ecs_sdk_demo");
        request.setInternetMaxBandwidthOut(1);
        request.setPassword("<yourPassword>");
        request.setPeriod(1);
        request.setPeriodUnit("Month");
        request.setInstanceChargeType("PrePaid");

        try {
            RunInstancesResponse response = client.getAcsResponse(request);
            System.out.println(new Gson().toJson(response));
        } catch (ServerException e) {
            e.printStackTrace();
        } catch (ClientException e) {
            System.out.println("ErrCode:" + e.getErrCode());
            System.out.println("ErrMsg:" + e.getErrMsg());
            System.out.println("RequestId:" + e.getRequestId());
        }

    }
}
```

返回结果如下所示。

```
{
    "requestId": "9582F9F2-349C-438E-A6A2-3E7B6B56****",
    "tradePrice": ****,
    "instanceIdSets": ["i-bp1hcv43i3glqxbv****"]
}
```

## 连接ECS实例

此示例介绍通过Cloud Shell登录Linux实例。如果您安装的是Windows实例，登录方式请参见[在本地客户端上连接Windows实例](/cn.zh-CN/实例/连接实例/连接Windows实例/在本地客户端上连接Windows实例.md)。

1.  查询实例公网IP地址。

    |API|参数|示例取值|
    |---|--|----|
    |[DescribeInstances](/cn.zh-CN/API参考/实例/DescribeInstances.md)|RegionId|地域：cn-hangzhou|
    |InstanceIds|实例ID：使用[购买ECS实例](#section_nls_s4t_eon)返回的结果。 示例：'\["i-bp1hcv43i3glqxbv\*\*\*\*"\]' |

    以下代码示例表示查询实例公网IP。

    ```
    aliyun ecs DescribeInstances \
    --RegionId cn-hangzhou \
    --InstanceIds '["i-bp1hcv43i3glqxbv****"]'
    ```

    在返回结果中找到以下公网IP信息。

    ![公网IP](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9396958951/p100712.png)

2.  通过SSH登录ECS实例。

    ![ssh登录](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0496958951/p100726.png)


## 释放ECS实例

包年包月实例到期后，您可以手动释放。如果一直未续费，实例也会自动释放。

如果您想要提前释放包年包月实例，请参见[退款规则及退款流程](https://help.aliyun.com/document_detail/37096.html)。

