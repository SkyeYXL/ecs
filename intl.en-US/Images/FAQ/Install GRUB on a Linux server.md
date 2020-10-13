---
keyword: [install GRUB, upgrade the kernel version, early kernel version, upgrade GRUB to version 2.02]
---

# Install GRUB on a Linux server

To migrate a Linux server to Alibaba Cloud by using Server Migration Center \(SMC\), you must upgrade the system boot program GRand Unified Bootloader \(GRUB\) of the server to version 2.02 or later if the following conditions are met: The server runs an early Linux distribution such as CentOS 5 or Debian 7, the GRUB version is earlier than 2.02, and the "Do Grub Failed" error message appears in the log file.

This topic describes how to install GRUB on a Linux server. GRUB version 2.02 is used in the example. The procedure to install GRUB of other versions is similar. The source code package may vary with different GRUB versions. For more information, visit [Index of /gnu/grub](https://alpha.gnu.org/gnu/grub/).

1.  Log on to the Linux server.

2.  Run the following commands to find the paths of the grub, grub-install, and grub-mkconfig files:

    **Note:** If you are prompted that one or more of these paths do not exist, go to the next step.

    ```
    which grub
    ```

    ```
    which grub-install
    ```

    ```
    which grub-mkconfig
    ```

3.  Run the `mv` command to rename the grub, grub-install, and grub-mkconfig files.

    **Note:** If you are prompted that one or more of these files do not exist, go to the next step.

    After you use SMC to migrate the server, you can restore the files by changing their names back to the original ones.

    ```
    mv /sbin/grub /sbin/grub-old
    ```

    ```
    mv /sbin/grub-install /sbin/grub-install-old
    ```

    ```
    mv /sbin/grub-mkconfig /sbin/grub-mkconfig-old
    ```

4.  Install the GRUB dependencies including bison, gcc, and make.

    ```
    yum install -y bison gcc make
    ```

5.  Perform the following operations to install flex:

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

    6.  Create a symbolic link.

        ```
        ln -s /usr/local/bin/flex /usr/bin/flex
        ```

6.  Perform the following operations to install GRUB:

    Upgrade GRUB to version 2.02 or later if you are using an early distribution of the Linux operating systems such as CentOS 5, Red Hat Enterprise Linux 5, Debian 7, Amazon Linux, or Oracle Linux.

    1.  Check whether the tools folder exists. If the folder does not exist, create it.

        ```
        test -d /root/tools || mkdir -p /root/tools
        ```

    2.  Go to the tools folder and download the GRUB installation package.

        ```
        cd /root/tools
        wget https://alpha.gnu.org/gnu/grub/grub-2.02~rc1.tar.gz
        ```

    3.  Decompress the GRUB installation package.

        ```
        tar xzf grub-2.02~rc1.tar.gz
        ```

    4.  Go to the directory to which the GRUB installation package is decompressed, and create a folder named build.

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

    6.  Create symbolic links.

        ```
        ln -s /usr/local/sbin/grub-install /sbin/grub-install
        ln -s /usr/local/sbin/grub-mkconfig /sbin/grub-mkconfig
        ```

    **Note:** If the `-Werror` error is reported during compilation, find the makefile file, remove the `-Werror` option from the file, and then try again.

7.  Run the `grub-install --version` command to check the GRUB version.


-   If the GRUB version that you installed appears in the command output, you can use SMC to migrate the server to Alibaba Cloud. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md) in *Server Migration Center User Guide*.
-   \(Optional\) After the migration is complete, run the following commands to restore GRUB to the original version:

    ```
    rm /sbin/grub-install
    rm /sbin/grub-mkconfig
    rm /boot/grub/grub.cfg
    mv /sbin/grub-old /sbin/grub
    mv /sbin/grub-install-old /sbin/grub-install
    ```


