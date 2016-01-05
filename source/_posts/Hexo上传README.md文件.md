---
title: Hexo上传README.md文件
date: 2015-12-31 14:33:25
categories: [➎电脑技术, hexo]
tags: [教程, hexo]
---
在`D:\hexo\source`目录下新建一个`README.md`文件，并编辑输入以下内容：
``` bash
# 我的hexo博客
# [http://jerry011235.github.io][1]
# [http://starsky.gitcafe.io][2]


```
然后编辑站点的`_config.yml`文件即`D:\hexo\_config.yml`文件，添加一行：
``` bash
skip_render: README.md
```
目的是防止`README.md`文件被渲染。
保存后就OK了。
然后`hexo clean && hexo g`发现`README.md`文件已经生成在`D:\hexo\public`文件夹中。

参考：

 - [怎么用hexo上传一个README.md到github?][3]
 - [Hexo系列教程: (五)部署时保证README.md不被渲染][4]


  [1]: http://jerry011235.github.io/
  [2]: http://starsky.gitcafe.io/
  [3]: https://www.zhihu.com/question/28058973
  [4]: http://iread.io/2015/09/hexo-guide-5/