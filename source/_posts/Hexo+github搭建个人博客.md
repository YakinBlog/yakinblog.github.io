---
title: Hexo+Github搭建个人博客
#categories: 教程
tags: [hexo, github, nodejs, 教程] 
description: Hexo+Github搭建个人博客
---
[Hexo](https://hexo.io/)是一款基于[NodeJS](https://nodejs.org)的静态博客框架，以下介绍的是在Mac系统下的搭建过程，简单实用，足够满足个人点滴的分享和记录，而无需个人服务器，可绑定域名。

## 环境配置

### 必要软件

* XCode：[APP Store](https://developer.apple.com/xcode/)下载安装
* Git：XCode内置有git，或者[官网](https://git-scm.com/downloads)下载
* NodeJS：[官网](https://nodejs.org)下载
* Npm：安装NodeJS时会连带安装

## 搭建站点

### 安装Hexo

``` bash
$ sudo npm install -g hexo
```

<!-- more -->

### 初始化博客

新建一个空文件夹blog, 在blog文件夹下运行：

``` bash
$ hexo init
```

### 启动本地服务

``` bash
$ hexo s[server]
```

在浏览器里访问 http://localhost:4000 ， 预览博客。

## 部署到github

在github上创建个同账号名的repository，仓库名为：your_user_name.github.io
再修改blog/_config.yml配置文件，与github建立关联。

``` bash
deploy:
  type: git
  repo: git@github.com:your_user_name/your_user_name.github.io.git
  #git的方式可以轻易配置免密码deploy，而用http/https的地址每次deploy都需要输入密码
  branch: master
```

安装部署插件包:

``` bash
$ sudo npm install hexo-deployer-git --save
```

执行deploy命令就可以将生成的静态页面push到github中：

``` bash
$ hexo deploy
```

访问 [http://your_user_name.github.io](https://yakinblog.github.io/) ，就可以浏览你的博客站点了！！！
站点默认部署到master分支，可建hexo分支存放站点源码。

## Hexo 常用命令

### 新建文章

``` bash
hexo n[new] "我的博客" 
```

More info: [Writing](https://hexo.io/docs/writing.html)

### 启动服务

服务会检测文件变动自动更新，无需重启服务

``` bash
$ hexo s[server]
	-s #静态模式
	-p [端口号] #更新端口号
	-i [ip] #更新IP
```

More info: [Server](https://hexo.io/docs/server.html)

### 生成静态文件

``` bash
$ hexo g[generate]
	--watch #监控文件变动
```

More info: [Generating](https://hexo.io/docs/generating.html)

### 部署到远程仓库

``` bash
$ hexo d[deploy]
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

### 修改后，重新部署

``` bash
$ hexo clean #清理缓存
$ hexo g[generate]
$ hexo d[deploy]
```

## 配置域名

### 域名解析

以万网为例：
域名->解析->添加解析

|记录类型|主机记录|解析线路|记录值|TTL值|
|:----|:----:|----:|----:|----:|
|CNAME|www|默认|yakinblog.github.io|10分钟|
|A|@|默认|192.30.252.153|10分钟|
|A|@|默认|192.30.252.154|10分钟|

记录类型选A或CNAME，A记录的记录值就是ip地址，github(官方)提供了两个IP地址，192.30.252.153和192.30.252.154，这两个IP地址为github的服务器地址，解析记录设置两个www和@，其他的默认即可，CNAME记录值填github博客网址。

### 站点配置

创建写有域名的CNAME文件，放到根目录下source目录里，如我的CNAME域名：yakinblog.com

``` bash
$ echo [域名] > source/CNAME
```

重新部署站点，即可使用 [yakinblog.com](http://yakinblog.com/) 访问站点。

注意：CNAME里的域名如果带有www，如www.yakinblog.com，则访问时只能使用www.yakinblog.com访问，如果不带www，如yakinblog.com，则www.yakinblog.com和yakinblog.com都可访问。

## 提交搜索引擎(百度 + 谷歌)

### 查看是否被搜索引擎收录

在搜索框里使用下边格式搜索域名，查看是否被收录，如我的：site:yakinblog.com

``` text
site:[域名]
```

### 验证网站

搜索引擎入口：

* [Google搜索引擎提交入口](https://www.google.com/webmasters/tools/home?hl=zh-CN)

* [百度搜索引擎入口](http://www.baidu.com/search/url_submit.htm)

> [为什么要验证网站](http://zhanzhang.baidu.com/college/courseinfo?id=267&page=1#h2_article_title3)

> 站长平台推荐站长添加主站（您网站的链接也许会使用www 和非 www 两种网址，建议添加用户能够真实访问到的网址），添加并验证后，可证明您是该域名的拥有者，可以快捷批量添加子站点，查看所有子站数据，无需再一一验证您的子站点。

>[如何验证网站](http://zhanzhang.baidu.com/college/courseinfo?id=267&page=1#h2_article_title13)

> 首先如果您的网站已使用了百度统计，您可以使用统计账号登录平台，或者绑定站长平台与百度统计账号，站长平台支持您批量导入百度统计中的站点，您不需要再对网站进行验证。

> 百度站长平台为未使用百度统计的站点提供三种验证方式：文件验证、html标签验证、CNAME验证。
　　1.文件验证：您需要下载验证文件，将文件上传至您的服务器，放置于域名根目录下。
　　2.html标签验证：将html标签添加至网站首页html代码的标签与标签之间。
　　3.CNAME验证：您需要登录域名提供商或托管服务提供商的网站，添加新的DNS记录。
> 验证完成后，我们将会认为您是网站的拥有者。为使您的网站一直保持验证通过的状态，请保留验证的文件、html标签或CNAME记录，我们会去定期检查验证记录。

### 站点地图

> 站点地图是一种文件，您可以通过该文件列出您网站上的网页，从而将您网站内容的组织架构告知Google和其他搜索引擎。Googlebot等搜索引擎网页抓取工具会读取此文件，以便更加智能地抓取您的网站。

谷歌插件：

``` bash
$ npm install hexo-generator-sitemap --save
```

百度插件：

``` bash
$ npm install hexo-generator-baidu-sitemap --save
```

在根目录_config.yml中添加如下配置：

``` text
# 自动生成sitemap
sitemap:
  path: sitemap.xml
baidusitemap:
  path: baidusitemap.xm
```

* 让谷歌收录：

&nbsp;&nbsp;在站点验证通过后，选择站点，抓取 -> 站点地图 -> 添加/测试站点地图，添加上sitemap.xml即可。

* 让百度收录：

&nbsp;&nbsp;正常情况，是要等百度爬虫来爬到你的网站，才会被收录。但是github屏蔽了百度爬虫，所以我们要主动把网站提交给百度，这就要使用到[百度站长平台](http://zhanzhang.baidu.com/).

&nbsp;&nbsp;在站点验证通过后，选择站点，数据引入 -> 链接提交，选择提交方式。由于github封禁了百度的ip，所以建议使用自动提交。

## RSS

RSS插件：

``` bash
$ sudo npm install hexo-generator-feed --save
```

开启RSS功能，编辑根目录下_config.yml，添加如下代码：

``` bash
rss: /atom.xml #rss地址  默认即可
```

## 流程图

flow插件：

``` bash
$ sudo npm install --save hexo-filter-flowchart
```

## 问题收集

### 找不到git部署

``` bash
ERROR Deployer not found: git
```

解决方法：

``` bash
$ sudo npm install hexo-deployer-git --save
```

### xcodebuild

``` bash
xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
```

解决方法：

``` bash
$ sudo npm install bcrypt
```
