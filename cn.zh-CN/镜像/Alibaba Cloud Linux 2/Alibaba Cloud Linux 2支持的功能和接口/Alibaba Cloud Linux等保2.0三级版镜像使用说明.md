# Alibaba Cloud Linux等保2.0三级版镜像使用说明

本文介绍Alibaba Cloud Linux等保2.0三级版镜像及镜像的使用说明。

阿里云根据国家信息安全部发布的*GB/T22239-2019信息安全技术网络安全等级保护基本要求*中对操作系统提出的一些等级保护要求，推出自研云原生操作系统Alibaba Cloud Linux等保2.0三级版镜像。您使用本镜像无需额外配置即可满足以下等保合规要求：

-   身份鉴别
-   访问控制
-   安全审计
-   入侵防范
-   恶意代码防范

## 使用Alibaba Cloud Linux等保2.0三级版镜像

1.  创建ECS实例，并选择Alibaba Cloud Linux等保2.0三级版镜像。

    创建ECS实例的具体操作步骤请参见[使用向导创建实例](/cn.zh-CN/实例/创建实例/使用向导创建实例.md)。创建过程中需注意以下配置项：

    -   在**镜像**区域选择`Alibaba Cloud Linux 2.1903 LTS 64位 等保2.0三级版`镜像。

        ![dengbao image](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7246462061/p172961.png)

    -   由于等保合规的要求，等保镜像不支持使用密钥对的方式创建和远程连接ECS实例，只支持用户名密码的方式。因此**登录凭证**请选择**自定义密码**。
2.  远程连接ECS实例，并手动进行等级保护加固的配置。

    按照*GB/T22239-2019信息安全技术网络安全等级保护基本要求*，同时也为了不影响用户正常登录和使用，部分配置需要用户手动执行命令进行配置。用户可以通过用户名密码方式远程连接ECS实例后，执行`/root/cybersecurity.sh`脚本来实现等级保护的加固。

    1.  远程连接ECS实例。

        详情请参见[使用用户名密码验证连接Linux实例](/cn.zh-CN/实例/连接实例/连接Linux实例/使用用户名密码验证连接Linux实例.md)。

        成功登录ECS实例后可以看到以下说明：

        ![dengbao login](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7999382061/p174312.png)

    2.  执行脚本，完成镜像加固。

        执行脚本后，需要根据系统提示依次创建普通用户、审计员和安全员账户三个用户。

        1.  执行脚本。

            ```
            sh cybersecurity.sh
            ```

        2.  输入普通用户`admin`，并设置密码。
        3.  输入审计员用户`audit`，并设置密码。
        4.  输入安全员用户`security`，并设置密码。
        脚本执行的内容示例如下：

        ![dengbao site](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7999382061/p174315.png)

3.  使用系统。

    等级保护加固的配置，限制了root用户直接登录。您需要使用已创建的普通用户、审计员或安全员账户登录系统，然后切换至root用户使用系统。本步骤使用普通用户作为示例，介绍如何登录系统并切换用户。

    1.  使用普通用户`admin`远程连接ECS实例。

    2.  切换至root用户。

        ```
        su root
        ```

        输入root用户的密码即可成功切换用户。

    切换操作的示例如下图：

    ![result](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7246462061/p172992.png)


