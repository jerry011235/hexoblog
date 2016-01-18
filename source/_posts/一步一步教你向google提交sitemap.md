title: "一步一步教你向google提交sitemap"
date: 2015-05-06 17:53:11
categories: [o(^▽^)┛电脑技术, hexo]
tags: [教程, hexo, sitemap]
toc: ture
---
在已经生成站点地图的情况下我们来向google提交sitemap，用于让google能够找到我们的博客。
# 验证网站
首先google要验证你是否是你网站的管理员。
1.登录你的谷歌账号，打开[webmaster](https://www.google.com/webmasters/verification/home?hl=en)（也可以打开[webmaster中文界面][1]），然后点击`ADD A SITE`添加网站：
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap0.PNG)

输入你的网址（例如`http://starsky.gitcafe.io/`）后，点击continue.
<!--more-->
## HTML标记验证
2.点击alternate methods选择验证方法。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap1.PNG)
3.点击HTML tag，我们选择HTML标记验证方法。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap2.PNG)
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap3.PNG)

在这里你可以看到一串meta代码，一会儿要在我们的主页中加进去，你可以点击`show me an example`查看例子，就是在`<head>`和`<title>`之间插入这段代码。
## 插入meta代码
** 最重要的一步 **：
4.编辑`D:\hexo\themes\你的主题文件\layout\_partial\head.ejs`，在`<head>`下面，`<title>`上面插入代码保存后就行了。
![][2]

然后我们可以在gitcafe中查看（实际上可以不查看)
5.因为我们的hexo博客是托管在gitcafe上的，所以我们登录gitcafe账号，选中项目，然后点击右侧的`master`，选择`gitcafe-pages`,如图。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap4.PNG)

6.点击左侧的`index.html`,这个就是我们的主页文件了。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap5.PNG)
![][3]

7.然后回到谷歌页面点击verify按钮即完成验证。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap7.PNG)

成功后可以看到这样的画面。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap8.PNG)

# 添加sitemap
接下来还要把你的网址的sitemap添加进去。
8.点击进入[Webmaster Tools](https://www.google.com/webmasters/tools/home?hl=en "webmasters tools")，然后点击你的网址。
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap9.PNG)

9.点击右边的sitemaps.
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap10.PNG)

10.点击右上角的ADD/TEST SITEMAP.
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap11.PNG)
![](http://7xivmb.com1.z0.glb.clouddn.com/hexo向google提交sitemap12.PNG)

11.在弹出的框内直接填入`sitemap.xml`，然后按submit sitemap按钮就大功告成了！

参考：[｜Hexo优化｜如何向google提交sitemap（详细）](https://fionat.github.io/blog/2013/10/23/sitemap/)


  [1]: https://www.google.com/webmasters/verification/home?hl=zh-CN
  [2]: http://7xivmb.com1.z0.glb.clouddn.com/hexo%E5%90%91goole%E6%8F%90%E4%BA%A4sitemap14-%E6%8F%92%E5%85%A5meta%E4%BB%A3%E7%A0%81.PNG
  [3]: http://7xivmb.com1.z0.glb.clouddn.com/hexo%E5%90%91goole%E6%8F%90%E4%BA%A4sitemap13-%E5%9C%A8gitcafe%E4%B8%AD%E6%9F%A5%E7%9C%8B.PNG