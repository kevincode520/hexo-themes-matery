---
title: Centos7安装docker详细过程及报错解决
author: 李学志
img: medias/featureimages/10.jpg
top: false
cover: false
toc: true
mathjax: false
summary: Centos7安装docker详细过程及报错解决
categories: Centos7安装docker详细过程及报错解决
tags:
  - Centos7安装docker详细过程及报错解决
keywords: 李学志
essay: false
abbrlink: 18747
date: 2022-05-03 19:11:06
coverImg:
password:
---

## 一、安装docker

### 1.检查内核版本
* 注意:Docker **要求 CentOS 系统的内核版本高于 3.10** ，查看本页面的前提条件来验证你的CentOS 版本是否支持 Docker 。

* 通过 **uname -r** 命令查看你当前的内核版本
~~~1
[root@localhost ~]#  uname -r
~~~
### 2.确保yum版本为最新版
~~~1
[root@localhost ~]#  yum update
~~~
### 3、如果安装过旧版本的话卸载旧版本
~~~1
[root@localhost ~]#  yum remove -y docker  docker-common docker-selinux docker-engine
~~~

### 4.安装需要的软件包， yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的
~~~1
yum install -y yum-utils device-mapper-persistent-data lvm2
~~~
### 5.设置yum源
+ 使用官方源地址（比较慢）
~~~1
yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
~~~
* 国内的一些源地址
+ 阿里云
~~~1
yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
~~~
+ 清华大学源
~~~1
yum-config-manager \
    --add-repo \
    https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/docker-ce.repo
~~~

![image-20220503191439937](http://image.lxzcode520.xyz/img/image-20220503191439937.png)

### 6.查看仓库中所有docker的版本
~~~、
yum list docker-ce --showduplicates | sort -r
~~~

![image-20220503191507460](http://image.lxzcode520.xyz/img/image-20220503191507460.png)

### 7.安装 Docker Engine-Community
#### 1.安装最新版的

+ 推荐直接安装最新版，省事

~~~1
yum install -y docker-ce docker-ce-cli containerd.io    #  默认最新版
~~~
#### 2.指定版本安装
* 通过其完整的软件包名称安装特定版本，该软件包名称是软件包名称（docker-ce）加上版本字符串（第二列），从第一个冒号（:）一直到第一个连字符，并用连字符（-）分隔。例如：docker-ce-18.09.1。
~~~2
yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
~~~

![image-20220503191533660](http://image.lxzcode520.xyz/img/image-20220503191533660.png)

### 8.启动并设为开机自启
~~~3
systemctl start docker
systemctl enable docker
~~~

### 9.验证安装是否成功
* 有client和service两部分表示docker安装启动都成功了
~~~4
docker version
~~~

## 二、安装docker时报错解决
* **问题**

![image-20220503191610644](http://image.lxzcode520.xyz/img/image-20220503191610644.png)

* **解决方法**
**1、先按提示尝试添加 --skip-broken 选项来解决该问题**
~~~1
yum install -y docker-ce docker-ce-cli containerd.io --skip-broken
~~~

![image-20220503191633380](http://image.lxzcode520.xyz/img/image-20220503191633380.png)

+ 跳过依赖安装后docker无法启动

![image-20220503191700116](http://image.lxzcode520.xyz/img/image-20220503191700116.png)

**2、查看安装源目录**
+ 测试的好像只能用官网yum源安装docker-ce
+ 将repo.bak里面以CtenOS的都移到上层目录
+ == 后来发现自己的文件夹少了CentOS-Base.repo这个源==
+ 将所有repo文件移回/etc/yum.repos.d/下

![image-20220503191716803](http://image.lxzcode520.xyz/img/image-20220503191716803.png)

~~~2
[root@localhost bak]#  mv * /etc/yum.repos.d/
~~~

![image-20220503191731084](http://image.lxzcode520.xyz/img/image-20220503191731084.png)

再次进行安装
~~~3
yum install docker-ce docker-ce-cli containerd.io
~~~

成功后启动并设置为开机自启即可
