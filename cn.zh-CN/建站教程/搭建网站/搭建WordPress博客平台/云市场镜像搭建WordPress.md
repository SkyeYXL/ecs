# 云市场镜像搭建WordPress

WordPress是使用PHP语言开发的博客平台，在支持PHP和MySQL数据库的服务器上，您可以用WordPress架设自己的网站，也可以用作内容管理系统（CMS）。本文介绍如何使用云市场的WordPress镜像搭建WordPress网站。

-   已注册阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。
-   已创建网络类型为专有网络的安全组，并且安全组的入方向添加规则并放行80端口及8100端口，如果您使用SSH远程连接Linux实例，需要放行22端口。 具体操作请参见[添加安全组规则](/cn.zh-CN/安全/安全组/添加安全组规则.md)。

    |协议类型|端口范围|优先级|授权类型|授权对象|用途|
    |----|----|---|----|----|--|
    |自定义TCP|80/80|1|IPv4地址段访问|本示例中，设为0.0.0.0/0，表示允许所有IP地址的访问。建议您在实际场景中填写具体的IP地址或CIDR网段更安全。|访问web的默认端口号。|
    |自定义TCP|8100/8100|1|IPv4地址段访问|本示例中，设为0.0.0.0/0，表示允许所有IP地址的访问。建议您在实际场景中填写具体的IP地址或CIDR网段更安全。|用于访问MySQL数据库管理工具phpMyAdmin。|
    |自定义TCP|22/22|1|IPv4地址段访问|本示例中，设为0.0.0.0/0，表示允许所有IP地址的访问。建议您在实际场景中填写具体的IP地址或CIDR网段更安全。|用于SSH远程连接Linux实例。|


阿里云云市场提供WordPress镜像，用于快捷搭建WordPress网站，不需要部署Web环境，降低了建站的门槛，适用于刚开始使用阿里云ECS建站的企业或个人用户。本示例中使用的镜像基础环境如下。

-   操作系统版本：CentOS 7.4
-   Nginx版本：1.14
-   PHP版本：7.0
-   MySQL版本：5.7.22

    该镜像提供的MySQL账号信息如下。

    -   用户名：root
    -   密码：mysql57@onesul.com

## 搭建WordPress网站

1.  通过云市场购买免费版WordPress镜像。

    1.  单击[wordpress博客系统](https://market.aliyun.com/products/53398003/cmjj029781.html)进入镜像详情页。

    2.  单击**立即购买**，按提示步骤根据您的实际业务需求购买ECS实例。

        **说明：**

        -   如果要备案，您购买的ECS实例需包月3个月及以上（包含续费），且有公网带宽。备案限制条件请参见[限制说明]()。
        -   勾选分配公网IPv4地址，并选择已创建的安全组。
    3.  创建成功后，获取实例的公网IP地址。

2.  安装WordPress。

    1.  在浏览器地址栏中输入`http://实例公网IP`，屏幕上会显示提示页面。

    2.  选择语言（本示例中，选择简体中文），单击**继续**，然后单击**现在就开始！**。

    3.  填写镜像提供的数据库连接信息。

        默认参数如下：

        -   用户名：root
        -   密码：mysql57@onesul.com
        ![wp1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9112649951/p102141.png)

    4.  单击**提交**，然后单击**现在安装**。

    5.  根据您的业务需求填写基本信息，这些信息以后可以再次修改。填写完成后单击**安装WordPress**。

        填写信息参数说明：

        -   站点标题：WordPress网站的名称。例如：demowp。
        -   用户名：用户登录WordPress时使用的用户名，请注意安全性。例如：testwp。
        -   密码：建议用户设置安全性高的密码。例如：Wp.123456。
        -   您的电子邮件：用于接收通知的电子邮件。例如：1234567890@aliyun.com。
    6.  单击**登录**。

    7.  使用您设置的用户名和密码登录WordPress网站。

        出现如下界面，表示成功搭建WordPress网站。

        ![1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9112649951/p76546.png)


## WordPress网站域名解析

为WordPress网站设置一个单独的域名，以方便您的用户对WordPress网站的访问。您也可以通过实例公网IP直接访问您的WordPress网站，但不推荐您这样操作。如果您已有域名或者想为WordPress网站注册一个域名，可以参考以下步骤。本示例注册域名为`www.WordPress.EcsQuickStart.com`。

1.  注册域名。详情请参见[注册通用域名](/cn.zh-CN/域名注册/注册通用域名.md)。

2.  备案。如果您的域名指向的网站托管在阿里云中国内地节点服务器，您需要进行备案。如果您是首次备案，请参见[首次备案流程]()，其他情况请参见[ICP备案流程概述]()。

3.  解析域名。将域名指向实例公网IP。

    域名解析是使用域名访问您的网站的必备环节。具体操作流程，请参见[设置域名解析](http://help.aliyun.com/document_detail/29716.html)。

4.  域名解析完成后，使用浏览器访问`http://实例公网IP:8100`。

    进入MySQL数据库管理工具phpMyAdmin的登录页面。

    ![wp2](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9112649951/p102142.png)

5.  使用镜像提供的数据库用户名和密码，登录MySQL数据库管理工具phpMyAdmin。

6.  选择WordPress网站的数据库wordpress，单击**SQL**，并执行如下SQL语句。

    **说明：** SQL语句中使用`replace`方法，将数据库表中实例公网IP替换为您的域名。

    ```
    /*修改站点url和主页地址*/
    UPDATE wp_options SET option_value = replace(option_value, 'http://实例公网IP', 'http://www.WordPress.EcsQuickStart.com') WHERE option_name = 'home' OR option_name = 'siteurl'; 
    ```

    ![1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9112649951/p76539.png)

7.  单击**执行**，成功为WordPress网站设置域名。


