---
title: Hexo主题配置与优化（一）
date: 2015-05-05 23:12:15
categories: [⛺电脑技术, hexo]
tags: [教程, hexo]
toc: true
---

## 配置主题
搜索一个好看的主题，按照官网上的操作安装，更新。
我使用的是[xiangming][1]制作的[landscape-plus][2].
当然还是在`D:\hexo`目录下，安装：
``` bash
git clone https://github.com/xiangming/landscape-plus.git themes/landscape-plus
```
然后修改主题的设置文件_config.yml，把theme的值设置为`landscape-plus`

>启用指定主题:
如果你安装了多个主题的话，那么可以编辑站点的`_config.yml`文件，在里面修改：
    theme: 你的指定主题



配置时注意有两个`_config.yml`文件，一个在`D:\hexo`目录下，是整个站点的配置；第二个在`D:\hexo\themes\landscape-plus`目录下，是主题的配置。
<!--more-->
修改`D:\hexo\_config.yml`站点配置：
第15行：`url: http://starsky.gitcafe.io`
``` bash		
# Archives
2: Enable pagination
1: Disable pagination
0: Fully Disable
archives: 1
category: 1
tag: 1
```

接下来修改`D:\hexo\themes\landscape-plus\_config.yml`主题配置：
按你喜欢，把menu中相应的英语改成中文。
``` bash
menu:
  首页: /
  文章列表: /archives
  关于: /about
```
还有第11行：`excerpt_link: 阅读全文`	
其他默认即可。

## 配置插件
### 安装RSS插件和sitemap插件
``` bash
$ npm install hexo-generator-feed --save

$ npm install hexo-generator-sitemap --save
```
然后修改`D:\hexo\_config.yml`站点配置，添加：

    # Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
    
    #Feed Atom
    feed:
      type: atom
      path: atom.xml
      limit: 20
    
    #sitemap
    sitemap:
      path: sitemap.xml

然后注意再修改`D:\hexo\themes\landscape-plus\_config.yml`主题配置：
`menu:`里添加`网站地图: /sitemap.xml`
下面也添加`rss: /atom.xml`（如果有就不用添加了）。
<!--more-->
部署后就能看到“首页”那一栏多了个“网站地图”，点击后有内容且第一行为`This XML file does not appear to have any style information associated with it. The document tree is shown below.`就说明成功了。
RSS也是一样。

另外，附一下升级和卸载的命令行：

升级插件：

    npm update

卸载插件（比如卸载RSS插件）：

    npm uninstall hexo-generator-feed

**当然，卸载插件还有更简单的办法，就是去`D:\hexo\node_modules`目录下，直接删除你要卸载的插件文件夹即可。
安装插件也可以粘贴事先备份好的某个插件的文件夹。**
### 安装多说评论系统
实际上landscape-plus主题已经集成了多说评论系统，我们只需要添加`duoshuo_shortname`到两个配置文件即可。

#### 多说shortname是什么

`多说shortname`其实就是你注册多说时的用户名（账号），也就是当你使用豆瓣或微博账号注册多说时（因为多说没有邮箱注册），它要你注册一个多说域名，即 XXX.duoshuo.com，这个XXX就是你的`多说shortname`.

接下来在主题配置文件和站点配置文件里都加入：
``` bash
# Duoshuo
duoshuo_shortname: XXX
```
即可。注意XXX和冒号之间有个空格。
## 备份
平时备份时注意备份站点和主题的`_config.yml`文件，还有自己写的文章（在`D:\hexo\source\_posts`里）和其他一些文件。在这里贴出我的站点和主题的`_config.yml`文件，也算是备份吧。
### 站点`_config.yml`文件
``` bash
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 璀璨星空 ● 无垠宇宙
subtitle: 耐心 谦虚 平静
description: 璀璨星空的博客
author: 璀璨星空
email: 
language: zh-CN

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://starsky.gitcafe.io/
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
permalink_defaults: /404.html

# Directory
source_dir: source
public_dir: public

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Archives
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 1
category: 1
tag: 1

# Pagination
## Set per_page to 0 to disable pagination
per_page: 100
pagination_dir: page

# Server
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
server_ip: localhost
logger: false
logger_format: dev

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY/MM/DD
time_format: HH:mm:ss


# Disqus
disqus_shortname: 

# Extensions
## Plugins: https://github.com/hexojs/hexo/wiki/Plugins
Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
 
## Feed Atom
feed:
   type: atom
   path: atom.xml
   limit: 20
 
## sitemap
sitemap:
    path: sitemap.xml     
 
## Themes: https://github.com/hexojs/hexo/wiki/Themes
theme: landscape-plus
exclude_generator:

duoshuo_shortname: starsky001


# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://gitcafe.com/starsky/starsky.git 
  branch: gitcafe-pages
```

### 主题`_config.yml`文件
``` bash
# Header
menu:
  首页: /
  文章列表: /archives
  关于: /about
  联系: /contact
rss: /atom.xml

# Content
excerpt_link: 阅读全文
fancybox: false
mathjax: false

# Sidebar
sidebar: right
widgets:
- category
- recent_posts
- archive
- tagcloud
- tag
- links

# Links
links:
  主题作者: http://xiguabaobao.com
  热前端: http://reqianduan.com

# Miscellaneous
google_analytics:
favicon: /favicon.png
twitter:
google_plus:
fb_admins: 
fb_app_id:

switch_banner: true
banner_count: 6

tinysou: true
```

参考：

 - [如何使用RSS分享功能？][3]
 - [使用Hexo搭建博客][4]
 - [hexo-generator-sitemap][5]
 - [Hexo搭建Github静态博客][6]
 - [如何搭建一个独立博客——简明Github Pages与Hexo教程][7]
 - [hexo官方文档][8]


  [1]: http://jasonxiang.com/landscape-plus/
  [2]: https://github.com/xiangming/landscape-plus
  [3]: https://github.com/xiangming/landscape-plus
  [4]: http://blog.lmintlcx.com/post/blog-with-hexo.html
  [5]: https://github.com/hexojs/hexo-generator-sitemap
  [6]: http://www.cnblogs.com/zhcncn/p/4097881.html
  [7]: http://www.jianshu.com/p/05289a4bc8b2
  [8]: http://hexo.io/zh-cn/docs/setup.html