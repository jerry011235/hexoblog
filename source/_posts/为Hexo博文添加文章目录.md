title: "为Hexo博文添加文章目录"
date: 2015-05-06 21:07:18
categories: [⛺电脑技术, hexo]
tags: [教程, hexo]
toc: true

---
### 生成目录
以landscape-plus主题为例，编辑`D:\hexo\themes\landscape-plus\layout\_partial\article.ejs`文件，`ctrl＋f`查找`<%- post.content %>`，然后在这一行之前加入如下代码：
```
<!-- Table of Contents -->
<% if (!index && post.toc){ %>
  <div id="toc" class="toc-article">
    <strong class="toc-title">文章目录</strong>
    <%- toc(post.content) %>
  </div>
<% } %>
```
<!--more-->
插入后为（第2行到第8行为插入代码）：
``` bash
      <% } else { %>
	  <!-- Table of Contents -->
<% if (!index && post.toc){ %>
  <div id="toc" class="toc-article">
    <strong class="toc-title">文章目录</strong>
    <%- toc(post.content) %>
  </div>
<% } %>
        <%- post.content %>
```
### 设置目录样式
保存，然后编辑`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`，在文件的最后，添加如下代码：
```
/*toc*/
.toc-article
  background #eee
  border 1px solid #bbb
  border-radius 10px
  margin 1.5em 0 0.3em 1.5em
  padding 1.2em 1em 0 1em
  max-width 28%
.toc-title
  font-size 120%
#toc
  line-height 1em
  font-size 0.9em
  float right
  .toc
    padding 0
    margin 1em
    line-height 1.8em
    li
      list-style-type none
  .toc-child 
    margin-left 1em
```
2015-11-17更新目录代码样式为以下：
``` bash
//toc
#toc.toc-article
  background color-background
  border-radius 4px
  margin 1.6em 0 1.6em 2em
  line-height 1.5em
  font-size 0.9em
  -webkit-border-radius 4px

  h2, ol
    padding 0 0.4em
    margin 0
  h2
    cursor pointer
  @media mq-mobile
    margin 1.6em 0
    width 100%
  @media mq-tablet
    margin 1.6em 0
    width 100%
#toc
  line-height 1.3em
  font-size 0.8em
  float right
  .toc
    li
      list-style-type none
      a
        &:hover
          color color-font
          text-decoration none !important
  .toc-child 
    padding-left 1.5em
#toc.toc-aside
  display none
  width 13%
  position fixed
  right 2%
  top 360px
  line-height 1.5em
  max-height: 68%
  overflow: auto
  font-size 1em
  color color-heading
  opacity .6
  transition opacity 1s ease-out
  @media mq-mobile
    width 60%
    height 40%
    right 58px 
    padding 0 20px
    background #fff
    overflow auto
  @media mq-tablet
    width 60%
    height 40%
    right 58px 
    padding 0 20px
    background #fff
    overflow auto
  h2
    padding 0.3em 0
    color color-font
  &:hover
    transition opacity .3s ease-out
    opacity 1
  a
    transition color 1s ease-out
    text-decoration none
    color color-link
    &:hover
      color color-theme
      transition color .3s ease-out

/*! css3 animate */
.animated
  animation-fill-mode both
  animation-duration 1s

@-webkit-keyframes fadeIn
  0%
    opacity 0
  100%
    opacity 1

.fadeIn
  animation-name fadeIn

@keyframes fadeInDown
  0%
    opacity 0
    transform translateY(-20px)
  100% 
    opacity 1
    transform translateY(0)

.fadeOut
  animation-name fadeOut

.moveMain
  margin-left 10% !important
```
### 启用目录

保存，最后打开在需要添加文章目录的的博文md文件，在`tags`下方和
    --- 上方添加一行：

``` bash		
toc: true
```

保存后重新部署即可。

如果不喜欢链接的颜色，可以编辑`D:\hexo\themes\landscape-plus\source\css\_variables.styl`文件的`color-link`那一栏，添加自己喜欢的颜色代码：
``` bash
color-link = #5953F3
//color-link = #E32D40
//color-link = #258fb8
```

参考：
- [为Hexo博客添加目录](http://kuangqi.me/tricks/enable-table-of-contents-on-hexo/)
- [为Hexo添加文章目录](http://twiceyuan.com/2015/01/12/%E4%B8%BAHexo%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E7%9B%AE%E5%BD%95/)