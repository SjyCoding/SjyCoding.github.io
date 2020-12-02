---
title: Linux的一些小工具
date: 2020-12-02 19:09:10 +0800
updated:

categories: 
- Linux
- 工具
tags: 
- Linux

---





## screenfetch

- Ubuntu

    ```shell
    apt install screenfetch
    ```

- CentOS

    ```shell
    # 先下载：
    wget -O screenfetch-dev https://git.io/vaHfR
    # 然后丢到/usr/bin或类似的目录，如果在PATH就比较方便：
    sudo mv ./screenfetch-dev /usr/bin/screenfetch
    # 记得加上可执行权限：
    sudo chmod +x /usr/bin/screenfetch
    # 此时应该可以使用了：
    screenfetch
    ```

    