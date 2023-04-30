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
updated: Sun, 30 Apr 2023 03:42:19 GMT
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

1. 在你想要引用播放器的页面里输入

```
{% aplayer "China-Y" "徐梦圆" "https://www.ytmp3.cn/down/59298.mp3" %}
```

比如我想在音乐的页面里引入播放器就在编辑音乐页面的文件里输入以上命令（简单说成在 markdown里输入）

![3p0ij.png](https://i.imgtg.com/2023/04/30/3p0ij.png)

生成页面测试一下，可以看到播放器就可以了

删除上面的命令输入下面的命令：

```
{% aplayerlist %}
{
"narrow": false,                          // （可选）播放器袖珍风格
"autoplay": true,                         // （可选) 自动播放，移动端浏览器暂时不支持此功能
"mode": "random",                         // （可选）曲目循环类型，有 'random'（随机播放）, 'single' (单曲播放), 'circulation' (循环播放), 'order' (列表播放)， 默认：'circulation'
"showlrc": 3,                             // （可选）歌词显示配置项，可选项有：1,2,3
"mutex": true,                            // （可选）该选项开启时，如果同页面有其他 aplayer 播放，该播放器会暂停
"theme": "#e6d0b2",	                      // （可选）播放器风格色彩设置，默认：#b7daff
"preload": "metadata",                    // （可选）音乐文件预载入模式，可选项： 'none' 'metadata' 'auto', 默认: 'auto'
"listmaxheight": "513px",                 // (可选) 该播放列表的最大长度
"music": [
{
"title": "CoCo",
"author": "Jeff Williams",
"url": "caffeine.mp3",
"pic": "caffeine.jpeg",
"lrc": "caffeine.txt"
},
{
"title": "アイロニ",
"author": "鹿乃",
"url": "irony.mp3",
"pic": "irony.jpg"
}
]
}
{% endaplayerlist %}
```

这是手动引入歌单

## MeingJS 支持

[MetingJS](https://github.com/metowolf/MetingJS) 是基于[Meting API](https://github.com/metowolf/Meting) 的 APlayer 衍生播放器，引入 MetingJS 后，播放器将支持对于 QQ音乐、网易云音乐、虾米、酷狗、百度等平台的音乐播放。

如果想在本插件中使用 MetingJS，请在 Hexo 配置文件 `_config.yml` 中设置，我们之前设置过了所有不用

接着就可以通过 `{% meting ...%}` 在文章中使用 MetingJS 播放器了：

```
<!-- 简单示例 (id, server, type)  -->
{% meting "60198" "netease" "playlist" %}

<!-- 进阶示例 -->
{% meting "60198" "netease" "playlist" "autoplay" "mutex:false" "listmaxheight:340px" "preload:none" "theme:#ad7a86"%}
```

有关 `{% meting %}` 的选项列表如下:


| 选项          | 默认值     | 描述                                                        |
| ------------- | ---------- | ----------------------------------------------------------- |
| id            | **必须值** | 歌曲 id / 播放列表 id / 相册 id / 搜索关键字                |
| server        | **必须值** | 音乐平台:`netease`, `tencent`, `kugou`, `xiami`, `baidu`    |
| type          | **必须值** | `song`, `playlist`, `album`, `search`, `artist`             |
| fixed         | `false`    | 开启固定模式                                                |
| mini          | `false`    | 开启迷你模式                                                |
| loop          | `all`      | 列表循环模式：`all`, `one`,`none`                           |
| order         | `list`     | 列表播放模式：`list`, `random`                              |
| volume        | 0.7        | 播放器音量                                                  |
| lrctype       | 0          | 歌词格式类型                                                |
| listfolded    | `false`    | 指定音乐播放列表是否折叠                                    |
| storagename   | `metingjs` | LocalStorage 中存储播放器设定的键名                         |
| autoplay      | `true`     | 自动播放，移动端浏览器暂时不支持此功能                      |
| mutex         | `true`     | 该选项开启时，如果同页面有其他 aplayer 播放，该播放器会暂停 |
| listmaxheight | `340px`    | 播放列表的最大长度                                          |
| preload       | `auto`     | 音乐文件预载入模式，可选项：`none`, `metadata`, `auto`      |
| theme         | `#ad7a86`  | 播放器风格色彩设置                                          |

## 怎么开多个播放器？

这个简单以MeingJS为例：

在 `{% meting "60198" "netease" "playlist" %}`头上加入

```
<div id='demo1'></div>
```

例如：

```
1.
<div id='demo1'></div>
{% meting "60198" "netease" "playlist" %}
2.
<div id='demo2'></div>
{% meting "60198" "netease" "playlist" %}
3.
<div id='demo3'></div>
{% meting "60198" "netease" "playlist" %}
```

以此类推就可以多开了

这就是所有内容了我们下期见
