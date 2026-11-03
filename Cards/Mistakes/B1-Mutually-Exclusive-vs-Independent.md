---
type: mistake
subject: Probability and Mathematical Statistics
topic:
  - Probability of Events
  - Independence
tags:
  - mutually-exclusive
  - independence
  - inclusion-exclusion
  - union
  - complement
difficulty: easy
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-03
---

# B1：互斥与独立的区别——三问完整解答

## Original Problem｜完整原题

B1. 设 $A,B,C$ 为三个随机事件，$P(A)=P(B)=0.3$，$P(C)=0.4$，且当 $A$ 发生时 $C$ 必然发生，$B$ 与 $C$ 互不相容，求：

1. $C$ 发生的同时 $A$ 不发生的概率；
2. $A$ 与 $B$ 至少有一个发生的概率；
3. $A,B,C$ 都不发生的概率。

## First Step｜先翻译题目条件

「当 $A$ 发生时 $C$ 必然发生」表示事件包含：

$$
A\subseteq C
$$

「$B$ 与 $C$ 互不相容」表示两事件不能同时发生：

$$
B\cap C=\varnothing
$$

由于 $A\subseteq C$，且 $B$ 与整个 $C$ 都不相交，自然也与 $A$ 不相交：

$$
A\cap B=\varnothing
$$

**重要关系：** $A$ 在 $C$ 内部，$B$ 在 $C$ 外部，$A$ 和 $B$ 也互斥。因此计算前应先化简集合关系，而不是直接套概率乘法公式。

## Correct Solution｜三问完整解答

### （1）$C$ 发生而 $A$ 不发生

目标是：

$$
P(C\cap A^c)
$$

因为 $A\subseteq C$，所以 $C$ 被分为互不相容的两部分：$A$ 和「$C$ 中不属于 $A$ 的部分」。

$$
C=A\cup(C\cap A^c)
$$

由互不相容事件的可加性：

$$
P(C)=P(A)+P(C\cap A^c)
$$

因此：

$$
\begin{aligned}
P(C\cap A^c)
&=P(C)-P(A)\\
&=0.4-0.3\\
&=\boxed{0.1}
\end{aligned}
$$

**答案：$0.1$。**

### （2）$A$ 与 $B$ 至少一个发生

「至少一个发生」就是并事件 $A\cup B$。根据两事件容斥公式：

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B)
$$

已知 $A\cap B=\varnothing$，因此 $P(A\cap B)=0$：

$$
\begin{aligned}
P(A\cup B)
&=0.3+0.3-0\\
&=\boxed{0.6}
\end{aligned}
$$

**答案：$0.6$。**

**错误提醒：** 不可以把 $P(A^c\cap B^c)$ 直接算成 $0.7\times0.7$，因为题目没有给出 $A,B$ 独立；实际上已证明它们互斥。

### （3）$A,B,C$ 全都不发生

「三个都不发生」是：

$$
P(A^c\cap B^c\cap C^c)
$$

先由德摩根律转成并集的补集：

$$
A^c\cap B^c\cap C^c=(A\cup B\cup C)^c
$$

所以：

$$
P(A^c\cap B^c\cap C^c)=1-P(A\cup B\cup C)
$$

又因 $A\subseteq C$，并集中加入 $A$ 不会增加新部分：

$$
A\cup B\cup C=B\cup C
$$

由于 $B\cap C=\varnothing$，用容斥公式：

$$
\begin{aligned}
P(A\cup B\cup C)
&=P(B\cup C)\\
&=P(B)+P(C)-P(B\cap C)\\
&=0.3+0.4-0\\
&=0.7
\end{aligned}
$$

最终：

$$
\begin{aligned}
P(A^c\cap B^c\cap C^c)
&=1-P(A\cup B\cup C)\\
&=1-0.7\\
&=\boxed{0.3}
\end{aligned}
$$

**答案：$0.3$。**

这一问可以直观地理解为「先算至少一个发生，再用 $1$ 减掉」。这并非严格意义上将容斥公式倒过来，而是**德摩根律 + 补事件公式 + 容斥公式**的组合。

### Answers｜答案汇总

| 小问 | 核心关系 | 答案 |
| --- | --- | --- |
| （1）$C$ 发生而 $A$ 不发生 | $A\subseteq C$ | $\boxed{0.1}$ |
| （2）$A,B$ 至少一个发生 | $A\cap B=\varnothing$ | $\boxed{0.6}$ |
| （3）三个都不发生 | $A\cup B\cup C=B\cup C$ | $\boxed{0.3}$ |

## Context｜本次错误出现在哪里

错误主要发生在第（2）问：看到「至少一个发生」，我想到先求补集：

$$
P(A\cup B)=1-P(A^c\cap B^c)
$$

这一转换**本身正确**。但接下来把交事件概率直接相乘，得到：

$$
1-0.7\times0.7=0.51
$$

错误结果是 $0.51$，正确结果是 $0.6$。

## Wrong Idea & Why｜错误原因

错误步骤：

$$
P(A^c\cap B^c)=P(A^c)P(B^c)
$$

这个等式需要 $A^c$ 与 $B^c$ **独立**（等价于 $A$ 与 $B$ 独立），而本题没有这个条件。

本题由 $A\subseteq C$ 和 $B\cap C=\varnothing$ 推出 $A\cap B=\varnothing$，所以应按**互斥**处理，而不能按**独立**处理。

如果坚持使用补集方法，也可以正确计算：

$$
P(A^c\cap B^c)=1-P(A\cup B)=1-0.6=0.4
$$

于是：

$$
P(A\cup B)=1-0.4=0.6
$$

但这绕了一圈；直接用容斥公式更简洁。

## Key Distinction｜互斥与独立的联系与区别

### 1. 互斥（互不相容）

定义：

$$
A\cap B=\varnothing
$$

含义：$A$ 和 $B$ **不可能同时发生**。因此：

$$
P(A\cap B)=0
$$

从而：

$$
P(A\cup B)=P(A)+P(B)
$$

举例：掷一次骰子，事件「点数为 1」和「点数为 2」互斥。

### 2. 独立

定义：

$$
P(A\cap B)=P(A)P(B)
$$

含义：一个事件是否发生，不改变另一个事件发生的概率（当条件概率有定义时）。

独立时可以将交事件概率相乘；但**独立不表示不能同时发生**。

举例：分别掷两枚公平骰子，「第一枚为 1」和「第二枚为 2」独立，而且可以同时发生。

### 3. 二者究竟是什么关系？

**若 $P(A)>0$ 且 $P(B)>0$，互斥与独立不可能同时成立。**

证明：若互斥，则：

$$
P(A\cap B)=0
$$

若又独立，则：

$$
P(A\cap B)=P(A)P(B)
$$

二者结合必有：

$$
P(A)P(B)=0
$$

这与 $P(A)>0,P(B)>0$ 矛盾。

所以对于两个**概率都大于零**的事件：

- 互斥 $\Longrightarrow$ 不独立；
- 独立 $\Longrightarrow$ 不互斥。

**零概率例外：** 若 $P(A)=0$ 或 $P(B)=0$，则二者一定满足概率独立公式；若同时满足 $A\cap B=\varnothing$，也可以既互斥又独立。例如 $A=\varnothing$ 与任意事件 $B$。

**补事件的独立性：** 若 $A$ 与 $B$ 独立，则 $A^c$ 与 $B^c$ 也独立（$A$ 与 $B^c$、$A^c$ 与 $B$ 同样独立）；反之亦然。但不能在未验证独立时直接使用这一性质。

### 4. 考试快速对照

| 比较项 | 互斥 | 独立 |
| --- | --- | --- |
| 核心判断 | $A\cap B=\varnothing$ | $P(A\cap B)=P(A)P(B)$ |
| 直观含义 | 不能同时发生 | 发生与否不影响对方的概率 |
| 交事件概率 | $0$ | $P(A)P(B)$ |
| 并事件概率 | $P(A)+P(B)$ | $P(A)+P(B)-P(A)P(B)$ |
| 正概率的两个事件能否同时满足两者 | 不可以 | 不可以 |

注意：仅有 $P(A\cap B)=0$ 不能反推集合必然不相交；对于零概率交集，集合仍可能相交。互斥是集合层面的判断，独立是概率层面的判断。

## Trigger｜遇到哪些题目要警惕？

- 出现「$A$ 发生时 $C$ 必发生」：先写 $A\subseteq C$。
- 出现「互不相容」：先写交集为空，不能误写成独立。
- 出现「至少一个发生」：考虑并集及容斥。
- 出现「一个也不发生」：考虑德摩根律及补事件。
- 准备把 $P(X\cap Y)$ 写成 $P(X)P(Y)$ 时：**先证明 $X,Y$ 独立。**

## Exam Warning｜解题优先顺序

**文字条件 $\rightarrow$ 集合关系 $\rightarrow$ 事件化简 $\rightarrow$ 容斥/补集 $\rightarrow$ 数值计算。**

本题中最有价值的化简是：

$$
A\subseteq C,\qquad B\cap C=\varnothing
\quad\Longrightarrow\quad A\cap B=\varnothing
$$

以及：

$$
A\cup B\cup C=B\cup C
$$

不要看到多个事件就机械地套三事件容斥公式；先看是否存在包含关系。

## Personal Summary｜个人总结

我这次看到“至少一个发生”，先想到用补事件，这是没有问题的；真正错的是我把 $P(A^c\cap B^c)$ 直接写成了 $0.7\times0.7$，等于默认了 $A,B$ 独立。

以后只要我准备把两个概率直接相乘，就必须先检查“独立”这个条件。这个题里反而能由 $A\subseteq C$ 和 $B\cap C=\varnothing$ 推出 $A\cap B=\varnothing$，所以应该按互不相容来算。

**本轮新增理解（2026-11-03）：** 我注意到第（3）问可以从「三个都不发生」转为「至少一个发生」的对立事件，联想到「逆向使用容斥公式」。更准确的表达是：先用德摩根律取补，再用包含关系简化并集，最后用容斥求概率。
