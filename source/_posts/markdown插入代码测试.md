---
title: markdown插入代码测试
date: 2015-05-06 11:31:15
categories: [o(^▽^)┛电脑技术, markdown]
tags: [markdown, 代码, hexo]
---

“效果”上面为图片，下面为部署后真实代码效果。

1.基本插入代码方法：直接空四个格
![][1]
效果：

      # Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
    
<!--more-->
2.首尾三个" ` ",其他什么也不加（注意这个点是数字1左边的键）。
![][2]

效果：

```
# Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
```

3.首尾三个\` , 空格后加一个 `c` ，再回车输入代码。
![][3]
效果：

``` c
# Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
```

4.首尾三个\` ,空格后加一个`bash`，再回车输入代码。
![][4]
效果：

``` bash
# Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap
```

5.首尾三个\` , 空格后加一个 `bash` ，再回车输入c语言代码。
![][5]
效果：

``` bash
#include <stdio.h>

int main(void)
{

printf("hello markdown\n");

return 0;

}
```
6.首尾三个\` , 空格后加一个 `c` ，再回车输入bash代码。
![][6]
效果：

``` c
$ hexo generate
$ hexo server
$ hexo deploy
```

提示：在markdown中要输入\` ，可以在\`的前面加一个反斜杠`\`来输入。即输入![][7]才能打出\`

![][8]

**从中可以看出，最漂亮的写法是首尾三个\` , 空格后加一个 `bash`或者`c`，这样能对齐，又能显示行号。**

参考：

 - [markdown 书写代码][9]
 - [Markdown 语法说明 (简体中文版)][10]


  [1]: http://7xivmb.com1.z0.glb.clouddn.com/%E5%9F%BA%E6%9C%AC%E5%86%99%E6%B3%95%E7%A9%BA%E5%9B%9B%E6%A0%BC-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [2]: http://7xivmb.com1.z0.glb.clouddn.com/%E5%8F%AA%E6%9C%89%E4%B8%89%E7%82%B9-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [3]: http://7xivmb.com1.z0.glb.clouddn.com/%E4%B8%89%E7%82%B9%E5%8A%A0c-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [4]: http://7xivmb.com1.z0.glb.clouddn.com/%E4%B8%89%E7%82%B9%E5%8A%A0bash-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [5]: http://7xivmb.com1.z0.glb.clouddn.com/%E4%B8%89%E4%B8%AA%E7%82%B9bash%E5%90%8E%E6%98%AFC-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [6]: http://7xivmb.com1.z0.glb.clouddn.com/%E4%B8%89%E4%B8%AA%E7%82%B9C%E5%90%8E%E6%98%AFbash%E5%91%BD%E4%BB%A4-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [7]: http://7xivmb.com1.z0.glb.clouddn.com/%E5%8F%8D%E6%96%9C%E6%9D%A0%E5%8A%A0%E7%82%B9-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [8]: http://7xivmb.com1.z0.glb.clouddn.com/Markdown%E6%94%AF%E6%8C%81%E4%BB%A5%E4%B8%8B%E8%BF%99%E4%BA%9B%E7%AC%A6%E5%8F%B7%E5%89%8D%E9%9D%A2%E5%8A%A0%E4%B8%8A%E5%8F%8D%E6%96%9C%E6%9D%A0%E6%9D%A5%E5%B8%AE%E5%8A%A9%E6%8F%92%E5%85%A5%E6%99%AE%E9%80%9A%E7%9A%84%E7%AC%A6%E5%8F%B7-markdown%E6%8F%92%E5%85%A5%E4%BB%A3%E7%A0%81%E6%B5%8B%E8%AF%95.PNG
  [9]: http://blog.csdn.net/pegasuswang_/article/details/37966169
  [10]: http://wowubuntu.com/markdown/