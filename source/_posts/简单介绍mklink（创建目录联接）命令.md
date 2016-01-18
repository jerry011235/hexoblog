---

title: '简单介绍mklink  / j（创建目录联接）命令'
date: 2014-02-23 07:39
tags: mklink
categories: [o(^▽^)┛电脑技术, 经验技巧]
---
在D盘根目录新建一个123文件夹,C盘根目录原来没有123文件夹,然后:
对于win7系统，开始,所有程序,附件,右键点击"命令提示符",选择"以管理员命令打开",输入以下命令(注意:其中"k "和 "/"之间有一个空格,"/j"之间没有空格,其中双引号""应为英文输入法时的双引号):
mklink /j "C:\123"  "D:\123"
此时C盘多出了一个123文件夹（注意：C盘一定原来没有此文件夹，如果有，则不成功）。
现在的情况：
① D:\123为源文件，c盘123文件夹是D盘的映射；
② D:\123占用硬盘空间，C:\123不占用硬盘空间；
③ D:\123是“真”的，C:\123是“假”的。
删除 D:\123 则 C:\123文件夹及其子文件夹和文件  无法访问（留着没有什么用，又无法访问，所以最后被删除了）。 
删除 C:\123 则 D:\123文件夹及其子文件夹和文件  保留原样。
其他操作（比如复制，剪切，粘贴等）同步进行。

提示：win7系统可以直接在命令提示符中使用mklink /j命令，如果电脑是xp系统，则需要下载Junction软件。
下载地址： [http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx) ，然后把下载到的Junction.zip解压到C盘跟目录。然后cmd后切换到c盘根目录，C:>junction "映射文件路径" "源文件路径"

应用：如果D盘空间不够了，而E盘还有很大的空间富余，而平常经常打开D盘操作，则可以把文件先转移到E盘，然后映射到D盘即可。（注意先用U盘或移动硬盘备份好文件，转移时可以剪切或复制）
其他资料：
[活用 MKLINK 命令保护、节省你的硬盘](http://www.sinosky.org/mklink-cmd-useful-tips.html)
[玩转WIN7的MKLINK](http://www.cnblogs.com/asion/archive/2011/03/10/1979282.html)
[Winxp下修改Chrome的User Data目录](http://www.9enjoy.com/winxp-move-chrome-user-data/)