---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 1
topic: [Random Variables, Event Notation]
tags: [probability-notation, random-variable, set-membership, discrete-events]
difficulty: easy
exam_priority: medium
status: learning
source: [2026-11-07 ChatGPT 学习讨论]
related: [Event-Union-and-Intersection.md]
created: 2026-11-07
updated: 2026-11-07
---

# 随机变量取多个指定值的概率如何表示

## One Sentence

想表达“随机变量 $X$ 取 $1,2,3$ 中任意一个值”，规范写法是 **$P(X\in\{1,2,3\})$**，而不是含义不明确的 $P(X=1,2,3)$。

## Definition

事件 $\{X\in\{1,2,3\}\}$ 意味着 $X=1$、$X=2$、$X=3$ 三种情况中至少一种发生；它们是同一个随机变量取不同值的互斥事件。

## Intuition｜直觉

- $=$ 表示等于一个指定值：$P(X=1)$。
- $\in$ 表示属于一个集合：$P(X\in\{1,2,3\})$。
- 逗号直接放在等号右侧不能清楚地定义这一事件，因此 $P(X=1,2,3)$ **不属于规范的概率事件写法**。

## Why

避免在列举多个可能取值时，把事件表示、区间表示和概率相加混为一谈，尤其是在考试书面解答中。

## Key Formula

$$
P(X\in\{1,2,3\})
=P(X=1\lor X=2\lor X=3)
=P(X=1)+P(X=2)+P(X=3).
$$

最后一步成立，因为 $\{X=1\}$、$\{X=2\}$、$\{X=3\}$ 两两互斥。

## Conditions

$$
\{X\in\{1,2,3\}\}\subseteq\{1\le X\le 3\}.
$$

通常 **不能** 直接写 $P(X\in\{1,2,3\})=P(1\le X\le3)$；只有当 $P(X\in(1,2)\cup(2,3))=0$ 时，二者才相等。例如整数值随机变量满足这一条件；连续取值的随机变量一般不满足。

## Key Mechanism

将“取多个离散值”改写为多个互斥事件的并，再利用有限可加性求和。

## Typical Example

假设 $X$ 是掷一次公平骰子的点数，则

$$
P(X\in\{1,2,3\})=\frac16+\frac16+\frac16=\frac12.
$$

在这个例子中，$P(1\le X\le3)$ 也等于 $1/2$，因为骰子点数只能取整数。

## Exam Focus

| 写法 | 是否规范 | 含义 |
| --- | --- | --- |
| $P(X=1,2,3)$ | 否 | 事件定义不清晰 |
| $P(X\in\{1,2,3\})$ | 是 | $X$ 为三个值之一 |
| $P(X=1)+P(X=2)+P(X=3)$ | 是 | 三个互斥事件概率之和 |
| $P(1\le X\le3)$ | 是 | $X$ 落在闭区间 $[1,3]$ 内，可能包含其他值 |

## Common Traps

- **集合不等于区间**：如果 $X$ 可以取 $1.5$ 或 $2.5$，那么 $1\le X\le3$ 可能包含更多事件。
- **逗号不是逻辑或**：不要用 $P(X=1,2,3)$ 代替集合成员关系。
- **互斥才可以直接相加**：这里三种取值互斥；一般事件的并集概率需要考虑交集。

## Related

- [和事件、积事件与集合交并运算](Event-Union-and-Intersection.md)

## My Questions

- 用户原始提问：“P(X=1,2,3)这种写法是合法的吗？”

## Personal Summary｜个人总结

- 本次确认：写多个指定取值时，改成 $P(X\in\{1,2,3\})$ 更规范。
- 需要特别区分“取几个指定值”和“落在一个连续区间内”。
- 尚未通过独立练习确认是否完全掌握。
