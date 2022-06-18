---
title: 初入jQuery(二)
author: 李学志
img: medias/featureimages/12.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 初入jQuery(二)
categories: 初入jQuery(二)
tags:
  - 初入jQuery(二)
keywords: 李学志
essay: false
abbrlink: 65379
date: 2022-05-28 15:38:05
coverImg:
password:
---

# 初入jQuery(二)

## 1.jQuery显示/隐藏

#### jQuery hide() 和 show()

通过 jQuery，您可以使用 hide() 和 show() 方法来隐藏和显示 HTML 元素：

~~~js
//jQuery
$(function () {
    //隐藏
    $("#hide").click(function () {
        $("p").hide();
    });

    //显示
    $("#show").click(function () {
        $("p").show();
    });

})

//HTML
<p>如果你点击“隐藏” 按钮，我将会消失。</p>
<button id="hide">隐藏</button>
<button id="show">显示</button>

~~~

**语法:**

$(*selector*).hide(*speed,callback*);

$(*selector*).show(*speed,callback*);

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

~~~js
$("#box_hide").click(function () {
    $(".box").hide(1000, "linear", function () {
        alert("Hide() 方法已完成!")
    });
});
~~~

第二个参数是一个字符串，表示过渡使用哪种缓动函数。（译者注：jQuery自身提供"linear" 和 "swing"，其他可以使用相关的插件）。

#### jQuery toggle()

通过 jQuery，可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：

~~~js
$("#toggle").click(function () {
    $("p").toggle(); //参数同show(),hide()
});
~~~

## 2.jQuery 效果 - 淡入淡出

#### jQuery Fading 方法

通过 jQuery，您可以实现元素的淡入淡出效果。

jQuery 拥有下面四种 fade 方法：

- fadeIn()
- fadeOut()
- fadeToggle()
- fadeTo()

**语法:**

$(*selector*).fade方法(*speed,callback*);

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。.

可选的 callback 参数是 fading 完成后所执行的函数名称。

#### 1.jQuery fadeIn() 方法

jQuery fadeIn() 用于淡入已隐藏的元素。

下面的例子演示了带有不同参数的 fadeIn() 方法：

~~~js
$("button").click(function () {
    $("#div1").fadeIn();
    $("#div2").fadeIn("slow");
    $("#div3").fadeIn(3000);
});
~~~

#### 2.jQuery fadeOut() 方法

jQuery fadeOut() 方法用于淡出可见元素。

~~~js
$("button").click(function(){
  $("#div1").fadeOut();
  $("#div2").fadeOut("slow");
  $("#div3").fadeOut(3000);
});
~~~

#### 3.jQuery fadeToggle() 方法

jQuery fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。

如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果。

如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果。

~~~js
$("button").click(function(){
  $("#div1").fadeToggle();
  $("#div2").fadeToggle("slow");
  $("#div3").fadeToggle(3000);
});
~~~

#### 4.jQuery fadeTo() 方法

jQuery fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。

**语法:**

$(*selector*).fadeTo(*speed,opacity,callback*);

fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。

~~~js
//fadeTo()  没有默认参数，必须加上  slow/fast/Time 
$("button").click(function(){
  $("#div1").fadeTo("slow",0.15);
  $("#div2").fadeTo("slow",0.4);
  $("#div3").fadeTo("slow",0.7);
});
~~~

## 3.jQuery 效果 - 滑动

#### jQuery 滑动方法

通过 jQuery，您可以在元素上创建滑动效果。

jQuery 拥有以下滑动方法：

- slideDown()
- slideUp()
- slideToggle()

#### 1.slideDown() 方法

jQuery slideDown() 方法用于向下滑动元素。

**语法:**

~~~js
$(selector).slideDown(speed,callback);
~~~

#### 2.slideUp() 方法

jQuery slideUp() 方法用于向上滑动元素。

**语法:**

~~~
$(selector).slideUp(speed,callback);
~~~

#### 3.slideToggle() 方法

jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们。

如果元素向上滑动，则 slideToggle() 可向下滑动它们。

#### **以上三个方法的事例**：

~~~html
<head>
  <style type="text/css">
    #panel,
    #flip1,
    #flip2,
    #flip3 {
      padding: 5px;
      text-align: center;
      background-color: #e5eecc;
      border: solid 1px #c3c3c3;
    }

    #panel {
      padding: 50px;
      display: none;
    }

  </style>
  <script>
    $(function () {
      //slideDown()方法
      $("#flip1").click(function () {
        $("#panel").slideDown("slow");
      });

      //slideUp()方法
      $("#flip2").click(function () {
        $("#panel").slideUp();
      });

      //slideToggle()方法
      $("#flip3").click(function () {
        $("#panel").slideToggle();
      });
    });
  </script>
</head>

<body>
  <div id="flip1">点我下滑面板</div>
  <div id="flip2">点我上滑面板</div>
  <div id="flip3">点我上滑/下滑面板</div>
  <div id="panel">Hello world! ! !</div>
</body>
~~~

