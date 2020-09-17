---
keyword: [Cloud Assistant, remote script, O&M plug-in, Alibaba Cloud, ECS]
---

# Install the Cloud Assistant client

The Cloud Assistant client is used to run Cloud Assistant scripts on ECS instances. This topic describes how to install the Cloud Assistant client.

-   You must install and use the Cloud Assistant client as an administrator. The administrator username is root for Linux instances, and system for Windows instances.
-   Before you install the Cloud Assistant client, ensure that your instance type and operating system support Cloud Assistant. For more information, see the "Limits" section in [Cloud Assistant overview](/intl.en-US/Deployment & Maintenance/Cloud assistant/Cloud Assistant overview.md).

ECS instances created from public images after December 1, 2017 are pre-installed with the Cloud Assistant client. For ECS instances created on and before December 1, 2017, you must manually install the Cloud Assistant client.

This topic describes three installation methods:

-   [Install the client from the download link \(Windows instances\)](#section_e5n_k2x_ydb): You must establish a remote connection to the Windows Server instance.
-   [Install the client from the download link \(Linux instances\)](#section_anv_mzg_1zr): You must establish a remote connection to the Linux instance.
-   [Install the client by using Alibaba Cloud CLI for Windows or Linux instances](#section_qkk_yt2_ngb): You can use this method for both Windows Server instances and Linux instances. This method does not require you to establish a remote connection to the instance. However, you must install Alibaba Cloud Command Line Interface \(CLI\) to use this method. For more information about how to install Alibaba Cloud CLI, see [Alibaba Cloud CLI Installation Guide]().

## Install the client from the download link \(Windows instances\)

1.  Establish a remote connection to an ECS instance as the system user. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

2.  Download the Cloud Assistant installation file. Download link: [Cloud Assistant client](https://aliyun-client-assist.oss-accelerate.aliyuncs.com/windows/aliyun_agent_latest_setup.exe).

3.  Double-click the installation file and follow the instructions to install the client.

    The default installation path is C:\\ProgramData\\aliyun\\assist\\ for Windows instances.

4.  If the instance is in the classic network, create a file named region-id in the installation directory. Do not add extensions to the file, such as .txt or .conf. Enter the region ID of the instance in the region-id file, such as cn-hangzhou. For more information about region IDs, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).

    **Note:** In Windows, you must disable the **Hide extensions for known file types** feature to check whether the region-id file has an extension.


## Install the client from the download link \(Linux instances\)

1.  Remotely connect to an ECS instance as a root user. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

2.  Based on the operating system of your instance, select one of the following methods to install the Cloud Assistant client:

    -   Install the client by using an RPM package. This method is applicable to operating systems such as CentOS, Red Hat Enterprise Linux \(RHEL\), and SUSE Linux.
        1.  Download the RPM package of the Cloud Assistant client.

            ```
            wget "https://aliyun-client-assist.oss-accelerate.aliyuncs.com/linux/aliyun_assist_latest.rpm"
            ```

        2.  Install the Cloud Assistant client.

            ```
            rpm -ivh --force aliyun_assist_latest.rpm
            ```

        3.  If the operating system of the instance is Red Hat, perform the following steps:
            1.  Stop the qemu-ga service.

                ```
                systemctl stop qemu-guest-agent
                systemctl disable qemu-guest-agent
                ```

            2.  Restart Cloud Assistant.

                ```
                systemctl restart aliyun.service
                ```

        4.  If the instance is in the classic network, create a file named region-id in the installation directory. Do not add extensions to the file, such as .txt or .conf. Enter the region ID of the instance in the region-id file, such as cn-hangzhou. For more information about region IDs, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).
    -   Install the client by using a Debian package. This method is applicable to operating systems such as Debian and Ubuntu.
        1.  Download the Debian package of the Cloud Assistant client.

            ```
            wget "https://aliyun-client-assist.oss-accelerate.aliyuncs.com/linux/aliyun_assist_latest.deb"
            ```

        2.  Optional. Uninstall earlier versions of the Cloud Assistant client.

            ```
            dpkg -r aliyun-assist
            ```

        3.  Install the Cloud Assistant client.

            ```
            dpkg -i aliyun_assist_latest.deb
            ```

        4.  If the instance is in the classic network, create a file named region-id in the installation directory. Do not add extensions to the file, such as .txt or .conf. Enter the region ID of the instance in the region-id file, such as cn-hangzhou. For more information about region IDs, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).
    -   Install the client by compiling the source code.
        1.  Download the source code of the Cloud Assistant client.

            ```
            git clone https://github.com/aliyun/aliyun_assist_client
            ```

        2.  Access the source code directory.
        3.  Run the `cmake .` command to generate the compilation file.

            **Note:** If the `CMAKE_MINIMUM_REQUIRED` error is reported during compilation, go to the [official CMake website](https://cmake.org/download/) to update the CMake service to V3.1 or later.

        4.  Run the `make` command to start compiling.
        5.  If the instance is in the classic network, create a file named region-id in the installation directory. Do not add extensions to the file, such as .txt or .conf. Enter the region ID of the instance in the region-id file, such as cn-hangzhou. For more information about region IDs, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).
        6.  Run the `aliyun-service -d` command to install the Cloud Assistant client.
    The following list shows the default installation paths for Linux instances:

    -   CoreOS: /opt/local/share/aliyun-assist/.
    -   Other operating systems: /usr/local/share/aliyun-assist/. Other operating systems are: Ubuntu, Debian, Red Hat, SUSE Linux Enterprise Server, openSUSE, and Alibaba Cloud Linux.

## Install the client by using Alibaba Cloud CLI for Windows or Linux instances

**Note:** The Red Hat system does not support installation by calling API operations. You can only install the client by using the download link. For more information, see [Install the client from the download link \(Linux instances\)](#section_anv_mzg_1zr).

1.  Call the [DescribeCloudAssistantStatus](/intl.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md) operation to query whether the Cloud Assistant client has been installed on your ECS instance.

    ```
    aliyun ecs DescribeCloudAssistantStatus --RegionId TheRegionId --InstanceId.1 i-bp1g6zv0ce8og\*\*\*\*\*\*p --output cols=CloudAssistantStatus rows=InstanceCloudAssistantStatusSet.InstanceCloudAssistantStatus[]
    ```

    If `CloudAssistantStatus=true` is returned, the Cloud Assistant client has been installed on the instance. Otherwise, proceed to the next step.

2.  Call the [InstallCloudAssistant](/intl.en-US/API Reference/Cloud assistant/InstallCloudAssistant.md) operation to install the Cloud Assistant client.

    ```
    aliyun ecs InstallCloudAssistant --RegionId TheRegionId --InstanceId.1 i-bp1g6zv0ce8og\*\*\*\*\*\*p
    ```

3.  Call the [RebootInstance](/intl.en-US/API Reference/Instances/RebootInstance.md) operation to restart the ECS instance.

    ```
    aliyun ecs RebootInstance --InstanceId i-bp1g6zv0ce8og\*\*\*\*\*\*p
    ```

4.  If the instance is in the classic network, add a region declaration within the instance.

    1.  Connect to an ECS instance as the root or system user. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

    2.  View the version of Cloud Assistant. For Linux instances, run the following command. For Windows instances, see [Update or disable updates for the Cloud Assistant client](/intl.en-US/Deployment & Maintenance/Cloud assistant/Configure the Cloud Assistant client/Update or disable updates for the Cloud Assistant client.md).

        ```
        aliyun-service -v
        ```

        If the version of Cloud Assistant is V1.0.1.400 or later, the client is installed. Otherwise, proceed to the next step.

    3.  create a file named region-id in the installation directory. Do not add extensions to the file, such as .txt or .conf. Enter the region ID of the instance in the region-id file, such as cn-hangzhou. For more information about region IDs, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm).

        **Note:** In Windows, you must disable the **Hide extensions for known file types** feature to check whether the region-id file has an extension.


**References**  


[InvokeCommand](/intl.en-US/API Reference/Cloud assistant/InvokeCommand.md)

[DescribeCloudAssistantStatus](/intl.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md)

[InstallCloudAssistant](/intl.en-US/API Reference/Cloud assistant/InstallCloudAssistant.md)

[RebootInstance](/intl.en-US/API Reference/Instances/RebootInstance.md)

[Alibaba Cloud GitHub repository](https://github.com/aliyun/aliyun_assist_client)

