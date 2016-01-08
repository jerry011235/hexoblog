---
title: Git简易操作教程和一些技巧
date: 2016-01-08 23:36:50
categories: [➎电脑技术, Git]
tags: [教程, git]
toc: true
---
这是一篇在windows平台使用git上传本地代码并同步到github远程仓库的简易教程。
环境：windows7 32位，Git-1.9.5-preview20150319.exe
# 创建github远程仓库

先注册[github][1]账号，登录后，点击右上角头像旁边的`+`号下拉菜单按钮，选择`New repository`，然后`Repository name`下方就是仓库的名字，我们这里输入`test`，然后下方的`Public`保持勾选，然后点击勾选下面的`Initialize this repository with a README`,如果你喜欢，可以点击`Add a license:`来增加一个许可证，我们这里选择`GNU Lesser General Public License v3.0`，最后点击绿底白字的`Creating repository`完成创建。

创建后页面自动跳转到你的仓库地址，比如我的就是[https://github.com/jerry011235/test][2]，然后复制`HTTPS`右侧的网址：
``` bash
https://github.com/jerry011235/test.git
```
# 本地克隆
在D盘根目录或一个你喜欢的文件夹（推荐路径全部为英文），右键选择`Git Bash`,输入：
``` bash
git clone https://github.com/jerry011235/test.git
```
回车后，会发现D盘根目录多了一个test文件夹，里面和github网页上的文件是一样的（包括一个`LICENSE`文件和一个`README.md`文件），最重要的是多了一个`.git`隐藏文件夹。这个test文件夹就是你的本地工作目录。
**然后关闭gitbash窗口。**
<!--more-->
然后把要上传到github的文件粘贴到test文件夹里（或者新建几个文件夹和文件）。然后进入`D:\test`文件夹，右键选择`Git Bash`,会发现变成master了，即`/D/test (master)`，然后**依次**输入：
``` bash
git add -A      
//它会把我们的新文件和修改的文件全部提交到stage区域（当然不包括本地删除的文件）
git commit -m '我的第一个提交'
// 提交更新
git push origin master
// push到远端master上
```
**注意：这三个命令是连续动作，必须依次执行，才能成功。**
如果要把`git add`和`git commit`以及`git push`合并成一步命令，可以使用下面的代码：
``` bash
git add -A && git commit -m '你的注释' && git push origin master
```
等命令运行完后，刷新<https://github.com/jerry011235/test>，会发现本地的文件全部都上传到github远程仓库上了。

# 测试同步
然后我们进行文件和文件夹的修改操作，就是看看修改后的本地目录能否和github同步（目录里的文件和文件夹一模一样）。
我们先在[http://mofas.github.io/mindMap/dist/index.html][3]上画一个文档修改的思维导图。
![文档操作][4]

接着我们就开始在工作目录`D:\test`文件夹里面进行增加和删除文件和文件夹、修改文件内容和文件名等操作。
经过测试，这行代码完全可以同步本地目录和github远程仓库。
``` bash
git add -A && git commit -m '你的注释' && git push origin master
```
**但注意：本地新建一个空文件夹并不会被同步到github远程仓库上。**

# gitbash小技巧
## 快捷键
1. 按方向键`↑`（上键）可以显示上一条命令，`Ctrl + p`也有同样效果。
2. Ctrl + c可以终止命令。

更多快捷键可以参考：[Bash Shell 快捷键][5]或搜索`Bash Shell 快捷键`来得到更多信息。
## “git add -A” and “git add .”的区别
上述代码为什么要用`git add -A`而不用`git add .`，因为

 - `git add -A` :stages All
 - `git add .` :stages new and modified, without deleted
 - `git add -u` :stages modified and deleted, without new

git add操作  | 对应的提交操作
------------- | -------------
`git add -A`   | stages All
`git add .`   | stages new and modified, without deleted
`git add -u`  | stages modified and deleted, without new
Git Version 1.X：
![Git Version 1.X ][6]
Git Version 2.X：
![Git Version 2.X ][7]

来自：[http://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add][8]


  [1]: https://github.com
  [2]: https://github.com/jerry011235/test
  [3]: http://mofas.github.io/mindMap/dist/index.html
  [4]: http://7xivmb.com1.z0.glb.clouddn.com/%E6%96%87%E6%A1%A3%E4%BF%AE%E6%94%B9.png
  [5]: http://www.cnblogs.com/include/
  [6]: http://i.stack.imgur.com/YfLUZ.jpg
  [7]: http://i.stack.imgur.com/KwOLu.jpg
  [8]: http://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add