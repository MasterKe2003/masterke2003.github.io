---
title: 考研高数笔记
date: 2024-07-24 22:13:12 +0800
categories: [考研, 万恶之源数学]
tags: [数学,不定积分,三角函数]
math: true
---

# 不定积分
## 三角函数相关
### 分子为常数，分母为`sinx`和`cosx`的倍数组合

$$
\frac{A}{Bsinx+Ccosx+D}
$$

---
> 分析：将$tan\frac{x}{2}$设为t后，x就等于$2arctant$，因此dx就等于$\frac{2}{1+t^2}dt$，将其放到d前面后分母上正好可以化简抵消，因此直接使用万能公式换元即可。
{: .prompt-tip }

> 例题1：

$\int\frac{\mathrm{d}x}{2+\sin x};$

> 答案1：

$\frac2{\sqrt{3}}\arctan\frac{2\tan\frac x2+1}{\sqrt{3}}+C.$

> 例题2：

$\int\frac{1+sinx}{sinx(1+cosx)}\mathrm{d}x\text{ ;}$

> 注意此题分子中虽然有sinx，但是分母中也有一个sinx抵消了
{: .prompt-warning }

> 答案2：

$\frac14\tan^2\frac x2+\tan\frac x2+\frac12\mathrm{ln}\left|\tan\frac x2\right|+C.$


### 分子分母为sinx和cosx的倍数组合

$$
\frac{Asinx+Bcosx}{Csinx+Dcosx}
$$

---

> 分析：可以将其整理成$\frac{M(Asinx+Bcosx)+N(Asinx+Bcosx)^{'}}{Asinx+Bcosx}$，前半部分化简为一个常数，后半部分进行凑微分。
写出方程，对于sinx和cosx的系数列出两个=方程，解出M和N。
{: .prompt-tip }

> 例题1：

$\int\frac{7cosx-3sinx}{5cosx+2sinx}\mathrm{d}x\mathrm{~;}$

> 答案1：

![](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F24%2F1721808219.png)

> 例题2：

$\int\frac{\mathrm{d}x}{1+\tan x};$

> 答案2：

![](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F24%2F1721809281.png)