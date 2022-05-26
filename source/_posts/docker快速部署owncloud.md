---
title: docker快速部署owncloud
author: 李学志
img: medias/featureimages/3.jpg
top: false
cover: false
toc: true
mathjax: false
summary: docker快速部署owncloud
categories: docker快速部署owncloud
tags:
  - docker快速部署owncloud
keywords: 李学志
essay: false
abbrlink: 22533
date: 2022-05-08 09:52:29
coverImg:
password:
---

## 1.拉取镜像

~~~linux 
docker pull owncloud
docker pull mysql:5.7
~~~

## 2、启动mysql容器(非必须)

其实owncloud自带sqllite，但是为了更快更好的建立文件索引，所以我还是推荐我们安装一个MySQL 来存数据(当然，如果你觉得麻烦的话，这一步也是可以省去的，可以直接跳过这一步)，下面我们介绍一下MySql 的快速安装

~~~
docker run --name owncloud-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=root -d mysql:5.7
~~~

## 3、启动owncloud容器

+ 使用MySQL：

~~~ 
docker run -p 8080:80 -d  --link mysql:mysql -v /data/owncloud/:/var/www/html owncloud
~~~

+ 不使用MySQL：

~~~
docker run -p 8080:80 -d   -v /data/owncloud/:/var/www/html owncloud
~~~

### 解释

`--link mysql:mysql`:
 是用来连接上一步创建MySQL容器的，使其能和MySQL容器通信，这个不填也是可以的，只不过后面的操作的麻烦一点，参考 [关于对docker run --link的理解](https://www.jianshu.com/p/21d66ca6115e)
 `-p 80:80`:
 这里是为了将容器内的端口映射到我们的树莓派的操作系统的端口上
 `-v /data/owncloud/:/var/www/html owncloud`:
 这一步是为将容器里面的路径映射到容器外面来，这样就方便我们对文件的管理
 `-d`： 守护态运行，即后台运行

## 4.访问

IP:8080

## 5、设置管理员账户

admin/admin123

![img](https://upload-images.jianshu.io/upload_images/2109322-37ddedb23afc242d.png?imageMogr2/auto-orient/strip|imageView2/2/w/939/format/webp)

## 6.配置 owncloud

+ 不使用MySQL可不配置

![img](https://upload-images.jianshu.io/upload_images/2109322-efe42e72b9627011.png?imageMogr2/auto-orient/strip|imageView2/2/w/360/format/webp)



## 7.登录查看最终效果

![image-20220508105653923](http://image.lxzcode520.xyz/img/image-20220508105653923.png)