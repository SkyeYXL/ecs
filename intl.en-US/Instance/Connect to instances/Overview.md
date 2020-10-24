---
keyword: [remote connection, VNC, Workbench]
---

# Overview

You can use a variety of methods to connect to an instance, including VNC and third-party client tools. Select a method to connect to your instance based on the operating system of your instance, the operating system of your local machine, and the operations that you want to perform.

## Connection methods

|Operating system of your instance|Operating system of your local machine|Connection method|
|---------------------------------|--------------------------------------|-----------------|
|Linux|Windows|-   VNC

For more information, see [Connect to a Linux instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using VNC.md).

-   Client tools such as PuTTY
    -   For information about how to connect to an instance by using an SSH key pair as the credential, see [Use an SSH key pair to connect to a Linux instance from a Windows device](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using an SSH key pair.md).
    -   For information about how to connect to an instance by using a password as the credential, see [Use a username and password for authentication on a Windows device](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a username and password.md). |
|Unix-like operating systems such as Linux and macOS|-   VNC

For more information, see [Connect to a Linux instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using VNC.md).

-   SSH commands
    -   For information about how to connect to an instance by using an SSH key pair as the credential, see [Use SSH key pairs in operating systems that support SSH commands \(configure the private key file by using commands\)](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using an SSH key pair.md).
    -   For information about how to connect to an instance by using a password as the credential, see [Use a username and password for authentication on a Linux or Mac OS X device](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a username and password.md). |
|Operating systems of mobile devices, such as iOS and Android|Apps such as SSH Control Lite and JuiceSSH For more information, see [Connect to a Linux instance from a mobile device](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance from a mobile device.md). |
|Windows|Windows|-   VNC

For more information, see [Connect to a Windows instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance by using VNC.md).

-   Client tools such as Remote Desktop Connection \(formerly called MSTSC\)

For more information, see [Connect from a local client that runs a Windows operating system](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance from a local client.md). |
|Linux|-   VNC

For more information, see [Connect to a Windows instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance by using VNC.md).

-   Client tools such as rdesktop

For more information, see [Connect from a local client that runs a Linux operating system](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance from a local client.md). |
|MacOS|-   VNC

For more information, see [Connect to a Windows instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance by using VNC.md).

-   Client tools such as Microsoft Remote Desktop Connection for Mac

For more information, visit [Get started with the macOS client](https://docs.microsoft.com/zh-cn/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac). |
|Operating systems of mobile devices, such as iOS and Android|Apps such as Microsoft Remote Desktop For more information, see [Connect to a Windows instance from a mobile device](/intl.en-US/Instance/Connect to instances/Connect to Windows instances/Connect to a Windows instance from a mobile device.md). |

**Note:**

-   Except for VNC, all other connection tools require that the instances have public IP addresses or elastic IP addresses \(EIPs\) assigned.
-   After a Windows instance is created, it takes two to three minutes to initialize the operating system. Do not restart the instance when it is being initialized. After a non-I/O optimized Windows instance is created, it takes 10 minutes to initialize the operating system. Do not connect to the instance when it is being initialized.

## Comparison of connection tools

The following table compares the advantages of VNC and other third-party client tools.

|Item|VNC|Third-party client tool|
|----|---|-----------------------|
|Allocation of a public IP address or an EIP to the instance|Optional. VNC can be used to troubleshoot exceptions including network misconfigurations, such as firewall being enabled by mistake.|Required.|
|Enabling services such as SSH on the instance|Optional. VNC can be used to troubleshoot exceptions including SSH service exceptions, such as SSHD being disabled.|Required.|
|Logon by using the ECS console|Supported.|Not supported. The local client must be installed.|
|Independence of the instance operating system|VNC can be used to connect to both Linux and Windows instances.|Depends on the client tool.|
|Simultaneous logons by multiple operating system users to a single instance|Not supported.|Depends on the client tool.|
|Ease of interaction|VNC does not allow you to copy and paste text. To copy and paste text, use the feature for copying long commands.|Depends on the client tool.|
|Visually viewing Linux system file resources|Not supported.|Depends on the client tool.|
|Permissions to control and modify hardware|Supported. VNC can be used to manage resources such as BIOS and troubleshoot exceptions such as system startup failure.|Not supported.|
|Terminal configurability|Not supported.|Supported, but detailed capabilities depend on the client tool.|

