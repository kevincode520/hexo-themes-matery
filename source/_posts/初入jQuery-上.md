---
title: 初入jQuery(上)
author: 李学志
img: medias/featureimages/5.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 初入jQuery(上)
categories: 初入jQuery(上)
tags:
  - 初入jQuery(上)
keywords: 李学志
essay: false
abbrlink: 40897
date: 2022-05-26 17:44:32
coverImg:
password:
---

# 初入jQuery(上)

在开始学习 jQuery 之前，应该对以下知识有基本的了解：

- HTML
- CSS
- JavaScript

## 1.什么是 jQuery ？

jQuery 是一个 JavaScript 函数库。

jQuery 是一个轻量级的"写的少，做的多"的 JavaScript 库。

jQuery 库包含以下功能：

- HTML 元素选取
- HTML 元素操作
- CSS 操作
- HTML 事件函数
- JavaScript 特效和动画
- HTML DOM 遍历和修改
- AJAX
- Utilities

**提示：** 除此之外，jQuery 还提供了大量的插件。

+ 为什么使用 jQuery ？
  + 目前网络上有大量开源的 JS 代码库, 但是 jQuery 是目前最流行的 JS 代码库，而且提供了大量的扩展。

## 2.jQuery 安装

可以通过多种方法在网页中添加 jQuery。 您可以使用以下方法：

- 从 [jquery.com](http://jquery.com/download/) 下载 jQuery 库
- 从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery

### 下载 jQuery

有两个版本的 jQuery 可供下载：

- Production version - 用于实际的网站中，已被精简和压缩。
- Development version - 用于测试和开发（未压缩，是可读的代码）

以上两个版本都可以从 [jquery.com](http://jquery.com/download/) 中下载。

jQuery 库是一个 JavaScript 文件，您可以使用 HTML 的 <script> 标签引用它

<head> <script src="jquery-1.10.2.min.js"></script> </head>

### 替代方案

如果您不希望下载并存放 jQuery，那么也可以通过 CDN（内容分发网络） 引用它。

Staticfile CDN、百度、又拍云、新浪、谷歌和微软的服务器都存有 jQuery 。

如果你的站点用户是国内的，建议使用百度、又拍云、新浪等国内CDN地址，如果你站点用户是国外的可以使用谷歌和微软。

**注：**本站实例均采用菜鸟教程 CDN 库。

如需从 Staticfile CDN、又拍云、新浪、谷歌或微软引用 jQuery，请使用以下代码之一：

+ Staticfile CDN:

<head> <script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js"> </script> </head>

+ 百度 CDN:

<head> <script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"> </script> </head>

+ 又拍云 CDN:

<head> <script src="https://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js"> </script> </head>

+ 新浪 CDN:

<head> <script src="https://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js"> </script> </head>

### jQuery 使用版本

我们可以在浏览器的 Console 窗口中使用 **$.fn.jquery** 命令查看当前 jQuery 使用的版本：

![img](http://image.lxzcode520.xyz/img/B05C63FB-9989-4607-A4FE-5FF8AEE6C770.jpg)

## 3.jQuery 语法

通过 jQuery，您可以选取（查询，query） HTML 元素，并对它们执行"操作"（actions）。

jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： **$(\*selector\*).\*action\*()**

- 美元符号定义 jQuery
- 选择符（selector）"查询"和"查找" HTML 元素
- jQuery 的 action() 执行对元素的操作

实例:

- $(this).hide() - 隐藏当前元素
- $("p").hide() - 隐藏所有 <p> 元素
- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
- $("#test").hide() - 隐藏 id="test" 的元素

两种函数写法：

~~~js
$(document).ready(function(){

   // 开始写 jQuery 代码...
   //$(document).ready() 方法允许我们在文档完全加载完后执行函数
});


$(function(){

   // 开始写 jQuery 代码...

});
~~~

## 4.jQuery 选择器

### 元素选择器

jQuery 元素选择器基于元素名选取元素。

在页面中选取所有 <p> 元素:

$("p")

**实例**

用户点击按钮后，所有 <p> 元素都隐藏：

~~~js
$(document).ready(function(){
  $("button").click(function(){
    $("p").hide();
  });
});

~~~

### #id 选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

$("#test")

**实例**

当用户点击按钮后，有 id="test" 属性的元素将被隐藏：

~~~js
$(document).ready(function(){
  $("button").click(function(){
    $("#test").hide();
  });
});
~~~

### .class 选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

$(".test")

**实例**

用户点击按钮后所有带有 class="test" 属性的元素都隐藏：

~~~js
$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide();
  });
});
~~~

## 5.jQuery 事件

jQuery 是为事件处理特别设计的。

**什么是事件**？

页面对不同访问者的响应叫做事件。

事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。

实例：

- 在元素上移动鼠标。
- 选取单选按钮
- 点击元素

在事件中经常使用术语"触发"（或"激发"）例如： "当您按下按键时触发 keypress 事件"。

常见 DOM 事件：

| 鼠标事件                                                     | 键盘事件                                                     | 表单事件                                                  | 文档/窗口事件                                             |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------------------------------------------------- | :-------------------------------------------------------- |
| [click](https://www.runoob.com/jquery/event-click.html)      | [keypress](https://www.runoob.com/jquery/event-keypress.html) | [submit](https://www.runoob.com/jquery/event-submit.html) | [load](https://www.runoob.com/jquery/event-load.html)     |
| [dblclick](https://www.runoob.com/jquery/event-dblclick.html) | [keydown](https://www.runoob.com/jquery/event-keydown.html)  | [change](https://www.runoob.com/jquery/event-change.html) | [resize](https://www.runoob.com/jquery/event-resize.html) |
| [mouseenter](https://www.runoob.com/jquery/event-mouseenter.html) | [keyup](https://www.runoob.com/jquery/event-keyup.html)      | [focus](https://www.runoob.com/jquery/event-focus.html)   | [scroll](https://www.runoob.com/jquery/event-scroll.html) |
| [mouseleave](https://www.runoob.com/jquery/event-mouseleave.html) |                                                              | [blur](https://www.runoob.com/jquery/event-blur.html)     | [unload](https://www.runoob.com/jquery/event-unload.html) |
| [hover](https://www.runoob.com/jquery/event-hover.html)      |                                                              |                                                           |                                                           |

### jQuery 事件方法语法

在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。

页面中指定一个点击事件：

~~~js
$("p").click();
~~~

下一步是定义了点击后触发事件。您可以通过一个事件函数实现：

~~~js
$("p").click(function(){    // 动作触发后执行的代码!! });
~~~

### 常用的 jQuery 事件方法

#### $(document).ready()

$(document).ready() 方法允许我们在文档完全加载完后执行函数。该事件方法在 [jQuery 语法](https://www.runoob.com/jquery/jquery-syntax.html) 章节中已经提到过。

#### click()

click() 方法是当按钮点击事件被触发时会调用一个函数。

该函数在用户点击 HTML 元素时执行。

在下面的实例中，当点击事件在某个 <p> 元素上触发时，隐藏当前的 <p> 元素：

~~~js
$("p").click(function(){
  $(this).hide();
});
~~~

#### dblclick()

当双击元素时，会发生 dblclick 事件。

dblclick() 方法触发 dblclick 事件，或规定当发生 dblclick 事件时运行的函数：

~~~js
$("p").dblclick(function(){
  $(this).hide();
});
~~~

#### mouseenter()

当鼠标指针穿过元素时，会发生 mouseenter 事件。

mouseenter() 方法触发 mouseenter 事件，或规定当发生 mouseenter 事件时运行的函数：

~~~js
$("#p1").mouseenter(function(){
    alert('您的鼠标移到了 id="p1" 的元素上!');
});
~~~

#### mouseleave()

当鼠标指针离开元素时，会发生 mouseleave 事件。

mouseleave() 方法触发 mouseleave 事件，或规定当发生 mouseleave 事件时运行的函数：

~~~js
$("#p1").mouseleave(function(){
    alert("再见，您的鼠标离开了该段落。");
});
~~~

#### mousedown()

当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。

mousedown() 方法触发 mousedown 事件，或规定当发生 mousedown 事件时运行的函数：

~~~js
$("#p1").mousedown(function(){
    alert("鼠标在该段落上按下！");
});
~~~

#### mouseup()

当在元素上松开鼠标按钮时，会发生 mouseup 事件。

mouseup() 方法触发 mouseup 事件，或规定当发生 mouseup 事件时运行的函数：

~~~js
$("#p1").mouseup(function(){
    alert("鼠标在段落上松开。");
});
~~~

#### hover()

hover()方法用于模拟光标悬停事件。

当鼠标移动到元素上时，会触发指定的第一个函数(mouseenter);当鼠标移出这个元素时，会触发指定的第二个函数(mouseleave)。

~~~js
$("#p1").hover(
    function(){
        alert("你进入了 p1!");
    },
    function(){
        alert("拜拜! 现在你离开了 p1!");
    }
);
~~~

#### focus()

当元素获得焦点时，发生 focus 事件。

当通过鼠标点击选中元素或通过 tab 键定位到元素时，该元素就会获得焦点。

focus() 方法触发 focus 事件，或规定当发生 focus 事件时运行的函数：

~~~js
$("input").focus(function(){
  $(this).css("background-color","#cccccc");
});
~~~

#### blur()

当元素失去焦点时，发生 blur 事件。

blur() 方法触发 blur 事件，或规定当发生 blur 事件时运行的函数：

~~~js
$("input").blur(function(){
  $(this).css("background-color","#ffffff");
});
~~~
