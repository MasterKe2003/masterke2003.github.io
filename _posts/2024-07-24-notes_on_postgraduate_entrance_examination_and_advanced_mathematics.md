---
title: 考研高数笔记
date: 2024-07-24 22:13:12 +0800
categories: [考研, 万恶之源数学]
tags: [数学,不定积分,三角函数]
math: true
---

# 不定积分
## 三角函数相关

### 万能公式

$$
\frac{A}{Bsinx+Ccosx+D}
$$

---
> 分析：分子为常数，分母为`sinx`和`cosx`的倍数组合，将$tan\frac{x}{2}$设为t后，x就等于$2arctant$，因此dx就等于$\frac{2}{1+t^2}dt$，将其放到d前面后分母上正好可以化简抵消。
{: .prompt-tip }


### M分母+N分母导数

$$
\frac{Asinx+Bcosx}{Csinx+Dcosx}
$$

---

> 分析：分子分母为sinx和cosx的倍数组合，可以将其整理成$\frac{M(Asinx+Bcosx)+N(Asinx+Bcosx)^{'}}{Asinx+Bcosx}$，前半部分化简为一个常数，后半部分进行凑微分。
写出方程，对于sinx和cosx的系数列出两个=方程，解出M和N。
{: .prompt-tip }

### 积化和差

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

​	