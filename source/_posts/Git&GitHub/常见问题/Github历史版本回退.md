---
title: Github历史版本回退
date: 2020-12-02 19:09:10 +0800
updated: 

categories: 
- [Git,常见问题]
tags: 
- Git
- GitHub

---



## 问题描述

最近几天的GitHub提交出了些问题，导致之前提交的更新丢失，考虑回退到之前的版本。在GitHub的Web页面上并没有找到回退的解决方案（如果大家知道的话，感谢告知），于是决定通过本地的 Git Bash来操作。

- **查找 commit id：**浏览GitHub上的提交历史记录，找到要回退的版本，复制commit id。

    类似这种

    ![这里写图片描述](https://s3.ax1x.com/2020/12/02/DI4MQ0.jpg)



- **恢复历史版本：**

```
git reset --hard [你的commit id] 
```

- **push：**推送到GitHub远程仓库

```
git push -f -u origin master 
```

