---
layout: post
title: "C - How to Get the Greatest Common Divisor"
date: 2014-07-17 20:50:47 +0800
comments: true
categories: [C, GCD, Interview]
keywords: C, GCD, Interview
description: C - How to Get the Greatest Common Divisor
---

{% codeblock lang:c %}
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int a, b, temp;

    while(scanf("%d %d", &a, &b) == 2)
    {
        while(a%b)
        {
            temp = a;
            a = b;
            b = temp % b;
        }

        printf("%d\n",b);
    }
    system("PAUSE");
    return 0;
}
{% endcodeblock %}
