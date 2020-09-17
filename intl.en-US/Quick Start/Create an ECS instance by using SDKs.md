# Create an ECS instance by using SDKs

If you are a developer, you can create an ECS instance by using SDKs. This topic describes how to use SDK for Java to create an ECS instance.

## Prepare the SDK for Java environment

Before you create an instance by using SDK for Java, you must configure the SDK for Java environment and add the aliyun-java-sdk-core, aliyun-java-sdk-ecs, aliyun-java-sdk-vpc, and fastjson dependencies to the pom.xml file in the Maven project. For more information, see [Install ECS SDK for Java](/intl.en-US/SDK Reference/Java example/Install ECS SDK for Java.md).

The following code shows how to add the aliyun-java-sdk-vpc dependency to the pom.xml file:

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

## Obtain AccessKey pair information

For more information about how to create an AccessKey pair, see [Create an AccessKey pair](https://www.alibabacloud.com/help/doc-detail/53045.htm).

**Note:** To protect the AccessKey pair of your Alibaba Cloud account, we recommend that you create a RAM user, grant the RAM user permissions to access ECS instances, and then use the AccessKey pair of the RAM user to call SDK for Java. For more information, see [Implement access control by using RAM](/intl.en-US/Security/Implement access control by using RAM.md).

![Create an AccessKey pair](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9957219951/p101727.png)

![Create an AccessKey pair - 2](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9957219951/p101729.png)

## Resources needed to create an instance

Before you create an instance, you must create a VPC and a security group.

**Note:** If a VPC and a security group already exist, you can purchase an instance after you obtain the VSwitch ID and the security group ID. For more information, see [Purchase an ECS instance](#section_nls_s4t_eon).

1.  Create a VPC.

    Create a VPC in the **China \(Hangzhou\)** region. The CIDR block of the VPC is 192.168.0.0/16.

    |API|Parameter|Example|
    |---|---------|-------|
    |[CreateVpc](/intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md)|RegionId|The ID of the region. Example: cn-hangzhou.|
    |CidrBlock|The CIDR block of the VPC. Example: 192.168.0.0/16|

    The following code shows how to create a VPC:

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

    The following command output is generated:

    ```
    {
        "requestId":"5BE6AEA4-347F-46A9-9808-B429EF02****",
        "vpcId":"vpc-bp1h99qfh290thxml****",
        "vRouterId":"vrt-bp1cbum5ozelljyet****",
        "routeTableId":"vtb-bp1qm6p3yoww2cv10****",
        "resourceGroupId":"rg-acfmzw2jz2z****"
    }
    ```

2.  Creates a VSwitch.

    Create a VSwitch in the VPC. The CIDR block of the VSwitch is 192.168.0.0/24.

    |API|Parameter|Example|
    |---|---------|-------|
    |[CreateVSwitch](/intl.en-US/API reference/VSwitch/CreateVSwitch.md)|ZoneId|The ID of the zone. Example: cn-hangzhou-i.|
    |VpcId|The ID of the VPC, which is the parameter value returned in the [1](#step_il8_ffp_gry) section. Example: vpc-bp1h99qfh290thxml\*\*\*\*. |
    |CidrBlock|The CIDR block of the VSwitch. Example: 192.168.0.0/24.|

    The following code shows how to create a VSwitch:

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

    The following command output is generated:

    ```
    {
        "requestId": "BAFBC8C4-3C65-427B-B470-3D257288****",
        "vSwitchId": "vsw-bp1mihse903i05oxn****"
    }
    ```

3.  Create a security group.

    |API|Parameter|Example|
    |---|---------|-------|
    |[CreateSecurityGroup](/intl.en-US/API Reference/Security groups/CreateSecurityGroup.md)|RegionId|The ID of the region. Example: cn-hangzhou.|
    |VpcId|The ID of the VPC, which is the parameter value returned in the [1](#step_il8_ffp_gry) section. Example: vpc-bp1h99qfh290thxml\*\*\*\*. |

    The following code shows how to create a security group:

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

    The following command output is generated:

    ```
    {
        "requestId": "718D29C6-6183-4196-AD76-A53F6A6E****",
        "securityGroupId": "sg-bp1dve08xy2c8y9g****"
    }
    ```

4.  Add an inbound rule to the security group.

    |API|Parameter|Example|
    |---|---------|-------|
    |[AuthorizeSecurityGroup](/intl.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md)|RegionId|The ID of the region. Example: cn-hangzhou.|
    |SecurityGroupId|The ID of the security group, which is the parameter value returned in the [3](#step_pxb_p7m_rwb) section. Example: sg-bp1dve08xy2c8y9g\*\*\*\*. |
    |IpProtocol|The Internet protocol. Example: tcp.|
    |SourceCidrIp|The source CIDR block. Example: 0.0.0.0/0.|
    |PortRange|The port range:     -   Linux instances: 22/22
    -   Windows instances: 3389/3389 |

    The following code shows how to add an inbound rule to the security group:

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

    The following command output is generated:

    ```
    {
        "requestId": "7052E70F-4678-4400-81CF-E0133CCB****"
    }
    ```


## Purchase an ECS instance

Purchase a subscription ECS instance.

|API|Parameter|Example|
|---|---------|-------|
|[RunInstances](/intl.en-US/API Reference/Instances/RunInstances.md)|RegionId|The ID of the region. Example: cn-hangzhou.|
|ImageId|The ID of the image. The aliyun\_2\_1903\_x64\_20G\_alibase\_20200324.vhd Alibaba Cloud Linux image is recommended.|
|InstanceType|The instance family. -   Individual applications: The ecs.s6-c1m2.small instance type with 1 vCPU and 2 GiB memory is recommended.
-   Applications for small and medium-sized enterprises: The ecs.c5.large instance type with 2 vCPUs and 4 GiB memory is recommended. |
|SecurityGroupId|The ID of the security group, which is the parameter value returned in the [3](#step_pxb_p7m_rwb) section. Example: sg-bp1dve08xy2c8y9g\*\*\*\*. |
|VSwitchId|The ID of the VSwitch, which is the parameter value returned in the [2](#step_024_7jm_nl1) section. Example: vsw-bp1mihse903i05oxn\*\*\*\*. |
|InstanceName|The name of the instance. Example: ecs\_sdk\_demo. |
|InstanceChargeType|The billing method of the instance. For a subscription instance, the corresponding value is PrePaid. **Note:** You must make sure that you have sufficient account balance. |
|PeriodUnit|The unit of the billing cycle. Example: Month.|
|Period|The period of the billing cycle. Example: 1.|
|InternetMaxBandwidthOut|The maximum outbound bandwidth to the Internet. Example: 1.|
|Password|The logon password of the instance: <yourPassword\>. **Note:** You must customize a complex password to ensure instance security. |

The following code shows how to create a subscription instance:

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

The following command output is generated:

```
{
    "requestId": "9582F9F2-349C-438E-A6A2-3E7B6B56****",
    "tradePrice": ****,
    "instanceIdSets": ["i-bp1hcv43i3glqxbv****"]
}
```

## Connect to the ECS instance

This section describes how to log on to a Linux instance by using Cloud Shell. For information about how to log on to a Window instance, see [Connect to a Windows instance from a local client](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance from a local client.md).

1.  Query the public IP address of the instance.

    |API|Parameter|Example|
    |---|---------|-------|
    |[DescribeInstances](/intl.en-US/API Reference/Instances/DescribeInstances.md)|RegionId|The ID of the region. Example: cn-hangzhou.|
    |InstanceIds|The ID of the instance, which is the parameter value returned in the [Purchase an ECS instance](#section_nls_s4t_eon) section. Example: '\["i-bp1hcv43i3glqxbv\*\*\*\*"\]'. |

    The following code shows how to query the public IP address of the instance:

    ```
    aliyun ecs DescribeInstances \
    --RegionId cn-hangzhou \
    --InstanceIds '["i-bp1hcv43i3glqxbv****"]'
    ```

    The following command output is generated.

    ![Public IP address](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9957219951/p100712.png)

2.  Use an SSH key pair to log on to the instance.

    ![Logon with SSH key pair](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/0067219951/p100726.png)


## Release an expired instance

You can manually release a subscription instance after it expires. If you do not renew the instance after it expires, the instance is automatically released.

