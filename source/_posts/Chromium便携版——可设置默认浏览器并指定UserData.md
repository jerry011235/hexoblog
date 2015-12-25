---

title: 'Chromium便携版——可设置默认浏览器并指定UserData'
date: 2014-02-23 07:15
tags: chrome
categories: [➎电脑技术, chrome]
---
1.在你想要安装Chromium的目录新建两个文件夹:[Application]和[User Data],比如D:\Program Files\Chromium\Application和D:\Program Files\Chromium\User Data
2.去[https://download-chromium.appspot.com](https://download-chromium.appspot.com)下载最新chromium压缩包,并把chrome-win32文件夹里的所有内容(其中包含chrome.exe程序)复制或剪切到D:\Program Files\Chromium\Application文件夹里.
3.如果以前有User Data的备份,把备份的User Data文件复制到D:\Program Files\Chromium\User Data，注意D:\Program Files\Chromium\User Data文件夹下面有Default、pnacl文件夹，其中Default\Extensions里有你的扩展等等。
4.使用mklink  / j（创建目录联接）命令。
注意：
①如果以前安装过Chromium的话,那要检查下C:\Users\你的用户名\AppData\Local\Chromium文件夹,这个文件夹要留空。
②win7系统可以直接在命令提示符中使用mklink  / j命令，如果电脑是xp系统，则需要下载Junction软件。
下载地址： [http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx) ，然后把下载到的Junction.zip解压到C盘跟目录。然后cmd后切换到c盘根目录，C:\>junction "映射文件路径" "源文件路径"

开始,所有程序,附件,右键点击"命令提示符",选择"以管理员命令打开",输入以下命令:
(注意:其中"k "和 "/"之间有一个空格,"/ j"之间没有空格,其中双引号""应为英文输入法时的双引号)

mklink /j "C:\Users\你的用户名\AppData\Local\Chromium\User Data" "d:\Program Files\Chromium\User Data"

mklink /j "C:\Users\你的用户名\AppData\Local\Chromium\Application" "d:\Program Files\Chromium\Application"

然后去C:\Users\你的用户名\AppData\Local\Chromium文件夹,发现多了两个文件夹。
5.找到C:\Users\你的用户名\AppData\Local\Chromium\Application中的chrome.exe,发送到桌面快捷方式.改名为Chromium.
6.如果要使用Flash,则先下载pepflashplayer.dll文件,然后使用"--ppapi-flash-path"命令指定使用此flash.即在Chromium桌面快捷方式右键,属性,目标的后面加上 --ppapi-flash-path="pepflashplayer.dl的路径"
比如 目标为(其中chrome.exe 和"--"之间有个空格): 
C:\Users\你的用户名\AppData\Local\Chromium\Application\chrome.exe --ppapi-flash-path="D:\Program Files\Chromium\User Data\PepperFlash\pepflashplayer.dll"
其中pepflashplayer.dll可以在网上下载,也可以在虚拟机中安装chrome稳定版,然后在其安装目录里找.完成后,这样就能看优酷等视频了.如果还是看不了,就不知道是什么问题了.

7.运行Chromium,如果需要,可以设置Chromium为默认浏览器,
 检查默认浏览器是否设置成功的方法：在“开始”菜单 > “运行” (或者按win+R)中输入网址（如 www.baidu.com ），按“确定”后打开的浏览器即为当前默认浏览器.
 
8.如果以后要更新,就全部删除D:\Program Files\Chromium\Application文件夹里的文件,然后做第二步就OK.
9.如果某天打开chromuim发现扩展消失（我也不知道为什么，可能因为使用了某个优化清理程序，比如CCleaner），则 解压缩 以前备好分的User Data压缩包，把包含Default文件夹的其他整个文件[全选]，[剪切]，然后[粘贴]到D:\Program Files\Chromium\User Data里，即可。
注意：不要删除D:\Program Files\Chromium\User Data这个“源”文件夹，否则又要重新mklink一次。

Enjoy!


