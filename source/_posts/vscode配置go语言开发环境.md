---
title: vscode配置go语言开发环境
author: 李学志
img: medias/featureimages/14.jpg
top: false
cover: false
toc: true
mathjax: false
summary: vscode配置go语言开发环境
categories: vscode配置go语言开发环境
tags:
  - vscode配置go语言开发环境
keywords: 李学志
essay: false
abbrlink: 43388
date: 2022-05-09 12:44:54
coverImg:
password:
---

# VS Code配置Go语言开发环境

Go语言是采用UTF8编码的，理论上使用任何文本编辑器都能做Go语言开发。大家可以根据自己的喜好自行选择。编辑器/IDE没有最好只有最适合

## 1.安装中文简体插件

点击左侧菜单栏最后一项`管理扩展`，在`搜索框`中输入`chinese` ，选中结果列表第一项，点击`install`安装。

安装完毕后右下角会提示`重启VS Code`，重启之后你的VS Code就显示中文啦！

![安装简体中文插件](https://www.liwenzhou.com/images/Go/install_go_dev/vscode1.gif)

## 2.安装Go开发扩展

现在我们要为我们的VS Code编辑器安装`Go`扩展插件，让它支持Go语言开发。

![image-20220509124750836](http://image.lxzcode520.xyz/img/image-20220509124750836.png)

## 3.安装Go语言开发工具包

在座Go语言开发的时候为我们提供诸如代码提示、代码自动补全等功能。

在此之前请先设置`GOPROXY`，打开终端执行以下命令：

```bash
go env -w GOPROXY=https://goproxy.cn,direct
```

Windows平台按下`Ctrl+Shift+P`，Mac平台按`Command+Shift+P`，这个时候VS Code界面会弹出一个输入框，如下图：

![vscode09](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode09.png)

我们在这个输入框中输入`>go:install`，下面会自动搜索相关命令，我们选择`Go:Install/Update Tools`这个命令，按下图选中并会回车执行该命令（或者使用鼠标点击该命令）

![vscode10](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode10.png)

在弹出的窗口选中所有，并点击“确定”按钮，进行安装。

![vscode12](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode12.png)

## 4.配置代码片段快捷键

还是按`Ctrl/Command+Shift+P`,按下图输入`>snippets`，选择命令并执行：

![vscode16](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode17.png)

然后在弹出的窗口点击选择`go`选项：

![vscode18](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode18.png)

然后弹出如下页面：

![vscode19](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode19.png)

大家可以简单看下上面的注释，介绍了主要用法：

```js
“这里放个名字”:{
    "prefix": "这个是快捷键",
    "body": "这里是按快捷键插入的代码片段",
    "description": "这里放提示信息的描述"
}
```

其中`$0`表示最终光标提留的位置。 举个例子，我这里创建了两个快捷方式，一个是输入`pln`就会在编辑器中插入`fmt.Println()`代码；输入`plf`，就会插入`fmt.Printf("")`代码。

```json
{
	"println":{
		"prefix": "pln",
		"body":"fmt.Println($0)",
		"description": "println"
	},
	"printf":{
		"prefix": "plf",
		"body": "fmt.Printf(\"$0\")",
		"description": "printf"
	}
}
```

把上面的代码，按下图方式粘贴到配置文件中，保存并关闭配置文件即可。

![vscode20](https://www.liwenzhou.com/images/Go/00_config_VSCode/vscode20.png)

添加如上配置后，保存。 我们打开一个go文件，测试一下效果：

![image-20220509125906090](http://image.lxzcode520.xyz/img/image-20220509125906090.png)

## 6.关于vscode安装gotools失败问题的解决方案

### 第一步，下载gotpools

在https://github.com/golang/tools上去下载。

![img](https://img-blog.csdnimg.cn/20181223152232931.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1pIQU9KVU5XRUkwOA==,size_16,color_FFFFFF,t_70)

在本地go的安装目录，到{GOPATH}\src\golang.org\x\tools目录 下，没有就自己创建。

右键-->git bash here，然后输入：

~~~
git clone https://github.com/golang/tools.git ./
~~~

回车下载 ：

![img](https://img-blog.csdnimg.cn/20181223152527519.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1pIQU9KVU5XRUkwOA==,size_16,color_FFFFFF,t_70)

+ 如果你没有安装git，那也没关系，你 自己下载 zip包，放到这个目录下就可以了。

### 第二步，安装

切换到vscode工具，打开。

终端->新建终端 或者用 Ctrl+shift+' (我用的是vscode insider 版本，可能各个版本快捷键不一样)

![img](https://img-blog.csdnimg.cn/20181223152806861.png)

接下来很简单了，执行命令安装就可以，安装后生成的exe文件是在{GOBIN}目录下的，不知道的可以用go env查看。

安装的命令也不需要多说吧，按个执行下面的命令就可以（当然你也可以在windows的 cmd窗口去执行，两个是一样的）

~~~
go install github.com/ramya-rao-a/go-outline
go install github.com/acroca/go-symbols
go install golang.org/x/tools/cmd/guru
go install golang.org/x/tools/cmd/gorename
go install github.com/josharian/impl
go install github.com/rogpeppe/godef
go install github.com/sqs/goreturns
go install github.com/golang/lint/golint
go install github.com/cweill/gotests/gotests
go install github.com/ramya-rao-a/go-outline
go install github.com/acroca/go-symbols
go install golang.org/x/tools/cmd/guru
go install golang.org/x/tools/cmd/gorename
go install github.com/josharian/impl
go install github.com/rogpeppe/godef
go install github.com/sqs/goreturns
go install github.com/cweill/gotests/gotests
~~~

### 第三步，安装golint

同样，先去下载golint，然后执行命令安装。

在{GOPATH}\src\golang.org\x下建立一个 golint的目录，在目录里面git bash，执行下面的命令

```ruby
git clone https://github.com/golang/lint.git ./
```

![img](https://img-blog.csdnimg.cn/2018122315312063.png)

在vscode的终端上 执行 如下命令安装：

```go
go install golang.org\x\lint\golint
```

这样应该就差不多了。

如果你要安装其他的go插件或者工具，也可以这么安装。