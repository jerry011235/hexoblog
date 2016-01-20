---
title: Hexo文章末尾添加版权或自定义文本
date: 2015-11-15 21:39:26
categories: [⛺电脑技术, hexo]
tags: [教程, hexo, 版权]
toc: true
---

## 文章末尾添加版权
### 方法一
编辑`D:\hexo\themes\landscape-plus\layout\_partial\post\nav.ejs`文件，在文件的最头上，也就是`<% if (post.prev || post.next){ %>`这段代码的上面，添加以下代码：
``` bash
<% if (post.original != false){ %>
<div class="copyright">
  <p><span>本文标题:</span><a href="<%- url_for(post.path) %>"><%= post.title %></a></p>
  <p><span>文章作者:</span><a href="/" title="访问 <%=theme.author%> 的个人博客"><%=theme.author%></a></p>
  <p><span>发布时间:</span><%= post.date.format("YYYY年MM月DD日 - HH时mm分") %></p>
  <p><span>最后更新:</span><%= post.updated.format("YYYY年MM月DD日 - HH时mm分") %></p>
  <p>
    <span>原始链接:</span><a href="<%- url_for(post.path) %>" title="<%= post.title %>"><%= post.permalink %></a>
    <span class="btn" data-clipboard-text="原文: <%= post.permalink %>　　作者: <%=theme.author%>" title="点击复制文章链接">
        <i class="fa fa-clipboard"></i>
    </span>
  </p>
 <p><span>许可协议:</span><i class="fa fa-creative-commons"></i> <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/cn/" title="中国大陆 (CC BY-NC-SA 3.0 CN)">"署名-非商用-相同方式共享 3.0"</a> 转载请保留原文链接及作者。</p>
  <script src="/js/clipboard.min.js"></script>
  <script> var clipboard = new Clipboard('.btn'); </script>
</div>

<style type="text/css">
  .copyright p .btn {
    margin-left: 1em;
  }
  .copyright:hover p .btn::after {
    content: "复制"
  }
  .copyright p .btn:hover {
      color: gray;
      cursor: pointer;
    };
</style>
<% } else { %>
<% } %>

```
<!--more-->
然后上面的“复制（原文链接）”需要一个js脚本文件：`clipboard.min.js`，在[这里][1]下载，下载的方法参见[这里][2]，然后把它放到`D:\hexo\themes\landscape-plus\source\js`目录下就OK.

最后编辑`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，在最下面把样式代码添加进去：
``` bash
.copyright
  font-size: .93em
  line-height: 1.6em
  padding: .5em 2em
  border: 1px solid lightgray
  span
    color: #B5B5B5
    font-weight: bold
    margin-right: 1em 
  a 
    color: color-link
```
保存后重新部署就OK。
### 方法二
在`D:\hexo\themes\landscape-plus\layout\_partial\post`里新建一个`statement.ejs`文件，然后输入以下内容：
``` bash
<% if (!index && page.source != 'about/index.md'){ %>
  <div class="article-statement">
    版权声明：<br>
    <hr>  
    除非注明，本博文章均为原创，转载请以链接形式标明本文地址。<br>
  </div>
<% } %>
```
然后编辑`D:\hexo\themes\landscape-plus\layout\_partial\article.ejs`文件，添加对其的引用，在`<%- post.content %>`下方插入一行代码`<%- partial('post/statement') %>`，即变成：
``` bash
   <%- post.content %>
   <%- partial('post/statement') %>
<% } %>
```
最后修改`statement`的样式，在`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件下方加入：
``` bash
.article-statement
  font-size: 1em
  font-family: "微软雅黑"  
```
保存后重新部署就OK。

当然，如果要在文字开头加入一些公告类文字，也可以仿照此办法，只是把`<%- post.content %>`和`<%- partial('post/statement') %>`的顺序上下调换一下就OK，即：
``` bash
   <%- partial('post/statement') %>
   <%- post.content %>
<% } %>
```
### 方法三
经过[yongf][3]的提醒，发现还可以直接编辑`D:\hexo\scaffolds`里的文件，也就是编辑或新建模版文件来达到目的。
编辑`D:\hexo\scaffolds\post.md`，在下方输入：
``` html
版权声明：<br>
<hr>
除非注明，本博文章均为原创，转载请以链接形式标明本文地址。<br>
```
然后保存好就OK.
这样每次新建文章，就要去gitbash里输入以下命令：

     hexo new post "你的标题"
     
等它创建好以后，才能打开文章进行编辑。

### 比较
这三种方法都可以在文章末尾添加版权等信息，只是位置稍微不同。方法一是在“标签”、“评论”和“分享到”的那一行的下方加入版权信息；而方法二和方法三则真正是在文章末尾加入版权信息。三种方法各有千秋，最终选择哪种就看自己的喜好了。

今天又发现网友的一个新办法，似乎是用Filter插件的特点，它会在文章正式渲染之前执行，链接在此：[为Hexo博客的每一篇文章自动追加版权信息][4]，有兴趣的朋友可以去看看。
## 文章末尾添加自定义文本

当然在实际操作中，我不想添加版权等信息，感觉千篇一律，没有新意，于是仿照上面的办法，创建了一些自定义的文字。

编辑`D:\hexo\themes\landscape-plus\layout\_partial\post\nav.ejs`文件，在文件的最头上添加以下代码：
``` bash
<% if (post.original != false){ %>
<div class="article-end-text">
<p>每晚一问：你今天都做了些什么？</p>
</div>
<% } else { %>

<% } %>
```
然后编辑`D:\hexo\themes\landscape-plus\source\css\_partial\article.styl`文件，在最下面把样式代码添加进去：
``` bash
.article-end-text
  font-family: "微软雅黑"
  font-size: 20px
  line-height: 1.6em
  text-align:center
  padding: 1em 2em
  border: 2px solid lightgray
```

保存后`hexo clean && hexo g && hexo d`重新部署上传就OK.

2015-11-19更新`nav.ejs`相关代码改为：
``` bash
<div class="article-end-text-wrap">
  <div class="article-end-text">
<p>每晚一问：你今天都做了些什么？</p>
  </div>
</div>
```
而`article.styl`相关代码改为：
``` bash
//自定义文章末尾文字样式“每晚一问”
.article-end-text-wrap
  margin: 5px 0
.article-end-text
  font-family: "微软雅黑"
  font-size: 20px
  line-height: 1.6em
  text-align:center
  padding: 1em 2em
  
  background: color-widget-background
  box-shadow: 1px 2px 3px color-border
  //border: 1px solid color-widget-border
  border-radius: 3px
```

参考：[MOxFIVE's blog：增加文末版权信息][5]


  [1]: https://github.com/MOxFIVE/M-Hexo-Blog/blob/master/themes/Yilia/source/js/clipboard.min.js
  [2]: http://starsky.gitcafe.io/2015/11/12/GitHub%E4%B8%8A%E4%B8%8B%E8%BD%BD%E5%8D%95%E6%96%87%E4%BB%B6/
  [3]: http://blog.54yongf.com/2015/11/17/No18-%E3%80%90%E5%8E%9F%E3%80%91%E8%B7%9F%E6%88%91%E4%B8%80%E8%B5%B7%E6%9D%A5%E4%BA%86%E8%A7%A3hexo%E7%9A%84%E7%BB%93%E6%9E%84%EF%BC%8C%E8%87%AA%E5%AE%9A%E4%B9%89%E4%B8%80%E4%BA%9B%E7%BB%84%E4%BB%B6/
  [4]: http://kuangqi.me/tricks/append-a-copyright-info-after-every-post/
  [5]: https://github.com/MOxFIVE/M-Hexo-Blog/commit/79b0f4419adb908924f674b3626ad433aabf329a