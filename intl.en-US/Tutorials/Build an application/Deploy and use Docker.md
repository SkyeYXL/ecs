---
keyword: [Docker, container, Linux, ECS, ECS, Alibaba Cloud, Alibaba Cloud Linux 2, Alibaba Cloud Linux]
---

# Deploy and use Docker

This topic describes how to deploy and use Docker in an ECS instance that runs Alibaba Cloud Linux 2.1903 LTS 64-bit. This tutorial is intended for developers who are familiar with Linux but new to Alibaba Cloud ECS.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, go to the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   At least one instance is created. For more information, see [Create an instance by using the provided wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the provided wizard.md).

    The following instance configurations are used in the example:

    -   Instance type: ecs.g6.large
    -   Operating system: Alibaba Cloud Linux 2.1903 LTS 64-bit

        **Note:** The commands in the example are also applicable to CentOS 7.

    -   Network type: VPC
    -   IP address: public IP address

## Procedure

1.  [Deploy Docker](#section_gtl_cjs_ls2)
2.  [Use Docker](#section_x1c_w5u_5wb)
3.  [Create an image](#section_i4r_m92_6ev)

## Deploy Docker

You can purchase the required image from [Alibaba Cloud Marketplace](https://market.aliyun.com/software) and easily deploy Docker. You can also manually install Docker as described in this topic.

1.  Remotely connect to an ECS instance. For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

2.  Run the following commands in sequence to add the YUM repository:

    ```
    yum update
    yum install epel-release -y
    yum clean all
    yum list
    ```

3.  Install and run Docker.

    ```
    yum install docker-io -y
    systemctl start docker
    ```

4.  Check the installation result.

    ```
    docker info
    ```

    If the following information is displayed, Docker is installed.

    ![site](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9629919951/p128549.png)


## Use Docker

You can use Docker in these ways:

-   Manage the Docker daemon.

    ```
    systemctl start docker     #Run the Docker daemon.
    systemctl stop docker      #Stop the Docker daemon.
    systemctl restart docker   #Restart the Docker daemon.
    ```

-   Manage images. In the following example, Apache images from Alibaba Cloud Container Registry are used.

    ```
    docker pull registry.cn-hangzhou.aliyuncs.com/lxepoo/apache-php5
    ```

    -   Modify the tags of images in Alibaba Cloud Container Registry to simplify image identification.

        ```
        docker tag registry.cn-hangzhou.aliyuncs.com/lxepoo/apache-php5:latest aliweb:v1
        ```

    -   Check existing images.

        ```
        docker images
        ```

    -   Force delete an image.

        ```
        docker rmi -f registry.cn-hangzhou.aliyuncs.com/lxepoo/apache-php5
        ```

-   Manage containers.
    -   Access a container. Run the `docker images` command to obtain the ImageId value, which is e1xxxxxxxxxe. Then, run the `docker run` command to access the container.

        ```
        docker run -it e1xxxxxxxxxe /bin/bash
        ```

    -   Exit the container. Run the `exit` command to exit the container.
    -   You can combine the `run` command with the `–d` parameter to run the container in the background. The `--name` parameter specifies apache as the container name.

        ```
        docker run -d --name apache e1xxxxxxxxxe
        ```

        exit

    -   Access the container that runs in the background.

        ```
        docker exec -it apache /bin/bash
        ```

    -   Create an image from the container. Description of parameters in the command: `docker commit <Container ID or container name> [<Repository name>[:<Tag>]]`.

        ```
        docker commit containerID/containerName repository:tag
        ```

    -   To easily test and restore an image, you can run the source image, derive a new image with a simple name from the source image, and then test the new image.

        ```
        docker commit 4c8066cd8**** apachephp:v1
        ```

    -   Run the container and map port 8080 of the host to the container.

        ```
        docker run -d -p 8080:80 apachephp:v1
        ```

        In a browser, enter the IP address of the instance followed by the port number 8080 to connect to the container. The following response indicates that the container runs normally.

        ![Mapping result](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9629919951/p12348.png)


## Create an image

1.  Prepare the following content in Dockerfile:

    1.  Create and edit the Dockerfile file.

        ```
        vim Dockerfile
        ```

    2.  Press the I key to enter the edit mode. Add the following content to the file:

        ```
        FROM apachephp:v1  #Declare the source of the base image.
        MAINTAINER DTSTACK #Declare the image owner.
        RUN mkdir /dtstact #The commands that you want to run before the container starts. You must append these commands to the end of the RUN command. Dockerfile can contain only a maximum of 127 lines. If you have commands that exceed 127 lines, we recommend that you write these commands to a script.
        ENTRYPOINT ping www.aliyun.com #The commands that run at system startup. The last command must be a frontend command that runs constantly. Otherwise, the container will exit after running all commands.
        ```

    3.  Press the Esc key. Enter `:wq` and press the Enter key to save and exit the Dockerfile file.

2.  Build an image.

    ```
    docker build -t webaliyunlinux:v1 .   # . specifies the path of Dockerfile and cannot be ignored.
    docker images                    #Check whether the image is built.
    ```

3.  Run the container and check its status.

    ```
    docker run -dwebaliyunlinux:v1       #Run the container in the background.
    docker ps                        #Query the containers that are in the running state.
    docker ps –a                     #Query all containers including those in the stopped state.
    docker logs CONTAINER ID/IMAGE   #Check the startup log to troubleshoot the issue based on the container ID or name if the container do not exist in the query result.
    ```

4.  Create an image.

    ```
    docker commit fb2844b6**** dtstackweb:v1 #Append the container ID and the name and version number of the new image to the end of the commit command.
    docker images                    #Query images that have been downloaded and created on premises.
    ```

5.  Push the image to a remote repo.

    By default, the image is pushed to Docker Hub. You must log on to Docker, bind a tag to the image, and then name the image in the `Docker username/image name:tag` format. Then the push is completed.

    ```
    docker login --username=dtstack_plus registry.cn-shanghai.aliyuncs.com #Specify the password of the image repository. Enter the password after you run this command.
    docker tag [ImageId] registry.cn-shanghai.aliyuncs.com/dtstack123/test:[Tag]
    docker push registry.cn-shanghai.aliyuncs.com/dtstack123/test:[Tag]
    ```


