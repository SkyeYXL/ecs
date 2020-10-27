# Build multiple websites in Windows

This topic describes how to use Internet Information Services \(IIS\) to build multiple websites on a Windows instance. Windows Server 2012 R2 64-bit is used in this topic.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, go to the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An instance is created and the web environment that consists of IIS, PHP, and MySQL is deployed on the instance. You can use a Windows image from [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/) that is installed with the environment to deploy the environment.

This tutorial is intended for users who are familiar with Windows and want to optimize the O&M process by making efficient use of resources and managing sites in a centralized manner. For example, you can configure multiple blogging platforms of different categories or build multiple websites to handle complex business tasks on an instance.

In this tutorial, IIS is used to build the `windows-testpage-1` and `windows-testpage-2` websites simultaneously and configure different domain names on the same port to access the websites.

The following instance configurations are used in the example:

-   Instance type: ecs.c6.large
-   Operating system: Windows Server 2012 R2 64-bit

## Create test websites

1.  Connect to the instance that has the web environment deployed.

    For more information, see [Connect to a Windows instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance by using VNC.md).

2.  On the desktop, click **This PC** and go to the C:\\wwwroot path in the default root directory.

3.  Create the `windows-testpage-1` and `windows-testpage-2` folders.

4.  Open the `windows-testpage-1` folder, create a test1.php file in the folder, and then enter the following content in the file:

    ```
    <? php
    echo "<title>Test-1</title>";
    echo "windows-test-1";
    ? >
    ```

5.  Open the `windows-testpage-2` folder, create a test2.php file in the folder, and then enter the following content in the file:

    ```
    <? php
    echo "<title>Test-2</title>";
    echo "windows-test-2";
    ? >
    ```


## Configure IIS

1.  In the taskbar that is located at the bottom of the desktop, click the **Server Manager** icon![server](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5703243061/p128809.png).

2.  In the top menu bar, choose **Tools** \> **Internet Information Services \(IIS\) Manager**.

3.  In the left-side navigation pane of Internet Information Services \(IIS\) Manager, click the name of the server and click **Sites**.

4.  In the right-side Actions section, click **Add Website**. Add the `windows-testpage-1` website.

    The following list specifies how to configure corresponding parameters:

    -   Site name: Enter `windows-testpage-1`.
    -   Application pool: Select DefaultAppPool.
    -   Physical path: Select a physical path for the `windows-testpage-1` website.
    -   Host name: Specify the `test1.com` domain name as the hostname.
5.  In the right-side Actions section, click **Add Website**. Add the `windows-testpage-2` website.

    The following list specifies how to configure corresponding parameters:

    -   Site name: Enter `windows-testpage-2`.
    -   Application pool: Select DefaultAppPool.
    -   Physical path: Select a physical path for the `windows-testpage-2` website.
    -   Host name: Specify the `test2.com` domain name as the hostname.

## \(Optional\) Configure the hosts file on the local host

You must configure IP mapping in the local hosts file. The information used in this tutorial consists of only test values. If you use the actual server domain names when you configure the websites, skip this step. In this tutorial, the local physical machine uses the Windows operating system.

1.  Go to the C:\\Windows\\System32\\drivers\\etc directory.

2.  Copy the hosts file for backup.

    Keep the hosts - copy file to restore the hosts file to its initial status after the configuration is complete.

3.  Modify the hosts file.

    Append the following content to the end of the file, save the file, and then exit:

    ```
    <Public IP address of the instance> test1.com
    <Public IP address of the instance> test2.com
    ```

4.  Go back to the Windows desktop and press Win+R.

5.  In the **Run** dialog box, enter cmd and click **OK**.

6.  Run the following command in the command line to ensure that the configurations of the hosts file take effect immediately:

    ```
    ipconfig /flushdns
    ```


You can access the two test websites from a browser on the local host.

-   If you go to `test1.com/test1.php`, you can view the `windows-testpage-1` website, as shown in the following figure.

    ![test1.php](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8897773061/p128826.png)

-   If you go to `test2.com/test2.php`, you can view the `windows-testpage-2` website, as shown in the following figure.

    ![test2.php](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8897773061/p128827.png)


Multiple websites are built. In your actual operations, you only need to make sure that the hostnames and project paths are correctly configured to access your websites. You can install SSL certificates in IIS. For more information, see [Install SSL certificates in IIS servers](/intl.en-US/Download and install SSL certificates/Install SSL certificates in IIS servers.md).

