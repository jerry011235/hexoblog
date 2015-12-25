---
title: Hexo主题配置与优化（二）
date: 2015-05-06 14:38:26
categories: [➎电脑技术, hexo]
tags: [教程, hexo]
toc: true
---

## 修改调试技巧
在chrome浏览器中按F12，调出审查元素，然后点击最左端的搜索图标，就可以单独页面上查看任意元素的样式。然后再点击元素，就可以在右侧的`Styles`选项的下方调整其代码，而且**改动实时生效**，代码改动完页面相应元素马上就会改变，显示出效果，这点非常棒！等到调整满意后就复制到别的地方备份一下。因为只要一刷新，页面就会恢复成原来的样子。

## 添加网站小图标
到`D:\hexo\themes\landscape-plus\layout\_partial`编辑`head.ejs`文件，按`Ctrl＋f`查找关键词`favicon`，找到在第28行和第29行。
在 ` <% if (theme.favicon){ %>`的下面插入以下代码：

`<link href="<%- config.root %>favicon.ico" rel="icon" type="image/x-ico">`


即变成：

```
<% if (theme.rss){ %>
    <link rel="alternative" href="<%- theme.rss %>" title="<%= config.title %>" type="application/atom+xml">
  <% } %>
  <% if (theme.favicon){ %>
    <link href="<%- config.root %>favicon.ico" rel="icon" type="image/x-ico">
  <% } %>
  <%- css('css/style') %>
```

然后在网上找个好看的图标，或者去图标生成网站：[http://www.faviconer.com/](http://www.faviconer.com/)生成一个后缀名为`.ico`的图标文件，最后把该文件放到`D:\hexo\source`目录下，重新部署即可。

## 添加自定义404页面
直接新建一个404.html文件放到`D:\hexo\source`目录下，然后编辑即可，注意最上面要写：
``` bash
layout: false
---
```
### 404音乐电台
因为熊海做的这个音乐电台只有一个html文件和一张背景图片，所以可以添加到404页面（在此感谢熊海）。
在[这个百度网盘](http://pan.baidu.com/s/1gd3tnOJ)下载`熊海博客电台.rar`，然后新建一个404.html文件，在`---`下方粘贴代码，然后把这个文件放到`D:\hexo\source`和`D:\hexo\themes\landscape-plus`目录下，接着把下载文件中的`bg.jpg`放到`D:\hexo\source\images`目录下即可。
<!--more-->
## 修改正文字体大小及调整行间距
在`D:\hexo\themes\landscape-plus\source\css\_variables.styl`中的第34行，改为`font-size = 16px`，然后顺便把正文的行间距也一起改了：`line-height = 1.8em`。
但是改了后所有的行间距都变成`1.8em`了，我想把侧边栏的文字的行间距改小一点，于是去`D:\hexo\themes\landscape-plus\source\css\_partial\sidebar.styl`修改`.widget`下为`line-height: 1.6em`，**注意还要删掉`@extend $base-style`这一行才能起效果。**


## 修改副标题字体大小和颜色

### 修改副标题字体颜色

我想修改副标题的字体颜色，这里推荐给大家一个办法:
先去[爱词霸](http://www.iciba.com/) 翻译 “副标题字体颜色”，结果会出来 “Subtitle font color” ，然后去[hexo-theme-landscape](https://github.com/hexojs/hexo-theme-landscape/ "hexo-theme-landscape")，在上方的搜索框搜索`Subtitle font color`回车，然后我们就找到了修改字体颜色的目录为`hexo-theme-landscape（主题目录）/source/css/_partial/header.styl`，接着去我们自己相应的**主题目录**编辑`D:\hexo\themes\landscape-plus\source\css\_partial\header.styl`文件，还是搜索关键字`subtitle`，找到第60行修改为：
```
##subtitle
  @extend $logo-text
  font-size: subtitle-size
  line-height: subtitle-size
  letter-spacing: 5px
  color: ##fff
```
其中`letter-spacing`是字符间距，你可以调整它试一下，颜色color改为`##fff`白色，和主标题一致。


### 修改副标题字体大小
因为副标题字体大小的英语是`subtitle size`，所以同样在[hexo-theme-landscape](https://github.com/hexojs/hexo-theme-landscape/ "hexo-theme-landscape")中搜索`subtitle size`，得到[结果页面](https://github.com/hexojs/hexo-theme-landscape/search?utf8=✓&q=subtitle+size&type=Code "结果页面")，很明显看出要修改主题目录下的`source/css/_variables.styl `文件，于是查找`subtitle`后把16px改为20px：
```
// Header
logo-size = 40px
subtitle-size = 20px
banner-height = 300px
banner-url = "images/banner.jpg"
```
经过测试可以知道上面的`logo-size`表示你的主标题字体大小，而`你的主题目录/source/css/_partial/header.styl`文件中`logo-text`那一栏的下面color就表示主标题字体的颜色。

>**这里一定要提醒各位：`=` 和`:`后面一定要加个空格。**

修改后保存文件，然后在博客目录执行：
``` bash
hexo clean && hexo g && hexo d
```

重新部署后，刷新就会看到效果了。

## 调整右侧边栏顺序
编辑主题配置文件，比如你使用的默认主题，就到`D:\hexo\themes\landscape\_config.yml`调整`widgets:`那一栏的顺序。
原来的：
``` bash
widgets:
- category
- tagcloud
- archive
- recent_posts
```
改为：
``` bash
widgets:
- recent_posts
- category
- archive
- tagcloud
```
## 页面底部添加自定义文字
打开`D:\hexo\themes\landscape-plus\layout\_partial\footer.ejs`,在最底下  `</div>`的下面和`</footer>`上面之间插入以下代码：
``` bash
  <div style="font-family:楷体; font-size: 28px; position:relative; left: 350px;bottom:70px;">人不是因为没有信念而失败，而是因为不能把信念化成行动，并且坚持到底。
  </div>
  <div style="font-family:楷体; font-size: 28px; position:relative; left: 920px;bottom:50px;">——戴尔·卡耐基《人性的弱点》
  </div>   
```
2015-11-15更新：因为上述代码会撑大窗口，故而更新成下面的代码：
``` bash
  <div style="font-family:楷体; font-size: 22px;position:absolute;left: 220px;margin: -100px 0px 0px 0px;">人不是因为没有信念而失败，而是因为不能把信念化成行动，并且坚持到底。——戴尔·卡耐基《人性的弱点》
  </div> 
```
2015-11-20更新：增加单独样式以及移动端的适配。
具体详见另一篇博文：[Hexo博客移动端适配的优化][1]
## 修改返回顶部图标位置
觉得返回顶部图标的位置太高了，要调低点。
打开`D:\hexo\themes\landscape-plus\source\css\_partial\totop.styl`，第5行改为`bottom 2em`。

## 修改文章主题样式细节
### 添加标题顶部日期和分类的图标 
打开`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，修改`.article-date`（第16行）为：
``` bash
  &:before
    font-family: font-icon
    color: ##ccc
    content: "\f073"
```

`.article-date`第27行:
``` bash
  &:before
    font-family: font-icon
    content: "\f06c"
```
顺便调整一下日期前面图标的位置：`margin-left: 20px`
### 修改文章底部标签前面的图标
``` bash
.article-tag-list-link
  a&:hover
    color: color-link
  &:before
    content: "@"
```
这个图标我们使用特殊符号，而不使用`FontAwesome`图标，就不用写`font-family: font-icon`这一行代码，反之则要写。
直接把你要使用的特殊符号粘贴进`content`的双引号之间就行了。
>注意：
1.粘贴特殊符号时，在“notepad++”里是显示为“□”，但是部署或者启动服务预览后会显示出来。
2.上面的`  a&:hover  color: color-link`是指鼠标滑过“标签”时，会显示链接颜色。
3.查找一些常见的FontAwesome图标对应的CSS代码可以搜索关键词“FontAwesome CSS content values”。参见[文章底部的附录][2]。

### 标题前面加条蓝线
修改`.article-header`条目,添加`border-left`这一行：
``` bash
.article-header
  padding: article-padding article-padding 0
  border-left: 5px solid color-twitter     //标题前面加条蓝线
```
其中`color-twitter`在`D:\hexo\themes\landscape-plus\source\css\_variables.styl`第21行为蓝色，你也可以修改为其他颜色或者自定义一个新的颜色属性。

### 修改文章正文字体为宋体
打开`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，修改`.article`条目为：
``` bash
.article
  margin: block-margin 0
  font-family: SimSun   //修改正文字体为宋体
  letter-spacing: 1px   //调整文字间距
```
然后修改正文旁边的日期、分类、标题等其他字体为微软雅黑。
``` bash
.article-date              //修改正文旁边的日期字体
  font-family: "微软雅黑"   //添加这一行
```
同样也添加这一行到`article-category .article-header .article-tag-list-item .article-comment-link .article-share-link`这些条目中。

### 修改文章一到六级标题字体为微软雅黑，并且不加粗
编辑`D:\hexo\themes\landscape-plus\source\css\_extend.styl`文件，修改相关代码为如下：
``` bash
  h1
    font-family: "微软雅黑"      
    font-size: 1.5em
  h2
    font-family: "微软雅黑"  
    font-size: 1.5em
  h3
    font-family: "微软雅黑"  
    font-size: 1.3em
  h4
    font-family: "微软雅黑"  
    font-size: 1.2em
  h5
    font-family: "微软雅黑"  
    font-size: 1em
  h6
    font-family: "微软雅黑"  
    font-size: 1em
    color: color-grey
```
然后把他们不加粗只要删掉相关条目下的`font-weight: bold`和`font-weight`类似代码就OK。
先在landscape-plus的github主页[搜索`bold`][3]，发现相关代码的文件是`source/css/_extend.styl`和`source/css/_partial/article.styl `。
于是删除`source/css/_extend.styl`文件中`$base-style`下的`h1, h2, h3, h4, h5, h6`条目下的`font-weight: bold`代码，注意也要删除下方 `h2, h3, h4, h5, h6`条目下的`font-weight: 600`这一行代码。
接着去`source/css/_partial/article.styl `文件，删除`.article-entry`下的`h1, h2, h3, h4, h5, h6`条目下的`font-weight: bold`代码。
于是1-6级标题不加粗就完成了。

### 修改侧边栏字体为宋体
打开`D:\hexo\themes\landscape-plus\source\css\_partial\sidebar.styl`，在`.widget`下方添加一行，如下：
``` bash
.widget
  font-family: SimSun    //修改侧边栏字体为宋体
```

### 标题字体不加粗
打开`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，删掉`.article-title`条目下方的`font-weight: bold`这一行。

### 修改右侧分类、近期文章等字体为宋体
打开`D:\hexo\themes\landscape-plus\source\css\_partial\sidebar-aside.styl`文件，修改`.widget-title`条目如下：
``` bash
.widget-title
  font-weight: bold         //字体加粗
  font-family: SimSun       //修改字体为宋体
  @extend $block-caption
```

重新部署后，刷新即可。

## 附录
### 特殊符号大全

 1. [http://tw.piliapp.com/symbol/][4]
 2. [http://w13.loxa.edu.tw/ctjh930220/][5]
 3. [http://star.gg/special-symbols][6]
 4. [http://www.1t2t.com/3t/soft/28.htm][7]
 
### FontAwesome对应CSS值
 1. [A list of Font Awesome icons and their CSS content values][8]
 2. [Every Font Awesome 4.3.0 Icon, CSS Class, & Unicode][9]
 3. [Font Awesome icons and their CSS content values][10]


  [1]: http://starsky.gitcafe.io/2015/11/20/Hexo%E5%8D%9A%E5%AE%A2%E7%A7%BB%E5%8A%A8%E7%AB%AF%E9%80%82%E9%85%8D%E7%9A%84%E4%BC%98%E5%8C%96/#%E4%BF%AE%E6%94%B9%E9%A1%B5%E9%9D%A2%E5%BA%95%E9%83%A8%E5%BA%A7%E5%8F%B3%E9%93%AD%E7%9A%84%E4%BD%8D%E7%BD%AE
  [2]: http://starsky.gitcafe.io/2015/05/06/Hexo%E4%B8%BB%E9%A2%98%E9%85%8D%E7%BD%AE%E4%B8%8E%E4%BC%98%E5%8C%96%EF%BC%88%E4%BA%8C%EF%BC%89/##FontAwesome%E5%AF%B9%E5%BA%94CSS%E5%80%BC
  [3]: https://github.com/xiangming/landscape-plus/search?utf8=%E2%9C%93&q=bold
  [4]: http://tw.piliapp.com/symbol/
  [5]: http://w13.loxa.edu.tw/ctjh930220/
  [6]: http://star.gg/special-symbols##star_symbols
  [7]: http://www.1t2t.com/3t/soft/28.htm
  [8]: http://astronautweb.co/snippet/font-awesome/
  [9]: http://fortawesome.github.io/Font-Awesome/cheatsheet/
  [10]: http://navaneeth.me/font-awesome-icons-css-content-values/##.VW2oT9qJjIU