---
type: concept
subject: Probability and Mathematical Statistics
topic:
  - Conditional Probability
tags:
  - conditional-probability
  - sample-space
  - certain-event
difficulty: easy
exam_priority: high
status: learning
related: []
created: 2026-11-01
updated: 2026-11-01
---

# 条件概率符号与 $P(S\mid B)=1$

## One Sentence

$P(A\mid B)$ 表示“在事件 $B$ 已经发生的条件下，事件 $A$ 发生的概率”；若 $S$ 是样本空间且 $P(B)>0$，则 $P(S\mid B)=1$。

## Core Idea

条件概率把原来的样本空间“缩小”到条件事件内部。

定义为：

```math
P(A\mid B)
=
\frac{P(A\cap B)}{P(B)},
\qquad P(B)>0
```

其中竖线左边是“要求谁”，右边是“已知谁发生”。

## Why $P(S\mid B)=1$

因为任意事件 $B$ 都满足：

```math
B\subseteq S
```

所以：

```math
S\cap B=B
```

于是：

```math
P(S\mid B)
=
\frac{P(S\cap B)}{P(B)}
=
\frac{P(B)}{P(B)}
=
1
```

## Example

掷一个骰子。设：

- $B=$“掷出偶数”；
- $S=$整个样本空间。

一旦已经知道 $B$ 发生，结果必然仍然属于样本空间 $S$，因此 $P(S\mid B)=1$。

## Exam Focus

1. 看到 $P(A\mid B)$，先读成“已知 $B$，求 $A$”。
2. 不要把条件概率和交概率混淆。
3. 使用条件概率定义时必须注意 $P(B)>0$。
4. $S$ 是必然事件，因此在任何合法条件下，$P(S\mid B)=1$。

## Personal Summary｜个人总结

我一开始主要是不熟悉竖线 $\mid$ 的含义。现在我把 $P(A_2\mid A_1)$ 理解成“已经知道 $A_1$ 发生后，再看 $A_2$ 的概率”。

对 $P(S\mid B)=1$，我的理解是：既然 $B$ 本身就在整个样本空间 $S$ 里面，那么已经知道 $B$ 发生以后，结果属于 $S$ 是必然的。公式上就是 $S\cap B=B$。
