---
title: 禁止IDM(Internet_Download_Manager)更新提示
author: 李学志
img: medias/featureimages/8.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 禁止IDM(Internet_Download_Manager)更新提示
categories: 禁止IDM(Internet_Download_Manager)更新提示
tags:
  - 禁止IDM(Internet_Download_Manager)更新提示
keywords: 李学志
essay: false
abbrlink: 65281
date: 2022-05-09 16:55:22
coverImg:
password:
---

# 禁止IDM(internet download manager)更新提示

IDM(internet download manager)用起来不错，下载神器，但更新提示比较烦人。

## 方法

**修改注册表**

1.输入`win + R`打开运行，键入`regedit`确定打开注册表编辑器；

2.在注册表编辑器中按照图片路径找到 LstCheck 项目：

```
HKEY_CURRENT_USER > Software > DownloadManager
```

3.双击它,把后面的年份改成未来的时间 99,
重启，搞定，然后它不会再显示更新了。

![修改注册表](https://i.loli.net/2021/04/16/Q1mjl4EABfpFnXo.jpg#vwid=837&vhei=732)

![image-20220509165809347](http://image.lxzcode520.xyz/img/image-20220509165809347.png)