---
title: Hexo+Github搭建个人博客
#categories: 教程
tags: [hexo, github, nodejs] 
description: Hexo+Github搭建个人博客
---
[Hexo](https://hexo.io/)是一款基于[NodeJS](https://nodejs.org)的静态博客框架，以下介绍的是在Mac系统下的搭建过程，简单实用，足够满足个人点滴的分享和记录，而无需个人服务器，可绑定域名。

## 环境配置

### 必要软件

XCode：[APP Store](https://developer.apple.com/xcode/)下载安装
Git：XCode内置有git，或者[官网](https://git-scm.com/downloads)下载
NodeJS：[官网](https://nodejs.org)下载
Npm：安装NodeJS时会连带安装

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

在浏览器里访问(http://localhost:4000)， 预览博客。

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

访问[http://your_user_name.github.io](https://yakinblog.github.io/)，就可以浏览你的博客站点了！！！
站点默认部署到master分支，可建hexo分支存放站点源码。

## Hexo 常用命令

### 新建文章

``` bash
hexo n[new] "我的博客" 
```

More info: [Writing](https://hexo.io/docs/writing.html)

### 启动服务，服务会检测文件变动自动更新，无需重启服务

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

### RSS不显示

安装RSS插件

``` bash
$ sudo npm install hexo-generator-feed --save
```

开启RSS功能，编辑hexo/_config.yml，添加如下代码：

``` bash
rss: /atom.xml #rss地址  默认即可
```
