---
layout: post
title: "C - How to Delete Space of String?"
date: 2014-07-17 20:13:29 +0800
comments: true
categories: [C, String, Interview]
keywords: C, String, Delete, Space, Interview
description: C - How to Delete Space of String
---

{% codeblock lang:c %}
#include <stdio.h>
#include <stdlib.h>

void delete_space(char *s1, char *s2)
{
    while(*s1 != NULL)
    {
        if(!isspace(*s1))
        {
            *s2 = *s1;
            s2++;
        }
        s1++;
    }
    *s2 = '\0';
}

int main(int argc, char *argv[])
{
    char buf[80], buf1[80];

    int i;

    printf("Please input a string\n");

    gets(buf);

    delete_space(buf, buf1);

    printf("The result of delete space from string\n");

    puts(buf1);

    system("PAUSE");

    return 0;
}
{% endcodeblock %}
