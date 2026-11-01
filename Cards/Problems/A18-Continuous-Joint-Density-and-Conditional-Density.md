---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic:
  - 二维连续型随机变量
  - 边际密度函数
  - 条件密度函数
tags:
  - A18
  - Joint-PDF
  - Marginal-PDF
  - Conditional-PDF
  - Conditional-Notation
difficulty: medium
exam_priority: high
status: learning
source:
  - 用户提供的 A18 题目截图（具体教材页码未核实）
related:
  - A12-Joint-Distribution-from-Marginal-CDFs.md
created: 2026-11-01
updated: 2026-11-01
---

# A18｜由联合密度求边际密度、条件密度与条件概率

## Source

用户提供的 A18 截图。以下完整誊写原题的文字、函数及三个小问。

## Problem｜完整原题

**A18.** 设二维连续型随机变量 $(X,Y)$ 的联合密度函数为

$$
f(x,y)=
\begin{cases}
\dfrac{2x+y}{4}, & 0<x<1,\ 0<y<2,\\
0, & \text{其他}.
\end{cases}
$$

（1）分别求 $X$ 与 $Y$ 的边际密度函数；

（2）分别求条件密度函数 $f_{X\mid Y}(x\mid y)$ 和 $f_{Y\mid X}(y\mid x)$；

（3）分别求 $P(X\le 0.5\mid Y=0.5)$ 和 $P(Y\le 0.5\mid X=0.5)$。

## Tested Knowledge

- 对联合密度的有效区域积分，求边际密度。
- 用联合密度除以条件变量的边际密度求条件密度。
- 在条件密度中代入已知条件，然后对所求变量积分。
- 识别记号 $f_{X\mid Y}(x\mid y)$、$F_{X\mid Y}(x\mid y)$ 与 $F_{X\mid Y=0}(x)$ 的含义。

## Recognition｜识别思路

联合密度非零区域为矩形 $0<x<1,\ 0<y<2$。求 $X$ 的边际密度时对 $y$ 积分；求 $Y$ 的边际密度时对 $x$ 积分。求条件密度时，分母用“被给定条件”的变量的边际密度。

## First Thought｜真实疑问

用户特别问：“为什么这里老师的写法里还有 $(x\mid y)$，我看之前那道题最后的结果里也有 $(x\mid0)$ 这种形式”，随后归纳：“所以老师一般不是写 $Y=0$ 而是放在括号里写竖线”。

## Attempt

未提供独立书面解题尝试，暂不虚构。

## Correct Solution｜完整过程

### （1）边际密度函数

由联合密度定义，$X$ 的边际密度是沿 $y$ 方向积分：

$$
\begin{aligned}
f_X(x)
&=\int_{-\infty}^{+\infty}f(x,y)\,dy\\
&=\int_0^2\frac{2x+y}{4}\,dy\\
&=\frac14\left[2xy+\frac{y^2}{2}\right]_0^2\\
&=x+\frac12,\qquad 0<x<1.
\end{aligned}
$$

因此：

$$
\boxed{f_X(x)=
\begin{cases}
x+\frac12,&0<x<1,\\
0,&\text{其他}.
\end{cases}}
$$

类似地，$Y$ 的边际密度是沿 $x$ 方向积分：

$$
\begin{aligned}
f_Y(y)
&=\int_{-\infty}^{+\infty}f(x,y)\,dx\\
&=\int_0^1\frac{2x+y}{4}\,dx\\
&=\frac14[x^2+xy]_0^1\\
&=\frac{1+y}{4},\qquad 0<y<2.
\end{aligned}
$$

所以：

$$
\boxed{f_Y(y)=
\begin{cases}
\dfrac{1+y}{4},&0<y<2,\\
0,&\text{其他}.
\end{cases}}
$$

校验：

$$
\int_0^1\left(x+\frac12\right)\,dx=1,
\qquad
\int_0^2\frac{1+y}{4}\,dy=1.
$$

### （2）条件密度函数

若 $f_Y(y)>0$，则

$$
f_{X\mid Y}(x\mid y)=\frac{f(x,y)}{f_Y(y)}.
$$

代入 $f_Y(y)=(1+y)/4$，得到：

$$
\boxed{
f_{X\mid Y}(x\mid y)=
\begin{cases}
\dfrac{2x+y}{1+y},&0<x<1,\quad 0<y<2,\\
0,&\text{其他 }x,\quad 0<y<2.
\end{cases}}
$$

这里条件变量 $y$ 只考虑 $0<y<2$；当 $f_Y(y)=0$ 时，不应直接用密度比值公式求条件密度。

若 $f_X(x)>0$，则

$$
f_{Y\mid X}(y\mid x)=\frac{f(x,y)}{f_X(x)}.
$$

代入 $f_X(x)=x+1/2$，得到：

$$
\boxed{
f_{Y\mid X}(y\mid x)=
\begin{cases}
\dfrac{2x+y}{4x+2},&0<y<2,\quad 0<x<1,\\
0,&\text{其他 }y,\quad 0<x<1.
\end{cases}}
$$

验证对每个有效条件值积分为 $1$：

$$
\int_0^1\frac{2x+y}{1+y}\,dx
=\frac{1+y}{1+y}=1,
$$

$$
\int_0^2\frac{2x+y}{4x+2}\,dy
=\frac{4x+2}{4x+2}=1.
$$

### （3）条件概率

先计算 $P(X\le0.5\mid Y=0.5)$。

由上一问，固定 $y=0.5$：

$$
f_{X\mid Y}(x\mid0.5)
=\frac{2x+0.5}{1.5}
=\frac{4x+1}{3},
\qquad 0<x<1.
$$

因此：

$$
\begin{aligned}
P(X\le0.5\mid Y=0.5)
&=\int_0^{0.5}f_{X\mid Y}(x\mid0.5)\,dx\\
&=\int_0^{0.5}\frac{4x+1}{3}\,dx\\
&=\frac13[2x^2+x]_0^{0.5}\\
&=\boxed{\frac13}.
\end{aligned}
$$

再计算 $P(Y\le0.5\mid X=0.5)$。

固定 $x=0.5$：

$$
f_{Y\mid X}(y\mid0.5)
=\frac{1+y}{4},\qquad 0<y<2.
$$

故：

$$
\begin{aligned}
P(Y\le0.5\mid X=0.5)
&=\int_0^{0.5}f_{Y\mid X}(y\mid0.5)\,dy\\
&=\int_0^{0.5}\frac{1+y}{4}\,dy\\
&=\frac14\left[y+\frac{y^2}{2}\right]_0^{0.5}\\
&=\boxed{\frac5{32}}.
\end{aligned}
$$

**注意：** 连续型随机变量在单点 $Y=0.5$ 处通常满足 $P(Y=0.5)=0$，不能将离散型的普通条件概率商式直接用于这一零概率事件。此处通过条件密度（联合密度除以边际密度）定义适当版本的条件分布。

## Key Notation｜老师为什么写 $(x\mid y)$？

**条件密度：**

$$
f_{X\mid Y}(x\mid y)
$$

表示“已知 $Y=y$ 的条件下，$X$ 在 $x$ 处的条件密度”。其中 $x$ 是被研究的取值，$y$ 是条件值；竖线表示“在……条件下”，不是除号。

**条件分布函数：**

$$
F_{X\mid Y}(x\mid y)=P(X\le x\mid Y=y).
$$

上式作为事件条件概率的普通定义适用于 $P(Y=y)>0$ 的情况；若 $Y$ 连续且单点概率为零，则使用由条件密度得到的条件分布函数：

$$
F_{X\mid Y}(x\mid y)
=\int_{-\infty}^{x} f_{X\mid Y}(t\mid y)\,dt.
$$

**条件值固定为 $0$ 时，两种常用记法：**

$$
F_{X\mid Y=0}(x)
\quad\text{与}\quad
F_{X\mid Y}(x\mid0)
$$

二者表示同一条件分布函数。老师常把“给定的取值”写在括号的竖线右侧，因而 A12 的最终答案也可写作 $F_{X\mid Y}(x\mid0)$。离散与连续均可用此类记法。下标标明“研究谁、条件是谁”，括号标明“具体取值”。

## Calculation Skeleton｜可复用解题模板

1. 标明联合密度的非零区域及 $x,y$ 取值范围。
2. $f_X(x)=\int f(x,y)\,dy$，$f_Y(y)=\int f(x,y)\,dx$。
3. $f_{X\mid Y}(x\mid y)=f(x,y)/f_Y(y)$，$f_{Y\mid X}(y\mid x)=f(x,y)/f_X(x)$，仅在对应分母为正的条件值上使用。
4. 将已给定的条件值代入条件密度。
5. 对被研究变量在目标区间上积分；积分限取该变量的支持集与所求事件区间的交。

## Mistake｜易错点

- 将 $f_{X\mid Y}(x\mid y)$ 中的竖线当成除号。
- 已知 $Y=y$ 却误除以 $f_X(x)$。
- 误将连续情形的 $P(Y=y)=0$ 作为普通分母，导致 $0/0$。
- 条件密度求出后，未代入具体条件值或对错误的变量积分。
- 忽略密度非零区域及分母非零条件。

## Transfer｜与 A12 对比

- A12（离散型）由边际分布函数的跳跃得到边际概率，借助表格求联合分布律，再将条件分布律**求和**为条件分布函数。
- A18（连续型）由联合密度**积分**得边际密度，借助密度商式求条件密度，再将条件密度**积分**成条件概率。
- 两种题均可使用 $F_{X\mid Y}(x\mid y)$ 这一记法，区别在于计算方式与条件的适用定义。

## Similar Problems

- A12｜由边际分布函数求二维离散型联合分布律与条件分布函数。

## Personal Summary｜个人总结

- 真实问题：“为什么这里老师的写法里还有 $(x\mid y)$，我看之前那道题最后的结果里也有 $(x\mid0)$ 这种形式”。
- 进一步归纳：“所以老师一般不是写 $Y=0$ 而是放在括号里写竖线”。
- 当前记录：认识到固定条件既可以写在下标 $F_{X\mid Y=0}(x)$，也可以写在括号 $F_{X\mid Y}(x\mid0)$；一般条件可以保留 $y$。这属于记号理解，不能据此推断已独立掌握全部积分计算。
- 复习时重点：分清 $f$（密度）和 $F$（分布函数），以及条件分母对应的变量。
