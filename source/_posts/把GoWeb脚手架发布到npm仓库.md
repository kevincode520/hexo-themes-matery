---
title: 把GoWeb脚手架发布到npm仓库
author: 李学志
img: medias/featureimages/19.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 把GoWeb脚手架发布到npm仓库
categories:
  - npm
  - Golang
tags:
  - npm
  - Golang
keywords: 李学志
essay: false
abbrlink: 57795
date: 2022-01-25 21:51:21
coverImg:
password:
---

# 把 GoWeb 模板脚手架发布到 npm 仓库通过 npm 初始化项目

## 首先打开 npm 官网： https://www.npmjs.com/

![image-20220125220547864](https://qiniuyun.code520.com.cn/images/20220125220555.png)

## 注册账号

### 成功登入

![image-20220125220918678](https://qiniuyun.code520.com.cn/images/20220125220918.png)

#### 创建&发布包

#### 本地登陆 npm

![image-20220125222151053](https://qiniuyun.code520.com.cn/images/20220125222151.png)

#### 遇到的问题

![image-20220125222220310](https://qiniuyun.code520.com.cn/images/20220125222220.png)

#### 登陆之前需要切换 npm 源

```
或者在提交时提交源

npm publish --registry=https://registry.npmjs.org
```

[关于 npm 登陆 code 500 的问题](https://blog.csdn.net/qq_29483485/article/details/117949698)

#### 这里需要 npm init -y

![image-20220125224722841](https://qiniuyun.code520.com.cn/images/20220125224722.png)

```
npm 包的名字就是name
```

![image-20220125224638521](https://qiniuyun.code520.com.cn/images/20220125224638.png)

![image-20220125224754749](https://qiniuyun.code520.com.cn/images/20220125224754.png)

#### 成功

![image-20220125225501471](https://qiniuyun.code520.com.cn/images/20220125225501.png)

#### 这是全局安装之后的效果明天搞个命令行的版本

#### 现在已经使用 node.js 把脚手架工具写出来了明天发布

```
create-golang-app
```

[create-golang-app](https://www.npmjs.com/package/create-golang-app)
