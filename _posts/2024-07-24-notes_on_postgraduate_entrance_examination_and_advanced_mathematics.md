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

### 定积分的应用

#### 几何应用

##### 平面面积

###### 直角坐标![image-20240729222400843](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F29%2F1722263040.png)

$$
S=\int_a^{b}f(x)dx
$$

或者
$$
S=\int_a^{b}f(y)dy
$$


**高减低，右减左，确保面积为正。**

###### 极坐标系

$$
S=\frac{1}{2}\int_{\alpha}^{\beta}r^2(\theta)d\theta
$$

> 补充：扇形面积公式

$$
S=\frac{1}{2}LR=\frac{1}{2}{\theta}R^2，其中弧长L={\theta}R
$$

> 补充：重要的极坐标曲线

![image-20240730083751830](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722299878.png)

![image-20240730083823925](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722299904.png)

###### 参数方程

$$
S=\int_{a}^{b}y_(t)x^{'}_{(t)}dt
$$

![image-20240730150046254](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722322846.png)

> 补充：重要的极坐标曲线

![image-20240730084141005](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722300101.png)

##### 旋转体体积

###### 直角坐标

- 绕x轴

$$
V_x=\int_a^b{\pi}y^2dx=>其中{\pi}y^2为圆柱体的表面积,dx为圆柱体的高
$$

- 绕y轴

$$
V_y=\int_a^b2{\pi}xydx=>其中2{\pi}x为周长即展开长方体的长,y为长方体的高,dx为长方体的厚度
$$

###### 极坐标系

使用极坐标方程将[直角坐标系](#旋转体体积)下的公式中x、y、dx代换掉。

###### 参数方程

使用参数方程将[直角坐标系](#旋转体体积)下的公式中x、y、dx代换掉。

##### 弧长L

> **积分限从小写到大（牵扯到弧微分一律从小写到大）**

![image-20240730124236639](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722314556.png)

易得：
$$
ds=\sqrt{(dx)^2+(dy)^2}
$$

###### 直角坐标

$$
L=\int_a^b\sqrt{1+(y^{'}_{x})^2}dx
$$

###### 参数方程

$$
L=\int_\alpha^\beta\sqrt{(x^{'}_t)^2+(y^{'}_t)^2}dt
$$

###### 极坐标

$$
L=\int_\alpha^\beta\sqrt{r^2+(r^{'}_\theta)^2}d\theta
$$

##### 旋转侧表面积

> **积分限从小写到大（牵扯到弧微分一律从小写到大）**

![image-20240730131657408](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F30%2F1722316617.png)

###### 直角坐标

> 公式中的y是高，要确保是正的

$$
S=\int_a^{b}2\pi{y}\sqrt{1+(y^{'}_{x})^2}dx=>其中a≤x≤b
$$

###### 参数方程

$$
S=\int_\alpha^{\beta}2\pi{y_{t}}\sqrt{(x^{'}_t)^2+(y^{'}_t)^2}dt=>其中\alpha≤x≤\beta
$$

###### 极坐标

$$
S=\int_\alpha^{\beta}2{\pi}r*sin(\theta)\sqrt{r^2+(r^{'}_\theta)^2}d\theta=>其中\alpha≤x≤\beta
$$

#### 物理应用

##### 变力做工问题

使用微元法。

##### 力的问题

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

### 反常积分

#### 反常积分判断

- 积分区间无穷

- 存在瑕点

1. 找无定义点
2. 判断无定义点是否为无穷间断点

#### 反常积分计算

四则运算

#### 重要反常积分

![image-20240729104531369](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F29%2F1722221138.png)

![image-20240729104927329](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F29%2F1722221367.png)

1️⃣区间大的影响，大的喜欢大的，大于1就收敛。

2️⃣区间小的影响，小的喜欢小的，小于1就收敛。

3️⃣等于1永远收敛。

#### 反常积分奇偶性

![image-20240729105951085](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F29%2F1722221991.png)

#### 比较审敛法

# 常微分方程

![image-20240802171006672](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722589806.png)

### 一阶

#### 可分离变量

y的导数可以写成f(x)和g(y)组合的形式。

解法：
$$
\frac{1}{g(y)}dy=f(x)dx
$$

$$
=>\int\frac{1}{g(y)}dy=\int{f(x)}dx
$$

> 注意事项
>
> 1. 通解≠全部的解，除数为0的时候不用管
> 2. 整理的时候出现ln常数加lnc
> 3. 出现ln积分绝对值要加
> 4. 边界条件带入得到这个情况下的特解

#### 一阶齐次

##### 通解结构

$$
y=C*齐次解
$$

![image-20240802150755908](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722582475.png)

#### 一阶非齐次

![image-20240731200319178](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F31%2F1722427399.png)

### 高阶

#### 二阶可降阶

![image-20240802125632754](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722574599.png)

#### 二阶齐次线性

##### 形式

![image-20240802165355130](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722588835.png)

##### 通解结构

![image-20240802165128453](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722588688.png)

#### 二阶非齐次线性

##### 形式

![image-20240802165329177](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722588809.png)

##### 通解结构

![image-20240802165220599](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722588740.png)

#### 二阶常系数齐次

>考研只考察这种类型的求解

![image-20240802134535572](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722577535.png)

#### 线性微分方程的反问题

> 要想求方程必先知通解
> 要求非齐次必先求齐次

##### 反求特征值

![image-20240802171558875](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722590158.png)

三种形式判断出类型。

![image-20240802171503646](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722590103.png)

#### 二阶常系数非齐次

![image-20240802205642264](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F08%2F02%2F1722603402.png)
