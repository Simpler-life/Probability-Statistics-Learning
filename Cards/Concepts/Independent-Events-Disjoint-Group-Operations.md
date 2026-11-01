---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 1
topic: [Independence, Event Operations]
tags: [mutual-independence, disjoint-index-groups, union, intersection, complement]
difficulty: medium
exam_priority: high
status: learning
source: [2026-11-01 ChatGPT 学习讨论]
related: [Event-Union-and-Intersection.md]
created: 2026-11-01
updated: 2026-11-01
---

# 相互独立事件的非交叉分组运算仍然独立

## One Sentence

若 $A_1,\ldots,A_n$ **相互独立**，把它们按照**互不重叠的下标组**分组，在各组内部用交、并、补等运算构造新事件，则不同组得到的新事件相互独立。

## Definition

设 $A_1,\ldots,A_n$ 相互独立，$I_1,\ldots,I_m$ 是 $\{1,\ldots,n\}$ 的两两不交子集。每个 $B_j$ 仅由 $\{A_i:i\in I_j\}$ 通过有限次交、并、补运算得到，那么 $B_1,\ldots,B_m$ 相互独立。

这里“不重复”指**不同新事件不重复使用同一个原始事件**，不是要求事件所含样本点不相交，更不是要求新事件互斥。

## Intuition｜直觉

一个新事件只由一组原始事件决定，另一个新事件只由另一组原始事件决定。只要原始事件整体相互独立、两组没有复用原事件，两组各自的逻辑组合仍不相互影响。

## Why

快速判断复杂事件是否独立，避免逐个展开计算联合概率。

## Key Formula

例如，若 $A,B,C,D,E$ 相互独立，则

$$
A\cup B,\quad C\cap D,\quad \overline E
$$

相互独立。

若 $A,B,C$ 相互独立，则

$$
P((A\cup B)\cap C)=P(A\cup B)P(C).
$$

## Conditions

- 原始事件必须**相互独立**，仅两两独立不足以直接应用此定理。
- 新事件之间使用的**原始事件集合不交叉**。
- 各组内部可以组合交、并、补；差事件也可表示为交与补。

## Key Mechanism

由容斥公式和相互独立性：

$$
\begin{aligned}
P((A\cup B)\cap C)
&=P(A\cap C)+P(B\cap C)-P(A\cap B\cap C)\\
&=P(A)P(C)+P(B)P(C)-P(A)P(B)P(C)\\
&=P(A\cup B)P(C).
\end{aligned}
$$

## Typical Example

- 可以直接判定：$A\cup B$ 与 $C\cap D$ 独立（已知 $A,B,C,D$ 相互独立）。
- **不可直接判定**：$A\cap B$ 与 $A\cup C$ 独立，因为复用了 $A$。注意这并不意味着它们必不独立，只是定理无法保证。

## Exam Focus

识别“原始事件相互独立 + 分组没有交叉”，直接使用独立性，而非每次繁琐推导。

## Common Traps

- “互不重叠的分组”不等于“事件互斥”。
- “两两独立”不等于“相互独立”。
- 复用同一个原事件时不能据本定理下结论。

## Related

- [和事件、积事件与交并运算](Event-Union-and-Intersection.md)

## My Questions

- 用户在课堂听到“相互独立的一堆事件，不重复的运算得到的事件仍然相互独立”，希望确认严格表述；已经解释“不同新事件不复用原始事件”，尚无独立解题验证。

## Personal Summary｜个人总结

- 用户的原始表述：“有一堆事件，它们相互独立，但是它们之间不重复的运算得到的事件也是相互独立的”。
- 需要保留的概念澄清：这里的“不重复”应落实为**构造不同新事件的原始事件没有重复使用**，而不是运算结果互斥。
- 当前掌握程度未验证，不标记 mastered。
