---
type: mistake
subject: Probability and Mathematical Statistics
topic:
  - Probability of Events
  - Independence
tags:
  - mutually-exclusive
  - independence
  - union
  - complement
difficulty: easy
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-01
---

# B1：把互不相容误当成独立

## Original Problem｜完整原题

B1. 设 $A,B,C$ 为三个随机事件，$P(A)=P(B)=0.3$，$P(C)=0.4$，且当 $A$ 发生时 $C$ 必然发生，$B$ 与 $C$ 互不相容，求：

1. $C$ 发生的同时 $A$ 不发生的概率；
2. $A$ 与 $B$ 至少有一个发生的概率；
3. $A,B,C$ 都不发生的概率。

## Context

本次错误发生在第（2）问。

## Wrong Idea

我想用补事件：

```math
P(A\cup B)
=
1-P(A^c\cap B^c)
```

然后直接写成：

```math
1-0.7\times0.7
```

得到 $0.51$。

## Why It Was Wrong

错误发生在：

```math
P(A^c\cap B^c)
=
P(A^c)P(B^c)
```

这一步只有在 $A$ 与 $B$ 独立时才成立。

但题目并没有说 $A,B$ 独立。相反，题目给出的条件可以推出它们互不相容：

“当 $A$ 发生时 $C$ 必然发生”意味着：

```math
A\subseteq C
```

而“$B$ 与 $C$ 互不相容”意味着：

```math
B\cap C=\varnothing
```

由于 $A\subseteq C$，所以：

```math
A\cap B=\varnothing
```

因此 $A$ 与 $B$ 是互不相容事件，而不是独立事件。

## Correct Idea

第（2）问直接用加法公式：

```math
P(A\cup B)
=
P(A)+P(B)-P(A\cap B)
```

因为：

```math
P(A\cap B)=0
```

所以：

```math
P(A\cup B)
=
0.3+0.3
=
0.6
```

## Key Distinction

### 互不相容

```math
A\cap B=\varnothing
```

意味着两个事件不能同时发生。

### 独立

```math
P(A\cap B)=P(A)P(B)
```

意味着一个事件是否发生不影响另一个事件的概率。

当 $P(A)>0$、$P(B)>0$ 时，两个互不相容事件不可能独立。

## Trigger

以后看到：

```math
P(A^c\cap B^c)
=
P(A^c)P(B^c)
```

或者任何“交概率 = 两个概率直接相乘”的写法时，先问：

> 题目真的给了独立吗？或者我已经证明它们独立了吗？

不要仅仅因为两个事件名字不同，就默认可以相乘。

## Exam Warning

“互不相容”和“独立”是概率论前期最容易混淆的两个概念：

- 互不相容：不能一起发生；
- 独立：可以一起发生，只是彼此不影响。

## Personal Summary｜个人总结

我这次看到“至少一个发生”，先想到用补事件，这是没有问题的；真正错的是我把 $P(A^c\cap B^c)$ 直接写成了 $0.7\times0.7$，等于默认了 $A,B$ 独立。

以后只要我准备把两个概率直接相乘，就必须先检查“独立”这个条件。这个题里反而能由 $A\subseteq C$ 和 $B\cap C=\varnothing$ 推出 $A\cap B=\varnothing$，所以应该按互不相容来算。
