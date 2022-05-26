---
title: go环境搭建
author: 李学志
img: medias/featureimages/9.jpg
top: false
cover: false
toc: true
mathjax: false
summary: go环境搭建
categories: go环境搭建
tags:
  - go环境搭建
keywords: 李学志
essay: false
abbrlink: 23540
date: 2022-05-09 12:22:00
coverImg:
password:
---

# go环境搭建

## 1.下载go安装包

[Go官方镜像站（推荐）：]: https://golang.google.cn/dl/
[Go语言中文网下载网址（推荐）：]: https://studygolang.com/dl

## 2. 版本选择

Windows平台和Mac平台推荐下载可执行文件版，Linux平台下载压缩文件版。

![image-20220509122631132](http://image.lxzcode520.xyz/img/image-20220509122631132.png)

## 3.安装

###  Windows安装

![image-20220509122814951](http://image.lxzcode520.xyz/img/image-20220509122814951.png)

有zip压缩版和msi安装版两个按本下载。（这里使用msi安装版，比较方便）。

+ 运行msi安装文件，千万不要在安装路径中出现中文，一路Next

![image-20220509122852988](http://image.lxzcode520.xyz/img/image-20220509122852988.png)

安装过程简单，一路"Next"即可，也可以自定义安装目录

**由于使用msi安装文件，所以Go语言的环境变量已经自动配置好了**

打开Windows中的命令提示符(cmd.exe)执行命令：

查看Go版本：

```
go version
```

 查看Go语言的环境信息：

```
go env
```

### Linux下安装

如果不是要在Linux平台敲go代码就不需要在Linux平台安装Go，我们开发机上写好的go代码只需要跨平台编译（详见文章末尾的跨平台编译）好之后就可以拷贝到Linux服务器上运行了，这也是go程序跨平台易部署的优势。

我们在版本选择页面选择并下载好go1.16.6.linux-amd64.tar.gz文件：

```
wget https://dl.google.com/go/go1.16.6.linux-amd64.tar.gz
```

将下载好的文件解压到/usr/local目录下：

```
tar -zxvf go1.16.6.linux-amd64.tar.gz -C /usr/local  # 解压
```

如果提示没有权限，加上sudo以root用户的身份再运行。执行完就可以在/usr/local/下看到go目录了。

配置环境变量： Linux下有两个文件可以配置环境变量，其中/etc/profile是对所有用户生效的；$HOME/.profile是对当前用户生效的，根据自己的情况自行选择一个文件打开，添加如下两行代码，保存退出。

~~~
export GOROOT=/usr/local/go
export PATH=$PATH:$GOROOT/bin
~~~

修改/etc/profile后要重启生效，修改$HOME/.profile后使用source命令加载$HOME/.profile文件即可生效。 检查：

~~~
~ go version
go version go1.16.6 linux/amd64
~~~

### Mac下安装

下载可执行文件版，直接点击**下一步**安装即可，默认会将go安装到/usr/local/go目录下。

![image-20220509123244515](http://image.lxzcode520.xyz/img/image-20220509123244515.png)

上一步安装过程执行完毕后，可以打开终端窗口，输入go version命令，查看安装的Go版本。

## 4.Go语言环境测试

新建一个hello.go文件，内容如下：

~~~go
package main
import "fmt"
func main(){
    fmt.Println("hello world!!!")
}
~~~

编译并直接运行程序：

进入hello.go文件所在的路径，打开cmd输入下面命令：

```
go run hello.go
```

![image-20220509123823850](http://image.lxzcode520.xyz/img/image-20220509123823850.png)

**安装完成**。
