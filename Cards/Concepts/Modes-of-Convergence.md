---
type: concept
subject: Probability and Statistics
topic: [Convergence of Random Variables]
tags: [Distribution, Probability, Mean Square, Almost Surely]
difficulty: hard
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-01
---
# 随机变量的四种收敛

## 核心结论
- 依概率收敛蕴含依分布收敛。
- 若 $X_n\xrightarrow{d}c$，极限是常数，则 $X_n\xrightarrow{P}c$。
- 均方收敛：$E[(X_n-X)^2]\to0$。
- 几乎处处收敛：$P(\lim_n X_n=X)=1$。

## 典型辨析
若 $\xi\sim U(-2,2)$，每个 $n$ 都有 $X_n=\xi$，而 $X=-\xi$，则 $X_n$ 与 $X$ 同分布，因此依分布收敛；但 $X_n-X=2\xi$ 不趋于零，故不依概率、均方或几乎处处收敛。

## Personal Summary｜个人总结
本轮涉及“依分布收敛于常数”及“四种收敛辨析”。AI 曾先误报选项 B 后更正为 A，属于 AI 答题错误。