---
title: 'Jave报错:java.lang.IllegalStateException'
author: 李学志
img: medias/featureimages/9.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 'Jave报错:java.lang.IllegalStateException'
categories: 'Jave报错:java.lang.IllegalStateException'
tags:
  - 'Jave报错:java.lang.IllegalStateException'
keywords: 李学志
essay: false
abbrlink: 63319
date: 2022-06-18 17:39:56
coverImg:
password:
---

## 非法访问：此Web应用程序实例已停止。无法加载[]。为了调试以及终止导致非法访问的线程，将抛出以下堆栈跟踪。

![image-20220618174156965](http://image.lxzcode520.xyz/img/image-20220618174156965.png)

这个是在关闭应用服务器或重新部署装载项目失败会发生。当应用程序卸载时，并不会关闭所有的线程。当tomcat已经关闭了其类加载器后，一些线程依然会继续运行，这样就导致出错，这些错误就会被到日志文件里。
解决方法是：修改tomcat目录下conf文件夹下的server.xml, 在Host标签添加子元素找到Context标签，把reloadble的属性值设为：reloadable="false"。重启tomcat即可。

reloadable:如果这个属性设为true，tomcat服务器在运行状态下会监视在WEB-INF/classes和WEB-INF/lib目录下class文件的改动，如果监测到有class文件被更新的，服务器会自动重新加载Web应用 ，也就是热部署。 有助于调试servlet和其它的class文件，但这样用加重服务器运行负荷，建议在Web应用的发存阶段将reloadable设为false。
