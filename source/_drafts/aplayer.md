---
abbrlink: ''
categories:
- - 折腾记
- - 教程
date: '2023-04-30 10:59:54'
tags:
- 折腾
- 教程
title: aplayer音乐折腾记
updated: Sun, 30 Apr 2023 02:59:04 GMT
---
## 前言

搭建完Hexo博客之后，看着别人的博客有一个音乐播放器我就非常心动决定我也要整一个。那么让我们开始吧！

## 准备工作

- 一个已经搭建好了的Hexo框架

## 部署

> 采用插件的方法引用aplayer

在Hexo源文件中右键点击Git Bash，输入：

```
npm install --save hexo-tag-aplayer
```

等待完成，之后在Hexo根目录的_config.yml中输入：

```
aplayer:
meting: true
```

方便我们后面用

## 怎么使用？

相信有些人看了插件文档还是不会用（包括我），我在文档看了好几遍后，我悟了！

1. 在你想要引用播放器的页面引入
