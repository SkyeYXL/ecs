# Install NVIDIA GRID drivers on vgn6i or vgn5i Linux instances

You must install an NVIDIA GRID driver if your GPU-accelerated instances require Open Graphics Library \(OpenGL\). By default, the NVIDIA GRID license granted to NVIDIA GPUs is not activated. You must purchase and activate the license to use OpenGL. This topic describes how to install an NVIDIA GRID driver and activate the GRID license. vgn6i or vgn5i lightweight GPU-accelerated instances that run the Ubuntu 16.04 64-bit operating system are used in the example.

-   A vgn6i or vgn5i instance that can access the Internet is created. We recommend that you select an image from the **Public Image** tab when you create an instance.

    **Note:** This topic describes how to install GRID drivers on Linux instances. For Windows instances, you can select paid images that have GRID drivers pre-installed when you create the instances. For more information, see [Create an instance equipped with NVIDIA GPUs](/intl.en-US/Instance/Instance type families/Compute optimized type family with GPU/Create an instance equipped with NVIDIA GPUs.md).

-   A remote connection tool such as VNC Viewer is installed on your local machine.
-   A GRID license is obtained from [NVIDIA](https://www.nvidia.com/object/nvidia-enterprise-account.html). You must build a license server. You can purchase an ECS instance and build the license server by following the tutorial on the official NVIDIA website.

This topic describes how to install GRID drivers on vgn6i or vgn5i GPU-accelerated instances that are equipped with vGPUs. For information about how to install GRID drivers on GPU-accelerated instances that are not equipped with vGPUs, see [Install NVIDIA GRID drivers on GPU-accelerated Linux instances](/intl.en-US/Instance/Instance type families/Compute optimized type family with GPU/Install NVIDIA GRID drivers on GPU-accelerated Linux instances.md).

1.  Disable nouveau.

    nouveau is an open source driver. It must be disabled before you can install another driver.

    1.  Connect to the Linux instance. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

    2.  Check whether the blacklist-nouveau.conf file exists.

        ```
        ls /etc/modprobe.d/blacklist-nouveau.conf
        ```

    3.  If the blacklist-nouveau.conf file exists and contains the following content, skip this step. If not, run the `vim /etc/modprobe.d/blacklist-nouveau.conf` command to create the file. Then, add the following content to the file to disable nouveau:

        ```
        blacklist nouveau
        blacklist lbm-nouveau
        options nouveau modeset=0
        ```

    4.  Generate kernel initramfs.

        ```
        rmmod nouveau
        update-initramfs -u
        ```

    5.  Restart the instance.

        ```
        reboot
        ```

2.  Download the NVIDIA GRID driver package.

    1.  Connect to the Linux instance. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

    2.  Download the NVIDIA GRID driver package.

        -   vgn5i GRID guest driver package:

            ```
            wget http://nvidia-418.oss-cn-shenzhen.aliyuncs.com/NVIDIA-Linux-x86_64-418.70-grid.run
            ```

        -   vgn6i GRID guest driver package:

            ```
            wget http://grid-9-2.oss-cn-hangzhou.aliyuncs.com/NVIDIA-Linux-x86_64-430.63-grid.run
            ```

3.  Install the NVIDIA GRID driver.

    -   vgn5i

        ```
        chmod +x NVIDIA-Linux-x86_64-418.70-grid.run
        . /NVIDIA-Linux-x86_64-418.70-grid.run
        ```

    -   vgn6i

        ```
        chmod +x NVIDIA-Linux-x86_64-430.63-grid.run
        . /NVIDIA-Linux-x86_64-430.63-grid.run
        ```

4.  Test whether the NVIDIA GRID driver is installed.

    ```
    nvidia-smi
    ```

    If a command output similar to the following one is displayed, the NVIDIA GRID driver is installed.

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4590359951/p47400.png)

5.  Add a license server.

    1.  Go to the /etc/nvidia directory.

        ```
        cd /etc/nvidia
        ```

    2.  Create a file named gridd.conf.

        ```
        cp gridd.conf.template gridd.conf
        ```

    3.  Add the license server information to the gridd.conf file.

        ```
        ServerAddress=<IP address of the license server>
        ServerPort=<Port of the license server (default port: 7070)>
        FeatureType=1
        ```

6.  Restart the instance for the license server configurations to take effect.

    ```
    reboot
    ```

7.  Check whether the license is activated.

    1.  Connect to the Linux instance. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

    2.  Check the license status.

        ```
        systemctl status nvidia-gridd
        ```

        If **License acquired successfully** is displayed, the license is activated.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4590359951/p47964.png)


