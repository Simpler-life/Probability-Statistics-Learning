---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Continuous Random Variable, Distribution Function, Density]
tags: [B18, CDF, PDF, continuity, differentiation]
difficulty: medium
exam_priority: high
status: review
source: [教材第二章习题 B18；用户上传照片]
related: [Cards/Concepts/Distribution-Function-and-Density.md]
created: 2026-11-01
updated: 2026-11-01
---

# B18｜分布函数反求密度

## Original Problem｜完整原题

B18. 设连续型随机变量 $X$ 的分布函数为：

$$
F(x)=
\begin{cases}
0,&x<0,\\
ax^2,&0\le x<1,\\
bx,&1\le x<2,\\
1,&x\ge2.
\end{cases}
$$

（1）求常数 $a,b$；（2）求 $X$ 的密度函数 $f(x)$；（3）求 $P\{0.5<X<1.5\}$。

## First Thought

用户原话：“这个 B18 怎么反求密度函数啊，直接求导吗？”

## Correct Solution

（1）连续型随机变量的 CDF 连续，在 $x=1,2$ 接起来：$a=b$、$2b=1$，故 $a=b=\frac12$。

（2）在可导点逐段求导：

$$
f(x)=
\begin{cases}
0,&x<0,\\
x,&0\le x<1,\\
\frac12,&1\le x<2,\\
0,&x\ge2.
\end{cases}
$$

$F$ 在 $x=1$ 不可导，但密度在单点取值不影响积分概率，以上为合法版本。

（3）优先用分布函数相减：

$$
P(0.5<X<1.5)=F(1.5)-F(0.5)=\frac34-\frac18=\frac58.
$$

也可分段积分：

$$
\int_{0.5}^{1}x\,dx+\int_1^{1.5}\frac12\,dx=\frac58.
$$

## Exam Warning

先求未知参数再求导；密度函数可有跳跃，不等于分布函数必须处处可导；遇分段积分需按断点拆开。

## Personal Summary｜个人总结

我先想到“直接求导”，正确方向是 $f=F'$，但要先由连续性求 $a,b$，再分段求导。单个分界点的密度值不影响概率。
