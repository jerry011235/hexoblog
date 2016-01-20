---
title: Hexo添加图片、音乐和视频
date: 2015-05-05 22:19:59
categories: [⛺电脑技术, hexo]
tags: [教程, hexo]
toc: true
---
## 插入图片
### 添加外部链接图片
实际上用小书匠编辑器就能简单地实现，代码样式为：

    ![“图片描述”（可以不写）](“图片地址”)

这里推荐注册一个七牛云存储用来存放图片，也可以用[围脖是个好图床][1]，当得到图片外链后，直接粘贴到小括号中即可。
<!--more-->
例如：
插入以下代码

    ![](http://ww2.sinaimg.cn/large/5e8cb366jw1e62o63tkv3j20dh078q5a.jpg)

结果如下
![](http://ww2.sinaimg.cn/large/5e8cb366jw1e62o63tkv3j20dh078q5a.jpg)
再来一次

    ![](http://7xivmb.com1.z0.glb.clouddn.com/smile33.jpg)

结果如下
![](http://7xivmb.com1.z0.glb.clouddn.com/smile33.jpg)

### 添加本地图片
在`D:\hexo\source`目录下新建文件夹，命名为`images`或者其他你喜欢的名字，然后编辑你的md博文，插入下面的代码样式：
``` bash
  ![“图片描述”（可以不写）](/images/你的图片名字.JPG)
```
例如我在`D:\hexo\source\images`放入了一个`smile01.gif`图片，然后写下：
``` bash
![](/images/smile01.gif)
```
重新生成，上传后就能看到了。结果如下：
![](/images/smile01.gif)

**注意：
1.如果使用的是小书匠编辑器和markdownpad等编辑器，上述代码是不能预览的。
2.图片路径和图片名称必须为英文，否则不能显示图片。**


## 插入音乐
比如网易云音乐，找到喜欢的歌曲，点击分享按钮，把里面的代码复制下来，直接粘贴到博文中即可。
比如插入以下代码：

    <iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=25706282&auto=0&height=66"></iframe>
    
效果如下：

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=25706282&auto=0&height=66"></iframe>

## 插入视频
视频也和音乐类似，先输入视频标题，回车换一行插入代码即可。

    Idina Menze和Caleb Hyles激情对唱Let It Go：
    <iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>

注意代码中的允许全屏要写上：`allowfullscreen`

效果如下：

Idina Menze和Caleb Hyles激情对唱Let It Go：
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>


  [1]: https://weibotuchuang.sinaapp.com