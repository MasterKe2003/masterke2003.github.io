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

## 数组和特殊矩阵

> 核心思想：总=满+零
>
> 例如：i行j列元素有i-1行满和j个零。
>
> {: .prompt-tip }

#### 对称矩阵

![img](https://images2015.cnblogs.com/blog/932246/201607/932246-20160723093306544-1405819987.png)

```bash
=================================
若以行优先进行：
对于矩阵a[i][j]压缩=>B[k],若i,j都从0开始

第1行 1个元素
第2行 2个元素
···
第i-1行 i-1个元素
第i行 i个元素

a[i][j]存储在B中第多少个位置分析如下:
第i行前有i-1行满的,满元素的行就有:
[1+(i-1)]*(i-1)/2=i(i-1)/2
再看元素所在行第几个
第j个从左往右数,所以是在第j个元素

总=i(i-1)/2+j [若下标从0开始,-1即可]
=================================
=================================
若以列优先进行：
对于矩阵a[i][j]压缩=>B[k],若i,j都从0开始

第1行 n个元素
第2行 n-1个元素
···
第j-1行 n-(j-1)+1=n-j+2个元素
第j行 n-j+1个元素 [每行减j个,少1个加回去]

a[i][j]存储在B中第多少个位置分析如下：
第j列前有j-1列满的,满元素的行就有:
[n+(n-j+2)](j-1)/2
再看元素所在列第几个
第i个从上往下数
第1列说5其实就是5,实际存了5个元素
第2列说5其实是4,实际存了4个元素
所以第i行说i其实是在第i-j+1个元素,实际存了i-j+1个元素
另外,j=i的时候是对角线上的元素,i-j为0,但对角线上的元素一定是第一个元素,所以+1,为什么是i-j而不是j-i呢？因为这里下半角矩阵i是≥j的
```

#### 三角矩阵

#### 三对角矩阵

## 树和二叉树

### 树的性质

1. 树的节点数n等于所有结点的度总和+1。
2. 度为m的树第i层最多有m的i-1次方个结点（i≥1）。
3. 高度为h的m叉树最多节点树为：

$$
\frac{m^h-1}{m-1}
$$

```
第一行有m^0个
第二行有m^1个
第三行有m^2个
第四行有m^3个
第h行有m^h-1个
利用等比数列求和公式即可解出
```

4. 度为m有n个结点的树最小高度是：
   $$
   {\lceil}log_m(n(m-1)+1){\rceil}
   $$

> 加一向下取整就是直接向上取整。
> ![image-20240731124015961](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F31%2F1722400823.png)

4. 具有n个结点、度为m的树最大高度是n-m+1。
5. 高度为h、度为m的树最少有n+m-1个结点。

### 二叉树

1. 非空二叉树叶子结点🍃的个数度为2的结点的个数+1。
2. 完全二叉树的最后一个分支结点是${\lfloor}\frac{n}{2}{\rfloor}$
3. 第i层最多有$2^{i-1}$个结点。
4. n个结点最多有n+1个空指针。
5. 满二叉树的结点数为：$$2^h-1$$

#### 平衡二叉树

1. 深度为i的平衡二叉树最少有多少个结点？

   公式：$ 对于 n \geq 3，有f(n) = f(n-1) + f(n-2) + 1 ，且 f(1) = 1 ) 和 (f(2) = 2 )$

2. 