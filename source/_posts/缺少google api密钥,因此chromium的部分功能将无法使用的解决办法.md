---
title: 缺少google api密钥,因此chromium的部分功能将无法使用的解决办法
date: 2016-01-12 21:55:36
categories: [➎电脑技术, chrome]
tags: [chrome, chromium]
---

一直关注此问题，但没找到解决办法，今天偶然看到[这篇文章][1]，然后搜索`setx Google_API_KEY`和`chromium portable google api keys are missing`找到了解决办法。

平台：windows 7 32位
浏览器：chromium便携版（[crportable][2]）
下载链接：[http://sourceforge.net/projects/crportable/][3]

解决办法：打开windows的cmd命令提示符，**依次输入**以下命令：
``` bash
setx GOOGLE_API_KEY "no"
setx GOOGLE_DEFAULT_CLIENT_ID "no"
setx GOOGLE_DEFAULT_CLIENT_SECRET "no"
```
注销或重启后，再运行ChromiumPortable.exe就不会出现上述提示了。

来源：<https://stackoverflow.com/questions/21276763/google-api-keys-missing-warning-message-when-using-chromium-portable>


  [1]: http://www.5169.info/motion/que-shao-google-api-mi-yue-yin-ci-chromium-di-bu-fen-gong-neng-jiang-wu-fa-shi-yong.html
  [2]: http://crportable.sourceforge.net/
  [3]: http://sourceforge.net/projects/crportable/