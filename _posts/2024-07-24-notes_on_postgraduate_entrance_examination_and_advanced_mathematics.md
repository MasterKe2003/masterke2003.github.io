---
title: 考研高数笔记
date: 2024-07-24 22:13:12 +0800
categories: [考研, 万恶之源数学]
tags: [数学,不定积分,三角函数]
math: true
---



[TOC]

## 极限

> 先定形后定法，定法之前先四化

### 洛必达法则

### 数列极限

#### 求和形式

##### 定积分定义

##### 夹逼准则

## 不定积分

### 有理分式

#### 真分式

- 分子凑分母的导数

  ![](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F25%2F1721918063.png)
- 因式分解

  ![](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F25%2F1721918142.png)

#### 假分式

眼瞅分母写分子，将其变成真分式，然后再使用真分式的求解方法。

### **无理根式**

#### 根号换元

直接令t等于一坨，反解出x，dx计算出来丢前面。

#### 三角换元

- $1+tanx=secx^2$
- $sinx+cosx=1$

### 三角函数

#### 见到双眼要发光系列✨

$$
1{\pm}sinx=(sin\frac{x}{2}{\pm}cos\frac{x}{2})^2
$$

$$
1+cosx=2cos^2\frac{x}{2}
$$

$$
1-cosx=2sin^2\frac{x}{2}
$$



#### 万能公式

$$
\frac{A}{Bsinx+Ccosx+D}
$$

---
> 分析：分子为常数，分母为`sinx`和`cosx`的倍数组合，将$tan\frac{x}{2}$设为t后，x就等于$2arctant$，因此dx就等于$\frac{2}{1+t^2}dt$，将其放到d前面后分母上正好可以化简抵消。
{: .prompt-tip }


#### M分母+N分母导数

$$
\frac{Asinx+Bcosx}{Csinx+Dcosx}
$$

---

> 分析：分子分母为sinx和cosx的倍数组合，可以将其整理成$\frac{M(Asinx+Bcosx)+N(Asinx+Bcosx)^{'}}{Asinx+Bcosx}$，前半部分化简为一个常数，后半部分进行凑微分。
写出方程，对于sinx和cosx的系数列出两个=方程，解出M和N。
{: .prompt-tip }

#### 积化和差

$$
sin(Ax)sin(Bx)
$$

$$
cos(Ax)cos(Bx)
$$

$$
sin(Ax)cos(Bx)
$$

> 使用积化和差公式整理后很好积分。
>
> {: .prompt-tip }

![](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F25%2F1721876131.png)

## 定积分

### 定积分性质

![image-20240726112801335](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F26%2F1721964481.png)

### 定积分几何意义

##### 圆面积

##### 偏心圆

![image-20240726105412604](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F26%2F1721962452.png)

##### 椭圆

### 定积分存在定理

#### 充分条件

- f(x)在[a,b]连续

- f(x)在[a,b]有界，且有有限个第一类间断点

#### 必要条件

- f(x)在[a,b]有界



### 定积分的计算

#### 直接计算

##### 凑微分

##### 分部积分

##### 第二类换元法

#### 技巧计算

##### [几何意义](#定积分几何意义)

##### 奇偶性

##### 周期性

##### 区间再现公式

![image-20240727101130822](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F27%2F1722046297.png)

![image-20240727102540932](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F27%2F1722047141.png)

##### 点火公式一家人

![image-20240728102520848](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F28%2F1722133530.png)

![image-20240727103322510](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F27%2F1722047602.png)

##### 重要结论

根据[区间再现公式](#区间再现公式)推出的重要结论：
$$
\int_0^\frac{\pi}{2}f(sinx)dx=\int_0^\frac{\pi}{2}f(cosx)dx
$$

$$
\int_0^{\pi}xf(sinx)dx=\frac{\pi}{2}\int_0^{\pi}f(sinx)dx
$$

$$
\int_{-a}^{a}f(x)dx=\int_{0}^{a}[f(x)+f(-x)]dx
$$

#### 题型

##### 对称区间定积分					

1. 奇偶性
2. 公式
3. 一半区间打开，一半进行负代换

### 变限函数

#### 变限函数存在性

变现函数存在性跟着[定积分存在定理](#定积分存在定理)一样。

#### 变限函数求导（标准型）

> 使用条件：被积分函数连续
>
> {: .prompt-info }

$$
\Phi'(x)=\frac{d}{dx}\int_{\phi(x)}^{\varphi(x)}f(t)dt=f[\varphi(x)]\varphi'(x)-f[\phi(x)]\phi'(x)
$$

上限移进去上限求导减下限移进去下限求导

证明：

![image-20240728125433552](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F28%2F1722142473.png)

#### 变限函数求导（非标准型）

- 将自变量踢出去，用乘法求导法则求导
- 换元

#### 牛逼爸

![image-20240728131246848](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F28%2F1722143566.png)
