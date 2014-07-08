---
layout: post
title: "Vim - How to Change Vim default Comment Color?"
date: 2014-07-04 14:05:55 +0800
comments: true
categories: [Vim, Linux, Ubuntu]
keywords: Vim, Linux, Ubuntu, Editer
description: Vim - How to Change Vim default Comment Color?
---

The default VIM comment color(dark blue) is diffacult to read.

<!--more -->

So you can add .vimrc file in /YOUR\_HOME\_PATH/
```
$ cd
$ vim .vimrc
```

Add below contents then save and exit.
```
syntax on
set t_Co=256
hi Comment ctermfg=blue
```

Enjoy it.
