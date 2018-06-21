---
title: git-撤销已经push到远端的commit
date: 2018-06-21 18:46:27
tags: [git, push, commit, 教程]
---

在使用git时，push到远端后发现commit了多余的文件，或者希望能够回退到以前的版本。

先在本地回退到相应的版本：

``` bash
$ git reset --hard <版本号>
    // --hard 参数会抛弃当前工作区的修改
    // --soft 参数的话会回退到之前的版本，但是保留当前工作区的修改，可以重新提交
```

如果直接向远程push：

``` bash
$ git push origin <分支名>
```

<!-- more -->

会提示本地的版本落后于远端的版本：

![](/assets/resource/git-error1.png)

为了覆盖掉远端的版本信息，使远端的仓库也回退到相应的版本，需要加上参数`--force`

``` bash
git push origin <分支名> --force
```

[转自CSDN](https://blog.csdn.net/xs20691718/article/details/51901161)