---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 4
topic:
  - Mathematical Expectation
  - Distribution Functions
  - Order Statistics
tags:
  - B15
  - Maximum
  - Minimum
  - CDF
  - Uniform Distribution
  - Formula Recall
difficulty: medium
exam_priority: high
status: review
source:
  - 黄炜等《概率论与数理统计（第二版）》习题四 B15（题意据本轮学习对话记录）
  - 2026-11-14 学习对话：本人明确反馈最值分布函数方法未想起
related: []
created: 2026-11-14
updated: 2026-11-14
---

# 习题四 B15：最远距离——极值随机变量先求分布函数

## Problem

在区间 $(0,1)$ 上独立、均匀地随机取 $n$ 个点（$n\ge 2$），求相距最远的两个点之间距离的数学期望。

记各点为 $X_1,\ldots,X_n$，它们独立同分布于 $U(0,1)$。

## First Thought｜我的第一反应

- 我知道两点间的距离与位置之差有关，最开始想直接找某两个 $X$ 和 $Y$ 的最大差距，但这样不能保证挑出的就是所有随机点中最远的一对。
- 看完推导后，我明确反馈：“**我又忘了算最小最大这种可以用分布函数了**。”
- 本题**真正要复盘的不是积分难度，而是看到“随机变量中的最大/最小”时，没有主动调用“先求极值的分布函数（CDF）”这一方法**。
- 目前没有完成无提示复测，不能视为已经掌握。

## Recognition｜题型触发条件

看到下列词语时，先想极值随机变量的 CDF：

- “$n$ 个随机点中最远的两个点”
- “最大值/最小值”
- “最后一个到达”“最早发生”（适用时转换成最大/最小）
- “至少一个”“全部满足”

在一维数轴上，最远的两点必定是最左和最右的两点，因此定义：

```math
M=\max(X_1,\ldots,X_n),\qquad
m=\min(X_1,\ldots,X_n).
```

目标随机变量是：

```math
D=M-m.
```

先利用期望的线性性质，而非急于求 $D$ 的密度：

```math
E(D)=E(M)-E(m).
```

注意：此处不要求 $M$ 与 $m$ 独立。

## Correct Solution｜标准推导

### 1. 最大值 $M$：所有点均不超过 $x$

对 $0\le x\le1$：

```math
\begin{aligned}
F_M(x)
&=P(M\le x)\\
&=P(X_1\le x,\ldots,X_n\le x)\\
&=\prod_{i=1}^n P(X_i\le x)\\
&=x^n.
\end{aligned}
```

由此，完整 CDF 与区间内 PDF 为：

```math
F_M(x)=
\begin{cases}
0,&x<0,\\
x^n,&0\le x\le1,\\
1,&x>1,
\end{cases}
\qquad
f_M(x)=nx^{n-1},\quad0<x<1.
```

所以：

```math
\begin{aligned}
E(M)
&=\int_0^1 x\,nx^{n-1}\,dx\\
&=n\int_0^1x^n\,dx\\
&=\frac{n}{n+1}.
\end{aligned}
```

### 2. 最小值 $m$：转化为所有点都大于 $x$

“最小值不超过 $x$”表示**至少一个点不超过 $x$**。用对立事件更简单：

```math
\begin{aligned}
F_m(x)
&=P(m\le x)\\
&=1-P(m>x)\\
&=1-P(X_1>x,\ldots,X_n>x)\\
&=1-(1-x)^n,\qquad 0\le x\le1.
\end{aligned}
```

完整 CDF 与区间内 PDF：

```math
F_m(x)=
\begin{cases}
0,&x<0,\\
1-(1-x)^n,&0\le x\le1,\\
1,&x>1,
\end{cases}
\qquad
f_m(x)=n(1-x)^{n-1},\quad0<x<1.
```

按期望定义：

```math
E(m)=n\int_0^1x(1-x)^{n-1}\,dx.
```

分部积分，取 $u=x$、$dv=n(1-x)^{n-1}\,dx$，则 $du=dx$、$v=-(1-x)^n$：

```math
\begin{aligned}
E(m)
&=\left[-x(1-x)^n\right]_0^1
+\int_0^1(1-x)^n\,dx\\
&=0+\left[-\frac{(1-x)^{n+1}}{n+1}\right]_0^1\\
&=\frac1{n+1}.
\end{aligned}
```

### 3. 期望相减

```math
\begin{aligned}
E(D)
&=E(M)-E(m)\\
&=\frac{n}{n+1}-\frac1{n+1}\\
&=\boxed{\frac{n-1}{n+1}}.
\end{aligned}
```

验证：$n=2$ 时 $E(D)=1/3$；随着 $n$ 增大，结果趋近 $1$，符合取点越多越可能接近两端的直觉。

## Key Concept｜极值分布函数通法

若 $X_1,\ldots,X_n$ **独立同分布**，单个随机变量的 CDF 为 $F(x)$：

**最大值：**

```math
P(M\le x)
=P(X_1\le x,\ldots,X_n\le x)
=[F(x)]^n.
```

**最小值：**

```math
P(m\le x)
=1-P(X_1>x,\ldots,X_n>x)
=1-[1-F(x)]^n.
```

不能把两个公式弄反：

| 目标事件 | 转换为单个样本的事件 | CDF |
| --- | --- | --- |
| $M\le x$ | **所有** $X_i\le x$ | $F(x)^n$ |
| $m\le x$ | **至少一个** $X_i\le x$，取补集 | $1-[1-F(x)]^n$ |

这里写成 $n$ 次方的条件是样本独立同分布；若仅独立但不同分布，就应使用各自 $F_i(x)$ 的乘积。

## Calculation Skeleton｜考试中的四步

1. **最远距离写成极差：** $D=\max_i X_i-\min_i X_i$。
2. **先 CDF：** 最大值对应“所有都 $\le x$”；最小值对应“至少一个 $\le x$”，通常取补集。
3. 对 CDF 求导得 PDF，再按定义计算 $E(M),E(m)$。
4. **最后线性相减：** $E(D)=E(M)-E(m)$，不要求两者独立。

## Transfer / Retest

- 无提示复测：对独立同分布 $U(0,2)$ 的 $n$ 个样本，独立写出 $F_M(x)$、$F_m(x)$ 和最远距离的期望（正确结果为 $2(n-1)/(n+1)$）。
- 对比练习：若 $X_i$ 独立同分布于一般连续分布，先不求密度，仅用单个 $F(x)$ 写出 $F_M(x),F_m(x)$。
- 易混自测：为什么 $P(M\le x)$ 是“全部”，而 $P(m\le x)$ 是“至少一个”？

## Personal Summary｜个人总结

- 我最开始想通过两点 $X,Y$ 的差距最大来求距离，但没有明确把最远两点定位为样本中的**最大值和最小值**。
- **我这次明确意识到的遗忘点是：“算最小最大这种可以用分布函数”，但做题时没有主动想起来。**
- 下次遇到最大值、最小值、极差时，我需要第一时间写：$F_M(x)=P(M\le x)$ 或 $F_m(x)=P(m\le x)$，并翻译成“所有”或“至少一个”。
- 期望能通过最大值减最小值分别计算；现在只完成讲解，尚需无提示重做确认是否真正掌握。
