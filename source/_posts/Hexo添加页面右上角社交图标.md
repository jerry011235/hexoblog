---
title: Hexo添加页面右上角社交图标
date: 2015-05-28 18:19:25
categories: [➎电脑技术, hexo]
tags: [hexo, 教程, 图标]
toc: true
---
# 下载图标文件
在网上下载你喜欢的社交图标文件，我使用的是[https://github.com/nullice/NViconsLib_Silhouette][1]这里的图标文件，这个图标集几乎涵盖了国内外的所有图标，还很漂亮。
到官网提供的[网盘][2]下载后，在`Sample`文件夹中选择几个你喜欢的图标，我选择的是`sample_flat\32px`里的知乎、简书和微博这三个文件。用图标软件或者在线工具调整大小为25×25px，然后分别重命名为`zhihu.png`、`jianshu.png`以及`weibo.png`后放到`D:\hexo\source\images`目录里。
# 添加图标代码
打开`D:\hexo\themes\landscape-plus\layout\_partial\header.ejs`文件，找到`<nav id="sub-nav">`，然后修改为如下代码（从21行到32行）：
``` bash
      <nav id="sub-nav">	   	  
       <a class="nav-icon-social" href="http://www.jianshu.com/users/e2bf41f8a517/latest_articles" title="简书" target="_blank"><img src="/images/jianshu.png"></a>
	   
	   <a class="nav-icon-social" href="http://www.zhihu.com/people/istarsky" title="知乎" target="_blank"><img src="/images/zhihu.png"></a>
	   
	   <a class="nav-icon-social" href="http://weibo.com/istarsky" title="微博" target="_blank"><img src="/images/weibo.png"></a>
	   
        <% if (theme.rss){ %>		
          <a id="nav-rss-link" class="nav-icon" href="<%- theme.rss %>" title="RSS Feed"></a>
        <% } %>
        <a id="nav-search-btn" class="nav-icon" title="Search"></a>	
      </nav>
```
上面代码的图标地址使用的是本地的相对地址，当然也可以使用直接的网络图片的地址。
<!--more-->
# 修改图标样式
打开`D:\hexo\themes\landscape-plus\source\css\_partial\header.styl`文件，找到`.nav-icon`（第86行），然后修改为如下代码,然后再要添加一个`.nav-icon-social`：
``` bash
.nav-icon-social
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: font-size
  width: font-size
  height: font-size
  right: 5px
  top: 8px
  padding: 10px 23px
  position: relative
  cursor: pointer
  
.nav-icon
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: 16px
  width: font-size
  height: font-size
  top: 10px
  padding: 10px 18px
  position: relative
  cursor: pointer
```
为了和右侧的文字大小一致，我们要修改下页面左侧的“首页”“文章列表”“关于”“联系”等的字体大小和高度，我们先去`D:\hexo\themes\landscape-plus\layout\_partial\header.ejs`文件中发现首页主链接的class属性为`class="main-nav-link"`，于是我们就打开`D:\hexo\themes\landscape-plus\source\css\_partial\header.styl`文件，在`.main-nav-link`（第113行）下添加一行`font-size: 16px`（调整字体大小）；然后在下面又添加两行`top: -2px`和`position: relative`来保证和右侧的图标在同一高度和同一直线上。
修改后：
``` bash
.main-nav-link
  @extend $nav-link
  font-size: 16px
  font-weight: 300
  letter-spacing: 1px
  top: -2px
  position: relative
  @media mq-mobile
    display: none
```



  [1]: https://github.com/nullice/NViconsLib_Silhouette
  [2]: http://pan.baidu.com/s/18jcWe