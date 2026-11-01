---
type: concept
subject: Probability and Statistics
topic: [Expectation, Variance, Conditional Expectation]
tags: [Variance, Total Expectation, Covariance]
difficulty: medium
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-01
---
# 期望、方差与条件期望的计算

## 核心结论
- $E[(X-a)^2]=\operatorname{Var}(X)+(E[X]-a)^2$；当 $a\ne E[X]$ 时严格大于方差。
- 全期望公式：$E[Y]=E[E(Y\mid X)]$。
- 独立且二阶矩存在必然推出协方差为零；协方差非零可以直接否定独立性，但协方差为零通常不能推出独立。

## 典型题
- $X\sim U(0,1)$，且 $Y\mid(X=p)\sim B(5,p)$：$E(Y)=E(5X)=5/2$。
- $\operatorname{Var}(\xi)=\operatorname{Var}(\eta)=1$、相关系数 $1/2$，$X=4\xi/3+\eta$、$Y=\xi-\eta$：$\operatorname{Cov}(X,Y)=1/6\ne0$，故不独立。

## Personal Summary｜个人总结
本轮做了条件期望、方差最小化与协方差判断练习。条件期望题的 AI 曾先误报选项 B 后改正为 A；该错误属于 AI，不是用户错题。