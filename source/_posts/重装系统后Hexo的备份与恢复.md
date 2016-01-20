---
title: 重装系统后Hexo的备份与恢复
date: 2015-05-26 9:03:05
categories: [⛺电脑技术, hexo]
tags: [教程, hexo]
toc: true
---
最近重装了系统，顺便写下hexo的备份与恢复过程。当然要先在文件夹选项里选择“显示隐藏文件”和取消“隐藏已知文件的扩展名”。

## 备份

 1. 备份好hexo目录下的`source`文件夹，`theme`文件夹、`node_modules`文件夹（里面有你安装的插件，这个可选）和站点配置`_config.yml`文件（当然如果你硬盘空间够大，备份整个hexo文件夹也可以）。然后把hexo目录里面的东西全部删掉。
 2. 备份用户目录下的文件：开始，你的windows用户名，打开你的用户文件夹后备份`.ssh`文件夹和`.gitconfig`、`_netrc`以及`_viminfo`这三个文件。

## 恢复
 1. 安装Git
去[https://msysgit.github.io][1]直接点击download下载git，安装时我选择安装到D盘，然后勾选“`On the Desktop`”添加桌面快捷方式，然后一路next即可。
 2. 安装node.js
去[https://nodejs.org/download/][2]点击那个windows installer图标，下载`node-v0.12.4-x86.msi`，一路next即可。
<!--more-->
 3. 去[hexo官方][3]看到hexo的安装命令已经改为：
```
npm install hexo-cli -g
```
于是运行gitbash后，先在标题栏右键，属性，“快速编辑模式”打勾，然后右键（粘贴）以上命令，接着：
``` bash
cd D:\hexo
hexo init
npm install
```
安装插件：
``` bash
npm install hexo-deployer-git --save
npm install hexo-generator-feed --save
npm install hexo-generator-sitemap --save
```
**当然你也可以去事先备份的`node_modules`文件夹找到你想要安装的插件，然后粘贴到对应位置。**

下载主题：
```
git clone https://github.com/xiangming/landscape-plus.git themes/landscape-plus
```
 4. 复制事先备份的source文件夹，theme文件夹和站点配置`_config.yml`文件粘贴替换掉`D:\hexo`里的文件。
 5. 和gitcafe建立连接
在gitbash里输入：
``` bash
git config --global user.email "Your email"
git config --global user.name "Your name"
```
然后开始，你的windows用户名，打开你的用户文件夹，粘贴并替换事先备份的`.ssh`文件夹和`.gitconfig`、`_netrc`以及`_viminfo`这三个文件。
然后再输入：
``` bash
ssh -T git@gitcafe.com
```
这时会看到显示连接成功信息。

>注意：如果更换电脑的话，则在输入命令前需要新建一个用户的环境变量（计算机，右键属性，高级系统设置，最下面“环境变量”，好像新建系统环境变量也可以），变量名为`HOME`，变量值为 `%USERPROFILE%`。这样才能显示连接成功信息。

![][4]

这时，一切都回到了原来的样子。


  [1]: https://msysgit.github.io
  [2]: https://nodejs.org/download/
  [3]: https://hexo.io
  [4]: http://ww2.sinaimg.cn/large/5e8cb366jw1e51yjjv0okj20b00b5gmp.jpg