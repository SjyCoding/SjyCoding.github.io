---
title: 基于Hexo-Github搭建个人博客二：更改博客主题
comments: true
mathjax: false
toc: true
top: false
categories:
- Hexo搭建博客
tags:
- hexo
- volantis
date: 2020-11-23 13:33:16
updated: 2020年11月23日 13点36分
---
## 前言

> 本文所有内容来自于[这里](https://blog.csdn.net/weixin_44855907/article/details/105376826)， 略有修改

上篇博客讲述了实现把博客推到Github Page，接下来这篇博客就来讲一下更改和优化主题。
我使用的是volantis 主题（ Volantis是xaoxuu博主开发的主题），不是官方主题。其实这个主题对我来说难度挺大的，主要是因为主题 作者（我）的参考文档不够（太）详细~~ (菜)。 可我就是谗它好看，没办法。部署博客到远端Github用了一天，优化主题却整了整整三天（手动狗头，太难了）。
如何选主题：
强烈建议初学者选主题前先查阅一下这一个主题的使用人数多不多，这样出了问题比较好解决。帮助文档够不够详尽，这样可以少踩点坑。一开始还是使用中规中矩的官方主题，魔改的那些除非你比较有精力那就可以尝试。有了感觉之后再去自定义修改，尝试其他一下风格的主题，毕竟上手之后切换主题是分分钟钟的事。可以先看一下：[知乎的这篇文章](https://www.zhihu.com/question/24422335)

## volantis主题更改


### 1 下载与安装volantis主题
本地环境：我博客文件路径是E:\hexo\blog

#### 1.1 将主题下载到themes目录下
进入你本地放博客文件目录 进入到themes目录下
右键git bash here执行命令：

```shell
git clone https://github.com/xaoxuu/hexo-theme-volantis themes/volantis
```

执行成功后，themes目录下有volantis文件夹

![](https://s3.ax1x.com/2020/11/23/DJGRjx.jpg)

#### 1.2 修改站点配置文件

注意是站点的_config.yml文件不是主题的_config.yml
用vscode或notepad++打开_config.yml文件找到themes字段 将默认的lanscape修改为你的主题volantis
其实之所以有两个配置文件是有原因的，你想啊。站点（也就是你的博客）的_config.yml用于配置你整个博客，如果你想换个主题，那么只要在站点的_config.yml修改theme就可了，不用大动干戈。想实现主题的一些其他功能如评论系统只要在主题的配置文件_config.ym修改就可以了，由于每个主题都有一个配置我呢见，换主题时也不会互相影响。

#### 1.4 检查并安装依赖

安装 Hexo 搜索的依赖包：

```shell
npm i -S hexo-generator-search hexo-generator-json-content
```

安装 stylus 渲染器：

```shell
npm i -S hexo-renderer-stylus
```

4）将hexo默认主题更换为volantis

```shell
hexo clean #清除之前部署
hexo g #生成
hexo s# 本地预览
```

执行完上面操作就可以到 本地4000端口进行博客预览，可以发现主题已变了。
准备工作做足了，下面正式进入主题设置。由于主题官网已经对主题的配置做了比较详尽的介绍，我这里就不赘诉了，主要讲一下我的一下理解，和操作的大概流程。
一开始我由于没有站点/主题/页面这些概念所以也是比较蒙蔽，无从下手。其实不用看太多的教程，把官方文档看明白意思了，基本的博客框架就搭起来了，后续高级功能再慢慢学习优秀博主的Github源码，最后再自定义。个人觉得这个写文档的人逻辑表述能力不太强、将东西老是乱串的，反正我这个小白级博主是自己摸索之后才逐渐明白官网这样一个教程设置的顺序的。配置文件也鲜有中文注释，英文居多，我觉得这可能是难倒大多数新手的一个原因，遇到英文，不懂就整句百度翻译。

所以想首先对官网进行一下说明和解读。
官网顶端导航栏的几个按钮
【开始】：是我们volatis主题的下载与安装。

【站点】：是对我们整个博客的一个设置，如链接标签页显示的图标、标题等，所以是在博客的_config.yml下配置的。详细配置可以看hexo官网的官方文档https://hexo.io/zh-cn/docs/中的配置。

【主题】：是有关对我们当前选的这个主题volantis的一个修改配置。你想设置什么功能，如评论系统、搜索功能这些。可以根据自己的需要去配置，这是这篇博客的重点，但不会讲具体怎么操作，因为文档有教，而是讲一些注意事项和我踩到的一些坑。

这里对volantis文件夹下的子文件夹和文件做一些简单的介绍

```shell
_config.yml: 为对整个主题的配置文件
layout： 为页面、卡片（widget）、图标等源码和资源
source： 为样式、第三方插件等源码
```

## 一些实用功能
### 评论系统

gitalk：gitalk，需要依赖github，我试了一下没有成功，而且评论者还需要登录github才可以评论，不好用。因而我选择用valine，一步到位，可匿名评价 。配置详见：这篇博客

### 去掉封面的搜索框
打开layout/_cover/index.ejs 找到如下所示代码，将其注释（如果你决定以后也不会使用这个封面的搜索框了 去掉也可以）

```ejs
<% if (theme.search.enable === true) { %>
    <div class="m_search">
        <form name="searchform" class="form u-search-form">
            <input type="text" class="input u-search-input" placeholder="<%- theme.cover && theme.cover.search %>" />
            <i class="icon fas fa-search fa-fw"></i>
        </form>
    </div>
<% } %>
```

效果：

![](https://s3.ax1x.com/2020/11/23/DJJErV.jpg)

### 修改使手机端观看有外边距

打开source/css/_layout/main.styl
找到 @media screen and (max-width:$device-tablet)这一行 做如下修改

![](https://s3.ax1x.com/2020/11/23/DJJwRA.jpg)

### 配置模板文件使用new命令 自动生成模板文件
E:\hexo\blog\scaffolds
编辑post.md 没有则新建
加入如下代码

```markdown
---
title: {{ title }} 
date: {{ date }} 
comments: true # 是否开启评论
mathjax: false # 是否开启数学公式渲染
toc: true # 是否启用目录
top: false # 是否置顶

#若使用urlname作为永久链接则添加该项
urlname:

categories: 
- [父类,子类]
- 同级分类
tags: [标签1,标签2]
---

<!-- more -->
```

## Q&A

1）明明加了标签却无法在文章头部显示出来
不是用如下hexo命令new出来的文章标签是无法无法正常显示，即使是复制黏贴了用上面命令生成的文章的fromt-matter，也是不能正常显示的，所以先用hexo命令新建文件，再用markdown编辑器打开编辑。

hexo new '文章标题'
1


2）引用本地图片无法显示
你引用自己的本地图片发布路径写的是本地的路径，服务器无法访问你的本地文件当然无法正常加载啦。解决方法是实用图床生成外链。见博客[]
如外链之后引用图片，博客浏览过大或过小，可以先调整好大小再上传，如我遇到的问题就是，没有去查看博客头像预定的大小是多少（可以看别的已经搭好的博主的头像的参数 使用F12审查元素）

 

未完待续……

参考文章：
[Volantis主题DIY笔记](https://wa2000.cn/post/202003171229/)
[volantis官网](https://volantis.js.org/getting-started/)