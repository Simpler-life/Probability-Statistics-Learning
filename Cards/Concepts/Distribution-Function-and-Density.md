---
type: concept
subject: Probability and Statistics
topic: [Distribution Function, Probability Density]
tags: [CDF, PDF, Continuity, Normalization]
difficulty: medium
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-01
---
# 分布函数的连续点与概率密度归一化

## 核心结论
- 概率密度 $p(x)\ge 0$（几乎处处），且 $\int_{-\infty}^{+\infty}p(x)\,dx=1$。
- 任意分布函数 $F(x)$ 单调不减、右连续，不连续点至多可数，连续点集在实数轴上稠密。
- 分布函数的连续点集未必闭。

## 典型题
1. “连续型随机变量的概率密度在全实数上的积分为1”——正确。
2. “分布函数的连续点集为稠密集”——正确。
3. 若 $p(x)=ce^{-x^2/3+2x}$，则配方得到 $-x^2/3+2x=-(x-3)^2/3+3$，从而 $c=e^{-3}/\sqrt{3\pi}$。

## Personal Summary｜个人总结
本轮通过判断题和归一化计算题复习了这些性质；尚无用户自行陈述的理解或错误。

## 补充：A8 与 B18 的贯通理解（2026-11-01）

- 分布函数的**定义**是 $F(x)=P(X\le x)$；写成分段表达式时，分段条件的右端不要求都是“$\le$”。
- 离散型 $X$ 的 CDF 在有正概率的取值点跳跃：$P(X=a)=F(a)-F(a^-)$；在当点包含这一跳，故右连续。例见 [A8](../Problems/A8-Discrete-CDF-and-Endpoints.md)。
- 连续型 $X$ 的 CDF 连续；绝对连续情况下，可通过 $f(x)=F'(x)$（几乎处处）求密度。不要误以为 $F$ 必须处处可导，或密度必须连续。例见 [B18](../Problems/B18-Continuous-CDF-to-Density.md)。
- 对连续型分布，单点概率为零，$P(a<X<b)=F(b)-F(a)$；离散型遇严格端点时必须考虑点质量。
- 标准正态分布：$\Phi(-z)=1-\Phi(z)$，例如 $\Phi(-0.8)=1-\Phi(0.8)=0.2119$；$\Phi(0.8)=0.7881$。

## Personal Summary｜本轮新增的个人理解

我对离散型分布函数分段的端点感到陌生，提出“是否因为定义永远是小于等于，跨过取值点就换段”的猜想；在 B18 又追问“反求密度是不是直接求导”；在 B24 查表时询问负的标准化数值是不是用 $1-\Phi(0.8)$。这些疑问贯通了**累计、跳跃、求导、查表**四件事。此段保留了原 Personal Summary，不覆盖此前的个人记录。
