---
title: Windows中杀死占用某个端口的进程
author: 李学志
img: medias/featureimages/9.jpg
top: false
cover: false
toc: true
mathjax: false
summary: Windows中杀死占用某个端口的进程
categories: Windows中杀死占用某个端口的进程
tags:
  - Windows中杀死占用某个端口的进程
keywords: 李学志
essay: false
abbrlink: 20830
date: 2022-06-03 17:21:28
coverImg:
password:
---

# Windows中杀死占用某个端口的进程

启动tomcat时候，控制台报错，发现是端口占用，于是寻找方法关闭对应的程序。

在网上找了好久，觉得这个方法不错，以下以1099端口为例：

+ **第一步，根据端口号查找对应的进程号****

~~~bash
netstat -ano | findstr 1099 //显示1099端口下的进程
~~~

结果如下：

![image-20220603172625490](http://image.lxzcode520.xyz/img/image-20220603172625490.png)

发现 1099 端口被 PID(进程号)为 40808 的进程占用。

+ **第二步，据进程号寻找进程名称**

~~~bash
tasklist | findstr 40808
~~~



![image-20220603172556488](http://image.lxzcode520.xyz/img/image-20220603172556488.png)

从任务管理器中查找该程序，手动杀死即可。

至此，已经完成。

但是我发现，在任务管理器中找太过于麻烦还有可能找不到  , 所以直接命令行杀死该程序了，命令如下：

~~~bash
taskkill -PID <进程号> -F //强制关闭某个进程
~~~

![image-20220603173022786](http://image.lxzcode520.xyz/img/image-20220603173022786.png)

**完成！！！**