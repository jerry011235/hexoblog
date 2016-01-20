---
title: "为Hexo添加微搜索"
date: 2015-05-11 20:59:26
categories: [⛺电脑技术, hexo]
tags: [教程, hexo, 搜索]
toc: true
---
## 微搜索是什么

微搜索（[官网][1]）是一个非常快速的站内搜索引擎，全文搜索，实时索引，即输即搜，自动补全，帮助你轻松实现全文搜索功能。
而整个过程只需要简单的三步：创建引擎，添加站点地址，复制代码到 html。
关键它还**免费**（哈哈，就看中这点！），免费帐号可创建1个引擎，添加两个域名。
<!--more-->
## 添加微搜索到博客
### 添加微搜索代码
照着官网的帮助视频做，先创建个引擎，然后在“爬虫”那把自己的域名添加进去：http://starsky.gitcafe.io/
接下来就要安装了，它提供了一个最简单的安装方式，即直接复制代码到网页中，在视频中我们可以看到，这段代码是要粘贴在`index.html`中即可。

我们的本地hexo目录里没有`index.html`文件，所以我们要像[Hexo自动随机切换顶部图片][2]一样来新建个`tinysou.ejs`文件，把提供的代码粘贴进去，保存后放到`D:\hexo\themes\你的主题目录\layout\_partial`目录下。

然后编辑`D:\hexo\themes\你的主题目录\layout\_partial\header.ejs`,在最后一行（`</header>`标记）之前加入一行`<%- partial('tinysou') %>`即可。
``` bash
 </div>
  <%- partial('switch-banner') %>
  <%- partial('tinysou') %>
</header>
```
接着别忘了编辑你的**主题**配置文件`themes\你的主题目录\_config.yml`，在里面添加：
``` bash
tinysou: true
```
### 修改搜索框
编辑`D:\hexo\themes\你的主题目录\layout\_partial`目录下面的`header.ejs`文件，搜索`search-form-wrap`，把下面的代码修改成如下样式：
``` bash
     <div id="search-form-wrap">
        <form class="search-form">
           <input type="text" id="ts-search-input"  name="word" maxlength="20"  class="search-form-input" placeholder="搜索">
        </form>
     </div>
```
保存后重新部署即可。

  [1]: http://tinysou.com/
  [2]: http://starsky.gitcafe.io/2015/05/06/Hexo%E8%87%AA%E5%8A%A8%E9%9A%8F%E6%9C%BA%E5%88%87%E6%8D%A2%E9%A1%B6%E9%83%A8%E5%9B%BE%E7%89%87/