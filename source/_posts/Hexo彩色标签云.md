---
title: Hexo彩色标签云
date: 2015-05-16 16:43:25
categories: [➎电脑技术, hexo]
tags: [教程, hexo]
---
编辑`D:\hexo\themes\你的主题目录\layout\_widget\tagcloud.ejs`文件，搜索`<%- tagcloud`，然后把整个代码修改为如下样式：
``` bash
<% if (site.tags.length){ %>
  <div class="widget-wrap">
    <h3 class="widget-title"><%= __('tagcloud') %></h3>
    <div class="widget tagcloud">
      <%- tagcloud(site.tags, {
        min_font: 13,
        max_font: 23,
        amount: 65,
        orderby: 'count',
        color: true,
        start_color: '#9900FF',
        end_color: '#FF0000'
      }) %>
    </div>
  </div>
<% } %>
```
保存后重新部署即可。
其中`end_color`为最多标签的字体颜色，`start_color`为最少标签的字体颜色。
感谢[xfeng.me][1]


  [1]: http://xfeng.me/