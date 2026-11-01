---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Binomial Distribution, Independent Repeated Trials]
tags: [binomial, combinations, independence, exactly-k]
difficulty: easy
exam_priority: high
status: review
source: [本轮用户手写计算与口头澄清]
related: [Cards/Mistakes/B24-Conditional-Failure-and-Independence.md]
created: 2026-11-01
updated: 2026-11-01
---

# 二项分布：恰好成功 k 次

## One Sentence

若有 $n$ 次相互独立且成功概率都为 $p$ 的伯努利试验，则成功次数 $Y\sim B(n,p)$，$P(Y=k)=\binom nk p^k(1-p)^{n-k}$。

## Example｜本轮用户原始计算

用户上传了手写计算式，并明确纠正助教：“不是就五个选两个然后乘上选中的概率是11/16的二项分布啊”。

这是**计算片段而非可核实的完整习题原文**，因此保留为 Concept 示例，**不冒充完整原题或错题卡**。

若 $n=5,p=11/16,k=2$：

$$
P(Y=2)=\binom52\left(\frac{11}{16}\right)^2
\left(1-\frac{11}{16}\right)^3
=\frac{75625}{524288}\approx0.14424.
$$

## Key Mechanism

- “恰好两个成功”选出成功位置的组合数是 $\binom52$，不是 $\binom62$。
- $p^2$ 表示两个成功，$(1-p)^3$ 表示三个失败；三者**相乘**。
- 若问“至少两个”须将 $k=2,3,4,5$ 的概率相加，或采用补事件。
- 使用二项分布前先核查各次是否独立、成功概率是否相同。共享环境造成的条件独立未必推出无条件独立，参见 B24。

## Personal Summary｜个人总结

我指出助教把手写计算误读了：我的思路是“五个选两个、成功概率是 $11/16$ 的二项分布”，而不是其误识别的六选二和减法。以后遇到同类式子，先确认 $n,k,p$ 以及成功、失败两个指数，再按公式计算；这次的公式思路本身正确。
