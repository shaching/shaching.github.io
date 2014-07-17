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
#include <stdlib.h>

void reverse(char *s1, char *s2)
{
    char temp, *q1, *q2;

    char buf[80];

    strcpy(buf, s1);

    q1 = buf;

    q2 = buf + strlen(buf)-1;

    while( q1 < q2 )
    {
        temp = *q1;
        *q1 = *q2;
        *q2 = temp;
        q1++;
        q2--;
    }
    strcpy(s2, buf);
}

int main(int argc, char *argv[])
{
    char buf[80], buf2[80];

    puts("Please input a string");

    gets(buf);

    reverse(buf, buf2);

    puts("The result of reverse string.");

    puts(buf2);

    system("PAUSE");

    return 0;
}
{% endcodeblock %}
