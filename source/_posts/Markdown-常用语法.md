---
title: Markdown 常用语法
#categories: 教程
date: 2017-12-24 09:49:31
tags: [markdown, 语法, 标记语言, 教程] 
description: Markdown 常用语法
---

> [Markdown](https://link.jianshu.com/?t=http://zh.wikipedia.org/wiki/Markdown) 是一种轻量级的「标记语言」，它的优点很多，目前也被越来越多的写作爱好者，撰稿者广泛使用。看到这里请不要被「标记」、「语言」所迷惑，Markdown 的语法十分简单。常用的标记符号也不超过十个，这种相对于更为复杂的 HTML 标记语言来说，Markdown 可谓是十分轻量的，学习成本也不需要太多，且一旦熟悉这种语法规则，会有一劳永逸的效果。

## 官方文档

* [创始人 John Gruber 的 Markdown 语法说明](https://link.jianshu.com/?t=http://daringfireball.net/projects/markdown/syntax)
* [Markdown 中文版](https://link.jianshu.com/?t=http://wowubuntu.com/markdown/#list)
* [Markdown 公式指导手册](https://link.jianshu.com/?t=http://www.liuhaihua.cn/archives/143443.html/)

## 基本语法

### 代码

通常编辑器根据代码片段适配合适的高亮方法，你也可以用 \`\`\` 包裹一段代码，并指定一种语言，如果不需要高亮可以在语言处指定`nohighlight`

<!-- more -->

语法：

``` text
 ``` [语言]
 [代码块]
 ``` 
```

示例：

``` text
[代码块]
```

支持高亮显示的语言：

|名称|关键字|调用的js|
|:---|:---:|---:|
|AppleScript|applescript|shBrushAppleScript.js|
|ActionScript 3.0|actionscript3 , as3|shBrushAS3.js|	
|Shell|bash , shell|shBrushBash.js|
|ColdFusion|coldfusion , cf|shBrushColdFusion.js|
|C|cpp , c|shBrushCpp.js|
|C#|c# , c-sharp , csharp|shBrushCSharp.js|
|CSS|css|shBrushCss.js|
|Delphi|delphi , pascal , pas|shBrushDelphi.js|
|diff&patch|diff patch|shBrushDiff.js|
|Erlang|erl , erlang|shBrushErlang.js|
|Groovy|groovy|shBrushGroovy.js|
|Java|java|shBrushJava.js|
|JavaFX|jfx , javafx|shBrushJavaFX.js|
|JavaScript|js , jscript , javascript|shBrushJScript.js|
|Perl|perl , pl , Perl|shBrushPerl.js|
|PHP|php|shBrushPhp.js|
|text|text , plain|shBrushPlain.js|
|Python|py , python|shBrushPython.js|
|Ruby|ruby , rails , ror , rb|shBrushRuby.js|
|SASS&SCSS|sass , scss|shBrushSass.js|
|Scala|scala|shBrushScala.js|
|SQL|sql|shBrushSql.js|
|Visual|Basic	vb , vbnet|shBrushVb.js|
|XML|xml , xhtml , xslt , html|shBrushXml.js|
|Objective C|objc , obj-c|shBrushObjectiveC.js|
|F#|f# f-sharp , fsharp|shBrushFSharp.js|
||xpp , dynamics-xpp|shBrushDynamics.js|
|R|r , s , splus|shBrushR.js|
|matlab|matlab|shBrushMatlab.js|
|swift|swift|shBrushSwift.js|
|GO|go , golang|shBrushGo.js|

### 高亮

语法：

``` text
` [关键字] `
```

示例：

` [关键字] `

### 标题

文章内容较多时，可以用标题分段：

语法：

``` text
标题1
======

标题2
-----

## 大标题 ##
### 小标题 ###
```

示例：

标题1
======

标题2
-----

## 大标题 ##
### 小标题 ###

### 粗斜删除

语法：

``` text
*斜体文本* 
**粗体文本**
***粗斜体文本*** 
~~删除线~~
```

示例：

*斜体文本* 
**粗体文本**
***粗斜体文本*** 
~~删除线~~

### 链接

语法：

``` text
文字链接 [链接名称](http://链接网址)
网址链接 <http://链接网址>
```

示例：

文字链接 [链接名称](http://链接网址)
网址链接 <http://链接网址>

### 列表

* 普通无序列表

语法：

``` text
- 列表文本前使用 [减号+空格]
+ 列表文本前使用 [加号+空格]
* 列表文本前使用 [星号+空格]
```

示例：

+ 列表1
+ 列表2
+ 列表3

* 普通有序列表

语法：

``` text
1. 列表前使用 [数字+空格]
2. 我们会自动帮你添加数字
7. 不用担心数字不对，显示的时候我们会自动把这行的 7 纠正为 3
```

示例：

1. 列表1
3. 列表3
5. 列表5

嵌套列表可以使用空格缩进，也可以使用占位符`&nbsp；`

### 引用

* 普通引用

语法：

``` text
> 引用文本前使用 [大于号+空格]
> 折行可以不加，新起一行都要加上哦
```

示例：

> 普通引用
> 普通引用

* 嵌套引用

语法：

``` text
> 最外层引用
> > 多一个 > 嵌套一层引用
> > > 可以嵌套很多层
```

示例：

> 最外层引用
> > 多一个 > 嵌套一层引用
> > > 可以嵌套很多层

### 图片

跟链接的方法区别在于前面加了个感叹号 !，图片名称可以为空

语法：

``` text
![图片名称](http://图片网址)
```

示例：

![](/assets/img/avatar-001.jpg)

### 换行

如果另起一行，只需在当前行结尾加 2 个空格。

如果是要起一个新段落，只需要空出一行即可。

### 分隔符

如果你有写分割线的习惯，可以新起一行输入三个减号-。当前后都有段落时，请空出一行：

语法：

``` text
前面的段落

---

后面的段落
```

示例：

前面的段落

---

后面的段落

## 进阶语法

### 行内HTML元素

目前只支持部分段内 HTML 元素效果，包括 `<kdb> <b> <i> <em> <sup> <sub> <br>`

语法：

``` text
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd>
<pre>[代码块]</pre>
<b> Markdown 在此处同样适用，如 *加粗* </b>
```

示例：

<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd>

<pre>[代码块]</pre>

<b> Markdown 在此处同样适用，如 *加粗* </b>

### 符号转义

如果你的描述中需要用到 markdown 的符号，比如 `_ # *` 等，但又不想它被转义，这时候可以在这些符号前加反斜杠，如 `\_ \# \*` 进行避免

### 扩展

支持 jsfiddle、gist、runjs、优酷视频，直接填写 url，在其之后会自动添加预览点击会展开相关内容

``` text
http://{url_of_the_fiddle}/embedded/[{tabs}/[{style}]]/
https://gist.github.com/{gist_id}
http://runjs.cn/detail/{id}
http://v.youku.com/v_show/id_{video_id}.html
```

### 公式

当你需要在编辑器中插入数学公式时，可以使用两个美元符 $$ 包裹 TeX 或 LaTeX 格式的数学公式来实现。提交后，问答和文章页会根据需要加载 Mathjax 对数学公式进行渲染。如：

语法：

``` text
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a}. $$

$$ x \href{why-equal.html}{=} y^2 + 1 $$
```

示例：

$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a}. $$

$$ x \href{why-equal.html}{=} y^2 + 1 $$

同时也支持 HTML 属性，如：

``` text
$$ (x+1)^2 = \class{hidden}{(x+1)(x+1)} $$

$$ (x+1)^2 = \cssId{step1}{\style{visibility:hidden}{(x+1)(x+1)}} $$
```

示例：

$$ (x+1)^2 = \class{hidden}{(x+1)(x+1)} $$

$$ (x+1)^2 = \cssId{step1}{\style{visibility:hidden}{(x+1)(x+1)}} $$


### 占位符

|符号|说明|编码|
|:---|:---:|---:|
|&|AND符号|`&amp;`|
|<|小于|`&lt;`|
|>|大于|`&gt;`|
|空格| |`&nbsp;`|
|¿|倒问号	|`&iquest;`|
|?|问号|`&quest;`|
|«|左书名号|`&laquo;`|
|»|右书名号|`&raquo;`|
|"|引号|`&quot;`|
|‘|左单引号|`&lsquo;`|
|’|右单引号|`&rsquo;`|
|“|左双引号|`&ldquo;`|
|”|右双引号|`&rdquo;`|
|¶|段落符号|`&para;`|
|§|章节符	|`&sect;`|
|×|乘号|`&times;`|
|÷|除号|`&divide;`|
|±|加减号	|`&plusmn;`|
|ƒ|function|`&fnof;`|
|√|根号|`&radic;`|
|∞|无穷大	|`&infin;`|
|°|度|`&deg;`|
|≠|不等号|`&ne;`|
|≡|恒等于	|`&equiv;`|
|≤|小于等于|`&le;`|
|≥|大于等于|`&ge;`|
|⊥|垂直符号|`&perp;`|
|←|左箭头	|`&larr;`|
|→|右箭头	|`&rarr;`|
|↑|上箭头	|`&uarr;`|
|↓|下箭头	|`&darr;`|
|↔|水平箭头|`&harr;`|
|↕|竖直箭头|`&varr;`|
|⇐|双线左箭头|`&lArr;`|
|⇒|双线右箭头|`&rArr;`|
|⇑|双线上箭头|`&uArr;`|
|⇓|双线上箭头|`&dArr;`|
|⇔|双线水平双箭头|`&hArr;`|
|⇕|双线竖直箭头|`&vArr;`|
|♠|黑桃|`&spades;`|
|♥|红桃|`&hearts;`|
|♣|梅花|`&clubs;`|
|♦|方块|`&diams;`|
|©|版权|`&copy;`|
|®|注册商标|`&reg;`|
|™|商标|`&trade;`|
|¥|人民币	|`&yen;`|
|€|欧元|`&euro;`|
|¢|美分|`&cent;`|
|£|英磅|`&pound;`|
|⊕|	|`&oplus;`|
|½|二分之一|`&frac12;`|
|¼|四分之一|`&frac14;`|
|‰|千分符号|`&permil;`|
|∴|所以|`&there4;`|
|π|圆周率	|`&piv
|¹|商标1|`&sup1;`|
|α|alpha|`&alpha;`|
|β|beta|`&beta;`|
|γ|gamma|`&gamma;`|
|δ|delta|`&delta;`|
|θ|theta|`&theta;`|
|λ|lambda|`&lambda;`|
|σ|sigma|`&sigma;`|
|τ|tau|`&tau;`|

<iframe src="https://pandao.github.io/editor.md/examples/simple.html" id="CenterMainCenter" frameborder="no" border="0" marginwidth="0" marginheight="0" scrolling="no" allowtransparency="yes" width="100%" height="460px"></iframe>
