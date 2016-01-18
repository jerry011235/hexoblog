---
title: markdown禁止自动排序
date: 2015-06-02 22:05:16
categories: [o(^▽^)┛电脑技术, markdown]
tags: [markdown, 教程]
---
2015-11-20更新：其实更简单的做法是：不按照markdown语法写就行了，在`1.`后不加空格，直接输入字符即可。
可以用notepad++编辑器而不是小书匠编辑器，这样在修改编辑时，在本地的编辑器里就不会自动排序了。

有时在写多个列表时不希望markdown自动排序，我们可以在上一列表结束后回车空一行，然后在下一个列表的“数字”和“\.”之间加一个反斜杠`\`即可。
例如：
<!--more-->
``` c
## 特殊符号大全

 1. http://tw.piliapp.com/symbol/
 2. http://w13.loxa.edu.tw/ctjh930220/
 3. http://star.gg/special-symbols
 4. http://www.1t2t.com/3t/soft/28.htm
 
## FontAwesome对应CSS值
 1\. [A list of Font Awesome icons and their CSS content values][5]
 3\. [Every Font Awesome 4.3.0 Icon, CSS Class, & Unicode][6]
 2\. [Font Awesome icons and their CSS content values][7]
```
效果如下：
## 特殊符号大全

 1. http://tw.piliapp.com/symbol/
 2. http://w13.loxa.edu.tw/ctjh930220/
 3. http://star.gg/special-symbols
 4. http://www.1t2t.com/3t/soft/28.htm
 
## FontAwesome对应CSS值
1\. [A list of Font Awesome icons and their CSS content values][5]
3\. [Every Font Awesome 4.3.0 Icon, CSS Class, & Unicode][6]
2\. [Font Awesome icons and their CSS content values][7]