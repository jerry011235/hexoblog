---
title: Hexo自动随机切换顶部图片
date: 2015-05-06 15:53:27
categories: [➎电脑技术, hexo]
tags: [教程, hexo]
toc: true
---
### 先新建一个switch-banner.ejs文件
我先用Everything搜索`*.ejs`，然后随便复制一个ejs文件（最好是D盘的）到桌面。

然后用Notepad++打开，全部删除原来的代码，然后粘贴以下代码：
```
<script>
    <% if (theme.switch_banner){ %>
    var number_of_banners = 6;
    var randnum = Math.floor(Math.random() * number_of_banners + 1);
    document.getElementById("banner").style.backgroundImage = "url(/css/images/banner" + randnum + ".jpg)";
    <% } else { %>
    document.getElementById("banner").style.backgroundImage = "url(/css/images/banner.jpg)";
    <% } %>
</script>
```
保存后放到`themes\你的主题目录\layout\_partial\`，我就把他拖进`D:\hexo\themes\landscape-plus\layout\_partial`目录下。
<!--more-->
### 调用switch-banner.ejs文件
编辑`themes\你的主题目录\layout\_partial\header.ejs`,在最后一行（`</header>`标记）之前加入一行`<%- partial('switch-banner') %>`即可。
```
    </div>
  </div>
  <%- partial('switch-banner') %>
</header>
```

最后，编辑你的主题配置文件`themes\你的主题目录\_config.yml`，在里面添加：
``` bash
switch_banner: true
```

### 添加随机图片
在网上找6张高清图片（我找的是1920×1080），拖进`themes\你的主题目录\source\css\images`里，分别命名为banner1.jpg、banner2.jpg、banner3.jpg、banner4.jpg、banner5.jpg、banner6.jpg

最后在编辑`themes/你的主题目录/source/css/_partial/header.styl`，在`background: url(banner-url) center #000`的前面打两个f反斜杠注释掉。
```
#banner
  position: absolute
  top: 0
  left: 0
  width: 100%
  height: 100%
  //background: #21282E
  //background: url(banner-url) center #000
  background-size: cover
  z-index: -1
```

保存后重新部署。

OK! Enjoy!

参考：[http://kuangqi.me/tricks/hexo-banner-auto-switcher/](http://kuangqi.me/tricks/hexo-banner-auto-switcher/ "自动随机切换Hexo博客的banner图片")
