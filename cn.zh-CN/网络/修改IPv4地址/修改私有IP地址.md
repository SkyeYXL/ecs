---
keyword: 私有IP地址
---

# 修改私有IP地址

您可以直接修改专有网络中ECS实例的私有IP，也可以通过更改ECS实例所属的交换机来更改ECS实例的私有IP。

实例的弹性网卡未设置辅助私网IP地址。

1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。

2.  在左侧导航栏，单击**实例与镜像** \> **实例**。

3.  在顶部菜单栏左上角处，选择地域。

4.  在目标实例的**操作**列中，单击**更多** \> **实例状态** \> **停止**。

5.  实例停止运行后，单击目标实例的ID。

6.  在**配置信息**区域，单击**更多** \> **修改私有IP**。

7.  在修改私有IP对话框，完成配置，然后单击**修改**。

    -   如果您要更换交换机，请确保所选交换机的可用区和实例的可用区相同。
    -   如果您不需要更换交换机，则直接修改私有IP即可。
    ![修改私网IP](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2876649951/p5483.png)

8.  返回到实例列表页面，在**操作**列中，单击**更多** \> **实例状态** \> **启动**。

    **说明：** ECS实例重新启动后，修改的私有IP生效。

    以下示例演示了如何修改私有IP地址。

    ![修改私有IP地址](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2876649951/p127664.gif)


**相关文档**  


[ModifyInstanceVpcAttribute](/cn.zh-CN/API参考/网络/ModifyInstanceVpcAttribute.md)

