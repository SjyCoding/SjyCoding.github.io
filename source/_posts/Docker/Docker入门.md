---
title: Docker入门
date: 2020-12-03 10:35:19 +0800
updated:

categories: 
- [Docker]
tags: 
- Docker

---





## Docker概述

> 来源：维基百科，自由的百科全书

| ![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Docker_%28container_engine%29_logo.svg/250px-Docker_%28container_engine%29_logo.svg.png) |                                                              |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|       [原作者](https://zh.wikipedia.org/wiki/软件设计)       |                        Solomon Hykes                         |
|       [开发者](https://zh.wikipedia.org/wiki/軟件開發)       |                         Docker, Inc.                         |
|                           初始版本                           |                        2013年3月13日                         |
|  [源代码库](https://zh.wikipedia.org/wiki/仓库_(版本控制))   | [github.com/docker/docker-ce](https://github.com/docker/docker-ce)[![编辑维基数据链接](.static/Docker%E6%A6%82%E8%BF%B0-img/10px-OOjs_UI_icon_edit-ltr-progressive.svg.png)](https://www.wikidata.org/wiki/Q15206305#P1324) |
|      [编程语言](https://zh.wikipedia.org/wiki/编程语言)      |            [Go](https://zh.wikipedia.org/wiki/Go)            |
|      [操作系统](https://zh.wikipedia.org/wiki/操作系统)      | [Linux](https://zh.wikipedia.org/wiki/Linux)、[Windows](https://zh.wikipedia.org/wiki/Windows)、[macOS](https://zh.wikipedia.org/wiki/MacOS) |
|      [系统平台](https://zh.wikipedia.org/wiki/系統平台)      | [x86-64](https://zh.wikipedia.org/wiki/X86-64)、[ARM](https://zh.wikipedia.org/wiki/ARM架構)、s390x、[ppc64le](https://zh.wikipedia.org/wiki/Ppc64) |
|                             类型                             | [操作系统层虚拟化](https://zh.wikipedia.org/wiki/作業系統層虛擬化) |
|     [许可协议](https://zh.wikipedia.org/wiki/软件许可证)     | **可执行档：**[免费增值](https://zh.wikipedia.org/wiki/免費增值)[软件即服务](https://zh.wikipedia.org/wiki/软件即服务) **源代码：**[Apache许可证](https://zh.wikipedia.org/wiki/Apache许可证) 2.0 |
|                             网站                             |          [www.docker.com](https://www.docker.com/)           |

**Docker** 是一个[开放源代码](https://zh.wikipedia.org/wiki/開放原始碼)[软件](https://zh.wikipedia.org/wiki/軟體)，是一个[开放平台](https://zh.wikipedia.org/wiki/開放平臺)，用于开发应用、交付（shipping）应用、运行应用。 Docker允许用户将基础设施（Infrastructure）中的应用单独分割出来，形成更小的颗粒（容器），从而提高交付软件地速度。[[1\]](https://zh.wikipedia.org/wiki/Docker#cite_note-1)

**Docker容器** 与虚拟机类似，但原理上，容器是将[操作系统层虚拟化](https://zh.wikipedia.org/wiki/作業系統層虛擬化)，虚拟机则是虚拟化硬件，因此容器更具有便携性、高效地利用服务器。 容器更多的用于表示 软件的一个标准化单元。由于容器的标准化，因此它可以无视基础设施（Infrastructure）的差异，部署到任何一个地方。另外，Docker也为容器提供更强的业界的隔离兼容。[[2\]](https://zh.wikipedia.org/wiki/Docker#cite_note-2)

**Docker** 利用[Linux核心](https://zh.wikipedia.org/wiki/Linux核心)中的资源分离机制，例如[cgroups](https://zh.wikipedia.org/wiki/Cgroups)，以及Linux核心[名字空间](https://zh.wikipedia.org/w/index.php?title=Linux命名空間&action=edit&redlink=1)（namespaces），来创建独立的[容器](https://zh.wikipedia.org/wiki/作業系統層虛擬化)（containers）。这可以在单一Linux实体下运作，避免引导一个[虚拟机](https://zh.wikipedia.org/wiki/虛擬機器)造成的额外负担[[3\]](https://zh.wikipedia.org/wiki/Docker#cite_note-3)。Linux核心对名字空间的支持完全隔离了工作环境中应用程序的视野，包括行程树、[网络](https://zh.wikipedia.org/wiki/计算机网络)、用户ID与挂载文件系统，而核心的cgroup提供资源隔离，包括[CPU](https://zh.wikipedia.org/wiki/CPU)、[存储器](https://zh.wikipedia.org/wiki/電腦記憶體)、block I/O与网络。从0.9版本起，Dockers在使用抽象虚拟是经由[libvirt](https://zh.wikipedia.org/wiki/Libvirt)的[LXC](https://zh.wikipedia.org/wiki/LXC)与systemd - nspawn提供界面的基础上，开始包括libcontainer库做为以自己的方式开始直接使用由Linux核心提供的虚拟化的设施，

依据行业分析公司“451研究”：“Dockers是有能力打包应用程序及其虚拟容器，可以在任何Linux服务器上运行的依赖性工具，这有助于实现灵活性和便携性，应用程序在任何地方都可以运行，无论是[公用云](https://zh.wikipedia.org/wiki/公用雲)、[私有云](https://zh.wikipedia.org/wiki/私有雲)、单机等。” [[4\]](https://zh.wikipedia.org/wiki/Docker#cite_note-4)。

## 安装Docker

### 通过安装脚本 - 推荐

- CentOS

    Docker 仅支持以下的 64 位 CentOS 版本：

    - CentOS 7
    - CentOS 8

    ```shell
    # 使用官方安装脚本安装
    curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
    # 使用国内 daocloud 一键安装命令
    curl -sSL https://get.daocloud.io/docker | sh
    ```


### 手动安装

TODO: 待更新

### 启动Docker

> 如果使用dockers的

```shell
systemctl start docker
```



## Docker常用命令

### 辅助命令

```shell
docker --version			# 版本信息
	= docker -v
docker info					# 详细信息
docker --help				# 帮助
```



### images 镜像命令

```shell
# 查看本机中所有镜像
docker images				# 列出本地所有镜像
	-a							# 列出所有镜像(包含中间映像层)
	-q							# 只显示镜像id

# 搜索镜像
docker search [options] 镜像名	# 去dockerhub上查询镜像
	-s 指定值						# 列出收场数不少于指定值的镜像
	--no-trunc					  # 显示完整镜像信息
	
# 从仓库下载镜像
docker pull 镜像名[:TAG|@DIGEST]	# 下载镜像

# 删除镜像
docker rmi 镜像名				# 删除镜像
	-f							# 强制删除
```



### Contrainer 容器命令

#### 基本命令(容器外操作)

```shell
# 运行容器
docker run 镜像名					# 镜像名新建并启动容器
	--name			# 别名 为容器起一个名字
	-d				# 启动守护式容器(在后台启动容器)
	-p				# 映射端口号:原始端口号
	
	例:
		
# 查看运行的容器
docker ps						# 列出所有正在运行的容器
	-a				# 正在运行的和历史运行过的容器
	-q				# 静默模式, 只显示容器id

# 停止|关闭|重启容器
docker start 容器名或id				# 开启容器
docker restart 容器名或id			# 重启容器
docker stop 容器名或id				# 停止容器
docker kill 容器名或id				# 关闭容器

# 删除容器
docker rm -f 容器名或id
	
	例	docker rm -f $(docker ps -aq)	# 删除所有容器

# 查看容器内进程
docker top 容器名或id				# 查看容器内进程

# 产看容器内部细节
docker inspect 容器id				# 产看容器内部细节

# 查看容器的运行日志
docker logs [options] 容器名或id	# 查看容器的运行日志
	-t				# 加入时间戳
	-f				# 跟随最新的日志打印
```

#### 进阶命令(容器内操作)

```shell
# 进入容器内部
docker exec [options] 容器id 容器内命令		# 进入容器内执行命令
	-i				# 以交互模式运行容器,通常与-t一起使用
	-t				# 分配一个伪终端

# 容器内安装软件
apt-get update
apt-get install 安装包名称

# 修改容器内文件

# 退出容器
exit		# 退出容器

# 将容器打包为性的镜像
docker commit -a="作者" -m="描述信息" 容器id 目标镜像名称:TAG

# 从容器中复制文件到宿主机目录中 
docker cp 容器id:容器内资源路径 宿主机目录路径		# 将容器内资源拷贝到宿主机上

# 容器目录与宿主机目录同步 (数据卷 必须在运行容器时进行设置)
docker run -it -v /宿主机目录:/容器目录:ro(只读) 镜像名
	注: 宿主机目录必须是绝对目录,宿主机目录会覆盖容器目录内容
	
    运行 docker inspect 容器id 检查json串里有没有如下内容, 有则证明挂载成功
    "Mounts":{
    	{
    		"Type":"bind",
    		"source":"宿主机目录",
    		"Destination":"容器目录",
    		"Mode":"",
    		"RW":true,
    		"Propagation":"rprivate",
    	}
    }

```

## Docker file

> ​	DockerFile可以认为是**Docker镜像的描述文件, 是由一系列的命令和参数构成的 '脚本' **
>
> ​	主要作用是**用来构建docker镜像的构建文件**

![](https://s3.ax1x.com/2020/12/03/DoxWHH.png)

### Dockerfile解析过程

![](https://s3.ax1x.com/2020/12/03/DozFrF.png)

### Dockerfile保留命令

| 保留字         |                             作用                             |
| -------------- | :----------------------------------------------------------: |
| **FROM**       |        当前镜像是基于哪个镜像的, 第一个指令必须是FROM        |
| **RUN**        |                 **构建镜像时需要运行的命令**                 |
| **MAINTAINER** |      镜像维护者的姓名和邮箱地址 (官方不再推荐使用 废弃)      |
| **WORKDIR**    |   指定咋创建容器后, 终端默认登录进来的工作目录, 一个落脚点   |
| **ENV**        |               用来在构建容器过程中设置环境变量               |
| **ADD**        | 将宿主机目录下的文件拷贝进镜像  且ADD命令会自动处理URL和解压tar包 |
| **COPY**       | 类似ADD  拷贝文件和目录到镜像中<br/>将从构建上下文目录中<原路径>的文件/目录复制到新的一层的镜像内的<目标路径>位置 |
| **VOLUME**     |             容器数据卷  用于数据保存和持久化操作             |
| **CMD**        | 指定一个容器启动时要运行的命令<br/>Dockerfile中可以有多个CMD命令, 但只有最后一个生效, CMD会被docker run之后的参数替换 |
| **ENTRYPOINT** | 指定一个容器启动时要运行的命令<br/>ENTRYPOINT的目的和CMD一样, 都是在指定容器启动程序及其参数 |

#### FROM

> ​	基于哪个镜像构建新的镜像, 在构建时会从dockerhub拉取base镜像, 必须作为Dockerfile的第一个指令出现

















