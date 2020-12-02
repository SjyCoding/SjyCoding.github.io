---
title: Hexo子分类和父分类
date: 2020-12-02 19:01:15 +0800
updated:

categories: 
- Hexo搭建博客 
tags: 
- hexo
---





## 前言

> 随着博客量的增加，更细致的分类变得更有必要

## 方法

- 格式

    ```yml
    categories:
    - Diary
    - Life
    ```

    这种格式会使分类Life成为Diary的子分类，而不是并列分类

- 更复杂的格式

    ```yml
    categories:
    - [Diary, PlayStation]
    - [Diary, Games]
    - [Life]
    ```

    此时这篇文章同时包括三个分类： PlayStation 和 Games 分别都是父分类 Diary 的子分类，同时 Life 是一个没有子分类的分类











