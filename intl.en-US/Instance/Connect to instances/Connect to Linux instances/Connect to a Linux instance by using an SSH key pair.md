# Connect to a Linux instance by using an SSH key pair

SSH key pairs are a secure and convenient method to authenticate logons. This topic describes how to use an SSH key pair to connect to a Linux instance from a Linux device or an SSH Windows client such as MobaXterm.

-   An SSH key pair is created and the .pem private key file is downloaded. For more information, see [Create an SSH key pair](/intl.en-US/Security/Key pairs/Use an SSH key pair/Create an SSH key pair.md).
-   The instance is in the Running state.
-   The SSH key pair is bound to the instance.
-   A public IP address or an elastic IP address \(EIP\) is bound to the instance.
-   A security group rule is added to a security group of the instance to allow traffic on the corresponding port, such as the default port 22 for SSH. For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

    |Network type|NIC type|Rule direction|Authorization policy|Protocol type|Port range|Priority|Authorization type|Authorized object|
    |------------|--------|--------------|--------------------|-------------|----------|--------|------------------|-----------------|
    |VPC|N/A|Inbound|Allow|SSH\(22\)|22/22|1|IPv4 CIDR block|0.0.0.0/0|
    |Classic network|Public|


## Use an SSH key pair to connect to a Linux instance from a Windows device

The following section describes how to convert the format of the private key file from .pem to .ppk and how to use an SSH key pair to connect to a Linux instance. PuTTYgen is used in this example.

1.  Download and install PuTTYgen and PuTTY.

    The following download URLs are used:

    -   [PuTTYgen](https://the.earth.li/~sgtatham/putty/latest/w64/puttygen.exe)
    -   [PuTTY](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe)
2.  Convert the private key file format from .pem to .ppk.

    1.  Start PuTTYgen.

        In this example, PuTTYgen 0.71 is used.

    2.  Set **Type of key to generate** to **RSA** and click **Load**.

        ![windows_puttygen_1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6847597851/p51179.png)

    3.  Select **All Files**.

        ![windows_puttygen_2](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6847597851/p5188.png)

    4.  Select the .pem private key file that you want to convert.

    5.  In the dialog box that appears, click **OK**.

    6.  Click **Save private key**.

    7.  In the dialog box that appears, click **Yes**.

    8.  Specify the name of the .ppk private key file and click **Save**.

3.  Start PuTTY.

4.  Configure the private key file that is used for authentication.

    1.  Choose **Connection** \> **SSH** \> **Auth**.

    2.  Click **Browse**.

    3.  Select the resulting .ppk private key file.

    ![windows_putty_3](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7847597851/p5191.png)

5.  Configure the required parameters to connect to a Linux instance.

    1.  Click **Session**.

    2.  In the **Host Name \(or IP address\)** field, enter the logon account and public IP address of the instance.

        The format is **root@<IP address\>**. Example: root@10.10.xx.xxx.

    3.  In the **Port** field, enter the port number **22**.

    4.  Set **Connection type** to **SSH**.

    ![windows_putty_4](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7847597851/p5192.png)

6.  Click **Open**.

    If the following message appears, you have logged on to the instance by using the SSH key pair.

    ![windows_putty_5](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7847597851/p51203.png)


## Use SSH key pairs in operating systems that support SSH commands \(configure the private key file by using commands\)

The following section describes how to use commands to configure the required parameters to connect to a Linux instance from a Linux device or an SSH Windows client such as MobaXterm.

1.  Find the path where the .pem private key file is located. Example: ~/.ssh/ecs.pem.

    The path and file name are for reference only. Modify the information based on your needs.

2.  Run the following command to modify the property of the private key file:

    ```
    chmod 400 <Path of the .pem private key file on your local PC>
    ```

    Example:

    ```
    chmod 400 ~/.ssh/ecs.pem
    ```

3.  Run the following command to connect to the instance:

    ```
    ssh -i <Path of the .pem private key file on your local PC> root@<Public IP address>
    ```

    Example:

    ```
    ssh -i ~/.ssh/ecs.pem root@10.10.xx.xxx
    ```


## Use SSH key pairs in operating systems that support SSH commands \(configure the private key file by using the config file\)

The following section describes how to use the config file to configure the required parameters to connect to a Linux instance from a Linux device or an SSH Windows client such as MobaXterm.

1.  Go to the .ssh directory under the root directory and modify the config file by using the following method.

    ~/.ssh/ecs.pem is the path of the private key file on your local PC.

    ```
    Host ecs    // Enter the name of the ECS instance.
    HostName 192. *. *. *   // Enter the public IP address of the ECS instance.
    Port 22   // Enter the port number. The default port number is 22.
    User root   // Enter the logon account.
    IdentityFile ~/.ssh/ecs.pem // Enter the path of the .pem private key file on the local PC.
    ```

2.  Save the config file.

3.  Restart the SSH service.

4.  Run the following command to connect to the instance:

    ```
    ssh <Name of the instance>
    ```

    Example:

    ```
    ssh ecs
    ```


