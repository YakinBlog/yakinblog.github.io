---
title: Weex学习第二篇-基础语法
#categories: 教程
date: 2018-03-09 14:27:28
tags: [Weex, Vue, 教程]
description: Weex 是一个使用Web开发体验来开发高性能原生应用的框架
---

Weex 的页面是基于 XML 标签化的语法的，一个 Weex 页面由三个大的顶层标签构成:

* `<template>`：描述Weex页面的结构，Weex页面是由一个个组件组合搭建而成的，通过不同类型的标签`tag`来使用这些组件。

* `<style>`：描述 Weex 页面的展示样式表，内容是基于很简单的 CSS 的语法。

* `<script>`：描述 Weex 页面的动态数据和行为，内容基于很简单的 JavaScript 语法，包括数据和必要的数据处理函数定义。同时，除了默认行为外，还提供两种额外的配置/数据定义（通过 type 特性设置）。

 - type="data"：定义用于初始化的数据，这部分数据会直接覆盖默认 `<script>` 中的数据定义。

 - type="config"：定义配置项。

<!-- more -->

``` html
<template>
  <!-- （必须）页面结构 -->
</template>

<style>
  /* (可选) 样式表 */
</style>

<script>
  /* (可选) 数据、方法、生命周期定义 */
</script>

<script type="data">
 /* （可选）定义初始化数据 */
</script>

<script type="config">
 /* （可选）定义配置项 */
</script>
```

## 视图模板（template）

``` html
<template>
  <div>
    <text>文本</text>
  </div>
</template>
```

`template` 标签是页面视图的区域标志，内部有且仅有一个根元素，且根元素不能使用 `if/repeat` 的指示器，目前推荐使用的根元素标签有：

* `<div>`：通用根元素。

* `<scroller>`：一个竖直的，可以容纳多个排成一列的子组件的滚动器。

* `<list>`：提供垂直列表功能且拥有平滑的滚动和高效的内存管理的长列表的展示器。

### 标签的通用特性：

* 唯一标识：id="..."。

* 样式：style="..."。

* CSS类：class="..."。

* 数据绑定："{&nbsp;{var}&nbsp;}" 和 "{&nbsp;{func()}&nbsp;}"。

* 指示器：if="..."、repeat="..." 和 append="..."。

* 事件处理：onxxx="..."。

## 样式表 (style)

描述 Weex 页面的样式表，语法是基于 CSS 的，且是一个很小的语法集。

内部CSS，多个组件上可以复用样式规则：

``` html
<template>
  <div>
    <text class="txt">内部CSS</text>
  </div>
</template>

<style>
  .txt {font-size: 64;}
</style>
```

内嵌CSS，强制是scoped即只能作用于当前组件：

``` html
<template>
  <div>
    <text style="font-size: 64;">内嵌CSS</text>
  </div>
</template>
```

## 页面数据和方法 (script)

`<script>` 标签的内容主要由 data ，methods 以及 created 三 部分组成，分别的含义是结构性数据、自定义方法，以及生命周期的入口，并通过赋值给 module.exports 完成定义。

``` html
<script>
module.exports = {
  data: {
    ...
  },
  methods: {
    ...
  },
  created: function() {
    ...
  }
}
</script>
```

### data

data 的值一定是一个结构型数据（JSON 对象）。

data 对象里的每个字段都可以在 `<template>` 中和某个标签特性或内容绑定起来。并且在任一方法中通过`this`上下文来读写。

### methods

methods 的所有字段都应该是函数类型的。

methods 里的每个自定义方法同样都可以 `<template>` 中和某个标签特性绑定起来。并且在任一方法中通过this上下文来调用。

### created

Weex 暂时提供了一个页面生命周期的入口：

创建上下文，并赋予访问数据和自定义方法的能力，此时通过this可以存取数据，调用方法。这个入口，等同于老版本的ready自定义方法。

### 上下文 this

通过方法中的上下文 this，我们可以访问到如下内容：

* data 中的数据。

* methods 中的自定义方法。

* $... 开头的内建接口。

这也意味着，通过 this，我们可以在方法里：

* 读写 data 中的数据。

* 调用 methods 中的自定义方法。

* 调用 Weex 预置的一些功能。

### 配置选项

Weex的配置页面选项标签 `<script type="config">`，目前支持的选型仅有 [downgrade](https://www.npmjs.com/package/@weex-project/downgrade)，用于降级规则的配置。

* downgrade.osVersion
* downgrade.appVersion
* downgrade.weexVersion
* downgrade.deviceModel

## 注意事项

* 支持 setTimeout，但暂不支持 `clearTimeout`、`setInterval`、`clearInterval`、`requestAnimationFrame`、`cancelAnimationFrame`。

* 不支持直接操作元素，界面展示逻辑通过数据和状态的改变来描述。

* 暂不支持通过 `<script src="...">` 或 `require` 等方式引入外部脚本。

## 相关资料

- [ES6](http://es6.ruanyifeng.com/?search=%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%A8%A1%E6%9D%BF&x=0&y=0#README)
- [Vue](https://cn.vuejs.org/v2/guide/single-file-components.html#%E4%BB%8B%E7%BB%8D)
