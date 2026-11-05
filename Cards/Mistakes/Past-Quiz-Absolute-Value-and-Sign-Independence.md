---
type: mistake
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Independence, Conditional Distribution, Absolute Value, Sign Indicator]
tags: [past-quiz, independence, conditional-CDF, sign-and-magnitude, final-review-priority]
difficulty: medium
exam_priority: high
status: review
source: [2026-11-05 第二套历年小测第5问及独立性专项追问]
created: 2026-11-05
updated: 2026-11-05
---

# 历年小测第二套第（5）问：绝对值与符号是否独立

## Original Problem｜原题

二维随机变量 $(X,Y)$ 的联合密度为：

~~~math
f_{X,Y}(x,y)=
\begin{cases}
cx^2y,&x^2\lt y\lt 1,\\
0,&\text{其他}.
\end{cases}
~~~

前面小问已求得：

~~~math
c=\frac{21}{4},
\qquad
f_X(x)=
\begin{cases}
\frac{21}{8}(x^2-x^6),&-1\lt x\lt1,\\
0,&\text{其他}.
\end{cases}
~~~

令：

~~~math
\xi=
\begin{cases}
1,&X\gt0,\\
0,&X\le0,
\end{cases}
\qquad
Z=
\begin{cases}
X,&X\gt0,\\
-X,&X\le0.
\end{cases}
~~~

即 $Z=|X|$，判断 $Z$ 与 $\xi$ 是否独立，并说明理由。

## First Attempt & Actual Difficulty｜本轮实际困惑

- 第（1）至第（4）问独立求解正确，第（5）问独立性证明没有建立稳定的方法。
- 用户先询问怎么判断独立性，又追问：**“这只是 $Z\le z$ 这个概率在等于 1 或 0 时都不变，怎么能直接就这样过了？”**
- 真正需要区分：**只验证一个固定 $z$ 远远不够；验证对所有实数 $z$ 和 $\xi$ 的所有可能取值都成立，才足以证明独立。**
- 本卡专门归档该独立性小问，不将整套卷重复保存。

## Core Idea｜为什么“分布不变”就能证明独立

$Z=|X|$ 是大小，$\xi$ 是符号。由 $f_X(-x)=f_X(x)$，可知 $X$ 的分布关于零对称。

~~~math
P(\xi=1)=P(X\gt0)=\frac12,
\qquad P(\xi=0)=\frac12.
~~~

要证明 $Z$ 与 $\xi$ 独立，一种等价方法是验证：

~~~math
P(Z\le z\mid \xi=i)=F_Z(z)
\quad\text{对所有实数 }z\text{ 及 }i=0,1.
~~~

这不是只检查一个概率值，而是在检查**整个条件分布函数**；因为分布函数对所有阈值的值决定整个概率分布。

## Standard Solution｜可直接模仿的考试证明

当 $0\le z\lt1$ 时：

~~~math
F_Z(z)=P(|X|\le z)
=P(-z\le X\le z)
=2\int_0^z f_X(x)\,dx.
~~~

因此：

~~~math
F_Z(z)=
\begin{cases}
0,&z\lt0,\\
\frac74z^3-\frac34z^7,&0\le z\lt1,\\
1,&z\ge1.
\end{cases}
~~~

当 $\xi=1$（即 $X\gt0$）时，对所有 $0\le z\lt1$：

~~~math
P(Z\le z\mid \xi=1)
=\frac{P(0\lt X\le z)}{P(X\gt0)}
=2\int_0^z f_X(x)\,dx
=F_Z(z).
~~~

当 $\xi=0$（即 $X\le0$）时：

~~~math
P(Z\le z\mid \xi=0)
=\frac{P(-z\le X\le0)}{P(X\le0)}
=2\int_{-z}^{0}f_X(x)\,dx
=2\int_0^z f_X(x)\,dx
=F_Z(z).
~~~

此外，$z\lt0$ 时以上条件分布函数都为 $0$；$z\ge1$ 时都为 $1$。所以对每一个实数 $z$，以及 $i\in\{0,1\}$，均有：

~~~math
P(Z\le z\mid\xi=i)=F_Z(z).
~~~

据此，$Z$ 的分布不因已知 $\xi$ 的取值而改变，故：

~~~math
\boxed{Z\text{ 与 }\xi\text{ 相互独立}.}
~~~

## Why This Is Sufficient｜与联合分布定义的联系

从条件概率公式，对于 $i=0,1$：

~~~math
P(Z\le z,\xi=i)
=P(Z\le z\mid\xi=i)P(\xi=i)
=F_Z(z)P(\xi=i).
~~~

又因为 $\xi$ 只取 $0$、$1$，任意阈值 $t$ 的事件 $\{\xi\le t\}$ 只有三种情形：空集（$t\lt0$）、$\{\xi=0\}$（$0\le t\lt1$）、全集（$t\ge1$）。于是对所有 $z,t$：

~~~math
F_{Z,\xi}(z,t)=F_Z(z)F_\xi(t),
~~~

这正是随机变量独立性的定义。**一个固定 $z$ 的等式不够，必须是所有 $z$。**

## Exam Checklist｜考试中的判断顺序

1. **明确要判断的两个随机变量是谁**：本题是 $Z$ 与 $\xi$，不是 $X$ 与 $Y$。
2. 识别 $Z=|X|$、$\xi$ 为正负号指示变量，并检查 $f_X$ 是否关于 0 对称。
3. 先写 $F_Z(z)$ 的完整分段，注意左 $0$、右 $1$。
4. 对 $\xi=0$ 与 $\xi=1$ 两种情况，分别计算 $P(Z\le z\mid \xi=i)$。
5. **不能只检验一个 $z$**；必须说明对所有 $z$ 都相同。
6. 不可以仅凭“两个随机变量都由 $X$ 构造”断言不独立。

## Open-Book Reference

教材 §3.4「随机变量的独立性」：联合分布函数可分解为边际分布函数的充要条件；同时回看 §2.5 随机变量函数的分布。

## Final Review｜迁移题

- 独立复述上述证明，尤其说清楚为什么对所有 $z$ 与 $\xi=0,1$ 的验证已经足够。
- 换为非对称的 $X\sim U(-1,2)$，仍定义 $Z=|X|$ 和 $\xi=\mathbf 1_{\{X\gt0\}}$，检查是否仍然独立（不要仅凭相同构造方式下结论）。

## Personal Summary｜个人总结

我这次最大的困惑不是计算某个积分，而是觉得“只证明 $P(Z\le z)$ 在条件下不变，凭什么就能认定独立”。真正要抓住的是：**要对每个 $z$ 都成立，而不是一个特定 $z$；并且 $\xi$ 只有两个取值，两个条件情况都要覆盖。**以后证明独立时先核对量词是否完整。
