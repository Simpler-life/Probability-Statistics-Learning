---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Discrete Random Variable, Distribution Function]
tags: [A8, CDF, endpoints, right-continuity]
difficulty: easy
exam_priority: high
status: review
source: [教材第二章习题 A8；用户上传照片]
related: [Cards/Concepts/Distribution-Function-and-Density.md]
created: 2026-11-01
updated: 2026-11-01
---

# A8｜离散分布函数与端点

## Original Problem｜完整原题

A8. 设随机变量 $X$ 的概率分布律为 $P\{X=0\}=0.4$，$P\{X=2\}=0.5$，$P\{X=3\}=0.1$，求 $X$ 的分布函数及 $P\{1\le X<3\}$。

## First Thought

用户原话：“分布函数是都要写成右边是小于等于的形式吗，那为什么这道题的答案不是这样”；后来猜测“因为这个分布函数总是会写成小于等于的形式，所以反过来会导致如果改变就分成不一样的段吗”，同时不知道考试过程怎么写。

## Correct Solution

定义 $F(x)=P(X\le x)$。按可能取值 $0,2,3$ 分段累计：$0$、$0.4$、$0.9$、$1$。

$$
F(x)=
\begin{cases}
0,&x<0,\\
0.4,&0\le x<2,\\
0.9,&2\le x<3,\\
1,&x\ge3.
\end{cases}
$$

$$
P(1\le X<3)=P(X=2)=0.5.
$$

端点提示：$F(2)=P(X\le2)=0.9$，所以 $x=2$ 属于第三段。标准定义中的“$\le$”并不是要求每个分段条件右端都用“$\le$”；它决定跳跃点把新概率计入当点，分布函数右连续。

## Exam Answer Skeleton

写定义；列出可能取值；逐步累加概率；写每段区间及左闭右开跳跃端点；最后单独计算事件概率。

## Personal Summary｜个人总结

我起初把 $F(x)=P(X\le x)$ 的等号和分段区间的等号混淆了。我提出：随着 $x$ 改变，累计到的取值改变，于是换段。还需要练习把这个理解稳定写成考试解题过程。
