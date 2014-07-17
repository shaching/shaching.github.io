---
layout: post
title: "C - What is Static Function?"
date: 2014-07-17 19:28:18 +0800
comments: true
categories: [C, Static, Function, Interview]
keywords: C, Static, Function, Interview
description: C - What is Static Function
---

A static function is a function whose scope is limited to the current source file.

靜態函式只能被所屬的檔案使用，其它檔案無法呼叫。

舉例：檔案 a.c 有 static functionA, 但檔案 b.c 無法呼叫 functionA 使用。

要注意的是 C++ 和 Java 的靜態函式功用和靜態變數相同。
