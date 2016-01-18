title: hexo页面底部添加知识共享许可协议图标
date: 2015-05-11 23:46:36
categories: [o(^▽^)┛电脑技术, hexo]
tags: [教程, hexo]
---

编辑`D:\hexo\themes\你的主题目录\layout\_partial`目录下的`footer.ejs`文件，在`<div id="footer-info" class="inner">`下面添加一行：
``` bash
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank"><img src="https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png" alt="知识共享许可协议"></a><br>
```
修改后：
``` bash
    <div id="footer-info" class="inner">
	  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank"><img src="https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png" alt="知识共享许可协议"></a><br>
      &copy; <%= date(new Date(), 'YYYY') %> <%= config.author || config.title %><br>
      Powered by <a href="http://hexo.io/" target="_blank">Hexo</a>
      .
      Theme by <a href="https://github.com/xiangming/landscape-plus" target="_blank">Landscape-plus</a> <br>
	  
    </div>
```
这里我选择了署名-非商业性使用-相同方式共享（CC BY-NC-SA）协议，如果你想选择其他协议，可以[在这里][1]找到你想要的协议，然后将上面代码中的`href`地址替换成该协议的普通文本地址；`img src`替换成该图片地址（右键，新标签页打开图片）。

保存后重新部署即可。


  [1]: https://creativecommons.org/licenses/