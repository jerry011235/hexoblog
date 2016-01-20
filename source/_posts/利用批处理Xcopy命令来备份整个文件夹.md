---
title: 利用批处理Xcopy命令来备份整个文件夹
date: 2015-11-18 13:52:17
tags: [Xcopy, cmd, 备份]
categories: [⛺电脑技术, 经验技巧]
---

Xcopy命令是能复制整个文件夹及其下所有子目录和文件到目标文件夹的一个CMD命令。详细介绍请看[xcopy_百度百科][1]。

今天我们主要用它来备份hexo文件夹。

首先我们先新建一个目的文件夹，即备份的文件夹。比如我新建了一个`E:\hexo博客备份`文件夹。
然后制作一个批处理，新建记事本，输入以下命令：
``` c
Xcopy D:\hexo E:\hexo博客备份 /s /e /y /d
```
然后另存为`Xcopy_backup_hexo.bat`，保存类型为`所有文件`即可。
<!--more-->
接下来直接双击这个批处理文件，就能看到效果了。

感觉速度很快，一会儿就复制完了：）

如果要最小化运行，可以创建一个快捷方式，然后右键，属性，运行方式，最小化，确定即可。

如果以后你的源文件夹`D:\hexo`有更新，比如更改了某些文件中的代码，新增加了某些文件，`/d`参数保证了可以及时更新。
唯一的缺点是如果你在源文件夹**删除**了某个文件或文件夹，这个命令就不能同步删除了，因为`Xcopy`只是复制。

注意：XCOPY默认不复制隐藏文件，需要复制请加上`/h`参数。

如果要实现镜像备份文件夹，可以把批处理的命令改成如下：
``` c
del /f/s/q E:\hexo博客备份 > nul
rmdir /s/q E:\hexo博客备份
md E:\hexo博客备份
Xcopy D:\hexo E:\hexo博客备份 /s /e /y /d
```
也就是先快速删除`E:\hexo博客备份`文件夹，然后新建`E:\hexo博客备份`文件夹，最后复制就ok。
还可以把这个批处理添加到windows的计划任务里，实现定时备份文件夹。

如果要用软件的话，开源的同步文件夹的软件有[Toucan][2]和[FreeFileSync][3]等等。

**注意：
如果使用xcopy命令出现“内存不足”的错误提示。
原因是设的目的路径太长（太深），将目的路径改为磁盘根目录或根目录下的一个目录就可以了。** 
来源：http://www.cnblogs.com/KevinJasmine/p/4159234.html

2016-1-6更新备份hexo的bat，代码如下：
``` bash
@echo off
set source="D:\hexo"
set target="D:\备份\hexoblog"

del /f/s/q "%target%\source" > nul
rmdir /s/q "%target%\source"

del /f/s/q "%target%\themes" > nul
rmdir /s/q "%target%\themes"

del /f/s/q "%target%\_config.yml" > nul

xcopy "%source%\source" "%target%\source\" /e /y /d /i
xcopy "%source%\themes" "%target%\themes\" /e /y /d /i
xcopy "%source%\_config.yml" "%target%\" /y /d

```

这里注意`/i`参数，它是在目标文件夹不存在的情况下自动创建文件夹并复制。另外目标路径的结尾如果不加`\`默认会弹出提示，加`\`就不弹提示。
比如 ：要把`%source%`复制到`%target%`，但是`%target%`文件夹并不存在，用下面的命令也能复制，并且不会弹出提示。
`xcopy "%source%" "%target%\" /e /y /d /i`
后来经过测试，`\` 和 `/i `只要有一个就不会出现提示了。


  [1]: http://baike.baidu.com/item/xcopy
  [2]: http://www.toucan.co/
  [3]: http://www.freefilesync.org/