---
title: IDEA连接GitHub并上传项目
author: 李学志
img: medias/featureimages/11.jpg
top: false
cover: false
toc: true
mathjax: false
summary: IDEA连接GitHub并上传项目
categories: IDEA连接GitHub并上传项目
tags:
  - IDEA连接GitHub并上传项目
keywords: 李学志
essay: false
abbrlink: 20819
date: 2022-05-16 16:54:21
coverImg:
password:
---

# IDEA连接GitHub并上传项目

首先，要确定自己已经安装git，并且自己已经注册了一个github！
下面看看idea怎么连接到github！不要嫌步骤繁琐，连上得时候超有成就感！
你要push到的github中的仓库最好要与idea中的项目名相同，否则仓库多了，项目多了，可能会搞混淆，下面的例子仓库名跟项目名一样

###  **一、IntelliJ IDEA连接Github**

#### **1.打开IDEA-->File-->settings,选择安装好的Git路径**

![image-20220516225201154](http://image.lxzcode520.xyz/img/image-20220516225201154.png)

#### **2.如上再到VersionControl下选择Github，添加自己的Github账号（已经登录的可以省略）**

![image-20220516225238434](http://image.lxzcode520.xyz/img/image-20220516225238434.png)

#### **3.创建程序本地Repository**

VCS –>Create Git Repository –>选择项目文件夹

![image-20220516170727699](http://image.lxzcode520.xyz/img/image-20220516170727699.png)



#### **4.上传工程**
VCS –>GitHub ->Share Project On GitHub–>填写名称和描述

![image-20220516170945893](http://image.lxzcode520.xyz/img/image-20220516170945893.png)

####  5.**进行修改上传操作**

遵循git的方式：先`add`后`commit`最后`push`

![image-20220516171957935](http://image.lxzcode520.xyz/img/image-20220516171957935.png)

![image-20220516172032717](http://image.lxzcode520.xyz/img/image-20220516172032717.png)

![image-20220516172123566](http://image.lxzcode520.xyz/img/image-20220516172123566.png)

#### **6.验证**

在GitHub上查看

![image-20220516172335011](http://image.lxzcode520.xyz/img/image-20220516172335011.png)

### 二、上传时遇到的一些错误

解决git@github.com: Permission denied (publickey). fatal: Could not read from remote repository. Pleas

![image-20220516225317045](http://image.lxzcode520.xyz/img/image-20220516225317045.png)

#### 1.**原因分析**

Permission denied (publickey) 没有权限的publickey ，出现这错误一般是以下两种原因

+ 客户端与服务端未生成 ssh key
+ 客户端与服务端的ssh key不匹配

找到问题的原因了，解决办法也就有了，重新生成一次ssh key ，服务端也重新配置一次即可。

#### 2.客户端生成ssh key

在cmd里面输入

ssh-keygen -t rsa -C "xxxxxxxx@qq.com"

~~~
ssh-keygen -t rsa -C "youremail@example.com"
~~~


xxxxxx@qq.com改为自己的邮箱即可，途中会让你输入密码啥的，不需要管，一路回车即可，会生成你的ssh key。（如果重新生成的话会覆盖之前的ssh key。）

![image-20220516172932953](http://image.lxzcode520.xyz/img/image-20220516172932953.png)

#### 3.打开id_rsa.pub文件,并且复制内容

![img](https://img-blog.csdnimg.cn/20200603102554725.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20200603102735768.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)

#### 4.在github上打开箭头处,点击Setting

找到SSH and GPG keys

![img](https://img-blog.csdnimg.cn/20200603102157756.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)

![img](http://image.lxzcode520.xyz/img/20200603102223280.png)

打开你刚刚生成的id_rsa.pub，将里面的内容复制，进入你的github账号，在settings下，SSH and GPG keys下new SSH key，然后将id_rsa.pub里的内容复制到Key中，完成后Add SSH Key。

![img](https://img-blog.csdnimg.cn/2020060310174263.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20200603101823216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)

#### 5.用idea再次提交文件到 github上,显示提交成功

![img](https://img-blog.csdnimg.cn/20200603103159683.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dfMzE3,size_16,color_FFFFFF,t_70)
