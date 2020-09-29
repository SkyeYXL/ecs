# Manually build a Drupal website

This topic describes how to use Drupal to deploy an e-commerce website on a CentOS 7 ECS instance.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, go to the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An ECS instance that has a public IP address is created and deployed with a LAMP environment. For more information, see [Build a LAMP environment](/intl.en-US/Tutorials/Build a software development environment/Build a LAMP environment.md).

Drupal is an open source content management framework \(CMF\) written in PHP. Drupal consists of a content management system \(CMS\) and a PHP development framework. You can use Drupal to build dynamic websites that provide various features and services. Drupal is commonly used in a variety of applications, from personal blogs to large communities.

This topic is intended for users who are familiar with Linux, but new to web development on Alibaba Cloud ECS instances. You can also build a Drupal website based on an Alibaba Cloud Marketplace image. For more information, see [Build a Drupal website based on an Alibaba Cloud Marketplace image](/intl.en-US/Tutorials/Build a website/Build a Drupal website/Build a Drupal website based on an Alibaba Cloud Marketplace image.md).

## Configuration

The following instance configurations and software versions are used in the example. The operations may vary depending on your instance configurations and software versions.

-   Instance type: ecs.c6.large
-   Operating system: CentOS 7.8 64-bit
-   Apache HTTP Server: 2.4.6
-   MySQL: 5.7.31
-   PHP: 7.0.33
-   Drupal: 8.1.1

## Configure the database information

1.  Use a local browser to access http://<Public IP address of the instance\>/phpMyAdmin.

2.  Use the username and password of a MySQL database to log on to phpMyAdmin.

3.  At the top of the page, click **SQL**.

4.  Create a database and user for Drupal.

    Enter the following SQL statement in the editor:

    ```
    CREATE DATABASE <DrupalDBName>;
    CREATE user '<UserName>'@'<IP>' IDENTIFIED BY '<UserPassWord>';
    FLUSH PRIVILEGES;
    ```

    Specify the parameters in the SQL statement:

    -   `<DrupalDBName>`: Specify a name for the database.
    -   `<UserName>`: Specify a user for the database.
    -   `<IP>`: Specify the IP address of the local host or 127.0.0.1.
    -   `<UserPassWord>`: Specify a password for the database.

        **Note:** You can execute the `show variables like 'validate_password%';` SQL statement to query the password strength rules for the database.

5.  Click **Go**.


## Install Drupal

1.  Connect to an ECS instance in which an LAMP environment is deployed.

    For more information about the remote connection methods, see [Connect to a Linux instance by using VNC](/intl.en-US/Instance/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using VNC.md).

2.  Download and configure Drupal.

    1.  Download the Drupal installation package.

        ```
        cd
        wget http://ftp.drupal.org/files/projects/drupal-8.1.1.zip
        ```

    2.  Decompress the Drupal installation package and move the installation files to the root directory of your Apache website.

        ```
        yum install unzip -y
        unzip drupal-8.1.1.zip 
        ```

        ```
        mv drupal-8.1.1/* /var/www/html
        ```

    3.  Modify the owner and group of the sites directory.

        ```
        chown -R daemon:daemon /var/www/html/sites
        ```

    4.  Restart the Apache service.

        ```
        systemctl restart httpd
        ```

3.  Use a browser to access the website and install Drupal.

    1.  User a local browser to access <Public IP address of the ECS instance\> and go to the Drupal installation page. Select the installation language from the Choose language drop-down list, and then click **Save and continue**.

        ![Select the installation language](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3429919951/p12509.png)

    2.  Select Standard, and click **Save and continue**.

    3.  Enter the information of the configured database, click **Save and continue**.

    4.  After the installation is complete, go to the website settings page, enter website information, and then click **Save and continue**.


After the installation is complete, you can customize your website pages.

