---
title: Git简易操作教程和一些技巧
date: 2016-01-08 23:36:50
categories: [⛺电脑技术, Git]
tags: [教程, git]
toc: true
---
这是一篇在windows平台使用git上传本地代码并同步到github远程仓库的简易教程。
环境：windows7 32位，Git-1.9.5-preview20150319.exe
## 创建github远程仓库

先注册[github][1]账号，登录后，点击右上角头像旁边的`+`号下拉菜单按钮，选择`New repository`，然后`Repository name`下方就是仓库的名字，我们这里输入`test`，然后下方的`Public`保持勾选，然后点击勾选下面的`Initialize this repository with a README`,如果你喜欢，可以点击`Add a license:`来增加一个许可证，我们这里选择`GNU Lesser General Public License v3.0`，最后点击绿底白字的`Creating repository`完成创建。

创建后页面自动跳转到你的仓库地址，比如我的就是[https://github.com/jerry011235/test][2]，然后复制`HTTPS`右侧的网址：
``` bash
https://github.com/jerry011235/test.git
```
## 本地克隆
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

## 本地目录和远程仓库进行文件同步
然后我们进行文件和文件夹的修改操作，就是看看修改后的本地目录能否和github同步（目录里的文件和文件夹一模一样）。
我们先在[https://josetomastocino.github.io/mindmapit/][3]上画一个文件和文件夹修改操作的思维导图。
![文件和文件夹的操作][4]

**小技巧：搜索`(online) mindmap (github.io)`会出来更多的在线思维导图（括号里的单词可加可不加）：**

 - [http://mindmap.4ye.me/br57Govl][5]
 - [jsMind][6]
 - [http://mofas.github.io/mindMap/dist/index.html][7]
 - [https://www.text2mindmap.com/][8]
 - [https://kampfer.github.io/mindMap/client/index.html][9]
 - [http://my-mind.github.io/][10]

接着我们就开始在工作目录`D:\test`文件夹里面进行增加和删除文件和文件夹、修改文件内容和文件名等操作。
经过测试，这行代码完全可以把本地目录的文件同步到github远程仓库。
``` bash
git add -A && git commit -m '你的注释' && git push origin master
```
**但注意：本地新建一个空文件夹并不会被同步到github远程仓库上。**
## 查看文件版本的历史纪录
你可以在<https://github.com/jerry011235/test>页面中点击`commits`链接来查看[提交更新的历史纪录][11]，如图：
![点击commits][12]
然后点击`<>`还可以查看当时的文件，一直点击打开文件后，对着`Raw`右键，选择`链接另存为`还可以下载该版本的文件。
![github下载文件][13]
以后就可以上传一些word文档来进行版本控制，而因为github地址是公开的，任何人打开就能看到，所以就上传一些可以公开的文档。
下面这样的日子就一去不复返了：）
![以前的版本控制][14]
## Gitbash小技巧
### 快捷键
1. 按方向键`↑`（上键）可以显示上一条命令，`Ctrl + p`也有同样效果。
2. Ctrl + c可以终止命令。

更多快捷键可以参考附录或搜索`Bash Shell 快捷键`来得到更多信息。
### “Git add -A” and “Git add .”的区别
上述代码为什么要用`git add -A`而不用`git add .`，因为

 - `git add -A` :stages All
 - `git add .` :stages new and modified, without deleted
 - `git add -u` :stages modified and deleted, without new

Git add操作  | 对应的提交操作
------------- | -------------
`git add -A`   | stages All
`git add .`   | stages new and modified, without deleted
`git add -u`  | stages modified and deleted, without new
Git Version 1.X：
![Git Version 1.X ][15]
Git Version 2.X：
![Git Version 2.X ][16]

来自：[http://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add][17]

## 附录：Bash Shell 快捷键
Bash Shell 快捷键（转载自：[天晴如许的博客][18]）

【CTRL 键】
Ctrl + a – Jump to the start of the line
Ctrl + b – Move back a char
Ctrl + c – Terminate the command //用的最多了吧?
Ctrl + d – Delete from under the cursor
Ctrl + e – Jump to the end of the line
Ctrl + f – Move forward a char
Ctrl + k – Delete to EOL
Ctrl + l – Clear the screen //清屏，类似 clear 命令
Ctrl + r – Search the history backwards //查找历史命令
Ctrl + R – Search the history backwards with multi occurrence
Ctrl + u – Delete backward from cursor // 密码输入错误的时候比较有用
Ctrl + xx – Move between EOL and current cursor position
Ctrl + x @ – Show possible hostname completions
Ctrl + z – Suspend/ Stop the command

【补充:】
Ctrl + h – 删除当前字符
Ctrl + w – 删除最后输入的单词

【ALT 键】
平时很少用。有些和远程登陆工具冲突。
Alt + < - Move to the first line in the history
Alt + > – Move to the last line in the history
Alt + ? – Show current completion list
Alt + * – Insert all possible completions
Alt + / – Attempt to complete filename
Alt + . – Yank last argument to previous command
Alt + b – Move backward
Alt + c – Capitalize the word
Alt + d – Delete word
Alt + f – Move forward
Alt + l – Make word lowercase
Alt + n – Search the history forwards non-incremental
Alt + p – Search the history backwards non-incremental
Alt + r – Recall command
Alt + t – Move words around
Alt + u – Make word uppercase
Alt + back-space – Delete backward from cursor
// SecureCRT 如果没有配置好，这个就很管用了。

【其他特定的键绑定:】
输入 bind -P 可以查看所有的键盘绑定。这一系列我觉得更为实用。
Here “2T” means Press TAB twice
$ 2T – All available commands(common) //命令行补全，我认为是 Bash 最好用的一点
$ (string)2T – All available commands starting with (string)
$ /2T – Entire directory structure including Hidden one
$ ./2T – Only Sub Dirs inside including Hidden one
$ *2T – Only Sub Dirs inside without Hidden one
$ ~2T – All Present Users on system from “/etc/passwd” //第一次见到，很好用
$ $2T – All Sys variables //写Shell脚本的时候很实用
$ @2T – Entries from “/etc/hosts” //第一次见到
$ =2T – Output like ls or dir //好像还不如 ls 快捷

Esc + T – 交换光标前面的两个单词

【命令行历史】
history 显示命令历史列表
↑(Ctrl p)  显示上一条命令
↓(Ctrl n)  显示下一条命令
!num 执行命令历史列表的第num条命令
!! 执行上一条命令
!?string? 执行含有string字符串的最新命令
Ctrl + r - 然后输入若干字符，开始向上搜索包含该字符的命令，继续按Ctrl r，搜索上一条匹配的命令
Ctrl + s - 与Ctrl + 类似,只是正向检索
Alt + < - 历史列表第一项
Alt + > - 历史列表最后一项
ls !$ 执行命令ls，并以上一条命令的参数为其参数

【命令行编辑】
Ctrl + u - 剪切命令行中光标所在处之前的所有字符（不包括自身）
Ctrl + k - 剪切命令行中光标所在处之后的所有字符（包括自身）
Ctrl + a - 移动到当前行的开头
Ctrl + e - 移动到当前行的结尾
Ctrl + d - 删除光标所在处字符
Ctrl + h - 删除光标所在处前一个字符
Ctrl + y - 粘贴刚才所删除的字符
Ctrl + c - 删除整行
Ctrl + (x u) - 按住Ctrl的同时再先后按x和u，撤销刚才的操作
Ctrl + w - 剪切光标所在处之前的一个词（以空格、标点等为分隔符）
Alt + d - 剪切光标之后的词
Ctrl + f - 光标向前移动一个字符,相当与->
Ctrl + b - 光标向后移动一个字符,相当与<-
Alt + f - 光标向前移动一个单词
Alt + b - 光标向后移动一个单词
Esc + f - 移动到当前单词的结尾
Esc + b - 移动到当前单词的开头
Ctrl + t - 颠倒光标所在处及其之前的字符位置，并将光标移动到下一个字符
Alt + t - 交换当前与以前单词的位置
Esc + t - 颠倒光标所在处及其相邻单词的位置
Alt + u - 把当前词转化为大写
Alt + l - 把当前词转化为小写
Alt + c - 把当前词汇变成首字符大写
Ctrl + v - 插入非凡字符,如Ctrl v Tab加入Tab字符键
alt + . — 插入最有输入的命令。
alt + b — 光标移动到前一个单词处。
Esc + w - 删除光标所在处之前的字符至其单词尾（以空格、标点等为分隔符）

【控制】
Ctrl + l - 清屏
ctrl + c — 终止当前命令或进程。
ctrl + d — 终止shell。
ctrl + z — 将进程放入后台，可以用fg命令将放入后台的命令调入前台。
Ctrl + s - 挂起当前shell
Ctrl + q - 重新启用挂起的shell
shell(bash)命令行快捷方式



  [1]: https://github.com
  [2]: https://github.com/jerry011235/test
  [3]: https://josetomastocino.github.io/mindmapit
  [4]: http://7xivmb.com1.z0.glb.clouddn.com/git_%E6%96%87%E4%BB%B6%E5%92%8C%E6%96%87%E4%BB%B6%E5%A4%B9%E7%9A%84%E6%93%8D%E4%BD%9C.PNG
  [5]: http://mindmap.4ye.me/br57Govl
  [6]: https://hizzgdev.github.io/jsmind/developer.html
  [7]: http://mofas.github.io/mindMap/dist/index.html
  [8]: https://www.text2mindmap.com/
  [9]: https://kampfer.github.io/mindMap/client/index.html
  [10]: http://my-mind.github.io/
  [11]: https://github.com/jerry011235/test/commits/master
  [12]: http://7xivmb.com1.z0.glb.clouddn.com/git_%E7%82%B9%E5%87%BBcommits.png
  [13]: http://7xivmb.com1.z0.glb.clouddn.com/git_%E5%8F%B3%E9%94%AEraw.png
  [14]: http://ww3.sinaimg.cn/large/5f7e4f3ejw1ezvybehvd7j207k08cgm5.jpg
  [15]: http://i.stack.imgur.com/YfLUZ.jpg
  [16]: http://i.stack.imgur.com/KwOLu.jpg
  [17]: http://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add
  [18]: https://www.cnblogs.com/include/archive/2011/12/31/2308313.html