---
title: Hexo博客移动端适配的优化
date: 2015-11-20 13:29:35
categories: [➎电脑技术, hexo]
tags: [hexo, 教程, 移动端]
toc: true
---

## 调试小技巧 ##
以前我总是很笨地在本地修改完代码，然后使用`hexo clean && hexo g && hexo d`重新上传部署，等部署完成后再在手机上打开我的博客，然后刷新页面，看看有哪些变化。这样操作很慢也很费时。

但是最近我偶然发现一个小技巧，就是直接把chrome窗口缩小，等他的宽度缩小到和手机一样大时，电脑上的chrome就自动适配成手机窗口，这样就可以方便地查看变化，也可以像手机一样点击按钮了。
如果再用第三方软件或手势把该chrome窗口置顶，那就比较舒服了：）

另一个技巧就是在chrome浏览器中按F12，调出审查元素，然后点击最左端的搜索图标，就可以单独页面上查看任意元素的样式。然后再点击元素，就可以在右侧的`Styles`选项的下方调整其代码，而且**改动实时生效**，代码改动完页面相应元素马上就会改变，显示出效果，这点非常棒！等到调整满意后就复制到别的地方备份一下。因为只要一刷新，页面就会恢复成原来的样子。
<!--more-->
## 修改标题顶部分类的位置 ##
当屏幕变窄后，标题顶部的分类和其上面日期的相对位置就有些错位。我们通过下面的操作让他们变整齐。

编辑`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，找到`.article-category`条目，在最底部增加一个移动适配的代码：
``` bash
  @media mq-mobile
    margin-left: 5px
    margin-bottom: 10px	
```
增加后整个`.article-category`条目就变成如下形式：
``` bash
.article-category
  font-weight: bold
  font-family: "微软雅黑"
  float: left
  line-height: 1em
  color: #ccc
  text-shadow: 0 1px #fff
  margin-left: 20px
  &:before
    font-family: font-icon
    content: "\f06c"
  @media mq-mobile
    margin-left: 5px
    margin-bottom: 10px	
```
保存好。

## 修改页面顶部图标的位置 ##
在手机端打开我的博客会发现页面顶部的社交图标和搜索rss图标都只能显示一半或者一部分界面，图标内容显示不完全，经过一番探索，终于调整好了，编辑`D:\hexo\themes\landscape-plus\source\css\_partial\header.styl`文件，依次修改以下条目即可：
``` bash
.nav-icon-social
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: font-size
  width: font-size
  height: font-size
  right: 5px
  top: 10px
  padding: 10px 23px
  position: relative
  cursor: pointer
  @media mq-mobile
    padding-left: 25px

.nav-icon
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: 16px
  width: font-size
  height: font-size
  top: 0px
  //padding: 10px 18px
  position: relative
  cursor: pointer

#nav-rss-link
  &:before
    content: "\f09e"
  @media mq-mobile
    top: 0px

#nav-search-btn
  &:before
    content: "\f002"
  @media mq-mobile
    top: 0px
```
后来在调试中偶然在`.nav-icon`中的`padding`前面加两道杠注释掉，结果社交图标竟然完全显示出来了，于是知道就是这行代码使得其他图标只能显示出一半。然后用审查元素发现移动端页面左上角的“四道杠”对应的样式是`#main-nav-toggle`，然后调整其高度为`10px`，接下来就只需要调整社交图标和搜索rss图标的高度了，调整好后把chrome窗口最大化一看，和左侧的导航又不一致，结果还要改导航样式`.main-nav-link`的高度。**修改时可以参考以前修改好的，是一条直线时的各个元素的高度，把相对位置记录下，调整高度就很方便了。**

下面就是修改后的代码：
``` bash
.nav-icon-social
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: font-size
  width: font-size
  height: font-size
  right: 5px
  top: 20px
  padding: 10px 23px
  position: relative
  cursor: pointer
  @media mq-mobile
    top: 20px
    
.nav-icon
  @extend $nav-link
  font-family: font-icon
  text-align: center
  font-size: 16px
  width: font-size
  height: font-size
  top: 10px
  //padding: 10px 18px
  position: relative
  cursor: pointer
  
 .main-nav-link
  @extend $nav-link
  font-size: 16px
  font-weight: 300
  letter-spacing: 1px
  top: 8px
  position: relative
  @media mq-mobile
    display: none
    
#main-nav-toggle
  top: 10px
  display: none
  &:before
    content: "\f0c9"
  @media mq-mobile
    display: block
```
上述两段代码都可以实现目标，任择其一，保存后重新部署即可。
后来发现`.nav-icon`控制“四道杠”和搜索rss图标。所以在第二段代码调整完`.nav-icon`，就要调整`#main-nav-toggle`（四道杠）而搜索rss图标不变，保证他们在同一直线；而第一段代码是`#main-nav-toggle`（四道杠）不变，单独调整搜索rss图标的位置（`#nav-rss-link`和`#nav-search-btn`）。

## 修改页面底部座右铭的位置 ##
当页面变窄后，底部座右铭就会超出界限，又是一番苦苦地调试和反复修改，终于解决了这个问题。

编辑`D:\hexo\themes\landscape-plus\source\css\_partial\footer.styl`文件，添加如下代码：
``` bash
.footer-text
  font-family: "楷体"
  //font-family: "隶书"
  font-size: 22px
  padding: 0px 70px
  @media mq-mobile
    padding: 0px
```
然后编辑`D:\hexo\themes\landscape-plus\layout\_partial\footer.ejs`文件，把原先的代码改成：
``` bash
  <div class="footer-text">人不是因为没有信念而失败，而是因为不能把信念化成行动，并且坚持到底。——戴尔·卡耐基《人性的弱点》
  </div> 
```
2015-12-8 更新：[更新见这里][1]。

就这样终于好了，最近感觉是有点强迫症了，哈哈！不过在这个过程中也确实学到了很多知识：）

## 总结 ##
一开始想到搜索关键词`mobile`来获取更多帮助和信息，这个方向是对的，但是全凭瞎撞，在`D:\hexo\themes\landscape-plus\source\css\_partial\mobile.styl`文件里添加样式也无效果，结果摸索了一阵才发现：只要在正常的样式后面加上`@media mq-mobile`，再在其后紧跟上的样式就可以适配到手机等移动端了。这样`@media mq-mobile`上面就是电脑的样式，下面就是手机的样式，可以按需调整。


  [1]: https://gitcafe.com/starsky/hexoblog/commit/948a3f7ff78ca358bdcfa7c1a54ebd8ac5ee1859?split=true