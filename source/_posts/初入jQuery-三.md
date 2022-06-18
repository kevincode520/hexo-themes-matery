---
title: 初入jQuery(三)
author: 李学志
img: medias/featureimages/15.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 初入jQuery(三)
categories: 初入jQuery(三)
tags:
  - 初入jQuery(三)
keywords: 李学志
essay: false
abbrlink: 28609
date: 2022-05-29 14:34:06
coverImg:
password:
---

# 初入jQuery(三)

## 1.jQuery - 获取内容和属性

### jQuery DOM 操作

jQuery 中非常重要的部分，就是操作 DOM 的能力。

jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。

### 获得及设置内容 - text()、html() 以及 val()

三个简单实用的用于 DOM 操作的 jQuery 方法：

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标记）
- val() - 设置或返回表单字段的值

### 获取及设置属性 - attr()

jQuery attr() 方法用于获取属性值。

### **以上方法实例：**

~~~HTML
<script>
    $(document).ready(function () {
        // text()方法 显示原本的值
        $("#btn1").click(function () {
            alert("Text:" + $("#test").text());
            // $("#test").text("Hello world! ! !");
            $("#test").html("<h1>Hello world! ! !</h1>");
        });

        // html() 显示HTML的内容
        $("#btn2").click(function () {
            alert("HTML:" + $("#test").html());
        });

        // val() 获得输入字段的值
        $("#btn3").click(function () {
            alert("值为:" + $("#test2").val());
            // 设置
            $("#test2").val("jQuery向你问好");
        });

        //  attr() 方法用于获取属性值
        $("#btn4").click(function () {
            alert($("#jquery").attr("href"));
            // 修改 href 和 title
            $("#jquery").attr({
                "href": "http://www.xxx.com/jquery",
                "title": "jQuery 教程"
            });
            // 通过修改的 title 值来修改链接名称
            title = $("#jquery").attr('title');
            $("#jquery").html(title);
        });
    });
</script>

<body>
  <p id="test">这是段落中的 <b>粗体</b> 文本。</p>
  <button id="btn1">显示文本</button>
  <button id="btn2">显示 HTML</button>
  <div>
    <p>名称: <input type="text" id="test2" value="jquery"></p>
    <button id="btn3">显示值</button>
  </div>
  <div>
    <p><a href="http://www.xxxxxx.com" id="jquery">jquery</a></a></p>
    <button id="btn4">显示 href 属性的值</button>
  </div>
</body>
~~~

## 2.添加元素

**添加新的 HTML 内容**

我们将学习用于添加新内容的四个 jQuery 方法：

- append() - 在被选元素的结尾插入内容
- prepend() - 在被选元素的开头插入内容
- after() - 在被选元素之后插入内容
- before() - 在被选元素之前插入内容

### append()与prepend()方法

~~~HTML
<script>
    $(document).ready(function () {
        // append() 方法在被选元素的结尾插入内容（仍然在该元素的内部
        $("#btn1").click(function () {
            $("p").append("<b>追加文本</b>");
        });
        $("#btn2").click(function () {
            $("ol").append("<li>追加列表项</li>")
        });

        // prepend() 方法在被选元素的开头插入内容
        $("#btn3").click(function () {
            $("p").prepend("<b>在开头追加文本</b>");
        });
        $("#btn4").click(function () {
            $("ol").prepend("<li>在开头追加列表项</li>")
        });
    });
</script>
<body>
    <p>这是一个段落。</p>
    <p>这是另外一个段落。</p>
    <ol>
        <li>List item 1</li>
        <li>List item 2</li>
        <li>List item 3</li>
    </ol>
    <button id="btn1">append添加文本</button>
    <button id="btn2">append添加列表项</button>
    <button id="btn3">prepend添加文本</button>
    <button id="btn4">prepend添加列表项</button>
</body>
~~~

+ 通过 append() 和 prepend() 方法添加若干新元素

~~~js
function appendText(){
    var txt1="<p>文本-1。</p>";              // 使用 HTML 标签创建文本
    var txt2=$("<p></p>").text("文本-2。");  // 使用 jQuery 创建文本
    var txt3=document.createElement("p");
    txt3.innerHTML="文本-3。";               // 使用 DOM 创建文本 text with DOM
    $("body").append(txt1,txt2,txt3);        // 追加新元素
}
~~~

### after() 和 before() 方法

jQuery after() 方法在被选元素之后插入内容。

jQuery before() 方法在被选元素之前插入内容。

~~~js
$("img").after("在后面添加文本");
 
$("img").before("在前面添加文本");
~~~

## 3.删除元素

如需删除元素和内容，一般可使用以下两个 jQuery 方法：

- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素

### remove() 方法

~~~js
// remove() 方法删除被选元素及其子元素。
$("#button1").click(function () {
    $("#div1").remove();
});
~~~

### empty() 方法

~~~js
// empty() 方法删除被选元素的子元素。
$("#button2").click(function () {
    $("#div1").empty();
});
~~~

### 过滤被删除的元素

jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤。

该参数可以是任何 jQuery 选择器的语法。

下面的例子删除 class="italic" 的所有 <p> 元素：

~~~js
$("#button3").click(function () {
    $("p").remove(".italic");
});
~~~

