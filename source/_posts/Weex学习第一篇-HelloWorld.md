---
title: Weex学习第一篇-HelloWorld
#categories: 教程
date: 2018-02-01 11:58:55
tags: [Weex, Vue, Rax, 教程]
description: Weex 是一个使用Web开发体验来开发高性能原生应用的框架
---

> Weex 是一个使用 Web 开发体验来开发高性能原生应用的框架。

Weex致力于使开发者能基于当前先进的Web开发技术，使用同一套代码来构建Android、iOS和Web应用，达到一次编写，多端运行。

Weex的主要目标是跟进当前先进的Web开发和原生开发技术，使生产力和性能共存，让开发Weex界面和开发普通网页一样简单，而渲染Weex页面达到和渲染原生页面一样的效果。架构是解耦的，渲染引擎和语法层是分开的，不依赖任何特定的前端框架，目前主要支持Vue.js和Rax两个前端框架。

Weex支持原生组件，如`<div>`这样通用的容器组件，`<text>`这样常用的文本组件。Weex支持内嵌CSS和内部CSS，内部CSS使用`<style>`标签声明，而内嵌CSS使用style属性声明，强制是scoped即只能作用于当前组件。

<!-- more -->

## 搭建环境

安装 Node.js 方式多种多样，最简单的方式是在 [Node.js 官网](https://nodejs.org/en/download/) 下载可执行程序直接安装即可。

对于 Mac，可以使用 [Homebrew](https://brew.sh/index_zh-cn.html) 进行安装：

``` shell
$ brew install node
```

安装完成后，可以使用以下命令检测是否安装成功：

``` shell
$ node -v
v8.9.3
$ npm -v
5.6.0
```

通常，安装了 Node.js 环境，npm 包管理工具也随之安装了。因此，直接使用 npm 来安装 weex-toolkit。

> npm 是一个 JavaScript 包管理工具，它可以让开发者轻松共享和重用代码。Weex 很多依赖来自社区，同样，Weex 也将很多工具发布到社区方便开发者使用。

注意: 在 `weex-toolkit` 1.0.8版本后添加了npm5规范的 `npm-shrinkwrap.json` 用于锁定包依赖，故npm版本<5的用户需要通过 `npm i npm@latest -g` 更新一下npm的版本，使用前请确认版本是否正确。

``` shell
npm install -g weex-toolkit
```

weex-toolkit也支持直接升级子依赖，如：

``` shell
$ weex update weex-devtool@latest //@后标注版本后，latest表示最新
```

国内开发者可以考虑使用淘宝的 npm 镜像 [cnpm](https://npm.taobao.org/) 安装 weex-toolkit

``` shell
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
$ cnpm install -g weex-toolkit
```

如果安装过程出现如下错误：

npm update check failed 
Try running with sudo or get access   
to the local update config store via  
sudo chown -R $USER:$(id -gn $USER) /var/root/.config

![](/assets/resource/npm_update_check_failed.png)

解决办法：

``` shell
$ npm config set user 0 
$ npm config set unsafe-perm true
```

## Hello World

创建 Weex 项目：

``` shell
$ weex create helloworld-project
```

执行过程中会让你进行项目配置，默认即可。

在 `package.json` 中，已经配置好了几个常用的 npm script，分别是：

``` text
"scripts": {
    "start": "npm run serve",
    "build": "webpack --env.NODE_ENV=common",
    "build:prod": "webpack --env.NODE_ENV=production",
    "build:plugin": "webpack --env.NODE_ENV=plugin",
    "clean": "rimraf ./web/build",
    "dev": "webpack --env.NODE_ENV=common --progress --watch",
    "unit": "karma start test/unit/karma.conf.js",
    "test": "npm run unit",
    "lint": "eslint --ext .js,.vue src",
    "serve": "webpack-dev-server --env.NODE_ENV=development --progress",
    "ios": "weex run ios",
    "web": "npm run serve",
    "android": "weex run android",
    "pack:ios": "npm run clean && weex build ios",
    "pack:android": "npm run clean && weex build android",
    "pack:web": "npm run clean && npm run build:prod"
  }
```

直接和npm组合即可使用，比如直接启动：

``` shell
$ npm start
```

也可以组合使用，比如开启 watch 模式和静态服务器：

``` shell
$ npm run dev & npm run serve 
```

工具会自动打开浏览器，即可看到 weex h5 页面。

![](https://weex.apache.org/guide/images/toolkit-preview.png)

## 目录结构

``` text
/dist				# 自动生成
	index.js 		# 客户端bundle
	index.web.js 	# web bundle
/src				# 开发目录
	App.vue        	# 组件源码
	entry.js       	# 入口文件
``` 

## 相关资料

- [搭建开发环境](http://weex.apache.org/cn/guide/set-up-env.html)
- [Weex接入](http://weex.apache.org/cn/guide/integrate-to-your-app.html)
- [Weex手册](http://weex.apache.org/cn/references)
- [前端框架](http://weex.apache.org/cn/guide/front-end-frameworks.html)
- [在线编辑器](http://dotwe.org/vue)
![效果体验](https://gw.alipayobjects.com/zos/rmsportal/MNIgWQQFnsXFVDgmXLrr.jpeg)