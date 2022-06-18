---
title: Flask迁移mysql数据库报错汇总
author: 李学志
img: medias/featureimages/22.jpg
top: false
cover: false
toc: true
mathjax: false
summary: Flask迁移mysql数据库报错汇总
categories: Flask迁移mysql数据库报错汇总
tags:
  - Flask迁移mysql数据库报错汇总
keywords: 李学志
essay: false
abbrlink: 44049
date: 2022-05-27 16:25:40
coverImg:
password:
---

# Flask迁移mysql数据库报错汇总

### **错误一：ERROR:root:Error: Directory migrations already exists**

![image-20220527162751919](http://image.lxzcode520.xyz/img/image-20220527162751919.png)

- 原因是：之前已经执行过一次 python3 manage.py db init 命令，已经存在migrations文件夹。**迁移环境只需要创建一次，后续不需要重新创建。**



### **错误二：误删migrations文件夹后再次创建时遭遇错误（Can't locate revision identified by ‘xxx’）**

原因是当把后台与数据库建立关系后，双方会分别产生一个“接口”，后台的“接口”是migrations文件夹中的versions文件夹中的文件；数据库的“接口”是这个表“alembic_version” ，我把migrations删除后，alembic_version没有改变。当我新建一个migrations后，两个“接口”对不上了，所以会报错。所以这种错误最简单的解决办法就是把数据库中的alembic_version表删掉，然后就可以继续后面的操作了


### **错误三：执行python3 manage.py db migrate 时，**

![image-20220527163124721](http://image.lxzcode520.xyz/img/image-20220527163124721.png)

- 原因是在项目中没有导入模型类，迁移时无法读取对应的模型。解决方法：

我的模型类定义在models.py中，项目是manage.py，所以只需要在manage,py中写上 from info import models

### **错误四:AttributeError: module 'datetime' has no attribute 'now'**

+ 原因是我导入时写成了import datetime  代码中用上datetime.now，而datetime中没有now这个属性，解决方法： from datetime import datetime （这里是我不太了解datetime这个包的情况，import datetime 和from datetime import datetime竟然不一样）


### 错误五：AttributeError: 'function' object has no attribute '_set_parent_with_dispatch'

原因是定义字段时出错 content = db.Column(db.text, nullable=False)   db.Text需要大写，这里给个总结：Flask中db.后面的第一个字母都需要大写，很多时候就是因为一个大小写困扰半天

### 错误六：sqlalchemy.exc.NoReferencedTableError: Foreign key associated with column 'info_user_collection.news_id' could not find table 'info_news,id' with which to generate a foreign key to target column 'None'

原因很简单，还是粗心大意，定义关联表时，db.ForeignKey('info_news，id')  info_news,id 应该是info_news.id  不是,而是.



#### **文章来自CSDN，第一次进行迁移就踩了三个坑，保存一下方便下次看  呜呜呜 ~~~~**

原文地址: https://blog.csdn.net/wenpy/article/details/99829375
