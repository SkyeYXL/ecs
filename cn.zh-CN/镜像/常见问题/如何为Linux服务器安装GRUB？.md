---
keyword: [安装GRUB, 升级内核版本, 内核版本低, 升级GRUB至2.02]
---

# 如何为Linux服务器安装GRUB？

通过服务器迁移中心迁移Linux源服务器时，若Linux源服务器的内核版本较低（如CentOS 5和Debian 7）、自带的系统引导程序GRUB（ GRand Unified Bootloader）版本低于2.02，日志文件提示Do Grub Failed时，您需要将GRUB升级至2.02及以上版本。

本文以GRUB 2.02版本为例，介绍在Linux服务器上安装系统引导程序GRUB的操作步骤。安装其他版本的操作步骤与此相同，主要差异在于安装过程中需下载相应版本的GRUB源码包。具体操作，请参见[下载相应版本的GRUB源码包](https://alpha.gnu.org/gnu/grub/)。

1.  登录Linux源服务器。

2.  依次运行以下命令查看原grub、grub-install以及grub-mkconfig的路径。

    **说明：** 如果提示路径不存在，则忽略该步骤。

    ```
    which grub
    ```

    ```
    which grub-install
    ```

    ```
    which grub-mkconfig
    ```

3.  运行`mv`命令为旧版本grub、grub-install以及grub-mkconfig改名以备份文件。

    **说明：** 如果提示文件不存在，则忽略该步骤。

    您可以在使用迁云工具迁移服务器后，恢复原名以使用原配置。

    ```
    mv /sbin/grub /sbin/grub-old
    ```

    ```
    mv /sbin/grub-install /sbin/grub-install-old
    ```

    ```
    mv /sbin/grub-mkconfig /sbin/grub-mkconfig-old
    ```

4.  安装GRUB依赖的bison、gcc以及make工具。

    ```
    yum install -y bison gcc make
    ```

5.  依次运行以下命令安装flex。

    1.  判断是否存在文件夹tools，如果不存在则创建。

        ```
        test -d /root/tools || mkdir -p /root/tools
        ```

    2.  进入tools文件夹，并下载flex安装包。

        ```
        cd /root/tools
        wget https://github.com/westes/flex/releases/download/v2.6.4/flex-2.6.4.tar.gz
        ```

    3.  解压flex安装包。

        ```
        tar xzf flex-2.6.4.tar.gz
        ```

    4.  进入安装包并创建build文件夹。

        ```
        cd flex-2.6.4
        mkdir -p build
        ```

    5.  进入build文件夹，编译安装flex。

        ```
        cd build
        ../configure
        ```

        ```
        make && make install
        ```

    6.  创建软连接。

        ```
        ln -s /usr/local/bin/flex /usr/bin/flex
        ```

6.  依次运行以下命令安装GRUB依赖。

    CentOS 5、Red Hat Enterprise Linux 5、Debian 7、Amazon Linux或Oracle Linux等低版本操作系统，更新至2.02及以上版本。

    1.  判断是否存在文件夹tools，如果不存在则创建。

        ```
        test -d /root/tools || mkdir -p /root/tools
        ```

    2.  进入tools文件夹，并下载GRUB依赖包。

        ```
        cd /root/tools
        wget https://alpha.gnu.org/gnu/grub/grub-2.02~rc1.tar.gz
        ```

    3.  解压GRUB依赖包。

        ```
        tar xzf grub-2.02~rc1.tar.gz
        ```

    4.  进入安装包并创建build文件夹。

        ```
        cd grub-2.02~rc1
        mkdir -p build
        ```

    5.  进入build文件夹，编译安装GRUB。

        ```
        cd build
        ../configure
        ```

        ```
        sed -i -e "s/-Werror//" ./grub-core/Makefile
        sed -i -e "s/-Werror//" ./Makefile
        make && make install
        ```

    6.  创建软连接。

        ```
        ln -s /usr/local/sbin/grub-install /sbin/grub-install
        ln -s /usr/local/sbin/grub-mkconfig /sbin/grub-mkconfig
        ```

    **说明：** 若编译过程中出现了`-Werror`报错，您可以定位到编译对象的编译文件makefile中，去掉`-Werror`选项重新编译。

7.  运行`grub-install --version`命令，检查GRUB版本是否更新。


-   成功更新系统引导程序GRUB后，您可以使用迁云工具迁移服务器至阿里云。具体操作，请参见 *服务器迁移中心文档*[迁移流程概述](/cn.zh-CN/用户指南/迁移流程概述.md)。
-   （可选）迁云成功后，运行以下命令将GRUB恢复为旧版本。

    ```
    rm /sbin/grub-install
    rm /sbin/grub-mkconfig
    rm /boot/grub/grub.cfg
    mv /sbin/grub-old /sbin/grub
    mv /sbin/grub-install-old /sbin/grub-install
    ```


