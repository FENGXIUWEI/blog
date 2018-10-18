---
title: Hexo的基本使用
date: 2018-04-18 17:09:08
bgimage: "/images/hexo/bg.png"
comments: true
categories:
- hexo
tags:
- Hexo的基本使用
---
## Hexo相关的网站
https://hexo.io/zh-cn/docs/commands.html

## Hexo 的安装
npm install hexo-cli g

## Hexo 环境变量的配置
![hexo图片](/images/hexo/18.png)

## Hexo命令

```javascript
hexo new [layout] <title>  hexo new post "新建一篇文章"  #新建一篇文章
hexo generate  简写 hexo g  #生成静态文件
hexo server #启动服务器
hexo deploy 简写 hexo d #部署网站
hexo clean #清理缓存文件和已生成静态的文件
hexo version #显示hexo的版本
```

## 本地图片的使用
主配置_config.yml文件中将post_asset_folder:true

运行下面代码

```javascript
npm install https://github.com/CodeFalling/hexo-asset-image –save
```

图片的路径写法："/images/hexo/bg.jpg"

![hexo图片](/images/hexo/hexoimg.png)

## Hexo 主题安装
## 主题的筛选

Hexo主题 ( https://hexo.io/themes/ )页面,可以欣赏到很多很优秀的主题

![hexo主题](/images/hexo/hexotheme.png)

## 下载主题

点击图片,就会跳到这个主题的博客,看到实际的效果
下载这个主题,就点击主题文字,进入主题Github页面,然后复制下载地址

![下载hexo主题](/images/hexo/downloadtheme.png)

进入blog目录,克隆主题到本地

```javascript
$ git clone https://github.com/TongchengQiu/hexo-theme-another.git themes/another
```

## 安装主题

修改blog根目录的_config.yml,将theme修改为another

*注意: 某些主题可能需要安装Node.js的插件,在安装主题时,最好在主题的Githu主页看看安装步骤*

![hexo主题](/images/hexo/edittheme.png)