---
title: bookdown一个小问题和解决过程
author: 老王
date: '2019-08-10'
slug: bookdown-explorer
categories:
  - R
  - Website
tags:
  - bookdown
  - R
  - website
---

想按[bookdown](https://bookdown.org/yihui/bookdown/)把一些记录做成书的样子。

按最简单能实现的途径，先下载bookdown的[demo](https://github.com/rstudio/bookdown-demo)，修改成自己的内容，本地serve没有问题。

按[JD Long](https://cerebralmastication.com/about/)（这好像是个大神）的自动在Netlify发布书的[介绍](https://cerebralmastication.com/2019/05/11/publishing-bookdown-to-netlify-automagically/)，把书push到Github上，关联Netlify——失败。

原因是没有把一个文件夹`_book`推上去。为什么会把这个文件夹忽略呢？百思不得其解，今天终于发现，是[谢益辉](https://yihui.name/)做这个包的时候把`_book`文件夹纳入git忽略名单了。是在隐藏文件`.gitignore`中定义的，只要在里面把这个文件夹去掉就行了。

另外，Mac中显示和隐藏隐藏文件的方法如下：

显示（在终端输入）：
> defaults write com.apple.finder AppleShowAllFiles -bool true

关闭显示：

> defaults write com.apple.finder AppleShowAllFiles -bool false

命令运行之后需要重新加载Finder，快捷键：

> option+command+esc

选中Finder，重新启动即可。

虽然是个小问题，不过因为基础知识太少还是费了不少劲才发现解决方法，记录一下。
