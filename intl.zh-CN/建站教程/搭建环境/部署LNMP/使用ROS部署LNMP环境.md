# 使用ROS部署LNMP环境

LNMP分别代表Linux、Nginx、MySQL和PHP。本文介绍如何使用阿里云资源编排服务（ROS）一键部署LNMP环境。

-   已注册阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。
-   如果您是首次使用ROS，必须先开通ROS服务。ROS服务免费，开通服务不会产生任何费用。

ROS是阿里云官网提供的免费服务，无需下载安装。您可以使用ROS创建JSON格式的资源栈模板文件，或者使用ROS控制台提供的模板示例创建一组阿里云资源，详情请参见[模板示例](https://ros.console.aliyun.com/#/template/list)。

您还可以使用ROS提供的模板示例搭建环境。例如：Java Web测试环境、Node.js测试开发环境、Ruby Web开发测试环境或Hadoop/Spark分布式系统。本教程以ROS控制台提供的**部署LNMP\(Linux+Nginx+MySQL+PHP\)环境**模板为例，使用ROS自动创建一台ECS实例并在该实例上部署LNMP环境。

更多ROS信息，请参见[ROS文档](/intl.zh-CN/产品简介/什么是资源编排服务.md)。

1.  登录[ROS管理控制台](https://ros.console.aliyun.com/)。

2.  在左侧导航栏中，单击**模板** \> **模板示例**。

3.  在顶部菜单栏左上角处，选择地域。

4.  从模板示例中，找到**部署LNMP\(Linux+Nginx+MySQL+PHP\)环境**。

    ![查找模板](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7802649951/p12071.png)

5.  单击**查看详情**查看模板的JSON文件。JSON文件各个顶级字段的解释如下表所示。

    |顶级字段|解释|
    |:---|:-|
    |`"ROSTemplateFormatVersion" : "2015-09-01"`|定义模板版本。|
    |    ```
"Description": "Deploy LNMP(Linux+Nginx+MySQL+PHP) stack on 1 ECS instance. ***
              WARNING *** Only support CentOS-7."
    ```

|解释说明模板。|
    |`"Parameters" : { }`|定义模板的一些参数。本示例中，模板定义的参数包括：镜像ID、实例规格等，并指定了默认值。|
    |`"Resources" : { }`|定义这个模板将要创建的阿里云资源。本示例中，申明将要创建一个ECS实例和一个安全组，这里申明的资源属性可以引用`Parameters`中定义的参数。|
    |`"Outputs": { }`|定义资源创建完成后，栈需要输出的资源信息。本示例中，资源创建完成后将输出ECS实例ID、公网IP地址和安全组ID。|

6.  单击**创建资源栈**。

7.  设置相关参数，然后单击**创建资源栈**。

    |参数名称|描述|
    |----|--|
    |**资源栈名称**|设置一个栈名，不可重复，而且创建之后不能修改。|
    |**Available Zone ID**|（必填）填写您需要创建资源的可用区ID。|
    |**Image ID**|填写创建ECS实例时使用的镜像ID。|
    |**Instance Type**|填写您需要的ECS实例规格。|
    |**System Disk Category**|选择系统盘的云盘类型。|
    |**Instance Password**|（必填）设置ECS实例的登录密码。根据模板定义，密码必须包含大写字母、小写字母、数字、特殊符号中的三个。|
    |**DB Name**|填写MySQL数据库名。|
    |**DB Username**|填写MySQL数据库的用户名。|
    |**DB Password**|（必填）设置访问MySQL数据库的密码。根据模板定义，密码由字母、数字、下划线（\_）组成，长度为6~32个字符。|
    |**DB Root Password**|（必填）设置MySQL root账号的密码。根据模板定义，密码由字母、数字、下划线（\_）组成，长度为6~32个字符。|
    |**Nginx Download Url**|使用默认的Nginx下载地址。|

8.  在左侧导航栏中，单击**资源栈**查看新建资源栈的状态。

    ![资源栈管理](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7802649951/p14331.png)

9.  单击新建资源栈的名称，然后单击**输出**页签，查看`NginxWebsiteURL`的值。

    您可以通过这个地址访问已创建的LNMP环境。

    ![查看栈概况](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7802649951/p14341.png)

    **说明：**

    -   在**资源**页签，查看栈中所有资源。
    -   在**事件**页签，查看ROS创建这个资源栈过程中产生的操作记录。任何涉及资源栈的操作失败后，列表中均会显示操作失败的原因。

