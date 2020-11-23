---
title: 基于Hexo Github搭建个人博客一：将博客推到Github Page
date: 2020-11-06 16:41:21
updated:

categories: 
- Hexo搭建博客 
tags: 
- hexo
- volantis
---


## 前言
> 本文所有内容来自于[Johnny](https://blog.csdn.net/weixin_44855907/article/details/105312948), 略有修改

## 什么是hexo
打开Hexo你会发现醒目的一行字：“Hexo is a fast, simple & powerful blog framework”。其实说白了hexo就是个博客框架。

## 安装hexo
### 前期准备
- 安装好 Nodejs
- 安装好 Git

- 以及注册一个Github账号

官网下载的Node.js安装包自带npm节点包管理工具，npm从其nmp官网下载对应的插件包到本地，因为该网站的服务器在国外，经常会出现下载缓慢或出现异常，这时便需要找到另外的方法提供稳定的下载。这个方法就是cnpm。阿里巴巴的淘宝团队把nmp官网的插件都同步到了在中国的服务器，提供给我们从这个服务器上稳定下载资源。简单来说就是为了防止因为下载速度过慢而导致失败，我们还要与预先处理一下。

### 预处理
解决上述问题有如下两个方法，我选择的是方法一：

#### 方法一、通过npm下载cnpm
命令

```shell
npm install -g cnpm --registry=https://registry.npm.taobao.org
# 其中-g是全局的意思
```

[![BhP5ct.jpg](https://s1.ax1x.com/2020/11/06/BhP5ct.jpg)](https://imgchr.com/i/BhP5ct)


检验cnpm有没有安装成功

```shell
cnpm
```

[![BhilUe.jpg](https://s1.ax1x.com/2020/11/06/BhilUe.jpg)](https://imgchr.com/i/BhilUe)

```shell
#或者
cnpm -v
```


#### 方法二、修改npm的默认镜像源

1）查询当前的npm的源，“http://registry.npmjs.org”为默认的官方源。

```shell
npm config get registry
```

2） 设置npm的淘宝镜像源，“https://registry.npm.taobao.org”为淘宝的镜像源。

```shell
npm config set registry https://registry.npm.taobao.org
# 通过这条set命令就可以把npm的镜像源改为国内淘宝的
```

### 正式安装hexo

由于我预处理是用的方法一 所以我用cnpm cnpm和npm是一样的 相当于双胞胎 用方法二的伙伴把cnpm改为npm就可以了 其他照旧

```shell
cnpm install -g hexo-cli
```

[![BhEbfe.jpg](https://s1.ax1x.com/2020/11/06/BhEbfe.jpg)](https://imgchr.com/i/BhEbfe)
验证hexo是否安装成功

```shell
hexo -v
```

[![BhVEXn.jpg](https://s1.ax1x.com/2020/11/06/BhVEXn.jpg)](https://imgchr.com/i/BhVEXn)
安装成功后进入对Hexo的初始配置

## Hexo初始配置

1. 新建文件夹：我这里在E:/hexo下新建文件夹blog
2. cmd下进入blog所在目录下 hexo init 初始化文件夹blog

```shell
hexo init
```

[![BhV6Bt.jpg](https://s1.ax1x.com/2020/11/06/BhV6Bt.jpg)](https://imgchr.com/i/BhV6Bt)

初始化成功后，得到如下文件

[![BhVLNT.jpg](https://s1.ax1x.com/2020/11/06/BhVLNT.jpg)](https://imgchr.com/i/BhVLNT)

这里对各个文件夹进行一个简单的说明，毕竟后面有些会用到

```shell
- node_modules：是依赖包
- public：存放的是生成的页面
- scaffolds：命令生成文章等的模板
- source：用命令创建的各种文章
- themes：主题
- _config.yml：整个博客的配置
- db.json：source解析所得到的
- package.json：项目所需模块项目的配置信息
```

## 安装deployer

```shell
#安装能够将hexo部署到git page的deployer
cnpm install hexo-deployer-git --save
```

[![BhZRq1.jpg](https://s1.ax1x.com/2020/11/06/BhZRq1.jpg)](https://imgchr.com/i/BhZRq1)


## 本地查看效果

```shell
常见hexo命令
1）generate

hexo generate

功能：生成静态文件。
参数描述
-d, --deploy 文件生成后立即部署网站
-w, --watch 监视文件变动
2）deploy

hexo deploy

功能：部署网站。
参数描述
-g, --generate 部署网站前，需要预先生成静态文件

3)server

hexo server

功能：启动服务器。
参数描述
-p, --port 重设端口
-s, --static 只使用静态文件
-l, --log 启动日记记录，或覆盖记录格式
```

```shell
#hexo默认会有个Hello-World的博客文件
hexo g
hexo s
```

[![BhZvIf.jpg](https://s1.ax1x.com/2020/11/06/BhZvIf.jpg)](https://imgchr.com/i/BhZvIf)

地址栏 输入：http://localhost:400就可以在本地看到Hello Word文章

[![BhePMj.jpg](https://s1.ax1x.com/2020/11/06/BhePMj.jpg)](https://imgchr.com/i/BhePMj)

上面只是在本地发布成功，要想让更多人看到，需要发布到远程服务器，这里部署到GitHUb

## 部署博客到Github

1）首先自己创建一个Github账户。
2）创建一个仓库

```shell
命名规范: 用户名.github.io
```

 3）配置SSH密钥
只有配置好 SSH 密钥后，我们才可以通过 git 操作实现本地代码库与 Github 代码库同步

```shell
在E:\hexo\blog目录下右键 bash here进入git窗口
ssh-keygen -t -C "你GitHub的邮箱"
两次密码直接回车
clip <~/ssh/id_sra.pub
```

[![BheDeI.jpg](https://s1.ax1x.com/2020/11/06/BheDeI.jpg)](https://imgchr.com/i/BheDeI)

[![BhecY8.jpg](https://s1.ax1x.com/2020/11/06/BhecY8.jpg)](https://imgchr.com/i/BhecY8)

在GitHub个人账号中进入setting选择SSH and GPG keys添加从bash生成的密钥

[![Bhe5mn.jpg](https://s1.ax1x.com/2020/11/06/Bhe5mn.jpg)](https://imgchr.com/i/Bhe5mn)

[![BheX6J.jpg](https://s1.ax1x.com/2020/11/06/BheX6J.jpg)](https://imgchr.com/i/BheX6J)

测试
在E:\hexo\blog目录下右键 bash here进入git窗口

输入如下命令

[![Bhm8Xj.jpg](https://s1.ax1x.com/2020/11/06/Bhm8Xj.jpg)](https://imgchr.com/i/Bhm8Xj)

提示如下

[![Bhmt7q.jpg](https://s1.ax1x.com/2020/11/06/Bhmt7q.jpg)](https://imgchr.com/i/Bhmt7q)

输入yes后显示如下，则表示Github的SSH设置正确

[![Bhm6BR.jpg](https://s1.ax1x.com/2020/11/06/Bhm6BR.jpg)](https://imgchr.com/i/Bhm6BR)

配置_config.yml

1. 获得SSH
    [![Bhmh9O.jpg](https://s1.ax1x.com/2020/11/06/Bhmh9O.jpg)](https://imgchr.com/i/Bhmh9O)

2. 配置_config.yml
    在E:/hexo/blog目录下找到_config.yml配置文件 用notepad++或者vscode打开修改
    [![BhnyRS.jpg](https://s1.ax1x.com/2020/11/06/BhnyRS.jpg)](https://imgchr.com/i/BhnyRS)

    找到deploy结点，编辑如下：
    repo为刚刚从GitHub复制来的SSH 粘贴即可
    [![Bhn2rj.jpg](https://s1.ax1x.com/2020/11/06/Bhn2rj.jpg)](https://imgchr.com/i/Bhn2rj)

## 配置 Git 个人信息

Git 会根据用户的名字和邮箱来记录提交，GitHub 也是用这些信息来做权限的处理，输入以下命令进行个人信息的设置，把名称和邮箱替换成你自己的，名字可以不是 GitHub 的昵称，但为了方便记忆，建议与 GitHub 一致

cmd下使用下面两条命令

```shell
git config --global user.email "邮箱"
git config --global user.name "用户名"
```


到这里为止 git 操作实现本地代码库与 Github 代码库同步

## 部署到远端Github

```shell
hexo g -d
```

生成静态网页并把它部署到远端
[![Bhnjd1.jpg](https://s1.ax1x.com/2020/11/06/Bhnjd1.jpg)](https://imgchr.com/i/Bhnjd1)
输入：https://你的仓库名 就可以访问到了在这里插入图片描述
一切都布置好了，只差一杯咖啡，接下来就可以开工慢慢写文章啦
3、博客编写（简单一提）

我们会发现发布成功的博客文章放在_posts目录下
在这里插入图片描述
那么可以使用支持 .md编辑提供Markdown 语法编辑的的编辑器，然后保存文件到 …\source_posts 文件夹下即可，用CSDN自带的Markdown编辑器和小书匠都可以。这里用前者。

1）Markdown编辑器编辑博客，将生成的.md文件复制到 ..\source\_posts
2）然后再hexo g -d 部署到远端GitHub就可以了

## 结束语

文章到这里就结束了，我自己搭建过程中还是有碰到不少坑的，所幸网上用Hexo搭建博客的人比较多，所以一搜基本上都有解决方案。所以也记录一下自己的搭建过程，也希望这篇文章能够帮助那些想用hexo搭建个人博客的小伙伴们少走点弯路。