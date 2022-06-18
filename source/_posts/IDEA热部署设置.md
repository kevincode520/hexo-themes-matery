---
title: IDEA热部署设置
author: 李学志
img: medias/featureimages/20.jpg
top: false
cover: false
toc: true
mathjax: false
summary: IDEA热部署设置
categories: IDEA热部署设置
tags:
  - IDEA热部署设置
keywords: 李学志
essay: false
abbrlink: 43624
date: 2022-06-03 16:26:41
coverImg:
password:
---

# IDEA热部署设置

JRebel是一款[JVM](https://so.csdn.net/so/search?q=JVM&spm=1001.2101.3001.7020)插件，它使得Java代码修改后不用重启系统，立即生效。
IDEA上原生是不支持热部署的，一般更新了 Java 文件后要手动重启 Tomcat 服务器，这个过程是相当痛苦的，尤其是项目稍微大点的话，开发期间可能你就是一直在重启项目。这里强力推荐jrebel插件，用过一段时间之后感觉是真的爽，妈妈再也不用担心我写bug了！！！！

## 一、安装Jrebel



安装完成之后重启
但是这是Jreble是没有激活的，可以免费试用一周。

## 二、试用Jrebel

重启后显示：

![image-20220603163436608](http://image.lxzcode520.xyz/img/image-20220603163436608.png)

开始激活

+ 去jrebel官网用Facebook或Twitter账号登陆之后可以免费领取一个激活码(需要翻墙)

![image-20220603164707003](http://image.lxzcode520.xyz/img/image-20220603164707003.png)

- 获取激活码后在idea中点击help>jrebel>configuration 点击activation

![image-20220603165005884](http://image.lxzcode520.xyz/img/image-20220603165005884.png)

- 然后选择activation code 填入刚才获取到的激活码 勾选 i agree with the term.... 进行激活，稍等几秒提示激活成功！！！！
- 查看Jrebel激活状态发现已经激活

![image-20220603165917772](http://image.lxzcode520.xyz/img/image-20220603165917772.png)

- 勾选你要热部署的项目

![image-20220603164339444](http://image.lxzcode520.xyz/img/image-20220603164339444.png)

+ 启动项目，如图分别是jreble模式下的run和debug该模式下启动jrebel才能生效

![image-20220603165139474](http://image.lxzcode520.xyz/img/image-20220603165139474.png)



+ 启动开始控制台显示如下图，说明jrebel正常工作

![image-20220603171742252](http://image.lxzcode520.xyz/img/image-20220603171742252.png)

- 测试 修改项目代码后按Ctrl+F9 编译项目 发现控制台打印jrebel Log信息，说明jrebel实时编译了，而并不用重启项目，有没有很爽！！！~~~~

## 三、破解

我们都知道白嫖才是最香的这种需要付费的插件网上自然有破解的方法

这里有四个链接个人觉得第一个最好用简单粗暴

安装完后进行激活 :

Service Address ：https://jrebel.qekang.com/{GUID}
GUID地址：

https://www.guidgen.com

http://www.ofmonkey.com/transfer/guid

https://www.guidgenerator.com/online-guid-generator.aspx
注意:邮箱随意,格式对就行

![image-20220603170210364](http://image.lxzcode520.xyz/img/image-20220603170210364.png)

这样就算激活了

![image-20220603170544305](http://image.lxzcode520.xyz/img/image-20220603170544305.png)

注意:jrebel激活之后默认是联网使用的 , 在该模式下 , jrebel会一直联网监测激活信息 . 所以要改为离线使用

![image-20220603170725436](http://image.lxzcode520.xyz/img/image-20220603170725436.png)

![image-20220603170803387](http://image.lxzcode520.xyz/img/image-20220603170803387.png)

完成了！！！！

