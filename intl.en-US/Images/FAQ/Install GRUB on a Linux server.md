---
keyword: [install GRUB, upgrade the kernel version, early kernel version, upgrade GRUB to v2.02, SMC]
---

# Install GRUB on a Linux server

To use Server Migration Center \(SMC\) to migrate a Linux server to Alibaba Cloud, if the system boot program GRand Unified Bootloader \(GRUB\) is not installed on the server, you must install GRUB v2.02 or later. If the server runs an early Linux distribution such as CentOS 5 or Debian 7, if the GRUB version is earlier than 2.02, or if the "Do Grub Failed" error message is displayed in the log file, you must upgrade GRUB to v2.02 or later.

This topic describes how to install GRUB on a Linux server. GRUB v2.02 is used in the example. The procedure to install GRUB of other versions is similar. The source code package may vary with GRUB versions. For more information, visit [Index of /gnu/grub](https://alpha.gnu.org/gnu/grub/).

1.  Log on to the Linux server.

2.  Run the following commands to check the paths of the grub, grub-install, and grub-mkconfig files of the current GRUB version:

    ```
    which grub
    ```

    ```
    which grub-install
    ```

    ```
    which grub-mkconfig
    ```

    -   If the outputs of preceding commands indicate that one or more of these paths do not exist, GRUB is not installed on the server or the corresponding files are missing. You must perform operations described in the following section to install GRUB.
    -   If you can view the paths of all the files, run the following commands to back up the grub, grub-install, and grub-mkconfig files by renaming them. When you install a new GRUB version, the new version overwrites the current version.

        ```
        mv /sbin/grub /sbin/grub-old
        ```

        ```
        mv /sbin/grub-install /sbin/grub-install-old
        ```

        ```
        mv /sbin/grub-mkconfig /sbin/grub-mkconfig-old
        ```

        **Note:** After you use SMC to migrate the server, you can restore the files by changing their names back to the original ones.

3.  Install the GRUB dependencies including bison, gcc, and make.

    ```
    yum install -y bison gcc make
    ```

4.  Perform the following operations to install flex:

    1.  Check whether the tools folder exists. If the folder does not exist, create it.

        ```
        test -d /root/tools || mkdir -p /root/tools
        ```

    2.  Go to the tools folder and download the flex installation package.

        ```
        cd /root/tools
        wget https://github.com/westes/flex/releases/download/v2.6.4/flex-2.6.4.tar.gz
        ```

    3.  Decompress the flex installation package.

        ```
        tar xzf flex-2.6.4.tar.gz
        ```

    4.  Go to the directory to which the flex installation package is decompressed, and create a folder named build.

        ```
        cd flex-2.6.4
        mkdir -p build
        ```

    5.  Go to the build folder, and compile and install flex.

        ```
        cd build
        ../configure
        ```

        ```
        make && make install
        ```

    6.  Create the symbolic link.

        ```
        ln -s /usr/local/bin/flex /usr/bin/flex
        ```

5.  Perform the following operations to install GRUB.

    You must use GRUB v2.02 or later for earlier distributions of operating systems such as CentOS 5, Red Hat Enterprise Linux 5, Debian 7, Amazon Linux, and Oracle Linux.

    1.  Check whether the tools folder exists. If the folder does not exist, create it.

        ```
        test -d /root/tools || mkdir -p /root/tools
        ```

    2.  Go to the tools folder and download the GRUB v2.02 installation package.

        ```
        cd /root/tools
        wget https://alpha.gnu.org/gnu/grub/grub-2.02~rc1.tar.gz
        ```

    3.  Decompress the GRUB v2.02 installation package.

        ```
        tar xzf grub-2.02~rc1.tar.gz
        ```

    4.  Go to the directory to which the GRUB v2.02 installation package is decompressed, and create a folder named build.

        ```
        cd grub-2.02~rc1
        mkdir -p build
        ```

    5.  Go to the build folder, and compile and install GRUB.

        ```
        cd build
        ../configure
        ```

        ```
        sed -i -e "s/-Werror//" ./grub-core/Makefile
        sed -i -e "s/-Werror//" . /Makefile
        make && make install
        ```

    6.  Create the symbolic links.

        ```
        ln -s /usr/local/sbin/grub-install /sbin/grub-install
        ln -s /usr/local/sbin/grub-mkconfig /sbin/grub-mkconfig
        ```

    **Note:** If the `-Werror` error is reported during compilation, find the makefile compile file, remove the `-Werror` option from the file, and then try again.

6.  Run the following command to check whether GRUB v2.02 is installed or GRUB is upgraded to v2.02:

    ```
    grub-install --version
    ```


-   If GRUB v2.02 is installed or GRUB is upgraded to v2.02, you can use SMC to migrate the server to Alibaba Cloud. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md).
-   Optional. After the sever is migrated, if you want to use the previous version of GRUB, run the following commands to restore GRUB to its previous version:

    ```
    rm /sbin/grub-install
    rm /sbin/grub-mkconfig
    rm /boot/grub/grub.cfg
    mv /sbin/grub-old /sbin/grub
    mv /sbin/grub-install-old /sbin/grub-install
    ```


