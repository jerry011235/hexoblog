---
title: Hexo添加多说最近评论
date: 2015-05-21 13:13:45
categories: [➎电脑技术, hexo]
tags: [hexo, 教程, 评论]
---
以landscape-plus主题为例：
在`D:\hexo\themes\landscape-plus\layout\_widget\`目录下新建 `recent_comments.ejs`文件，内容如下：
``` cpp
<% if (theme.duoshuo_shortname){ %>
<div class="widget-wrap">
  <h3 class="widget-title"><%= __('最近评论') %></h3>
<div class="widget">
<ul class="ds-recent-comments" data-num-items="5" data-show-avatars="1" data-show-time="1" data-show-title="1" data-show-admin="1" data-excerpt-length="70"></ul>
</div>
  </div>
<% } %>
```
注：其中上述代码第5行`<ul class="ds-recent-comments" data-num-items="5" data-show-avatars="1" data-show-time="1" data-show-title="1" data-show-admin="1" data-excerpt-length="70"></ul>`按照[官方提示][1]可以自行修改：

``` cpp
//以下参数均为可选
data-num-items="10"     //显示最新评论的条数，最大支持200条
data-show-avatars="1"   //是否显示头像，1：显示，0：不显示
data-show-time="1"      //是否显示时间，1：显示，0：不显示
data-show-title="0"     //是否显示标题，1：显示，0：不显示
data-show-admin="1"     //是否显示管理员的评论，1：显示，0：不显示
data-excerpt-length="70"//最大显示评论汉字数
```
然后在`D:\hexo\themes\landscape-plus`主题目录中的`_config.yml`下的`widgets`中添加`recent_comments`：
``` c
widgets:
- category
- recent_posts
- archive
- tagcloud
- tag
- links
- recent_comments
```
重新部署后刷新即可。

参考：
 - [在hexo中添加多说`最近评论`边栏][2]
 - [添加最新评论widget][3]
 - [为Hexo添加最近评论支持——以Landscape类主题为例][4]


  [1]: http://dev.duoshuo.com/docs/4ff28d95552860f21f000010
  [2]: http://www.lichanglin.cn/%E5%9C%A8hexo%E4%B8%AD%E6%B7%BB%E5%8A%A0%E5%A4%9A%E8%AF%B4%60%E6%9C%80%E8%BF%91%E8%AF%84%E8%AE%BA%60%E8%BE%B9%E6%A0%8F/
  [3]: http://bubkoo.com/2013/12/16/hexo-issure/#%E6%B7%BB%E5%8A%A0%E6%9C%80%E6%96%B0%E8%AF%84%E8%AE%BAwidget
  [4]: http://chriszheng.science/2015/09/13/Hexo-add-recent-comment/