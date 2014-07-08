---
layout: post
title: "Vim - How to Highlight Trailing Whitespace?"
date: 2014-07-08 14:12:45 +0800
comments: true
categories: [Vim, Linux, Ubuntu]
keywords: Vim, Linux, Ubuntu, Editer
description: Vim - How to Highlight Trailing Whitespace?
---

During Vim editing, We must have to delete unnecessary trailing whitespace which make code easy to read or merge.

<!--more -->

So you can add .vimrc file in /YOUR\_HOME\_PATH/
```
$ cd
$ vim .vimrc
```

Add below contents then save and exit.
```
hi Whitespace ctermbg=darkred guibg=darkcyan
autocmd BufEnter * if &ft != 'help' | match Whitespace /\s\+$/ | endif
autocmd BufEnter * if &ft == 'help' | match none /\s\+$/ | endif
```

Enjoy it.

Reference : [vim 顯示多餘空白( trailing whitespace ) ](http://kitoslab.blogspot.tw/2012/09/vim-trailing-whitespace.html)

