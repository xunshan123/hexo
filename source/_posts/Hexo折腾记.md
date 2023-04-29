---
abbrlink: ''
categories:
- - 折腾记
date: '2023-04-29 11:58:32'
tags:
- 折腾
title: Hexo折腾记
top_img: https://i.imgtg.com/2023/04/29/3efV1.png
updated: Sat, 29 Apr 2023 04:09:36 GMT
---
## 前言

大概是2022年的时候，我想搭建一个博客可是看了许多博客的框架就是找不到适合我的比如

WordPress它虽然好但是需要部署在动态服务器上，我没有太多钱去续费服务器免费的话也有一定的限制所以我不太喜欢。思来想去我看到了静态博客hexo，虽然没有后台但可以以后部署一个后台，那让我们一起来部署hexo吧

## 配置环境

在安装hexo之前，您需要安装nodejs和git

#### 1.下载nodejs

点击 [nodejs下载](https://nodejs.org/en/)，下载好后双击打开，默认一路next。

#### 2.下载Git

点击 [Git下载](https://git-scm.com/download/win)，下载好后双击打开，也是默认一路next。


## 检查安装的Node.js（内置npm） 和 Git 是否安装成功

步骤1：
找到我们的 Git Bash 并打开，一般都在任务菜单栏里

步骤2：
在命令行中输入： `node -v`和`npm -v`然后回车（Enter）

![31Cbx.png](https://i.imgtg.com/2023/04/29/31Cbx.png)

如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。

## 安装Hexo

先创建一个文件夹放置hexo文件

右键点击Git Bash，输入以下命令：

```
#安装hexo框架
npm install -g hexo-cli
#查看hexo框架版本
hexo -v
```

安装成功后，会显示如下图样式

![37qQv.png](https://i.imgtg.com/2023/04/29/37qQv.png)

然后输入 `hexo init` 初始化此文件夹（有时候会抽风多输几遍 `hexo init`就行）

初始化成功的时候：（会在文件夹中生成很多文件，请不要删除）

![375Cq.png](https://i.imgtg.com/2023/04/29/375Cq.png)

![37Tic.png](https://i.imgtg.com/2023/04/29/37Tic.png)


此时，可以输入 `hexo server` 生成html静态网页文件

生成成功样式：（之后就可以通过浏览器访问 [http://localhost:4000/](http://localhost:4000/) 访问网页啦，按Ctrl+C可以关闭网页）

访问的网页样子是这样的：

![3NJT1.png](https://i.imgtg.com/2023/04/29/3NJT1.png)

## 上传Github

首先你要注册一个Github账号，然后创建一个仓库

创建一个名为

```
xxxx.github.io
```

用于访问你的博客（把xxxx换成你的你github的名字就行了）例如

![3eGGY.png](https://i.imgtg.com/2023/04/29/3eGGY.png)

你要生成github秘钥

1.生成 Personal access tokens

进入 Developer settings：

![3e0iq.png](https://i.imgtg.com/2023/04/29/3e0iq.png)

生成 token，自己设置「过期时间」和「访问权限」，我是设置成了「永不过期」并开启了所有「访问权限」：

![3ectc.jpg](https://i.imgtg.com/2023/04/29/3ectc.jpg)

先把 token 复制一份留着，建议备份，以备下次使用，（本文后面也需要）

回到hexo文件里的Git Bash

1. 首先安装上传插件,输入以下命令

```
npm install --save hexo-deployer-git
```

2. 配置 文件夹下\_config.yml文件

在文件末尾，替换为以下代码，并需要你刚才备份的秘钥

```
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git 
  repository: https://<github生成的TOKEN>@github.com/你的github名/你的仓库名.git 
  branch: main
```

保存成功后，然后依次输入hexo上传三件套

```
hexo clean 
hexo generate
hexo d
```

上传成功后会出

![3ed2r.png](https://i.imgtg.com/2023/04/29/3ed2r.png)

github中也会出现文件

## 常见问题

1.为什么会出现两个main？

答：我也不知道，在项目中点击Settings。在里面找到Default branch

![3eVbM.png](https://i.imgtg.com/2023/04/29/3eVbM.png)

选择第二个最后选择Update就行了

这就是本期的所有内容了🙂
