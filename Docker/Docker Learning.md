## 

## 

## 官网

[官方文档](https://docs.docker.com/desktop/)

## 书籍

[深入浅出Docker-奈吉尔·波尔顿-微信读书](https://weread.qq.com/web/reader/a6332ce0718b75f2a63b772k16732dc0161679091c5aeb1?)

## Docker Learning

- Docker Overview

- Docker Install

- Docker Command
  
  - mirror command
  
  - container command
  
  - operation command
  
  - ...

- Docker mirror

- container data volume

- DockerFile

- Docker Net principle

- IDEA  integrate Docker

- Docker Compose

- Docker Swarm

## Docker Overview

Why we need Docker?

> Question:
> 
> 一款产品:开发--上线 两套环境!应用环境，应用配置!
> 开发 … 运维。问题:我在我的电脑上可以运行!版本更新,导致服务不可用!对于运维来说,考验就十分大?
> 环境配置是十分的麻烦，每一个机器都要部署环境(集群Redis、ES、Hadoop.)!费时费力。
> 发布一个项目(jar+(Redis MySQL jdk ES))，项目能不能都带上环境安装打包!
> 之前在服务器配置一个应用的环境 Redis MySQL jdk ES Hadoop,配置超麻烦了，不能够跨平台。
> Windows,最后发布到 Linux!
> 传统:开发jar，运维来做!
> 现在:开发打包部署上线，一套流程做完!

> Solution:
> 
> java- apk-发布(应用商店)…--张三使用apk… 安装即可用!
> java … jar(环境)…打包项目带上环境(镜像)…(Docker仓库:商店)…. 下载我们发布的镜像 … 直接运行即可!

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-23-09-59-59-image.png)

名词概念：

**镜像(image):**
docker镜像就好比是一个模板,可以通过这个模板来创建容器服务,tomcat镜像===>run ==>tomcat01 容器(提供服务器)通过这个镜像可以创建多个容器(最终服务运行或者项目运行就是在容器中的)

**容器(container):**
Docker利用容器技术，独立运行一个或者一个组应用，通过镜像来创建的。
启动，停止，删除，基本命令!
目前就可以把这个容器理解为就是一个简易的linux系统

**仓库(renository):**
仓库就是存放镜像的地方!
仓库分为公有仓库和私有仓库!
Docker Hub(默认是国外的)
阿里云...都有容器服务器(配置镜像加速!)

The role of docker

**VM**

虚拟机技术缺点：

- 资源占用多

- 冗余步骤多

- 启动慢

**Container**

容器化技术不是模拟一个完整的操作系统，用的是宿主内核

比较Docker 和 虚拟机技术的不同:

- 传统虚拟机，虚拟出一套硬件，运行一个完整的操作系统，然后在这个系统上安装和运行软件

- 容器内的应用査接运行在宿主机的内核，容器是没有自己的内核的，也没有虚拟我们的硬件，所以就轻便了

- 每个容器间是互相隔离，每个容器内都有一个属于自己的文件系统，互不影响

## Docker install

[Docker 最新安装教程（windows11）_docker下载安装-CSDN博客](https://blog.csdn.net/m0_62854966/article/details/136414726)

[windows11家庭版安装docker时缺少Hyper-V虚拟机如何解决_win11没有hyper-v-CSDN博客](https://blog.csdn.net/qq_39430295/article/details/135847263)

[Docker Desktop 解决 “Starting the Docker Engine...“ 问题-CSDN博客](https://blog.csdn.net/m0_62854966/article/details/136415387)

### Hello World

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-23-14-12-38-image.png)

流程：

<img src="file:///C:/Users/YW/AppData/Roaming/marktext/images/2024-04-23-14-13-38-image.png" title="" alt="" width="428">

### Underlying principle

**Docker是如何工作的？**

Docker 是一个 Client-Server 结构的系统，Docker的守护进程运行在主机上。通过Socket从客户端访问!

> "守护进程" 是指 Docker 的后台进程，也称为 Docker 守护进程（Docker Daemon）。它是在主机上运行的一个长期运行的服务，负责管理和监控 Docker 容器的生命周期、镜像的存储和管理、网络和存储卷的配置等。守护进程是 Docker 系统的核心组件，它负责处理来自 Docker 客户端的请求，并相应地执行操作。因此，它充当了 Docker 系统与用户之间的接口，负责响应用户的命令并执行相应的操作，比如创建、运行、停止和删除容器等。

DockerServer 接收到 Docker-Client的指令，就会执行这个命令!

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-23-14-44-49-image.png)

### Aliyun image acceleration

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-25-10-12-05-image.png)

## Common commands for Docker

#### Help command

```shell
docker version #版本信息
docker info #系统信息，包括镜像和容器的数量        
docker #command --help
```

[Reference](https://docs.docker.com/reference/)

**command format**

```shell
C:\Users\YW>docker images --help
Aliases:
  docker image ls, docker image list, docker images

Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Format output using a custom template:
                        'table':            Print output in table format
                        with column headers (default)
                        'table TEMPLATE':   Print output in table format
                        using the given Go template
                        'json':             Print in JSON format
                        'TEMPLATE':         Print output using the given
                        Go template.
                        Refer to https://docs.docker.com/go/formatting/
                        for more information about formatting output with
                        templates
      --no-trunc        Don't truncate output
  -q, --quiet           Only show image IDs

#Alias：别名

#-a, --all：-a是--all的简写

#--digests：按字母序排序，所以位于--all下一行
```

#### Image command

##### docker images 查看所有本地的主机上的镜像

```shell
docker imagesREPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    d2c94e258dcb   11 months ago   13.3KB

# 解释
REPOSITORY    镜像的仓库源
TAG           镜像的标签
IMAGE ID      镜像的id 
CREATED       镜像的创建时间
SIZE          镜像的大小
# 可选项
-a，--a11    # 列出所有镜像
-q，--quiet  # 只显示镜像的id
```

##### docker search  搜索镜像

```shell
C:\Users\YW>docker search mysql
NAME                            DESCRIPTION                                      STARS     OFFICIAL
mysql                           MySQL is a widely used, open-source relation…   15008     [OK]
mariadb                         MariaDB Server is a high performing open sou…   5722      [OK]
percona                         Percona Server is a fork of the MySQL relati…   627       [OK]
phpmyadmin                      phpMyAdmin - A web interface for MySQL and M…   966       [OK]
```

##### docker pull  下载镜像

```shell
#docker pull image[:tag]
#指定版本下载：docker pull mysql:5.7
C:\Users\YW>docker pull mysql
Using default tag: latest
latest: Pulling from library/mysql#默认tag为latest
72a69066d2fe: Pull complete #分层下载，docker image的核心-联合文件系统
93619dbc5b36: Pull complete
99da31dd6142: Pull complete
626033c43d70: Pull complete
37d5d7efb64e: Pull complete
ac563158d721: Pull complete
d2ba16033dad: Pull complete
688ba7d5c01a: Pull complete
00e060b6d11d: Pull complete
1c04857f594f: Pull complete
4d7cfa90e6ea: Pull complete
e0431212d27d: Pull complete
Digest: sha256:e9027fe4d91c0153429607251656806cc784e914937271037f7738bd5b8e7709
#签名
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest #真实地址
```

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-25-10-30-27-image.png)

联合文件系统的优势：当pull image存在相同层时，不再下载

##### docker rmi 删除镜像

```shell
docker rmi -f image #删除指定的镜像
docker rmi -f image1 image2 #删除多个镜像
docker rmi -f $(docker images -aq) #删除所有镜像，linux
docker rmi -f @(docker images -aq) #删除所有镜像，powershell
```

### Container command

#### docker run

**有了镜像才可以创建容器**

```shell
docker pull centos
```

```shell
新建容器并启动
docker run [可选参数] image
# 参数说明
--name="name"       容器名字，用来说明参数
-d                  后台方式运行
-it                 使用交互方式运行，进入容器查看内容
-P                  指定容器端口
    -P 主机端口：容器端口
    -P 容器端口
    -P ip：主机端口：容器端口
#example
C:\Users\YW>docker run -it centos
[root@f7103d6e4c69 /]#  ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@f7103d6e4c69 /]# mkdir YW
[root@f7103d6e4c69 /]# ls
YW  bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@f7103d6e4c69 /]# exit
exitr#
```

#### docker ps

```shell
#docker ps 
para：
   # 当前运行的容器
-a # 列出当前运行的容器+历史运行过的容器
-n =? #最近创建的容器，指定数量
-q #只显示ID
```

#### Exit container

```shell
exit #退出且停止容器
ctrl + P + Q #容器不停止退出
C:\Users\YW>docker run -it centos
[root@8d385fd7f8f5 /]#
C:\Users\YW>docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED              STATUS              PORTS     NAMES
8d385fd7f8f5   centos    "/bin/bash"   About a minute ago   Up About a minute             romantic_dirac
```

#### docker rm

```shell
docker rm image_id    #删除指定容器，不能删除正在运行的容器，强制删除-f
docker rm -f $(docker ps -aq) #删除所有容器 linux系统
docker rm -f @(docker ps -aq) #删除所有容器 powershell
```

#### start and stop

```shell
docker start    #启动容器
docker restart  #重新启动容器
docker stop     #暂停容器
docker kill     #强制停止容器
```

### Other commands

#### 后台启动容器

```shell
# 命令 docker run -d container
[rootakuangshen /# docker run -d centos
#问题docker ps，发现 centos 停止了
#常见的坑:docker 容器使用后台运行，就必须要有要一个前台进程，docker发现没有应用，就会自动停止
#nginx，容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了
```

#### 查看日志

```shell
#docker logs container
C:\Users\YW>docker logs -tf --tail 10 56255ffd3b2d
2024-04-25T11:17:12.008918170Z [root@56255ffd3b2d /]# ls
2024-04-25T11:17:12.011012503Z bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
2024-04-25T11:17:14.579661603Z [root@56255ffd3b2d /]# cd home
2024-04-25T11:17:15.881238271Z [root@56255ffd3b2d home]# exit
2024-04-25T11:17:15.881270921Z exit
```

#### 查看容器内的进程信息

```shell
#docker top
```

#### 查看镜像的源数据

```shell
# docker inspect container
C:\Users\YW>docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                     PORTS     NAMES
56255ffd3b2d   centos    "/bin/bash"   4 minutes ago   Exited (0) 4 minutes ago             affectionate_bose
C:\Users\YW>docker inspect 56255ffd3b2d
[
    {
#ID号    "Id": "56255ffd3b2dfd8dde9b8727664b39fc4dd90c3ce29bfe90dcb9c587ecfdf4b4",
#创建时间 "Created": "2024-04-25T11:17:10.966971641Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-04-25T11:17:11.249444716Z",
            "FinishedAt": "2024-04-25T11:17:15.883999908Z"
        },
        "Image": "sha256:5d0da3dc976460b72c77d94c8a1ad043720b0416bfc16c
52c45d4847e53fadb6",
         ...
```

#### 进入正在运行的容器

```shell
# docker exec container
C:\Users\YW>docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
9bb41cfca216   centos    "/bin/bash"   54 seconds ago   Up 53 seconds             hardcore_turing

C:\Users\YW>docker exec -it 9bb41cfca216 /bin/bash
[root@9bb41cfca216 /]#
```

**例子解释`docker exec`和`docker attach`的区别**
假设我们有一个正在运行的Docker容器，容器ID是`abc123`，这个容器运行的是一个web服务器。

1. **docker exec**：如果我们想在这个正在运行的容器中执行一个新的命令，比如查看容器内部的文件列表，我们可以使用`docker exec`命令，如下：
   
   ```
   docker exec abc123 ls
   ```
   
   这条命令会在`abc123`容器内部执行`ls`命令，列出容器内的文件列表。我们也可以使用`docker exec`命令启动一个新的shell会话，如下：
   
   ```
   docker exec -it abc123 /bin/bash
   ```
   
   这条命令会在`abc123`容器内部启动一个新的bash shell会话，我们可以在这个会话中执行任何命令，就像在本地终端一样。
2. **docker attach**：如果我们想查看`abc123`容器的输出，我们可以使用`docker attach`命令，如下：
   
   ```
   docker attach abc123
   ```
   
   这条命令会连接到`abc123`容器的主进程，我们可以看到web服务器的输出，包括访问日志等。如果我们在终端中按下`Ctrl+C`，容器的主进程会收到`SIGINT`信号，可能会导致容器停止。
   这就是`docker exec`和`docker attach`的主要区别。简单来说，`docker exec`用于在容器中执行新的命令，而`docker attach`用于查看或交互容器的输出。

#### 从容器中把文件拷贝到本地

```shell
[root@9bb41cfca216 /]# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@9bb41cfca216 /]# cd home
[root@9bb41cfca216 home]# touch test.py
##容器内新建文件
[root@9bb41cfca216 home]# ls
test.py

C:\Users\YW>docker cp 9bb41cfca216:\home\test.py D:\ 
##centos容器内的文件拷贝到D盘目录下
Successfully copied 1.54kB to D:\


##拷贝是一个手动过程，后面的-v卷技术可以实现自动同步     
```

![](C:\Users\YW\AppData\Roaming\marktext\images\2024-04-25-20-04-02-image.png)

### Summary

```shell
C:\Users\YW>多敲！
```
