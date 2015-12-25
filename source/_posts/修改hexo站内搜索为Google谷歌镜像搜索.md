---
title: 修改hexo站内搜索为Google谷歌镜像搜索
date: 2015-11-12 12:19:16
categories: [➎电脑技术, hexo]
tags: [教程, hexo, 站内搜索]
---

因为最近一阵[微搜索][1]半死不活，就连它自己官网上的站内搜索也挂了，而[swiftype][2]对中文汉字的识别又太差，所以想找一个靠谱的站内搜索，但是找来找去没找到，于是只好用自带的谷歌，但是谷歌在国内又是“你懂的”的状态。于是就有了这篇教程：修改hexo站内搜索为Google谷歌镜像搜索。

如果以前安装过微搜索，那么先对《[为Hexo添加微搜索][3]》其中的步骤进行逆操作：删除`tinysou.ejs`文件，删除相关文件中的`<%- partial('tinysou') %>`以及`tinysou: true`这几行代码。然后编辑`D:\hexo\themes\你的主题目录\layout\_partial目录下面的header.ejs`文件，把`<div id="search-form-wrap">`标签恢复成如下样式：
``` bash
      <div id="search-form-wrap">
        <%- search_form({button: '&#xF002;'}) %>
      </div>
```
<!--more-->

然后我们先去github的[hexo-theme-landscape][4]，在`This repository`中搜索关键字`google sarch`，但是没发现什么有价值的信息，于是转到大本营[hexo][5]搜搜看，[结果][6]很令人兴奋啊，于是知道了关键文件是`search_form.js`，马上打开`everything`，搜索`search_form.js`，得知在目录`D:\hexo\node_modules\hexo\lib\plugins\helper`下，这个路径也和网上搜索到的`lib/plugins/helper/search_form.js`路径类似，于是这个文件就是我们要修改的。

那我们使用Notepad++打开`D:\hexo\node_modules\hexo\lib\plugins\helper\search_form.js`文件，在第12行`return`标签后面，把`google.com`替换成你自己找的谷歌google镜像域名，我替换成`igogo.me`，然后我想把占位符从英文的“search”改成中文的“搜索”，于是修改第13行的`placeholder="'`为`placeholder="搜索"'`，这样就大功告成了。

修改后的代码如下：
``` bash
  return '<form action="//igogo.me/search" method="get" accept-charset="UTF-8" class="' + className + '">' +
    '<input type="search" name="q" results="0" class="' + className + '-input"' + (text ? ' placeholder="搜索"' + text + '"' : '') + '>' +
    (button ? '<button type="submit" class="' + className + '-submit">' + (typeof button === 'string' ? button : text) + '</button>' : '') +
    '<input type="hidden" name="sitesearch" value="' + config.url + '">' +
    '</form>';
```

最后只要`hexo clean && hexo g && hexo d`重新部署上传就OK了。


  [1]: http://tinysou.com/
  [2]: https://swiftype.com
  [3]: http://starsky.gitcafe.io/2015/05/11/%E4%B8%BAHexo%E6%B7%BB%E5%8A%A0%E5%BE%AE%E6%90%9C%E7%B4%A2/
  [4]: https://github.com/hexojs/hexo-theme-landscape
  [5]: https://github.com/hexojs/hexo
  [6]: https://github.com/hexojs/hexo/search?utf8=%E2%9C%93&q=google%20search