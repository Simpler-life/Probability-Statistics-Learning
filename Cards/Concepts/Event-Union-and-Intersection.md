---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 1
topic: [Events, Event Operations]
tags: [event-sum, event-product, union, intersection, independence, mutual-exclusion]
difficulty: easy
exam_priority: high
status: learning
source: [2026-11-01 ChatGPT 学习讨论]
related: [Independent-Events-Disjoint-Group-Operations.md]
created: 2026-11-01
updated: 2026-11-01
---

# 和事件、积事件与集合交并运算

## One Sentence

**和事件就是并事件，积事件就是交事件**；事件的和与积是集合运算，不是数值加减乘除。

## Definition

- **和事件**：$A+B$（部分教材记法）或 $A\cup B$，表示 $A,B$ 至少一个发生；也包括两者同时发生。
- **积事件**：$AB$ 或 $A\cap B$，表示 $A,B$ 同时发生。
- 补事件：$\overline A$，表示 $A$ 不发生。

## Intuition｜直觉

并集将两个事件覆盖的样本点都纳入；交集只保留共同样本点。

## Why

识别题目中“至少一个”“同时”“都不发生”等语言，正确转成事件运算与概率公式。

## Key Formula

一般情况下，容斥公式为：

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B).
$$

当 $A,B$ **相互独立**时：

$$
P(A\cap B)=P(A)P(B).
$$

因此：

$$
P(A\cup B)=P(A)+P(B)-P(A)P(B).
$$

当 $A,B$ **互斥**时，$A\cap B=\varnothing$，所以：

$$
P(A\cup B)=P(A)+P(B).
$$

## Conditions

- 容斥公式对任何两个事件成立。
- 交事件概率等于概率乘积须有独立性条件。
- 和事件概率等于概率之和须有互斥条件（或 $P(A\cap B)=0$）。

## Typical Example

掷一次公平骰子，设 $A=\{2,4,6\}$（出现偶数），$B=\{4,5,6\}$（大于 3）。

$$
A\cap B=\{4,6\},\qquad A\cup B=\{2,4,5,6\}.
$$

于是 $P(A\cap B)=2/6$，$P(A\cup B)=4/6$。

## Exam Focus

先分辨事件关系，再选择公式：一般用容斥；独立时交事件可乘；互斥时和事件可直接相加。

## Common Traps

- $A+B$ 是并事件的记号，不表示概率可以直接相加。
- $AB$ 是交事件的记号，不表示概率总是可以直接相乘。
- “独立”与“互斥”不能混淆；概率均大于零的两个互斥事件不可能独立。

## Related

- [相互独立事件的非交叉分组运算](Independent-Events-Disjoint-Group-Operations.md)

## My Questions

- 用户问：“积事件和和事件与交和并有什么关系”。
- 尚未通过独立练习检验是否已经熟练区分条件。

## Personal Summary｜个人总结

- 用户提出的真实疑问：“积事件和和事件与交和并有什么关系”。
- 本轮需要消除的术语疑惑：**积事件对应交，和事件对应并**。
- 未将疑惑虚构成一次已做错的题目，也未擅自断言用户完全掌握。
