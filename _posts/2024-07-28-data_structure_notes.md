---
title: 考研数据结构笔记
date: 2024-07-29 00:05:12 +0800
categories: [考研, 华美数据结构]
tags: [数据结构,考研,算法,C语言]
math: true
---

## 栈

### 括号匹配

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAXSIZE 10

typedef struct
{
    char data[MAXSIZE];
    int top;
} SqStack;

// 初始化顺序栈
void initStack(SqStack *S)
{
    S->top = -1;
}

// 判断是否为空
bool isEmpty(SqStack *S)
{
    return S->top == -1;
}

// 判断是否满
bool isFull(SqStack *S)
{
    return S->top == MAXSIZE - 1;
}

// 入栈
bool Push(SqStack *S, char *x)
{
    if (isFull(S))
        return false;
    S->data[++S->top] = *x;
    return true;
}

// 出栈
bool Pop(SqStack *S, char *x)
{
    if (isEmpty(S))
        return false;
    *x = S->data[S->top--];
    return true;
}

//检查字符串是否合法
bool checkString(char str[])
{
    int length = 0;
    int i = 0;
    while (str[i++] != '\0')
    {
        length++;
    }
    SqStack S;
    initStack(&S);
    for (int i = 0; i < length; i++)
    {
        if (str[i] == '(' || str[i] == '{' || str[i] == '[' || str[i] == ')' || str[i] == '}' || str[i] == ']')
        {

            if (str[i] == '(' || str[i] == '{' || str[i] == '[')
                Push(&S, &str[i]);
            else
            {
                if (isEmpty(&S))
                    return false; // 匹配到右括号且栈空，不合法

                char topElem;
                Pop(&S, &topElem);
                if (str[i] == ')' && topElem != '(')
                    return false;
                if (str[i] == '}' && topElem != '{')
                    return false;
                if (str[i] == ']' && topElem != '[')
                    return false;
            }
        }
    }
    return isEmpty(&S);
}

char a[10] = "(你好){}";
void main()
{
    if (checkString(a))
    {
        printf("括号合法");
    }
    else
    {
        printf("括号不合法");
    }
}

```

#### 中缀转后缀机算

![image-20240728235436110](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F28%2F1722182076.png)