# 手动搭建Drupal网站

本文介绍如何在CentOS 7操作系统的ECS实例上搭建Drupal电子商务网站。

-   已注册阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。
-   已创建了分配公网IP的ECS实例，并部署了LAMP环境，具体操作请参见[部署LAMP环境](/intl.zh-CN/建站教程/搭建环境/部署LAMP环境.md)。

Drupal是使用PHP语言编写的开源内容管理框架（CMF），它由内容管理系统（CMS）和PHP开发框架（Framework）共同构成。它用于构造提供多种功能和服务的动态网站，能支持从个人博客到大型社区等各种不同应用的网站项目。

本教程适用于熟悉Linux系统，刚开始使用阿里云进行建站的用户。您也可以通过云市场提供的镜像快速搭建Drupal网站，详情请参见 [云市场镜像搭建Drupal网站](/intl.zh-CN/建站教程/搭建网站/搭建Drupal网站/云市场镜像搭建Drupal网站.md)。

## 配置信息

本教程示例步骤中使用的实例配置与软件版本如下。实际操作时，请以您的配置信息为准。

-   实例规格：ecs.c6.large
-   操作系统：CentOS 7.8 64位
-   Apache：2.4.6
-   MySQL：5.7.31
-   PHP：7.0.33
-   Drupal：8.1.1

## 配置数据库信息

1.  通过本地浏览器访问http://实例公网IP/phpMyAdmin。

2.  使用MySQL的用户名和密码，登录phpMyAdmin。

3.  在页面顶部单击**SQL**。

4.  为Drupal创建数据库和用户。

    在编辑框中输入以下SQL语句：

    ```
    CREATE DATABASE <DrupalDBName>;
    CREATE user '<UserName>'@'<IP>' IDENTIFIED BY '<UserPassWord>';
    FLUSH PRIVILEGES;
    ```

    根据您的需求设置SQL语句中的参数：

    -   `<DrupalDBName>`：数据库名称
    -   `<UserName>`：数据库用户
    -   `<IP>`：本机可直接使用localhost或者127.0.0.1
    -   `<UserPassWord>`：数据库密码

        **说明：** 数据库的密码强度规则可以通过SQL语句`show variables like 'validate_password%';`查询。

5.  单击**执行**。


## 安装Drupal

1.  远程连已经部署了LAMP环境的ECS实例。

    远程连接的方式请参见[通过VNC远程连接登录Linux实例](/intl.zh-CN/实例/连接实例/连接Linux实例/通过VNC远程连接登录Linux实例.md)。

2.  下载并配置Drupal。

    1.  下载Drupal安装包。

        ```
        cd
        wget http://ftp.drupal.org/files/projects/drupal-8.1.1.zip
        ```

    2.  解压Drupal安装包，并将安装文件移动到Apache的网站根目录。

        ```
        yum install unzip -y
        unzip drupal-8.1.1.zip 
        ```

        ```
        mv drupal-8.1.1/* /var/www/html
        ```

    3.  修改sites目录属主属组。

        ```
        chown -R daemon:daemon /var/www/html/sites
        ```

    4.  重启Apache服务。

        ```
        systemctl restart httpd
        ```

3.  通过浏览器访问网站并安装Drupal。

    1.  通过本地浏览器访问<ECS实例公网IP地址\> ，进入到Drupal安装界面。选择安装语言，单击**Save and continue**。

        ![选择安装语言](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8212649951/p12509.png)

    2.  选择标准安装方式，单击**保存并继续**。

    3.  填写已配置完成的数据库信息，单击**保存并继续**。

    4.  自动安装完成后进入网站设置界面，填写站点信息，单击**保存并继续**。


安装完成，后续可以根据您的需求对网站进行个性化设置。

