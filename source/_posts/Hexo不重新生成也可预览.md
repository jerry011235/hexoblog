---
title: Hexo不重新生成也可预览
date: 2015-05-07 20:30:25
categories: [⛺电脑技术, hexo]
tags: [教程, hexo]
toc: true
---

# 方法一：用[hexo-browsersync][1]插件
按照官网的操作只有一行代码：
``` bash
$ npm install hexo-browsersync --save
```
安装好后，不需任何设置，直接打开`hexo s`即可。

修改文章后，当你按下`Ctrl+S`保存时，页面自动刷新产生改变，同时右上角显示`Connected to BrowserSync`字样。



<!--more-->


# 方法二：用[hexo-livereload][2]插件
``` bash
$ npm install hexo-livereload --save
```
然后在站点的`_config.yml`中配置 livereload 的端口为`35729`：
```
livereload:
  port: 35729
```
即可。
**经过测试，不设置端口也可以。**

然后我们随便打开一篇博文，修改后**保存**，然后直接使用`hexo s`命令启动服务预览，在保持服务启动的状态下，再次修改该文章，记住要**保存**，然后**刷新**http://localhost:4000 即可看到变化。

# 优缺点
如果使用`hexo-browsersync`，在连接网络的情况下，启动服务`hexo s`能很快地打开；而在没有网络的情况下，输入`hexo s`后至少要过5分钟才能启动服务进行预览。但保存后不用刷新即可看到变化。
而`hexo-livereload`在无论离线还是有网时都能很快打开，但是保存后需要手动刷新才能看到变化。

另外，编辑主题的`_config.yml`可以实时预览。而编辑`D:\hexo\_config.yml`文件不能实时预览，需要重新生成后再预览：
```
hexo s -g
```



参考：

 - https://github.com/hexojs/hexo-browsersync
 - http://hahack.com/codes/livereload-for-hexo/
 - https://github.com/hexojs/hexo-livereload


  [1]: https://github.com/hexojs/hexo-browsersync
  [2]: https://github.com/hexojs/hexo-livereload