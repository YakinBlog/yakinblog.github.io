---
title: Weex学习第三篇-内置组件
date: 2018-03-09 19:55:13
tags: [Weex, Vue, 教程, 组件]
description: Weex 是一个使用Web开发体验来开发高性能原生应用的框架
---

> Weex 支持文字、图片、视频等内容型组件，也支持 div、list、scroller 等容器型组件，还包括 slider、input、textarea、switch 等多种特殊的组件。Weex 的界面就是由这些组件以 DOM 树的方式构建出来的。

组件分为`内置组件`和`扩展组件`两类，内置组件随Weex SDK提供，提供构建界面的基础能力；如果觉得不够用或者满足不了特定需求，Weex也支持开发者自己创建扩展组件，并通过Weex提供的注册接口将组件集成到应用中使用。

<!-- more -->

## 资源路径

讲组件之前要先介绍下Weex的资源路径用法，包括图像、字体等资源。

Weex支持相对路径，与 HTML 用法类似，支持/、.、..、//开头相对 URI 将相对于 bunle url 解析。

### 本地资源：

Weex SDK 提供 local scheme 来访问打包在应用程序中的资源，此 scheme 无法在 H5 环境下使用。目前，开发者可以在 image 组件和字体文件中使用本地资源。

* iOS：Weex 会在 bundle resources 中查找。例如，image 组件的 src 属性为 local:///app_icon'， Weex 会加载 bundle resouce 中名为 app_icon 的图像资源，而字体文件也以相同的方式工作。

* Android：image 组件将从 drawable 资源文件夹加载，如 res/drawable-xxx。但加载字体文件是不同的，Android 框架无法从 res 加载字体文件，因此 SDK 将从 asserts 文件夹加载它。

### 网络资源：

工作方式与 web 相同。

### File：

访问本地磁盘文件的方案有其局限性：在不同的平台（iOS，Android）上，不同的设备上，差异很大。

# &lt;div&gt;

组件是用于包装其它组件的最基本容器。

> 不能在 `<div>` 中直接添加匿名文本，请用 `<text>` 包裹文本。

支持所有的通用样式、特性、flexbox 布局。支持所有通用事件。其类似于 HTML 的 `<div>` 容器，但不能直接在里面添加文本（字符串），如果要展示文本，应该使用 `<text>` 组件。历史版本中，`<div>` 别名是 `<container>`，**目前已经弃用**。

[效果预览](http://dotwe.org/vue/c3612312e9342dc21ecb3d5e3fcb68c0)

# &lt;image&gt;

用于在界面中显示单个图片。

> 注意：在HTML中通常使用的 `<img>` 标签在 Weex 中不支持，Weex使用 `<image>`。
> &nbsp;&nbsp;必须指定样式中的宽度和高度，否则无法工作。

Weex 没有内置的图片下载器，因为相关的下载、缓存、解码机制非常复杂，一些开源的工具如 SDWebImage 已经处理得很好， 所以在使用 `<image>`之前，请在 native 端先接入相应的 adapter 或者 handler。


[效果预览](http://dotwe.org/vue/955e1061b698153ed1de60e7673ee210)

### 属性

|属性名|类型|值|默认值|
|:---|:---:|---:|---:|
|placeholder|String|{URL / Base64}|-|
|resize|String|cover / contain / stretch|-|
|src|String|{URL / Base64}|-|

### placeholder

占位图的 URL，当由 src 表示的图片下载完成并展示后将被删除。

### resize 

![resize](https://weex.apache.org/references/images/image-resize-property.png)

* contain：缩放图片以完全装入 `<image>` 区域，可能背景区部分空白。
* cover：缩放图片以完全覆盖 `<image>` 区域，可能图片部分看不见。
* stretch：默认值. 按照 `<image>` 区域的宽高比例缩放图片。

参见: [background-size](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size)

### src

要显示图片的 URL，该属性是 `<image>` 组件的强制属性。

# &lt;text&gt;

用来将文本按照指定的样式渲染出来。只能包含文本值, 可以使用 `{ { } }` 标记插入变量值作为文本内容。

> 注意： `<text>` 里直接写文本头尾空白会被过滤，如果需要保留头尾空白，暂时只能通过数据绑定写头尾空格。

### 属性

* value {string}: 组件的值，与 `<text>` 标签中的文本内容相同。

### 样式

* lines {number}: 指定文本行数。默认值是 0， 代表不限制行数。
* 支持 color 样式。
* 支持 font-size 样式，默认值为32。
* 支持 font-style 样式。
* 支持 font-weight 样式。
* 支持 text-align 样式。
* 支持 text-decoration 样式。
* 支持 text-overflow 样式。
* 支持 line-height样式0.6.1+。

### 自定义字体 

支持ttf和woff字体格式的自定义字体, 可以通过调用 dom module 里面的 addRule方法, 构建自定义的font-family使用, addRule 建议在 beforeCreate 或者更早时调用。

[效果预览](http://dotwe.org/vue/964165062cd80be10a3816eec3e4e274)
[定义字体](http://dotwe.org/vue/a135864b804afd53a6d6d893503a4fee)

# &lt;a&gt;

用于实现页面间的跳转。

> 注意： 不能在 `<a>` 中直接添加匿名文本，请用 `<text>` 包裹文本。

### 属性

|属性名|类型|值|默认值|
|:---|:---:|---:|---:|
|href|String|{URL}|-|

### href

待跳转的页面URL，待跳转页面需要是一个Weex页面。如果待跳转页面是一个普通HTML，这会是一个未定义行为。

[效果预览](http://dotwe.org/vue/dd9584c57e67f4832a8ea04a307a51af)

# &lt;list&gt;

提供垂直列表功能的核心组件，拥有平滑的滚动和高效的内存管理，非常适合用于长列表的展示。

### 子组件

* &lt;cell&gt;

用于定义列表中的子列表项，类似于 HTML 中的 ul 之于 li。Weex 会对 `<cell>` 进行高效的内存回收以达到更好的性能。

* header 0.6.1+

当 `<header>` 到达屏幕顶部时，吸附在屏幕顶部。

* &lt;refresh&gt;

用于给列表添加下拉刷新的功能。

* &lt;loading&gt;

`<loading>` 用法与特性和 `<refresh>` 类似，用于给列表添加上拉加载更多的功能。

** 注意： **

`<list>` 的子组件只能包括以上四种组件或是 fix 定位的组件，其他形式的组件将不能被正确的渲染。

### 特性