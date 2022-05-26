---
title: 服务器搭建git仓库
author: 李学志
img: medias/featureimages/0.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 服务器搭建git仓库
categories:
  - 服务器
  - git
tags:
  - 服务器
  - git
keywords: 李学志
essay: false
abbrlink: 20741
date: 2021-11-29 11:34:29
coverImg:
password:
---

```
之前用docsify搭的一个文档网站一直要手动上传，那我为什么不搞一个git仓库来自动上传呢?
```

#### 服务器搭建 git 仓库

```
代码是在这个位置的
```

![image-20211129114818739](http://qiniuyun.code520.com.cn/images/20211129114818.png)

```
初始化仓库
```

![image-20211129114911315](http://qiniuyun.code520.com.cn/images/20211129114911.png)

```
添加git用户
```

```
adduser git
passwd git
```

```
改变权限
```

![image-20211129115525559](http://qiniuyun.code520.com.cn/images/20211129115525.png)

```
修改权限
```

```
chmod 740 /etc/sudoers
vim /etc/sudoers
```

![image-20211129194332007](http://qiniuyun.code520.com.cn/images/20211129194332.png)

```
创建证书登录(自己电脑的ssh文件)
```

![image-20211129120446526](http://qiniuyun.code520.com.cn/images/20211129120446.png)

![image-20211129194416587](http://qiniuyun.code520.com.cn/images/20211129194416.png)

![image-20211129151453111](http://qiniuyun.code520.com.cn/images/20211129151453.png)

```
在本地安装git
仓库添加的是
$ git remote add origin "git@121.4.48.188:/www/wwwroot/doc.code520.com.cn/docsify.git"
这里代码提交到服务器了
代码提交的地址
git@服务器地址:/文件存放的位置/.git文件夹
这里代码提交之后文件不会发生变化
可以通过git clone 拉取代码
git clone git@121.4.48.188:/www/wwwroot/doc.code520.com.cn/docsify.git
```

```
但是现在有一个问题hexo博客提交有一点问题
提交不要密码了
```

![image-20211129211242957](http://qiniuyun.code520.com.cn/images/20211129211243.png)
