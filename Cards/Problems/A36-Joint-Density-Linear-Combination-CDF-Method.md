---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Joint Density, Distribution Function Method, Linear Combinations]
tags: [A36, joint-density, CDF-method, double-integral, integration-region]
difficulty: medium
exam_priority: high
status: learning
source: [教材 A36 题图, 2026-11-07 手写解题与讨论]
related: [A35-Sum-of-Independent-Normals-Two-Methods.md, A20-Marginal-Density-on-Curved-Region.md]
created: 2026-11-07
updated: 2026-11-07
---

# A36｜已知联合密度求 Z=2X-Y 的密度（分布函数法）

## Problem｜完整题目

A36. 设二维随机变量 $(X,Y)$ 的联合密度函数为

$$
f_{X,Y}(x,y)=
\begin{cases}
\frac14,&0\lt x\lt2,\quad 0\lt y\lt2x,\\
0,&\text{其他}.
\end{cases}
$$

记 $Z=2X-Y$，求 $Z$ 的密度函数。

## Recognition｜识别

- 联合密度非零区域：三角形 $0\lt x\lt2,\;0\lt y\lt2x$，顶点 $(0,0),(2,0),(2,4)$。
- 没有说明独立，不可套用独立变量的普通卷积公式。
- **只用分布函数法**：先求 $F_Z(z)=P(Z\le z)$，再求导得到 $f_Z(z)$，不需要雅可比。

## First Thought｜用户真实手写尝试

用户正确画出了三角形，并写出

$$
F_Z(z)=P(2X-Y\le z)=P\left(X\le\frac{Y+z}{2}\right).
$$

也正确求得边缘密度

$$
f_X(x)=\int_0^{2x}\frac14\,dy=\frac x2,\qquad 0\lt x\lt2.
$$

但是接下来尝试只积分 $f_X(x)$，将随机变量 $Y$ 留在积分上限 $(Y+z)/2$ 中。**错误发生在这一步**：$F_Z(z)$ 是涉及 $X,Y$ 两者的联合事件，不能当作只有 $X$ 的概率来计算。

## Correct Solution｜分布函数法

### 1. 确定 Z 的范围

由 $0\lt y\lt2x$、$0\lt x\lt2$ 得

$$
0\lt Z=2X-Y\lt2X\lt4.
$$

因此仅需计算 $0\lt z\lt4$。

### 2. 将事件画成区域

$$
F_Z(z)=P(Z\le z)=P(2X-Y\le z)=P(Y\ge2X-z).
$$

对于一个**固定的数** $z$，在原三角形上截取直线 $y=2x-z$ 的**上方**。

该线与 $x$ 轴交于 $x=z/2$，需分两块：
1. $0\lt x\lt z/2$：$0\lt y\lt2x$；
2. $z/2\lt x\lt2$：$2x-z\lt y\lt2x$。

### 3. 先对 y 积分，再对 x 积分

$$
\begin{aligned}
F_Z(z)
&=\int_0^{z/2}\int_0^{2x}\frac14\,dy\,dx
+\int_{z/2}^{2}\int_{2x-z}^{2x}\frac14\,dy\,dx\\
&=\int_0^{z/2}\frac x2\,dx+\int_{z/2}^{2}\frac z4\,dx\\
&=\frac{z^2}{16}+\frac z4\left(2-\frac z2\right)\\
&=\frac z2-\frac{z^2}{16}.
\end{aligned}
$$

第二段内层积分展开：

$$
\int_{2x-z}^{2x}\frac14\,dy
=\left[\frac y4\right]_{2x-z}^{2x}
=\frac{2x}{4}-\frac{2x-z}{4}=\frac z4.
$$

**不是把上下限分别“积一下”**：先求关于 $y$ 的原函数，再“代入上限减代入下限”。对 $y$ 积分时，$x,z$ 都当作常数；外层对 $x$ 积分时，$z$ 当作常数。

所以完整分布函数为

$$
F_Z(z)=
\begin{cases}
0,&z\le0,\\
\frac z2-\frac{z^2}{16},&0\lt z\lt4,\\
1,&z\ge4.
\end{cases}
$$

### 4. 求导获得密度

$$
\boxed{
f_Z(z)=
\begin{cases}
\frac{4-z}{8},&0\lt z\lt4,\\
0,&\text{其他}.
\end{cases}
}
$$

检验：$\int_0^4(4-z)/8\,dz=1$。

## Calculation Skeleton｜考试简写

$$
F_Z(z)=P(Y\ge2X-z).
$$

当 $0\lt z\lt4$：

$$
\begin{aligned}
F_Z(z)&=\int_0^{z/2}\int_0^{2x}\frac14\,dy\,dx
+\int_{z/2}^2\int_{2x-z}^{2x}\frac14\,dy\,dx\\
&=\frac z2-\frac{z^2}{16}.
\end{aligned}
$$

求导得 $f_Z(z)=(4-z)/8$（$0\lt z\lt4$），其他为 $0$。

## Mistake / Knowledge Gap｜易错点

1. **边缘密度不能代替联合密度**：虽然 $f_X(x)=x/2$ 算得正确，但 $P(X\le(Y+z)/2)$ 的阈值里有随机变量 $Y$，不是普通的单变量累积概率。
2. **z 不是第三个积分变量**：在求 $F_Z(z)$ 时暂时固定 $z$，只对 $x,y$ 积分。
3. **无需把 x 与 y 分开**：二重积分内层上下限可以含有外层变量 $x$。
4. **分段是区域决定的**：分界点为 $x=z/2$，不能只用一个简单的矩形积分区间。
5. **先求分布函数，再求导**；这里不需要雅可比方法。

## Related

- [A35｜独立正态变量之和的两种做法](A35-Sum-of-Independent-Normals-Two-Methods.md)
- [A20｜曲线区域的边缘密度](A20-Marginal-Density-on-Curved-Region.md)

## My Questions

- “不是传统的 X+Y 了啊。”
- “老师的 chap03 PPT 也没有讲这些 [雅可比] 啊。”
- “x 和 y 都是分不开的，现在又多了一个 z，还有积分是把 y 的上下限都积一下吗？”
- 提交手写解：在求出正确的 $F_Z$ 事件和 $f_X$ 后，对随机上限积分感到困惑。

## Personal Summary｜个人总结

- 已正确画联合密度三角形，也能正确求出 $f_X(x)$。
- 仍需练习从联合事件画二维积分区域、找到 $x=z/2$ 分界并完成分段二重积分。
- 尚未独立完整重做本题；状态继续为 learning。
