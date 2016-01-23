---
title: Hexo自定义分类顺序
date: 2015-12-23 21:36:20
categories: [⛺电脑技术, hexo]
tags: [教程, hexo, 分类]
toc: true
---
Hexo的默认分类顺序不知道是按照什么规律排序的，如果想手动自定义分类的顺序，可以使用分类前面加上**数学序号**或其他特殊符号的办法。

调试可以直接替换，也可以先备份好`source`文件夹，然后每个分类只保留一篇文章，接着替换好以后再复制粘贴回去即可。
## 分类前面添加数学序号 ##

具体操作为：打开Sublime Text 3，然后按`Ctrl + Shift + F`（进行[多文件搜索][1]），在位置那一栏输入`D:\hexo\source\_posts`，查找那一栏输入`电脑技术`（某一个分类），然后在替换那一栏输入`➎电脑技术`（其中➎我是使用拼音加加输入法打出来的，其实在网上搜索特殊符号大全可以直接复制相应的[数学序号][2]）。

最后直接点击替换，然后文件，保存全部即可。
<!--more-->

## 分类前面添加特殊符号 ##
在网上搜索`特殊符号排序`可以得到下面两个参考资料：

 - [按名称排列时特殊符号排列顺序问题——百度知道][3]
 - [windows中文件或者文件名是按照什么原则排序的？命名时有什么技巧？——知乎][4]

然后我自己又试验了下，就是打开输入法的软键盘，调到特殊符号，然后先在记事本上输入所有的特殊符号，然后在D盘新建一个名为`特殊符号排序测试`的文件夹，然后在里面一个一个新建文件夹，文件夹名字为记事本的特殊符号。排序结果如下：
``` bash
―＃＆＠＼＿￣︿¤€■□▲△◆◇○◎●↑→↓←§°〓★♀♂‰※℃№
```
如图：
![特殊符号排序测试][5]
然后按照自己的喜好在分类前面添加特殊符号，最后按照上面的操作用Sublime Text 3进行替换保存即可。

## 分类前面添加颜文字和emoji表情 ##
既然能支持特殊符号，当然也能支持颜文字，如果你有更创意的想法，还能支持emoji表情哦👌
![颜文字排序][6]
## 更新记录 ##
2016-1-16更新分类为：
``` bash
( •̀ .̫ •́ )✦哲思感悟
(^▽^)♫♫♫原创诗词
o(^▽^)┛电脑技术
└(^o^)┘他山之石
╰(⊙_⊙)╯默认分类
```
2016-1-20更新分类为：
``` bash
☘原创诗词
☯️哲思感悟
⛺电脑技术
❤️他山之石
🍎默认分类
```

## 附录 ##
### 特殊符号网站 ###

 - [符号之家][7]
 - [特殊符号][8]

### emoji表情网站 ###
 - [Get Emoji][9]
 - [Emoji Ordering][10]

### 颜文字网站 ###

 - [搜狗颜文字][11]
 - [颜文字表情符号大全][12]
 - [【转】颜文字大全(～￣▽￣)～][13]


  [1]: https://sublime-text.readthedocs.org/en/latest/search_and_replace/search_and_replace_files.html
  [2]: http://www.fuhao123.com/fuhao/4.shtml
  [3]: http://zhidao.baidu.com/question/111363523.html
  [4]: https://www.zhihu.com/question/20227012
  [5]: http://7xivmb.com1.z0.glb.clouddn.com/hexo%E8%87%AA%E5%AE%9A%E4%B9%89%E5%88%86%E7%B1%BB%E9%A1%BA%E5%BA%8F-%E7%89%B9%E6%AE%8A%E7%AC%A6%E5%8F%B7%E6%8E%92%E5%BA%8F.png
  [6]: http://7xivmb.com1.z0.glb.clouddn.com/hexo%E8%87%AA%E5%AE%9A%E4%B9%89%E5%88%86%E7%B1%BB%E9%A1%BA%E5%BA%8F-%E9%A2%9C%E6%96%87%E5%AD%97%E6%8E%92%E5%BA%8F.png
  [7]: http://www.fuhao123.com/
  [8]: http://tw.piliapp.com/symbol/
  [9]: http://getemoji.com/
  [10]: http://unicode.org/emoji/charts/emoji-ordering.html
  [11]: http://pinyin.sogou.com/dict/ywz/
  [12]: https://www.douban.com/note/83616009/
  [13]: https://www.douban.com/note/235557738/