---
title: git提交丢失找回
#categories: 工具
date: 2018-11-19 20:18:18
tags: [git, push, sourcetree] 
description: git提交丢失找回
---

有同事在使用Sourcetree中，进行一次代码提交后(并未push到远程)，发现分支不对，重置了提交，可能是选择了混合合并(感觉更像是强行合并)，结果提交的代码都丢失了

解决方法如下： 

- 启动命令行模式，执行如下命令，查看丢失的commit还在不在：

``` bash
git reflog
```

- 如果在，恭喜你代码还可以找回，copy提交的丢失记录里最早的一次commit id备用。

- 在当前分支基础上点击新建分支，勾选“指定的提交”，填入刚刚copy的commit id，点击“创建分支”。

见证奇迹~

