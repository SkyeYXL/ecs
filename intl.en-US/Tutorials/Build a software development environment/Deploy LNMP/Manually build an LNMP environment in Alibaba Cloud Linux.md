---
keyword: [LNMP, Alibaba Cloud Linux, Nginx, MySQL, PHP7]
---

# Manually build an LNMP environment in Alibaba Cloud Linux

NGINX is a small and efficient web server platform that can be used to build an LNMP web service environment. LNMP is an acronym of the names of its original four open source components: the Linux operating system, NGINX web server, MySQL relational database management system, and PHP programming language. This topic describes how to manually build an LNMP environment on an ECS instance that runs Alibaba Cloud Linux 2.1903 LTS 64-bit.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, go to the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An instance is created and a public IP address is assigned to the instance. For more information, see [Creation method overview](/intl.en-US/Instance/Create an instance/Creation method overview.md).
-   An inbound rule is added to a security group of the ECS instance to allow traffic on port 80. For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

This topic is intended for individual users who are familiar with the Linux operating system, but new to using Alibaba Cloud ECS to build websites.

You can also purchase an LNMP image on [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/) and create an ECS instance from the image to build websites.

An instance of the ecs.c6.large instance type with the following configurations is used in this example. The actual operation depends on your instance configurations.

-   CPU: 2 vCPUs
-   Memory: 4 GiB
-   Network type: VPC
-   IP address: a public IP address

## Limits

The procedure described in this topic is applicable to the following software versions:

-   Operating system: Alibaba Cloud Linux 2.1903 LTS 64-bit
-   NGINX 1.16.1
-   MySQL 5.7.30
-   PHP 7.0.33

**Note:** If you use software versions different from the preceding ones, you may need to adjust the commands and parameter settings based on your actual conditions.

## Step 1: Prepare the compilation environment

1.  Connect to the CentOS 7 instance.

2.  Disable the firewall.

    1.  Run the systemctl status firewalld command to check the status of the firewall.

        ![firewalld status](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3129919951/p129002.png)

        -   If the firewall is in the inactive state, the firewall is disabled.
        -   If the firewall is in the active state, the firewall is enabled.
    2.  Disable the firewall. Skip this step if the firewall is already disabled.

        -   To temporarily disable the firewall, run the systemctl stop firewalld command.

            **Note:** After you run this command, the firewall is temporarily disabled. It will enter the active state when you restart the instance.

        -   To permanently disable the firewall, run the systemctl disable firewalld command.

            **Note:** You can re-enable the firewall after it is disabled. For more information, visit the [firewalld website](https://firewalld.org/).

3.  Disable Security-Enhanced Linux \(SELinux\).

    1.  Run the getenforce command to check the status of SELinux.

        ![SELinux](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3129919951/p129003.png)

        -   If SELinux is in the Disabled state, SELinux is disabled.
        -   If SELinux is in the Enforcing state, SELinux is enabled.
    2.  Disable SELinux. Skip this step if SELinux is already disabled.

        -   To temporarily disable SELinux, run the setenforce 0 command.

            **Note:** After you run this command, SELinux is temporarily disabled. It will enter the Enforcing state when you restart the instance.

        -   To permanently disable SELinux, run the vim /etc/selinux/config command to edit the SELinux configuration file. Press the Enter key. Move the pointer to the `SELINUX=enforcing` row and press the I key to switch to the edit mode. Change SELINUX=enforcing to `SELINUX=disabled` and press the Esc key. Enter :wq and press the Enter key to save and close the SELinux configuration file.

            **Note:** You can re-enable SELinux after it is disabled. For more information, see [Enable or disable SELinux](/intl.en-US/Best Practices/Security/Enable or disable SELinux.md).

            Restart the system to validate the settings.


## Step 2. Install NGINX

1.  Run the following command to install NGINX:

    ```
    yum -y install nginx
    ```

2.  Run the following command to check the NGINX version:

    ```
    nginx -v
    ```

    The following command output indicates that NGINX is installed:

    ```
    nginx version: nginx/1.16.1
    ```


## Step 3: Install MySQL

1.  Run the following command to update the YUM Repository:

    ```
    rpm -Uvh  http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
    ```

2.  Run the following command to install MySQL:

    ```
    yum -y install mysql-community-server
    ```

3.  Run the following command to check the MySQL version:

    ```
    mysql -V
    ```

    The following command output indicates that MySQL is installed:

    ```
    mysql  Ver 14.14 Distrib 5.7.30, for Linux (x86_64) using  EditLine wrapper
    ```

4.  Run the following command to start MySQL:

    ```
    systemctl start mysqld
    ```

5.  Run the following command to make MySQL start upon system startup:

    ```
    systemctl enable mysqld
    systemctl daemon-reload
    ```


## Step 4: Install PHP

1.  Update the YUM Repository.

    1.  Run the following commands to add the EPEL repository:

        ```
        yum install \
        https://repo.ius.io/ius-release-el7.rpm \
        https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
        ```

    2.  Run the following command to add the Webtatic repository:

        ```
        rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
        ```

2.  Run the following command to install PHP:

    ```
    yum -y install php70w-devel php70w.x86_64 php70w-cli.x86_64 php70w-common.x86_64 php70w-gd.x86_64 php70w-ldap.x86_64 php70w-mbstring.x86_64 php70w-mcrypt.x86_64  php70w-pdo.x86_64   php70w-mysqlnd  php70w-fpm php70w-opcache php70w-pecl-redis php70w-pecl-mongodb
    ```

3.  Run the following command to check the PHP version.

    ```
    php -v
    ```

    The following command output indicates that PHP is installed.

    ```
    PHP 7.0.33 (cli) (built: Dec  6 2018 22:30:44) ( NTS )
    Copyright (c) 1997-2017 The PHP Group
    Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
        with Zend OPcache v7.0.33, Copyright (c) 1999-2017, by Zend Technologies                
    ```


## Step 5. Configure NGINX

1.  Run the following command to back up the NGINX configuration file:

    ```
    cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bak
    ```

2.  Modify the NGINX configuration file to add NGINX support for PHP.

    **Note:** If you do not add this configuration, PHP-based pages cannot be displayed when you access them by using a browser.

    1.  Run the following command to open the NGINX configuration file:

        ```
        vim /etc/nginx/nginx.conf
        ```

    2.  Press the I key to enter the edit mode.

    3.  Add the following configuration information to the `server` braces:

        ```
                # Retain the default values for all settings except the following settings:
                location / {
                    # To configure the default homepage to be displayed when the website is accessed, add the following information to the location braces.
                    index index.php index.html index.htm;
                }
                # Add the following information to make NGINX process your PHP requests by using Fast Common Gateway Interface (FastCGI).
                location ~ .php$ {
                    root /usr/share/nginx/html;    # Replace /usr/share/nginx/html with the root directory of your website, which is /usr/share/nginx/html in this example.
                    fastcgi_pass 127.0.0.1:9000;   # NGINX forwards your PHP requests to PHP FastCGI Process Manager (PHP-FPM) through port 9000 of the ECS instance.
                    fastcgi_index index.php;
                    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
                    include fastcgi_params;   # NGINX calls the FastCGI operation to process the PHP requests.
                }                
        ```

        The configurations are as shown in the following figure.

        ![nginx-configuration](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8129919951/p69697.png)

    4.  Press the Esc key, enter :wq, and then press the Enter key to save and close the configuration file.

3.  Run the following command to start the NGINX service:

    ```
    systemctl start nginx 
    ```

4.  Run the following command to make NGINX start upon system startup:

    ```
    systemctl enable nginx
    ```


## Step 6. Configure MySQL

1.  Run the following command to check the /var/log/mysqld.log file, and obtain and record the initial password of the root user:

    ```
    grep 'temporary password' /var/log/mysqld.log
    ```

    The following command output is displayed:

    ```
    2016-12-13T14:57:47.535748Z 1 [Note] A temporary password is generated for root@localhost: p0/G28g>lsHD
    ```

    **Note:** This initial password will be used when you reset the password of the root user.

2.  Run the following command to perform security configurations for MySQL:

    ```
    mysql_secure_installation
    ```

    Perform the following steps:

    1.  Reset the password of the root user.

        ```
        Enter password for user root: # Enter the initial password that you obtained in the previous step.
        The 'validate_password' plugin is installed on the server.
        The subsequent steps will run with the existing configuration of the plugin.
        Using existing password for root.
        Estimated strength of the password: 100 
        Change the password for root ? (Press y|Y for Yes, any other key for No): Y
        New password: # Enter a new password that is 8 to 30 characters in length. It must contain lowercase and uppercase letters, digits, and special characters. Special characters include ( ) ` ~ ! @ # $ % ^ & * - + = | { } [ ] : ; ' < > , . ? /
        Re-enter new password:
        Estimated strength of the password: 100 
        Do you wish to continue with the password provided?( Press y|Y for Yes, any other key for No) : Y
        ```

    2.  Enter Y to delete anonymous users.

        ```
        By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
        Remove anonymous users? (Press y|Y for Yes, any other key for No): Y
        Success.
        ```

    3.  Enter Y to deny remote access from the root user.

        ```
        Disallow root login remotely? (Press y|Y for Yes, any other key for No): Y
        Success.
        ```

    4.  Enter Y to delete the test database and access permissions on this database.

        ```
        Remove test database and access to it? (Press y|Y for Yes, any other key for No): Y
        - Dropping test database...
        Success.
        ```

    5.  Enter Y to reload privilege tables.

        ```
        Reload privilege tables now? (Press y|Y for Yes, any other key for No): Y
        Success.
        All done!
        ```


For more information, visit [MySQL documentation](http://dev.mysql.com/doc/refman/5.7/en/mysql-secure-installation.html).

## Step 7. Configure PHP

1.  Create the phpinfo.php file to show the PHP information.

    1.  Run the following command to create the file:

        ```
        vim <Website root directory>/phpinfo.php  # Replace `<Website root directory>` with your website root directory.
        ```

        The website root directory is the `root` value within the `location ~ .php$` braces that you configured in the nginx.conf file as shown in the following figure.

        ![lnmp-root-dir](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8129919951/p69633.png)

        In this example, the website root directory is /usr/share/nginx/html. You can run the following command:

        ```
        vim /usr/share/nginx/html/phpinfo.php
        ```

    2.  Press the I key to enter the edit mode.

    3.  Enter the following content. The `phpinfo()` function will show all configuration information of PHP.

        ```
        <? php echo phpinfo(); ? >
        ```

    4.  Press the Esc key, enter :wq, and press the Enter key to save and close the configuration file.

2.  Run the following command to start PHP-FPM:

    ```
    systemctl start php-fpm
    ```

3.  Run the following command to make PHP-FPM start upon system startup:

    ```
    systemctl enable php-fpm
    ```


## Step 8: Test the connection to the LNMP environment

1.  Open your browser.

2.  In the address bar, enter `http://<Public IP address of the ECS instance>/phpinfo.php`.

    The following response indicates that the LNMP environment is deployed.

    ![php](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4129919951/p129004.png)


After you confirm that the LNMP environment is deployed, we recommend that you run the following command to delete the phpinfo.php file to ensure system security:

```
rm -rf <Website root directory>/phpinfo.php   # Replace the <Website root directory> with the website root directory that you configured in the nginx.conf file.
```

In this example, the website root directory is /usr/share/nginx/html. You can run the following command:

```
rm -rf /usr/share/nginx/html/phpinfo.php
```

