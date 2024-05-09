## Bug and question

**C:\Users\YW>docker images error during connect: this error may indicate that the docker daemon is not running: Get "http://%2F%2F.%2Fpipe%2Fdocker_engine/v1.24/images/json": open //./pipe/docker_engine: The system cannot find the file specified.**

>  没打开Docker for windows应用



**-t和/bin/bash都是打开一个终端，那么有区别吗？**

> 实际上，`-t` 和 `/bin/bash` 不同，它们的目的和行为是互补的，而不是相同的。
>
> `-t` 是 Docker 命令的一个选项，其目的是在你运行一种交互式的应用，例如 shell 时，为 Docker 容器分配一个伪终端（pseudo-TTY）。这意味着它仅仅创建了一个能够接收用户输入，并将输出返回给用户的环境。
>
> 而 `/bin/bash` 却是一个指向 Bash 的 shell 程序的路径。它被当做一个命令来运行，这个命令告诉 Docker 容器应该运行 bash shell 这一程序。
>
> 所以说，`-t` 在创建一个可以让程序与用户进行交互的环境，而 `/bin/bash` 则是在这个环境中实际运行的程序。没有 `-t` 选项，`/bin/bash` 还是可以运行，只是它运行在一个非交互的环境中，不能直接与用户进行交互。所以 `-t` 和 `/bin/bash` 是互补的：`-t` 提供了运行环境，`/bin/bash` 则是在这个环境中执行的程序。



**C:\Users\YW>docker rmi -f centos01**

 **Error response from daemon: No such image: centos01:latest**

>从错误信息来看，你试图移除的镜像 “centos01” 不存在。这是因为你的 `docker rmi` 命令没有指定一个完整的镜像名称。完整的镜像名称应该是 `<REPOSITORY>:<TAG>`的形式。
>
>在上述 `docker images` 命令的输出中，我们可以看到有一个 `centos01` 镜像，但它的 TAG 是 `1.0`，而不是默认的 `latest`

## 官网

[官方文档(doc-docker)](https://docs.docker.com/desktop/)

[dock-hub](https://hub.docker.com/)

## 书籍

[深入浅出Docker-奈吉尔·波尔顿-微信读书](https://weread.qq.com/web/reader/a6332ce0718b75f2a63b772k16732dc0161679091c5aeb1?)

# Docker Learning

- Docker Overview

- Docker Install

- Docker Command
  
  - images command
  
  - container command
  
  - operation command
  
  - ...

- Docker image

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

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-23-09-59-59-image.png)

名词概念：

**镜像(image):**
docker镜像就好比是一个模板,可以通过这个模板来创建容器服务,tomcat镜像===>run ==>tomcat01 容器(提供服务器)通过这个镜像可以创建多个容器(最终服务运行或者项目运行就是在容器中的)

**容器(container):**
Docker利用容器技术，独立运行一个或者一个组应用，通过镜像来创建的。
启动，停止，删除，基本命令!

目前可以把容器理解为是一个简易的linux系统。

它包含了运行一个应用程序所需的所有内容，包括应用程序本身、运行时环境、系统工具、系统库以及相关配置等。具体来说，容器内部通常包含以下内容：

1. **应用程序**：容器内部运行的主要应用程序或服务，例如 Web 服务器、数据库等。

2. **运行时环境**：包括操作系统和各种运行时库，用于支持应用程序的运行。

3. **系统工具**：常见的系统工具和命令行程序，用于管理和维护容器内部的环境，例如 Shell、文件操作工具等。

4. **系统库**：与应用程序相关的系统级库和依赖项，例如网络库、数据库驱动程序等。

5. **相关配置**：容器的配置文件、环境变量设置等，用于定义容器的运行时行为和参数。

以把Docker容器看作是一个轻量级的Linux环境，可以在其中执行各种Linux命令和操作，但它并不是一个完全独立的操作系统，所以可以start（启动容器），exec（进入容器）

**仓库(renository):**
仓库就是存放镜像的地方!
仓库分为公有仓库和私有仓库!
Docker Hub(默认是国外的)
阿里云...都有容器服务器(配置镜像加速!)

### The role of docker

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

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-23-14-12-38-image.png)

流程：

<img src="https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-23-14-13-38-image.png" title="" alt="" width="428">

### Underlying principle

**Docker是如何工作的？**

Docker 是一个 Client-Server 结构的系统，Docker的守护进程运行在主机上，通过Socket从客户端访问

> "守护进程" 是指 Docker 的后台进程，也称为 Docker 守护进程（Docker Daemon）。它是在主机上运行的一个长期运行的服务，负责管理和监控 Docker 容器的生命周期、镜像的存储和管理、网络和存储卷的配置等。守护进程是 Docker 系统的核心组件，它负责处理来自 Docker 客户端的请求，并相应地执行操作。因此，它充当了 Docker 系统与用户之间的接口，负责响应用户的命令并执行相应的操作，比如创建、运行、停止和删除容器等。

DockerServer 接收到 Docker-Client的指令，就会执行这个命令!

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-23-14-44-49-image.png)

### Aliyun image acceleration

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-25-10-12-05-image.png)

## Common commands for Docker

[Reference（帮助文档）](https://docs.docker.com/reference/)

### Help command

```shell
docker version #版本信息
docker info #系统信息，包括镜像和容器的数量        
docker #command --help
```

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

### Image command

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

> 在 Docker 中，镜像可以被标签，以便于识别和管理。每个 Docker 镜像至少有一个标签，这个标签可以在创建镜像的时候进行分配。如果你某次创建镜像的时候没有为镜像定义标签，Docker 会自动为其分配一个 `latest` 标签。
>
> 标签 `<TAG>` 是一种自由形式的文本标签，用于给镜像分配一个可读的名字。标签通常用于指定镜像的版本，如 `1.0`、`2.1` 等等。你也可以使用任何你想要的词语作为标签，如 `stable`、`latest`、`experimental` 等等。
>
> 完整的 Docker 镜像名称是由三部分组成的：`仓库名/repository`、`镜像名/image name` 和 `标签/tag`，以 `:` 分隔，如：`repository/imagename:tag`。例如 `ubuntu:20.04`，在这个名称中，`ubuntu` 是仓库名，`20.04` 是标签，这个标签表示的是 Ubuntu 20.04 版本的镜像。

##### docker search  搜索镜像

```shell
C:\Users\YW>docker search mysql
NAME                            DESCRIPTION                                      STARS     OFFICIAL
mysql                           MySQL is a widely used, open-source relation…   15008     [OK]
mariadb                         MariaDB Server is a high performing open sou…   5722      [OK]
percona                         Percona Server is a fork of the MySQL relati…   627       [OK]
phpmyadmin                      phpMyAdmin - A web interface for MySQL and M…   966       [OK]
```

##### docker pull 拉取镜像

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

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-25-10-30-27-image.png)

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
#-t参数的全称是--tty，意思是为容器分配一个伪终端（pseudo-TTY）
#可以在容器中看到一个命令行界面，就像在一个真正的终端中一样
-p                  指定容器端口
    -p 主机端口：容器端口
    -p 容器端口
    -p ip：主机端口：容器端口
#example
C:\Users\YW>docker run -it centos
[root@f7103d6e4c69 /]#  ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@f7103d6e4c69 /]# mkdir YW
[root@f7103d6e4c69 /]# ls
YW  bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@f7103d6e4c69 /]# exit
exitr
```

> 实战：运行docker python:alpine

```shell
# 直接运行Python解释器
C:\Users\YW>docker run -it python:alpine
Python 3.10.1 (main, Dec  8 2021, 04:32:13) [GCC 10.3.1 20211027] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("hello world")
hello world

# 查看python的配置文件
C:\Users\YW>docker run -it python:alpine /bin/sh
/ # cd usr/local/bin
/usr/local/bin # ls
2to3               idle3              pip3               pydoc3             python-config      python3.10
2to3-3.10          idle3.10           pip3.10            pydoc3.10          python3            python3.10-config
idle               pip                pydoc              python             python3-config     wheel
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
# 命令 docker run -d(--detach) container
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

![image-20200617210554147](https://raw.githubusercontent.com/113737038537/Pic/main/image-20200617210554147.png)

![image-20200617210932306](https://raw.githubusercontent.com/113737038537/Pic/main/image-20200617210932306.png)

![image-20200617211021003](https://raw.githubusercontent.com/113737038537/Pic/main/image-20200617211021003.png)

![image-20200617211039508](https://raw.githubusercontent.com/113737038537/Pic/main/image-20200617211039508.png)

### Practice

> Docker 安装 Nginx

```shell
#1、搜索镜像 search
#2、下载镜像 pull
#3、运行镜像

C:\Users\YW>docker run -d --name nginx01 -p 8080:80 nginx
ca78eafe9626d716728af4239e608ea77aa7e72a99e38c1548f6b530fdea0b31
#-d 后台运行
#--name 起名
#-p 主机端口,容器端口

C:\Users\YW>docker ps
CONTAINER ID   IMAGE     COMMAND                   CREATED         STATUS         PORTS                  NAMES
ca78eafe9626   nginx     "/docker-entrypoint.…"   7 seconds ago   Up 6 seconds   0.0.0.0:8080->80/tcp   nginx01

#进入容器
C:\Users\YW>docker exec -it nginx01 /bin/bash
root@ca78eafe9626:/# whereis nginx
nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
root@ca78eafe9626:/#
```

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-26-09-32-46-image.png)

* 端口暴露：通过外网访问容器服务，这里例子是3344

![](https://raw.githubusercontent.com/113737038537/Pic/main/2024-04-26-15-15-19-image.png)

思考问题:我们每次改动nginx配置文件，都需要进入容器内部?十分的麻烦，我要是可以在容器外部提供一个映射路径，达到在容器修改文件名，容器内部就可以自动修改?- 数据卷!

> Docker安装tomcat

```shell
1、#官方的使用
docker run -it --rm tomcat:9.0
#我们之前的启动都是后台，停止了容器之后，容器还是可以查到
#--rm，一般用来测试，用完就删除
2、# 下载再启动
docker pull tomcat
# 启动运行
docker run -d -p 3355:8080 --name tomcat0l tomcat
# 测试访问没有问题
# 进入容器
[root@kuanashen homel# docker exec -it tomcat01 /bin/bash
# 发现问题，1、1inux命令少了，2。没有webapps。 阿里云像的原因。默认是最小的像，所有不必要的都剔除掉。
# 保证最小可运行的环境!
```

## Docker 镜像讲解

> 镜像是一种轻量级、可执行的独立软件保，用来打包软件运行环境和基于运行环境开发的软件，他包含运行某
> 个软件所需的所有内容，包括**代码、运行时库、环境变量和配置文件**。
> 将所有的应用和环境，直接打包为docker镜像，就可以直接运行。

### 联合文件系统

> 我们下载的时候看到一层层的下载就是这个。
> UnionFs（联合文件系统）：Union文件系统（UnionFs）是一种分层、轻量级并且高性能的文件系统，他支
> 持对文件系统的修改作为一次提交来一层层的叠加，同时可以将不同目录挂载到同一个虚拟文件系统下（
> unite several directories into a single virtual filesystem)。Union文件系统是Docker镜像的基础。镜像可以通过分层来进行继承，基于基础镜像（没有父镜像），可以制作各种具体的应用镜像。
> **特性**：一次同时加载多个文件系统，但从外面看起来，只能看到一个文件系统，联合加载会把各层文件系
> 统叠加起来，这样最终的文件系统会包含所有底层的文件和目录。

![image-20240429164806063](https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429164806063.png)

### Linux基础知识

- `bootfs` 是引导文件系统（Boot Filesystem）。在系统启动过程中，`bootfs` 主要包含 Linux 内核（Kernel）和 bootloader。而 bootloader 是加载内核的小程序，存在于启动分区。当引导过程完成，即内核加载并初始化完毕后，`bootfs` 就会被卸载。
- `rootfs` 是根文件系统(Root File System)。主要包含操作系统在运行过程中需要的各种文件，所以其内容会根据具体的 Linux 发行版而有所差异。一般而言，`rootfs` 包含了 `/dev`, `/proc`, `/bin`, `/etc`, `/lib`, `/usr` 等目录和文件。



>  平时我们安装进虚拟机的CentOs都是好几个G，为什么Docker中才200M?
>
> 对于一个精简的0s，rootfs 可以很小，只需要包含最基本的命令，工具和程序库就可以了,因为底层直接用Host的kernel，自己只需要提供rootfs就可以了。由此可见对于不同的linux发行版,bootfs基本是一致的,roots会有差别,因此不同的发行版可以公用bootfs.

### 分层理解

> 思考:为什么Docker镜像要采用这种分层的结构呢?
> 最大的好处-资源共享了，比如有多个镜像都从相同的Base镜像构建而来，那么宿主机只需在磁盘上保留一份base镜像，同时内存中也只需要加载一份base镜像，这样就可以为所有的容器服务了，而且镜像的每一层都可以被共享。

* 特点

Docker镜像都是只读的，当容器启动时，一个新的可写层被加载到镜像的顶部!
这一层就是我们通常说的容器层，容器之下的都叫镜像层!

<img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429171240817.png" alt="image-20240429171240817" style="zoom:67%;" />

### Commit镜像

```shell
docker commit 提交容器成为一个新的副本
#类似于Git
docker commit -m="描述信息" -a="author" container_id tagert_image:[Tag]

#在centos中添加test.py后提交镜像
C:\Users\YW>docker commit -a="YW" -m="add test.py" 0c8da8340965 centos01:1.0
sha256:3a46df3e4be5539492aa35ffc8e886828a912f2a510bbf44723c94c05dd55c7b

C:\Users\YW>docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
centos01      1.0       3a46df3e4be5   7 seconds ago   231MB

```

>  到此，入门Docker

## 容器数据卷

> 如果数据都在容器中，那么我们容器删除，数据就会丢失! 需求:数据可以持久化MySQL，容器删了，删库跑路!需求:MySQL数据可以存储在本地容器之间可以有一个数据共享的技术!Docker 容器中产生的数据，同步到本地!这就是卷技术!目录的挂载，将我们容器内的目录，挂载到Linux上面!

<img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429174049319.png" alt="image-20240429174049319" style="zoom: 50%;" />

**总结一句话：容器的持久化和同步操作**

### 使用数据卷

> #方式一：直接使用命令挂载
>
> 容器数据卷的挂载，简单来说，就是将宿主机的某个文件系统目录（例如：/host/path）或一个已创建的数据卷，连接（Mount）到运行中的 Docker 容器内的一个指定路径（例如：/container/path）上。这样，容器内的这个路径下的所有数据就实际存储在宿主机的文件系统或者数据卷中，而不是在容器自己的文件系统中。
>
> 挂载的主要作用：
>
> 1. 数据持久化：在容器删除后，宿主机的文件系统或数据卷中的数据还可以存在。新的容器可以再次挂载这个文件路径或者数据卷，从而可以继续使用之前的数据。
> 2. 数据共享与通信：在不同的容器之间，都可以挂载同一个宿主机路径或者数据卷，实现数据的共享和通信。
>
> 挂载的操作方式：
>
> 使用 `docker run` 命令的 `-v` 或 `--mount` 参数，例如：
>
> plaintext
>
> ```plaintext
> docker run -v /host/path:/container/path -d container_name
> ```
>
> 这行命令将宿主机的 `/host/path` 目录挂载到容器的 `/container/path` 目录下。此后，在 `/container/path` 中创建的任何文件都会在宿主机的 `/host/path` 中同步创建，反之亦然。
>
> 同样，也可以替换 `-v` 为 `--mount` 参数，例如：
>
> plaintext
>
> ```plaintext
> docker run --mount type=bind,source=/host/path,target=/container/path -d container_name
> ```
>
> 这行命令与前一条命令的效果是一样的，区别在于 `--mount` 的语法更加清晰和灵活。
>
> 这就是 "挂载" 在容器数据卷中的含义和作用。

```shell
#docker run -it -v host_dir:container_dir container

C:\Users\YW>docker run -it -v D:\:/home centos /bin/bash

#docker inspect container_id 查看挂载详情
```

![image-20240430083621327](https://raw.githubusercontent.com/113737038537/Pic/main/image-20240430083621327.png)

> 挂载后内容同步

![image-20240430083845842](https://raw.githubusercontent.com/113737038537/Pic/main/image-20240430083845842.png)

### 实战：安装MySQL



### 具名和匿名挂载

``` shell
# 都使用的默认挂载点
# 匿名挂载
-v 容器内挂载
C:\Users\YW>docker run -d --name centos1 -v /home centos
#docker volumn list 查看数据卷挂载情况
C:\Users\YW>docker volume list
DRIVER    VOLUME NAME
local     3aef75f657ac8370c3bbdffa3ef1ea583c2274c8e617840818d111a993d50acb
local     29392ac1934b9c58aca26102568ecf99022ee09085b69ef382263925c4727b04
local     e3f4ea1cb0b035c338d541fd1d3b2af96b2cc4f5a1d65c4717c4d402871260f2
local     e94c96ebb1496e9136be7a4b959aff4d23c331d31f02396c49408a82d1183d1b
#具名挂载（注意和指定路径挂载的区别）
C:\Users\YW>docker run -d --name centos2 -v juming:/home centos
fc8b876960cb659bd6aa017386b5c2560e0a02e04b177db3d6b27656f3dcfd5c

C:\Users\YW>docker volume list
DRIVER    VOLUME NAME
local     3aef75f657ac8370c3bbdffa3ef1ea583c2274c8e617840818d111a993d50acb
local     29392ac1934b9c58aca26102568ecf99022ee09085b69ef382263925c4727b04
local     e3f4ea1cb0b035c338d541fd1d3b2af96b2cc4f5a1d65c4717c4d402871260f2
local     e94c96ebb1496e9136be7a4b959aff4d23c331d31f02396c49408a82d1183d1b
local     juming
```



## DockerFile

### DockerFile 介绍

Docker images和container都是使用别人的东西

Dockerfile 是用来构建dokcer镜像的命令参数脚本，创建自己的东西

构建步骤：

> 1. 编写一个 dockerfile 文件
> 2. docker build 构建成为一个镜像
> 3. docker run 运行镜像
> 4. docker push 发布镜像(DockerHub、阿里云镜像仓库)

**简单实例：**

```shell
#Docker.txt 
FROM centos
VOLUME ["volume1","volume2"]
cmd /bin/bash

#CMD
C:\Users\YW>docker build -f D:\Study\Docker\Code\dockerfile.txt -t yw_centos D:\Study\Docker\Code
[+] Building 0.2s (5/5) FINISHED                                                                         docker:default
 => [internal] load build definition from dockerfile.txt                                                           0.0s
 => => transferring dockerfile: 97B                                                                                0.0s
 => [internal] load metadata for docker.io/library/centos:latest                                                   0.0s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/1] FROM docker.io/library/centos:latest                                                                     0.0s
 => exporting to image                                                                                             0.0s
 => => exporting layers                                                                                            0.0s
 => => writing image sha256:99b6b862f5717393ee5bda3f1f6f86a15bc9d277092e1d488b8e3f68e16c23f9                       0.0s
 => => naming to docker.io/library/yw_centos                                                                       0.0s

View build details: docker-desktop://dashboard/build/default/default/pqmvtalq3ub6z8ijspvb41afo

```

### DockerFile构建过程

**基础知识**

1. 每个关键字必须是大写字母
2. 执行从上到下顺序运行
3. #表示注释
4. 每一条指令都会创建提交一个新的镜像层

### DockerFile指令

```shell
FROM            # 基础镜像，一切从这里开始构建
MAINTAINER      # 镜像是谁写的，姓名+邮箱
RUN             # 镜像构建的时候需要运行的命令
ADD/copy        # 添加文件或目录到镜像中
WORKDIR         # 镜像的工作目录
VOLUME          # 挂载的目录
EXPOSE          # 指明该镜像要暴露的端口
CMD             # 指定这个容器启动的时候要运行的命令,只有最后一个会生效，可被替代
ENTRYPOINT      # 指定这个容器启动的时候要运行的命令,可以追加命令
ONBUILD         # 当构建一个被继承 DockerFi1e 这个时候就会运行 ONBUILD 的指令，触发指令
ENV             # 构建的时候设置环境变量!
```

### 实战

Docker Hub 中99%镜像都是FROM scratch，然后配置需要的软件和配置来进行构建

> 创建自己的ubuntu

```shell
# 1.编写dockerfile文件
FROM ubuntu
MAINTAINER YW<1137038537@qq.com>

ENV MYPATH /usr/local #配置环境变量
WORKDIR $MYPATH

RUN apt-get update
RUN apt-get -y install vim # -y 参数用于自动确认所有的提示
RUN apt-get -y install net-tools


EXPOSE 80

CMD echo $MYPATH
CMD /bin/bash

# 2.通过这个文件构建镜像myubuntu
PS D:\Study\Docker\Code> docker build -f .\my_ubuntu.txt -t myubuntu:0.1 .
[+] Building 52.4s (9/9) FINISHED                                                                        docker:default
 => [internal] load build definition from my_ubuntu.txt                                                            0.0s
 => => transferring dockerfile: 263B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                   0.0s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/5] FROM docker.io/library/ubuntu:latest                                                                     0.0s
 => CACHED [2/5] WORKDIR /usr/local                                                                                0.0s
 => CACHED [3/5] RUN apt-get update                                                                                0.0s
 => [4/5] RUN apt-get -y install vim                                                                 49.4s
 => [5/5] RUN apt-get -y install net-tools                                                                         2.7s
 => exporting to image                                                                                             0.3s
 => => exporting layers                                                                                            0.3s
 => => writing image sha256:ae96c0df1e764e6ae4945bc55ed277c523836d7d4a92845ed588d85942108e3b                       0.0s
 => => naming to docker.io/library/myubuntu:0.1                                                                    0.0s

PS D:\Study\Docker\Code> docker images
REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
myubuntu      0.1       ae96c0df1e76   35 seconds ago   193MB

# 3.测试运行
PS D:\Study\Docker\Code> docker run -it myubuntu:0.1
root@71035fb7c3e2:/usr/local# ls
bin  etc  games  include  lib  man  sbin  share  src
root@71035fb7c3e2:/usr/local# vim test.py
root@71035fb7c3e2:/usr/local# cat test.py
print("hello world")

# 4.查看构建历史
PS D:\Study\Docker\Code> docker history ae96c0df1e76
IMAGE          CREATED          CREATED BY                                       SIZE      COMMENT
ae96c0df1e76   8 minutes ago    CMD ["/bin/sh" "-c" "/bin/bash"]                 0B        buildkit.dockerfile.v0
<missing>      8 minutes ago    CMD ["/bin/sh" "-c" "echo $MYPATH"]              0B        buildkit.dockerfile.v0
<missing>      8 minutes ago    EXPOSE map[80/tcp:{}]                            0B        buildkit.dockerfile.v0
<missing>      8 minutes ago    RUN /bin/sh -c apt-get -y install net-tools …   1.52MB    buildkit.dockerfile.v0
<missing>      8 minutes ago    RUN /bin/sh -c apt-get -y install vim # buil…   68.2MB    buildkit.dockerfile.v0
<missing>      9 minutes ago    RUN /bin/sh -c apt-get update # buildkit         50.7MB    buildkit.dockerfile.v0
<missing>      12 minutes ago   WORKDIR /usr/local                               0B        buildkit.dockerfile.v0
<missing>      12 minutes ago   ENV MYPATH=/usr/local                            0B        buildkit.dockerfile.v0
<missing>      12 minutes ago   MAINTAINER YW<1137038537@qq.com>                 0B        buildkit.dockerfile.v0
<missing>      2 years ago      /bin/sh -c #(nop)  CMD ["bash"]                  0B
<missing>      2 years ago      /bin/sh -c #(nop) ADD file:5d68d27cc15a80653…   72.8MB
```

### 补充说明

```shell
最后的.
```

> `.` 代表的是当前目录，这一命令就是在当前目录下寻找 Dockerfile 并根据 Dockerfile 来构建 Docker 镜像。
>
> 如果你不在当前目录下运行这个命令，或者想要在别的目录下寻找 Dockerfile，你可以将这个 `.` 替换成你需要的目录路径。例如，如果你的 Dockerfile 在 `/home/myUser/myDockerFiles/` 目录下，那你就可以这样执行命令：`docker build -f /home/myUser/myDockerFiles/my_ubuntu.txt -t myubuntu:0.1 /home/myUser/myDockerFiles/`。

```shell
CMD /bin/bash
```

> 在这种格式中，`/bin/bash` 就是你希望在 Docker 容器启动时执行的命令。
>
> shell 格式的 `CMD` 指令会被 `/bin/sh -c` 包裹，所以 `CMD /bin/bash` 实际上会被执行为 `/bin/sh -c "/bin/bash"`。
>
> 在这个命令中，`/bin/sh` 是一个常见的 Unix shell，`-c` 是其后接受一个可以直接在 shell 中执行的命令字符串的选项。`"/bin/bash"` 则是 `sh` 需要执行的命令。
>
> 所以，`/bin/sh -c "/bin/bash"` 命令的含义就是使用 `sh` 来执行 `/bin/bash` 这个命令。这个命令最终的结果就是启动一个新的 bash shell。

```
 CMD 和 RUN 的区别
```

> 在 Dockerfile 文件中，`RUN` 和 `CMD` 是两个的指令，它们的作用和使用的场景有所区别：
>
> 1. ```shell
>    RUN
>    ```
>
>    指令：
>
>    - `RUN` 用于在构建 Docker 镜像的过程中运行指定的命令。
>    - 这些命令通常是用来设置环境，或者是安装应用所需要的依赖。
>    - `RUN` 执行的结果将会生成一个新的 Docker 层，这个层将会被包含在最终的 Docker 镜像中。
>    - 一个 Dockerfile 文件可以包含多个 `RUN` 指令。
>
> 例如：
>
> Dockerfile
>
> ```Dockerfile
> RUN apt-get update
> RUN apt-get install -y git
> ```
>
> 1. ```
>    CMD
>    ```
>
>    指令：
>
>    - `CMD` 用来提供默认的执行命令，这个命令将会在 Docker 容器启动时运行。
>    - 如果用户在 `docker run` 命令后面提供了额外的参数，那么 `CMD` 的命令将会被覆盖。
>    - 一个 Dockerfile 文件只能有一个有效的 `CMD`，如果有多个 `CMD` 指令，那么只有最后一个 `CMD` 会生效。
>
> 例如：
>
> Dockerfile
>
> ```Dockerfile
> CMD ["echo", "Hello, Docker!"]
> ```
>
> 总的来说，`RUN` 用于构建镜像时运行命令，用来设置环境和装好应用依赖，而 `CMD` 是为了设置容器启动后的默认行为。

```shell
CMD 的两种代码格式
```

> Dockerfile 的 `CMD` 指令有两种格式，分别是：
>
> 1. shell 格式：`CMD command param1 param2`
> 2. exec 格式：`CMD ["executable", "param1", "param2"]`
>
> 在 `CMD ["echo", "Hello, Docker!"]` 这一命令中，我们使用了 exec 格式。这种格式被称为 JSON 数组格式，由于我们在编写 Dockerfile 时经常需要指定参数，这就需要用到 exec 格式。
>
> 使用 exec 格式的好处是：
>
> - Docker 会直接将第一个参数作为可执行文件，后面的参数作为这个可执行文件的参数。这样就不需要通过 shell 来解释 entire command，可以避免一些由 shell 引起的问题。
> - 这种格式的指令可执行文件的参数清晰明了，更加友好。
>
> 所以我们通常在 Dockerfile 文件中使用 exec 格式的 `CMD` 指令。当然，shell 格式的 `CMD` 也是可以使用的。例如，`CMD echo "Hello, Docker!"` 和 `CMD ["echo", "Hello, Docker!"]` 的执行结果是相同的。

```shell
CMD 和 ENTRYPOINT 的区别
```

```shell
CMD          # 指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代
ENTRYPOINT   # 指定这个容器启动的时候要运行的命令，可以追加命令
```

### 发布自己的镜像

> Dockerhub

1. [dock-hub](https://hub.docker.com/) 登录自己的账号
2. 服务器上提交自己的镜像
3. 在服务器上登录 `docker login`
4. 登录后提交镜像 `docker push`

```shell
C:\Users\YW>docker push yishengjun/myubuntu:0.1
The push refers to repository [docker.io/yishengjun/myubuntu]
An image does not exist locally with the tag: yishengjun/myubuntu

# 解决方法，添加一个标签

C:\Users\YW> docker tag myubuntu:0.1 yishengjun/myubuntu:0.1

C:\Users\YW>docker push yishengjun/myubuntu:0.1
The push refers to repository [docker.io/yishengjun/myubuntu]
4fd258d565c2: Pushed
b297e69d90ce: Pushed
eb8387891846: Pushed
5f70bf18a086: Pushed
9f54eef41275: Pushed
```

> 当你使用 Docker 创建一个镜像，你可以给这个镜像添加一个或者多个标签（tag）。标签是一个自由形式的字符串，通常用来添加版本信息，比如 "3.1" 或 "latest"。
>
> 在 Docker 中，镜像的名字由两部分组成，分别是 "repository" 和 "tag"。全名的形式如下：
>
> plaintext
>
> ```plaintext
> <repository>:<tag>
> ```
>
> "repository" 通常是 Docker Hub 用户名，后面跟着一个斜线和镜像的名字。"tag" 是镜像的版本标签。
>
> 在你的示例中，你尝试推送的是 "yishengjun/myubuntu:0.1" 这个镜像，这个名字的含义是，位于 Docker Hub 上用户名为 "yishengjun"，镜像名为 "myubuntu" 的版本为 "0.1" 的镜像。然而当 Docker 在本地查找这个镜像名时，并没有找到对应的项，所以会报错。
>
> 要解决这个问题，你需要使用 `docker tag` 命令为你的 "myubuntu:0.1" 镜像添加一个新标签 "yishengjun/myubuntu:0.1"。执行命令后，两个标签都会指向同一镜像，此时你可以用新标签将镜像推送到 Docker Hub。



## Docker网络







