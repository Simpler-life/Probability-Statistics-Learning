---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Poisson Distribution, Order Statistics, Conditional Probability]
tags: [B12, poisson, maximum-minimum, complementary-event, conditional-probability]
difficulty: medium
exam_priority: high
status: learning
source: [教材 B12 题图, 2026-11-07 学习讨论]
related: [A35-Sum-of-Independent-Normals-Two-Methods.md]
created: 2026-11-07
updated: 2026-11-07
---

# B12｜泊松分布的和、最大最小值与条件概率

## Problem｜原题

设一本书每页的错误个数 $`X`$ 服从参数为 $`\lambda`$ 的泊松分布，且各页错误个数相互独立。随机选 10 页，错误个数分别记作 $`X_1,\ldots,X_{10}`$。

（1）求 $`P\left(\sum_{i=1}^{10}X_i\ge2\right)`$。

（2）求 $`P\left(\max_{1\le i\le10}X_i\ge2\right)`$。

（3）求 $`P\left(\max_{1\le i\le10}X_i\ge2\mid\min_{1\le i\le10}X_i=0\right)`$。

## Recognition｜题目识别

- 求总数：泊松分布可加性；
- 求最大值：至少一页有 2 个或更多错误，先求“全部不超过 1”；
- 求最小值为 0：至少有一页零错误，先求“全部至少为 1”；
- 条件概率：将“至少一页为 0”和“至少一页至少有 2 个错误”两个事件结合，优先考虑补事件和差集。

## Knowledge Gap｜这次学习的真实薄弱点

用户明确反馈：“我对泊松分布不熟，并且没有第一时间想到第三问的做法。”

不要将此误写成独立作答已通过；目前状态为 learning。

## Prerequisite｜泊松分布速补

若 $`X\sim\mathrm{Pois}(\lambda)`$，$`\lambda>0`$，则

$$
P(X=k)=\frac{\lambda^k}{k!}e^{-\lambda},\quad k=0,1,2,\ldots
$$

特别重要：

$$
P(X=0)=e^{-\lambda},\qquad P(X=1)=\lambda e^{-\lambda}.
$$

于是

$$
P(X\le1)=(1+\lambda)e^{-\lambda},\qquad P(X\ge1)=1-e^{-\lambda}.
$$

性质：相互独立的泊松变量之和仍是泊松分布，参数相加。因此

$$
S=\sum_{i=1}^{10}X_i\sim\mathrm{Pois}(10\lambda).
$$

泊松分布的均值、方差均为 $`\lambda`$。不要与二项分布 $`B(n,p)`$ 混淆。

## Correct Solution｜三问完整解答

### （1）十页错误总数至少为 2

由泊松可加性，$`S\sim\mathrm{Pois}(10\lambda)`$，求补事件：

$$
\begin{aligned}
P(S\ge2)
&=1-P(S=0)-P(S=1)\\
&=1-e^{-10\lambda}-10\lambda e^{-10\lambda}\\
&=\boxed{1-(1+10\lambda)e^{-10\lambda}}.
\end{aligned}
$$

### （2）十页中至少有一页出现 2 个或以上错误

设 $`A=\lbrace \max_iX_i\ge2\rbrace `$。

$$
\begin{aligned}
P(A)
&=1-P(X_1\le1,\ldots,X_{10}\le1)\\
&=1-\prod_{i=1}^{10}P(X_i\le1)\\
&=\boxed{1-\left[(1+\lambda)e^{-\lambda}\right]^{10}}.
\end{aligned}
$$

第二步用到了各页独立。

### （3）条件为至少一页零错误

设

$$
A=\lbrace \max_iX_i\ge2\rbrace ,\qquad B=\lbrace \min_iX_i=0\rbrace .
$$

目标：

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)}.
$$

先算分母 $`P(B)`$。因为错误数非负，“最小值为 0”等价于“至少有一页为 0”，其补事件是全部页数都至少为 1：

$$
\begin{aligned}
P(B)
&=1-P(X_1\ge1,\ldots,X_{10}\ge1)\\
&=1-(1-e^{-\lambda})^{10}.
\end{aligned}
$$

再看分子。不直接枚举哪页为零、哪页大于等于 2，而是使用

$$
P(A\cap B)=P(B)-P(A^c\cap B).
$$

其中 $`A^c\cap B`$ 的意思是：所有页的错误数都不超过 1，且至少一页为 0。

因此它等于“全部错误数不超过 1”减去“全部恰好为 1”：

$$
\begin{aligned}
P(A^c\cap B)
&=P(\text{全部}\le1)-P(\text{全部}=1)\\
&=\left[(1+\lambda)e^{-\lambda}\right]^{10}
-\left[\lambda e^{-\lambda}\right]^{10}.
\end{aligned}
$$

代回条件概率：

$$
\boxed{
P(A\mid B)=1-
\frac{
\left[(1+\lambda)e^{-\lambda}\right]^{10}
-\left[\lambda e^{-\lambda}\right]^{10}
}{
1-(1-e^{-\lambda})^{10}
}
}
$$

## Calculation Skeleton｜考试速记

$$
\begin{aligned}
\text{(1)}\quad& 1-(1+10\lambda)e^{-10\lambda};\\
\text{(2)}\quad& 1-\left[(1+\lambda)e^{-\lambda}\right]^{10};\\
\text{(3)}\quad& 1-\frac{\left[(1+\lambda)e^{-\lambda}\right]^{10}-\left[\lambda e^{-\lambda}\right]^{10}}{1-(1-e^{-\lambda})^{10}}.
\end{aligned}
$$

## Key Mechanism｜为什么第三问难想到？

1. 先定义 A（至少一页错误数 $`\ge2`$）和 B（至少一页错误数等于 0）。
2. 先求 B：用“全部非零”的补事件。
3. 不直接求 $`A\cap B`$，而用 $`P(A\cap B)=P(B)-P(A^c\cap B)`$。
4. $`A^c\cap B`$ 对应“所有页只能为 0 或 1，但不能全是 1”。

这个“**大事件减去不符合要求的部分**”是条件概率综合题最值得训练的思维步骤。

## Common Traps｜考试易错点

- “总错误数至少为 2”和“至少一页有两个错误”不同。例如两页各 1 个错误，只满足前者。
- $`\max X_i\ge2`$ 表示至少有一页达到 2，不是每页都达到 2。
- $`\min X_i=0`$ 表示至少一页为 0，不是所有页都为 0。
- “所有页 $`\le1`$”不自动保证至少一页为 0，还可能全部为 1，所以第三问必须减去“全部为 1”的概率。
- 各页独立才能把多个页面事件的概率相乘。

## Similar Problems｜针对薄弱点的复测

1. 不看公式，写出泊松分布的 $`P(X=0)`$、$`P(X=1)`$、$`P(X\le1)`$。
2. 若十页错误总数至少为 3，如何利用补事件？
3. 已知至少有一页为 0，求所有页错误数都不超过 1 的条件概率，并说明为何要减去“全部为 1”。

## Related

- [A35｜独立正态变量之和（对照泊松可加性）](A35-Sum-of-Independent-Normals-Two-Methods.md)

## My Questions

- “这个题呢？”
- “把这道题放入GitHub，我对泊松分布不熟，并且没有第一时间想到第三问的做法。”

## Personal Summary｜个人总结

- 已明确：泊松分布相关公式不熟，需加强基本概率质量函数和可加性。
- 第三问的瓶颈是没有第一时间找到补事件和条件概率的组合路线，今后先将 max/min 翻译为“至少一个/全部”。
- 尚未独立完整重做本题，状态保持 learning。
