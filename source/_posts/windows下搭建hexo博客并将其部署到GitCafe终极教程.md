title: "windows下搭建hexo博客并将其部署到GitCafe终极教程"
date: 2015-05-05 00:41:59
categories: [➎电脑技术, hexo]
tags: [hexo, 教程, GitCafe, 博客, blog]
toc: true

---
这两天看了N多教程后，终于成功建立了个HEXO博客，并且将其托管到了GitCafe上。

下面是终极教程小白版（因为我就是小白－－！）

## 小提示(我走的弯路)：

>1. **所有标点符号都是英文的，所以输入时请切换到英文状态。**
>2. **冒号后面一定要有个空格,否则回报错。**
>3. **所有文件（不管是以md为后缀的，还是以yml结尾的），都必须转换成UTF-8格式，可以在notepad++的格式里转换下，否则在本地查看（localhost:4000）中会出现乱码。**
>4. **文件夹选项中要勾选“显示隐藏的文件”，而下面的“隐藏已知文件类型的扩展名”则不要勾选**。
>5. **最新版Hexo（3.0.0或以上版本）默认未安装hexo-deployer-git插件，即部署（上传）到gitcafe或github要用的插件，所以如果不安装这个插件，就要报错。**
>6. **Git Bash右键点击左上角的图标，选择属性，右侧编辑选项中“快速编辑模式”打勾，这是为了在Git Bash中点击右键就能粘贴。**
>7. **不建议用默认hexo主题，建议在网上找个其他主题，不仅因为好看，还因为其他主题往往集成了多说、支持中文简体等优势，省去了你自己折腾的时间。**

 
## 开始 
-------

 

### 环境准备 

1.安装 node.js
   去 [Node.js][1] 下载最新版的 Node.js，一路next安装到C盘。
2.安装Git
   如果是Windows平台，则下载[msysgit][2],我安装到D盘，安装时注意勾选“On the Desktop”添加桌面快捷方式，然后一路next即可。 

   反正以后重装系统后，这两个程序都要重新安装。

### 安装hexo博客
1.双击桌面Git Bash图标或者从开始菜单，所有程序，git，打开Git Bash：
![gitbash][3]
>**注意：这时右键点击左上角的图标，选择属性，右侧编辑选项中“快速编辑模式”打勾，这是为了在Git Bash中点击右键就能粘贴**。
<!--more-->
该输入代码了：

``` bash
$ npm install -g hexo
```

这条命令是安装hexo，然后

``` bash
#进入D盘
cd d:
# 创建文件夹hexo，为了存放你的博客各种内容及设置
mkdir hexo
# 进入hexo文件夹
cd  hexo
```

这时看到Git Bash标题栏的路径为/D/hexo,如图：
![][4]

``` bash
# 初始化文件hexo
hexo init
# 安装依赖包
npm install 
```


>**注意：安装hexo-deployer-git插件**


``` bash
npm install hexo-deployer-git --save
```



然后生成


``` bash
#生成
hexo g
#启动服务预览
hexo s
```


代码简写：
hexo g == hexo generate
hexo s == hexo server

当看到`INFO  Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.`时就说明我们已经搭建起本地的hexo博客了，然后到浏览器输入localhost:4000看看（或者打开http://127.0.0.1:4000/ 也行）。
**注意：不要打开提示的0.0.0.0:4000**。
![][5]

然后回到命令窗口按Ctrl+C停止服务（有时要按两次Ctrl+C，因为有时Git Bash认为当前在进行复制操作），直到出现 “$”标志就结束了。
然后关闭Git Bash.

### 配置gitcafe 
---------
>注意：以下假设你的gitcafe账号或者用户名是：`hello`，你的邮箱为：`hello@gmail.com`，密码为`hello123`


----------


到 [https://gitcafe.com][6] 注册个账号，然后创建项目，右上角的那个图标可以新建项目，右侧也有“新建”字样。
凡是选填的可以不填，其他默认。


>**注意：项目名需要与你的用户名相同，还有就是要选择“公开项目”。**

下图是别人的图片，虽然用户名（项目名）不是hello，但实际操作时注意项目名称要和注册ID一样，项目主页可以不填。
![gitcaf项目][7]


### 配置SSH公钥
首先我们需要检查你电脑上现有的ssh key：

``` bash
cd ~/.ssh
```

如果提示：No such file or directory 说明你是第一次使用git。

### 生成新的SSH Key


``` bash
ssh-keygen -t rsa -C "hello@gmail.com"

Generating public/private rsa key pair.
Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>
```


出现
![sshkeygen][8]

然后系统会要你输入密码：


    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:


这个设置是防止别人往你的项目里提交内容，我直接回车。

看到入下图所示后，SSH key就生成成功了。
![sshkeyok][9]

然后你可以去开始，打开你的用户目录，有一个“.ssh”文件夹，里面有
“id_rsa” “id_rsa.pub” 和 “known_hosts”这三个文件。
![ssh文件][10]
其中“id_rsa”是你的私钥文件，“id_rsa.pub”是你的公钥文件，一会儿要用。
接下来下载notepad++ 文本编辑器，比windows自带的记事本更强大，这里我们主要用它来打开id_rsa.pub文件。
这是他的官网：[notepad++官网][11]
下载后，直接把“id_rsa.pub”文件拖进notepad++中，然后复制里面的所有内容到剪贴板。

### 添加SSH Key到Gitcafe
然后去GitCafe，点击右上角的那个图标，选择账户设置，左侧SSH公钥管理，添加新的公钥，在名称文本框中输入任意字符，在公钥文本框粘贴刚才复制的公钥字符串**全部内容**（包括结尾的邮箱），输入GitCafe账户密码，按保存按钮完成操作。
![][12]
这样我们本地就和GitCafe服务端连接上了。

### 测试是否可以连接GitCafe服务器

在桌面上双击打开Git Bash，输入：

``` bash
ssh -T git@gitcafe.com 
```

如果是第一次连接的话，会出现:

``` bash
The authenticity of host 'gitcafe.com (50.116.2.223)' can't be established.
#RSA key fingerprint is 84:9e:c9:8e:7f:36:28:08:7e:13:bf:43:12:74:11:4e.
#Are you sure you want to continue connecting (yes/no)?
```

直接输入yes回车,然后会提示你输入 passphrase 口令：

``` bash
Enter passphrase for key ‘/c/Users/USERNAME/.ssh/id_rsa’: 
```

刚才我们根本就没设置，所以这次也直接回车,当看到

``` bash
Hi starsky! You've successfully authenticated, but GitCafe does not provide shell access.
```

我们就连接成功了。
![][13]

### 设置用户信息

``` bash
# 设置你的用户名
git config --global user.name "hello"  
# 设置你的邮箱
git config --global user.email "hello@gmail.com"
```

到此为止，SSH Key配置成功，本机已成功连接到gitcafe.
就差最后一步了，把博客部署到gitcafe.
### 修改hexo配置文件
在 Hexo 文件夹下找到 _config.yml 文件，并拖到notepad++ 打开。
![][14]
找到其中的 deploy 标签，改成下图所示，并保存：

``` bash
deploy:
  type: git
  repository: https://gitcafe.com/hello/hello.git 
  branch: gitcafe-pages
```

>**注意：除了 “https://” 中的冒号以外，其他每个冒号后面都有个空格,最后保存。**

### 把hexo博客部署到gitcafe
>**注意：以下假设你注册gitcafe时使用的密码是`hello123`**

打开我的电脑，进入D盘的hexo目录，在该目录内右键，选择Git Bash，打开后看到Git Bash标题栏的路径为/D/hexo.

>**注意：以后我们很多的博客操作都要在此目录下运行Git Bash才行，比如新建博文、上传部署等等。**

输入：

``` bash
hexo d
```

运行中要输入你的用户名：输入`hello`，回车，然后要输入密码，输入`hello123`（这时当你输入时，你会发现输入之后密码是不显示的，也不显示星号，这是为了安全，并非是你没输上），回车后显示Deploy done等等就成功部署上了！如图：
![][15]

如果出错改成下面的代码试一下：
``` bash
deploy:
  type: git
  repository: git@gitcafe.com:hello/hello.git
  branch: gitcafe-pages
```


### 每次deploy时不输入邮箱和密码
如果觉得每次部署的时候都要输入用户名和密码，可以这样解决：开始，到你的用户目录下新建一个`_netrc`文件。
我的操作：可以直接复制一个`.gitconfig`文件复件，然后改名为`_netrc`，**注意：n前面有个下划线。**
然后把`_netrc`文件拖入notepad++ 里，输入：

``` bash
machine gitcafe.com
login hello
password hello123
```

，这样每次部署的时候就不用输入用户名和密码了。
来源：
[把Hexo同时部署到GitHub和GitCafe][16]
[Git push时重复输入用户名密码的问题][17]

## 大功告成 ：）

这时你就成功把hexo博客部署到了gitcafe上，快打开 http://hello.gitcafe.io/ 看看吧！

最后的最后，别忘了最最重要的一件事，现在，跟着我一起做，闭上双眼，双手合十，心里默念：感谢[GitCafe][18]！！！

### 其他问题
问题集1:
>1. 有网友反应右键菜单中没有git bash选项，可以进入开始菜单找到git bash，然后通过cd进入相应目录执行命令。
>
>
>2. 在github部署完成之后，马上访问可能出现404错误，这是正常的，（最多）等待十分钟左右就可以访问了。如果还不行，那很可能是 github 发送给你的验证邮件你没有打开看，据多方反映，验证后就没问题了。
>3. 如果在hexo d之后出现fatal: 'username.github.io' does not appear to be a git repository，一是检查 repo 的名字是否合乎规范、是否含有大写字母、config.yml 中的 deploy 配置是否正确，二是把 git bash 关掉，重新打开再执行命令。
>4. 有的同学可能不是 IT 界的，或者对shell 命令不太了解。在要求输入密码时，你输入之后密码是不显示的，这是为了安全，并非是你没输上。
>5. 出现乱码的，不要使用 windows 中的「记事本」打开并编辑文件，推荐使用 sublime text，很简单。如果已经在「记事本」中编辑过，需要使用 sublime text 转码为「utf8」。
>6. 安装 hexo 时卡在那儿不动，很可能是网络不给力，能全局 break wall 就好了。
>7. 遇到什么其他的问题，不妨删除.deploy 和db.json 再重新生成试一试。

来源：[hexo系列教程：（二）搭建hexo博客][19]

问题集2:

>1.安装NoteJs，出现问题，安装到最后提示error 52** 
    过程：重新下载安装了几次都不行，不懂为什么，最后通过Hexo的文档提供下载地址进行下载，然后安装问题就没有出现了。 可能原因：
    a.下载的安装包有问题的原因 
    b.我的C盘占用过多，盘符标红，然后卸载一些不常用软件解决，再安装再加上上面重新下载的安装包，之后安装成功。
>
>2.部署提示找不到git 
解决办法： 在Hexo 3.0版本后deploy git 被分开的，所以需要安装，安装命令如下:npm install hexo-deployer-git --save ,安装好后在尝试一下就ok。
>
>3.部署提示 ｀event type error ***｀ 
解决办法： 
安装了git bash没有配置到环境变量path中，添加进去在试试。
>
>4.部署的时候执行：hexo deploy 命令行没有任何输出，也没有错误。 
解决办法： 
在部署的_config.yml文件中，找到deploy:标签，在每个冒号后面必须要空格，否则就会出现上述问题。我的配置如下：
>    deploy:
>    type: git
>   repository: https://github.com/wx962464/wx962464.github.io.git
>    branch: master
>顺便提示下，如果使用ssh部署不成功的话，请使用https的方式试试，这个就是每次会让你输入用户名和密码。其实效果是一样的。
>
>5.修改主题不起作用，而且hexo generate还报错 
解决办法： 
需要到相应的主题文件夹下面进行修改，比如我的主题为：themes\jacman 则在根目录下找到该文件夹下，修改_config.yml文件，根目录下面也有个同样的名字，不注意，容易弄混，要主要修改的文件是否正确。
>
>6.执行hexo server显示running at http://0.0.0.0:4000/ 
问题说明： 
开始的时候以为启动服务器有问题，一直在找问题，找了半天没有答案，最后在浏览器直接尝试http://0.0.0.0:4000/ 是没办法访问的，然后就试了下http://localhost:4000/ 发现是可以访问的，大喜！~~
>
>7.执行hexo server提示找不到该指令 
解决办法： 
>在Hexo 3.0 后server被单独出来了，需要安装server，安装的命令如下：npm install hexo-server --save 安装此server后再试，问题解决。
>
>8.以上就是我在这几天使用Hexo的一些问题，当然问题列的不够详细，只是一个大致思路，这些也是凭着自己的印象做的笔记，所以有些错误的地方希望大家指出，共同学习，共同进步！

来源：[Hexo 使用中遇到的问题总结][20]


----------


### 参考

 - [如何搭建一个独立博客——简明Github Pages与Hexo教程][21]
 - [将Hexo部署到GitCafe][22]
 - [hexo系列教程][23]
 - [hexo你的博客][24]
 - [Hexo博客系列][25]
 - [部署Hexo静态blog到gitcafe][26]
 - [Windows下一步步搭建自己的独立博客——使用 GitHub Pages + Hexo 基础教程][27]
 - [使用Hexo发表博文的整理][28]


  [1]: http://nodejs.org/
  [2]: https://msysgit.github.com
  [3]: http://haos.qiniudn.com/images/blog/Ashampoo_Snap_2014.09.18_21h14m25s_006_.png
  [4]: http://ww2.sinaimg.cn/large/5f7e4f3egw1ert79osvw2j20il03egm4.jpg
  [5]: http://files.colabug.com/forum/201405/07/235226qur8ku07nl777ki9.png
  [6]: https://gitcafe.com
  [7]: http://haos.qiniudn.com/images/blog/Ashampoo_Snap_2014.09.18_21h43m32s_007_.png
  [8]: http://images.cnitblog.com/blog/282019/201409/091222268402433
  [9]: http://cnfeat.qiniudn.com/11.png
  [10]: http://images.cnitblog.com/blog/541485/201307/02231907-ad2d073fc9a44ba4ac65f38ac575b156.png
  [11]: http://notepad-plus-plus.org/
  [12]: http://haos.qiniudn.com/images/blog/Ashampoo_Snap_2014.09.18_21h48m20s_008_.png
  [13]: http://haos.qiniudn.com/images/blog/Ashampoo_Snap_2014.09.18_17h30m36s_001_.png
  [14]: http://7xi78f.com1.z0.glb.clouddn.com/9.png
  [15]: http://7xi78f.com1.z0.glb.clouddn.com/9-3.png
  [16]: http://xote.tk/9.html
  [17]: http://zipperary.com/2013/05/26/ssh-errors-with-github/
  [18]: https://gitcafe.com
  [19]: http://zipperary.com/2013/05/28/hexo-guide-2/
  [20]: http://blog.csdn.net/wx_962464/article/details/44786929
  [21]: http://www.jianshu.com/p/05289a4bc8b2
  [22]: http://www.sumrday.com/2014/09-18-Hello-Hexo.html
  [23]: http://zipperary.com/2013/05/28/hexo-guide-2/
  [24]: http://ibruce.info/2013/11/22/hexo-your-blog/
  [25]: http://www.isetsuna.com/hexo/install-config/
  [26]: http://blog.magiclin.com/2013/12/20/hexo-gitcafe/
  [27]: http://yangruihan.com/categories/%E6%95%99%E7%A8%8B/
  [28]: http://smyh.me/2014/11/04/2014-11/%E4%BD%BF%E7%94%A8Hexo%E5%8F%91%E8%A1%A8%E5%8D%9A%E6%96%87%E7%9A%84%E6%95%B4%E7%90%86/