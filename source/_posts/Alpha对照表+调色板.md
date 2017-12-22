---
title: Alpha对照表+调色板
#categories: 工具
date: 2017-12-22 14:08:19
tags: [alpha, color, 工具] 
description: Alpha对照表，调色板
---

一般颜色是由ARGB构成，在程序中可以用8位十六进制值表示，前2位表示A（透明度），后6位表示RGB（颜色）。

### 透明度

``` java
StringBuilder str = new StringBuilder();
for (int i = 1; i <= 100; i++) {
    int round = Math.round(255 * i * 1.0f / 100f);
    String hexString = Integer.toHexString(round);
    if (hexString.length() < 2) {
        hexString += "0";
    }
    str.append("|" + i + "%|" + hexString.toUpperCase());
    if(i % 2 == 0) {
        str.append("|");
        System.out.println(str.toString());
        str.delete(0, str.length());
    }
}
```
<!-- more -->

对照表： 

|透明度|16进制|透明度|16进制|
|:---|:---:|---:|---:|
|全透|00|不透|FF|
|1%|30|2%|50|
|3%|80|4%|A0|
|5%|D0|6%|F0|
|7%|12|8%|14|
|9%|17|10%|1A|
|11%|1C|12%|1F|
|13%|21|14%|24|
|15%|26|16%|29|
|17%|2B|18%|2E|
|19%|30|20%|33|
|21%|36|22%|38|
|23%|3B|24%|3D|
|25%|40|26%|42|
|27%|45|28%|47|
|29%|4A|30%|4D|
|31%|4F|32%|52|
|33%|54|34%|57|
|35%|59|36%|5C|
|37%|5E|38%|61|
|39%|63|40%|66|
|41%|69|42%|6B|
|43%|6E|44%|70|
|45%|73|46%|75|
|47%|78|48%|7A|
|49%|7D|50%|80|
|51%|82|52%|85|
|53%|87|54%|8A|
|55%|8C|56%|8F|
|57%|91|58%|94|
|59%|96|60%|99|
|61%|9C|62%|9E|
|63%|A1|64%|A3|
|65%|A6|66%|A8|
|67%|AB|68%|AD|
|69%|B0|70%|B3|
|71%|B5|72%|B8|
|73%|BA|74%|BD|
|75%|BF|76%|C2|
|77%|C4|78%|C7|
|79%|C9|80%|CC|
|81%|CF|82%|D1|
|83%|D4|84%|D6|
|85%|D9|86%|DB|
|87%|DE|88%|E0|
|89%|E3|90%|E6|
|91%|E8|92%|EB|
|93%|ED|94%|F0|
|95%|F2|96%|F5|
|97%|F7|98%|FA|
|99%|FC|100%|FF|

### 常用色

分享几个常用色配色网站：[Color Hunt](http://colorhunt.co/)、[Adobe Color](https://color.adobe.com/), [Colllor](http://colllor.com/)


### 取色器

<iframe src="http://tools.jb51.net/static/rgbcolor/index.html" id="CenterMainCenter" frameborder="no" border="0" marginwidth="0" marginheight="0" scrolling="no" allowtransparency="yes" width="100%" height="460px"></iframe>