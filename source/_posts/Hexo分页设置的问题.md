---
title: Hexo分页设置的问题
date: 2015-05-18 21:41:06
categories: [⛺电脑技术, hexo]
tags: [hexo, 教程, 分页]
---
最近使用Landscape-plus主题发现了一个分页问题，即点击文章列表或者某一个分类时，如果设置开启分页和每页显示文章数，但是开启后页面下方却没有翻页数字标识。

折腾了一下，似乎这个主题不支持吧。目前只能做如下设置，即关闭分页，另外设置每页显示文章数是一个很大的数字（我设置为100），基本能满足需要。如果你的某一个分类（比如`hexo`）写的文章实在多，都超过100篇了，你可以在文章中设置另一个分类，取一个相似的名字（比如`hexo2`）。
``` bash
# Archives
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 1
category: 1
tag: 1

index_generator:
  per_page: 9 ##首页默认9篇文章标题 如果值为0不分页
archive_generator:
    per_page: 100 ##归档页面默认100篇文章标题
    yearly: true  ##生成年视图
    monthly: true ##生成月视图
tag_generator:
    per_page: 100 ##标签分类页面默认100篇文章
category_generator: 
    per_page: 100 ###分类页面默认100篇文章

```
