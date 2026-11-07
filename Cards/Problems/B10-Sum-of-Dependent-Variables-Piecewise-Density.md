---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Joint Density, Sum of Random Variables, Integration Bounds, Piecewise Density]
tags: [B10, convolution-like-formula, joint-density, piecewise-integral, integration-region, exam-review]
difficulty: medium
exam_priority: high
status: learning
source: [教材 B10 原题图片, 2026-11-07 用户手写过程与学习讨论]
related: [A36-Joint-Density-Linear-Combination-CDF-Method.md, A35-Sum-of-Independent-Normals-Two-Methods.md]
created: 2026-11-07
updated: 2026-11-07
---

# B10｜已知联合密度，求 Z=X+Y 的分段密度

## Problem｜完整题目

设二维随机变量 $(X,Y)$ 的联合密度为

$$
f_{X,Y}(x,y)=
\begin{cases}
\frac{3-x-y}{3},&0\lt x\lt1,\quad 0\lt y\lt2,\\
0,&\text{其他}.
\end{cases}
$$

记 $Z=X+Y$，求 $Z$ 的密度函数。

## Recognition｜识别题型

- 原联合密度的非零区域为矩形：$0\lt x\lt1$，$0\lt y\lt2$。
- 求和 $Z=X+Y$：固定 $z$，用直线 $y=z-x$ 截取矩形。
- 可以直接用**联合密度积分公式**，无需假设 $X,Y$ 独立：

$$
f_Z(z)=\int_{-\infty}^{+\infty} f_{X,Y}(x,z-x)\,dx.
$$

- 关键不是积分计算，而是代入 $y=z-x$ 后，检查 **原来的两个约束必须同时成立**。

## First Thought｜用户真实手写解

用户已写出正确的起点：

$$
f_Z(z)=\int_{-\infty}^{+\infty}f_{X,Y}(x,z-x)\,dx.
$$

并且正确代入、化简：

$$
f_{X,Y}(x,z-x)=\frac{3-x-(z-x)}3=\frac{3-z}{3}
$$

**出现问题的步骤**：把积分上下限直接固定为 $0$ 至 $1$，从而得到 $1-z/3$，没有根据 $0\lt y\lt2$ 继续限制 $x$。该结果只在 $1\le z\lt2$ 这一段成立，不是整个密度函数。

## Correct Solution｜完整过程

### 1. 找积分范围

要使联合密度不为 $0$，必须同时满足

$$
0\lt x\lt1,\qquad 0\lt z-x\lt2.
$$

第二个条件移项得

$$
z-2\lt x\lt z.
$$

两组条件取交集，得到

$$
\max(0,z-2)\lt x\lt\min(1,z).
$$

只有在下限小于上限时才有非零密度，即 $0\lt z\lt3$。

### 2. 为什么要分三段？

固定 $z$ 时，直线 $x+y=z$ 在矩形内截得的线段随 $z$ 变化：当 $z=1$、$z=2$ 时，截取方式发生变化。

| $z$ 的范围 | $x$ 的积分区间 | 原因 |
| --- | --- | --- |
| $0\lt z\lt1$ | $0\lt x\lt z$ | $z\lt1$，上界由 $x\lt z$ 决定 |
| $1\le z\lt2$ | $0\lt x\lt1$ | 整段 $0$ 到 $1$ 均有效 |
| $2\le z\lt3$ | $z-2\lt x\lt1$ | 下界由 $x\gt z-2$ 决定 |

### 3. 分段积分

代入后，被积函数简化为 $(3-z)/3$，对 $x$ 来说是常数。

**情况一：$0\lt z\lt1$**

$$
f_Z(z)=\int_0^z\frac{3-z}{3}\,dx
=\frac{z(3-z)}{3}.
$$

**情况二：$1\le z\lt2$**

$$
f_Z(z)=\int_0^1\frac{3-z}{3}\,dx
=\frac{3-z}{3}.
$$

**情况三：$2\le z\lt3$**

$$
\begin{aligned}
f_Z(z)
&=\int_{z-2}^{1}\frac{3-z}{3}\,dx\\
&=\frac{3-z}{3}[1-(z-2)]\\
&=\frac{(3-z)^2}{3}.
\end{aligned}
$$

### 4. 最终答案

$$
\boxed{
f_Z(z)=
\begin{cases}
\frac{z(3-z)}{3},&0\lt z\lt1,\\
\frac{3-z}{3},&1\le z\lt2,\\
\frac{(3-z)^2}{3},&2\le z\lt3,\\
0,&\text{其他}.
\end{cases}
}
$$

边界点处的密度取值不影响概率，以上写法使各段连续。

### 5. 检验结果

$$
\begin{aligned}
\int_0^1\frac{z(3-z)}{3}\,dz &= \frac{7}{18},\\
\int_1^2\frac{3-z}{3}\,dz &= \frac12,\\
\int_2^3\frac{(3-z)^2}{3}\,dz &= \frac19.
\end{aligned}
$$

三部分之和 $7/18+1/2+1/9=1$，符合密度的归一化要求。

## Calculation Skeleton｜考试速写

$$
f_Z(z)=\int f_{X,Y}(x,z-x)\,dx.
$$

$$
0\lt x\lt1,\quad 0\lt z-x\lt2
\quad\Longrightarrow\quad
\max(0,z-2)\lt x\lt\min(1,z).
$$

按 $z=1,2$ 两个分界点分成三段，分别积分得到上述最终结果。

## Mistake / Knowledge Gap｜本次出错原因

**不能仅根据 $0\lt x\lt1$ 就把积分设为 $0$ 到 $1$。** 原联合密度还要求 $0\lt y\lt2$，而代入 $y=z-x$ 后，这个条件改变了允许的 $x$ 范围。

例如 $z=0.5$ 时，只能 $0\lt x\lt0.5$；若取 $x=0.8$，则 $y=-0.3$，违反 $y\gt0$。

例如 $z=2.5$ 时，只能 $0.5\lt x\lt1$；若取 $x=0.2$，则 $y=2.3$，违反 $y\lt2$。

因此用户原来得到的 $f_Z(z)=1-z/3$ 恰好是中间一段 $1\le z\lt2$ 的正确结果。

## Common Traps

1. 把联合密度中的 $y$ 换成 $z-x$ 后，漏掉 $y$ 的支持集限制。
2. 忘记 $f_{X,Y}(x,z-x)$ **在矩形外等于零**；形式上化简成 $(3-z)/3$ 并不意味着在所有 $x$ 上都有这个值。
3. 在求和的公式中使用联合密度不需要独立；但若改用边缘密度乘积 $f_X(x)f_Y(z-x)$，才需要独立条件。
4. 应先定积分范围，再进行简单的代数积分；不要先把 $x$ 的原始范围直接照搬。
5. 即使积分函数不含 $x$，积分区间长度仍随 $z$ 变化。

## Related

- [A36｜分布函数法与区域分段](A36-Joint-Density-Linear-Combination-CDF-Method.md)
- [A35｜独立正态变量之和的两种解法](A35-Sum-of-Independent-Normals-Two-Methods.md)

## My Questions

- 用户提交 B10 原题和手写计算过程，并问：“这为什么不对啊”。
- 手写中能够正确代入 $f(x,z-x)$，但积分限固定为 $0$ 到 $1$。

## Personal Summary｜个人总结

- 本次已能正确使用联合密度的求和积分公式并化简被积函数。
- 尚需练习：代入变量后的**联合约束取交集**、什么时候按 $z$ 分段。
- 未提供独立重做后的答案，不标记为 mastered。
