---
title: Docker搜索超时
date: 2020-12-02 19:09:10 +0800
updated:

categories: 
- [Linux,Docker]
- [Linux,常见问题]
tags: 
- Docker
- 镜像源
---



## Docker搜索超时

报错信息如下：

```shell
[root@zengmg /]# docker search centos
Error response from daemon: Get https://index.docker.io/v1/search?q=centos: read tcp 52.200.132.201:443: i/o timeout
```

docker在中国已经有了仓库：https://www.docker-cn.com/registry-mirror



根据上面网站提供的修改方法。

进入/etc/docker目录下

查看有没有 daemon.json。这是docker默认的配置文件。

如果没有新建，如果有，则修改。

```shell
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
```

保存退出。

重启docker服务：service docker restart

成功！