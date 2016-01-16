---
title: CSS生成邮箱图片
date: 2016-01-09 16:46:30
categories: [➎电脑技术, 经验技巧]
tags: [教程, css]
---

Goole搜索`online css button maker`会出来很多网站，我们选择第一个网站即：<http://css3buttongenerator.com/>，然后可以自定义文字、边框和背景颜色等，调整好自己的样式后，复制下面的CSS代码。
注意到代码中有`hover`，[Goole了下][1]，发现[行内样式不能引用伪类hover][2]，所以只能去掉它的`hover`代码。
于是我们写在`markdown`中的最终的代码如下：
``` bash
<a href="mailto:abc@xyz.com" style=
" background: #3498db;
  -webkit-border-radius: 28;
  -moz-border-radius: 28;
  border-radius: 28px;
  font-family: Arial;
  color: #ffffff;
  font-size: 20px;
  background: #3498db;
  padding: 10px 20px 10px 20px;
  text-decoration: none;">abc@xyz.com</a>
```
效果如下：

<a href="mailto:abc@xyz.com" style=
" background: #3498db;
  -webkit-border-radius: 28;
  -moz-border-radius: 28;
  border-radius: 28px;
  font-family: Arial;
  color: #ffffff;
  font-size: 20px;
  background: #3498db;
  padding: 10px 20px 10px 20px;
  text-decoration: none;">abc@xyz.com</a>

  [1]: https://www.google.com/#newwindow=1&q=hover+inline+css
  [2]: http://stackoverflow.com/questions/1033156/how-to-write-ahover-in-inline-css