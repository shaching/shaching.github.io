---
layout: post
title: "C - How to Reverse String?"
date: 2014-07-17 20:31:22 +0800
comments: true
categories: [C, String, Interview, Pointer]
keywords: C, String, Reverse, Interview, Pointer
description: C - How to Reverse String
---

{% codeblock lang:c %}
#include <stdio.h>
#include <string.h>

void reverse(char* str)
{
    int i, j;
    char c;
    for(i = 0, j = strlen(str)-1; i<j; ++i, --j)
        c = str[i], str[i] = str[j], str[j] = c;
}

int main()
{
    char str[] = "ABCDE";
    reverse(str);
    puts(str);
    return 0;
}
{% endcodeblock %}
