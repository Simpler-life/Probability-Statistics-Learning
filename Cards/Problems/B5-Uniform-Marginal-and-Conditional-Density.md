---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic:
  - 二维连续型随机变量
  - 均匀分布
  - 联合密度和条件密度
  - 边际密度分段积分
tags:
  - B5
  - Uniform-Distribution
  - Joint-PDF
  - Conditional-PDF
  - Marginal-PDF
  - Piecewise-Integration
difficulty: hard
exam_priority: high
status: learning
source:
  - 用户提供的 B5 题目截图（教材页码未核实）
related:
  - A18-Continuous-Joint-Density-and-Conditional-Density.md
  - A20-Marginal-Density-on-Curved-Region.md
created: 2026-11-01
updated: 2026-11-01
---

# B5｜已知均匀边际与条件密度，反推联合密度及反向条件概率

## Source

用户提供的 B5 原题截图。以下完整誊写题意和三小问；解题过程单独列出。

## Problem｜完整原题

**B5.** 有一件工作需要甲、乙两人接力完成，完成时间不超过 4 h。设甲先干了 $X$ h，再由乙完成，加起来共用 $Y$ h。若 $X\sim U(1,2)$，给定 $\{X=x\}$ 的条件下，$Y$ 的条件密度函数

```math
f_{Y\mid X}(y\mid x)=
\begin{cases}
\dfrac{2(4-y)}{(3-x)^2}, & x+1\lt y\lt4,\\
0, & \text{其他}.
\end{cases}
```

（1）求 $(X,Y)$ 的联合密度函数 $f(x,y)$ 及 $P(Y\lt3)$；

（2）求 $Y$ 的边际密度函数；

（3）已知两人完成工作共花了 $3$ h，求甲的工作时间不超过 $1.5$ h 的概率。

## Tested Knowledge

- 均匀分布 $U(a,b)$ 的密度。
- 已知 $f_X(x)$ 和 $f_{Y\mid X}(y\mid x)$，利用乘法公式得到 $f(x,y)$。
- 同时满足 $1<x<2$ 和 $x+1<y<4$ 时的联合支持区域。
- 改以 $y$ 为外层变量时，根据 $\min(2,y-1)$ 的切换点 $y=3$ 分段。
- 已知 $Y=3$ 求关于 $X$ 的反向条件密度及概率。

## First Thought｜个人实际疑问

用户询问：“这个 U 是什么记号，还有这道题怎么做”。因此本题着重解释均匀分布记号，以及由条件密度得到联合密度的逆向思路。尚无用户独立解题记录。

## Recognition｜结构辨认

$X\sim U(1,2)$ 表示 $X$ 服从区间 $(1,2)$ 上的**均匀分布**，其边际密度为

```math
f_X(x)=
\begin{cases}
1,&1\lt x\lt2,\\
0,&\text{其他}.
\end{cases}
```

一般地，$X\sim U(a,b)$，则在 $a<x<b$ 内 $f_X(x)=1/(b-a)$，在其他位置密度为 $0$。

原题又给出 $Y\mid X=x$ 的条件密度，其支持范围是 $x+1<y<4$。将它与 $1<x<2$ 合并才是联合支持区域，不可只使用其中一个不等式。

## Correct Solution｜完整解答

### （1）联合密度及 $P(Y<3)$

条件密度满足

```math
f(x,y)=f_{Y\mid X}(y\mid x)f_X(x).
```

因 $f_X(x)=1$（$1<x<2$），联合密度为

```math
\boxed{
f(x,y)=
\begin{cases}
\dfrac{2(4-y)}{(3-x)^2},&1\lt x\lt2,\ x+1\lt y\lt4,\\
0,&\text{其他}.
\end{cases}}
```

要计算 $P(Y<3)$，在上述支持区域上新增 $y<3$。于是

```math
1\lt x\lt2,\qquad x+1\lt y\lt3.
```

注意当 $x=2$ 时下上界会相遇，因此直接在 $x\in(1,2)$ 上先积分 $y$：

```math
\begin{aligned}
P(Y\lt3)
&=\int_1^2\int_{x+1}^3
\frac{2(4-y)}{(3-x)^2}\,dy\,dx\\
&=\int_1^2
\frac{[8y-y^2]_{x+1}^3}{(3-x)^2}\,dx\\
&=\int_1^2\left(1-\frac1{(3-x)^2}\right)dx\\
&=\left[x-\frac1{3-x}\right]_1^2\\
&=\boxed{\frac12}.
\end{aligned}
```

### （2）求 $Y$ 的边际密度 $f_Y(y)$

定义：

```math
f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)\,dx.
```

为固定 $y$ 重新整理支持条件：

```math
1\lt x\lt2,\qquad x\lt y-1.
```

因此 $1<x<\min(2,y-1)$。为使这个区间非空，必须 $y>2$；而原题也有 $y<4$。

**关键分界点是 $y=3$，因为此处 $y-1=2$，约束 $x<y-1$ 与 $x<2$ 的强弱发生切换。**

- 当 $2<y<3$：$y-1<2$，积分上限是 $y-1$。
- 当 $3\le y<4$：$y-1\ge2$，积分上限是 $2$。

第一段：

```math
\begin{aligned}
f_Y(y)
&=\int_1^{y-1}\frac{2(4-y)}{(3-x)^2}\,dx\\
&=2(4-y)\left[\frac1{3-x}\right]_1^{y-1}\\
&=2(4-y)\left(\frac1{4-y}-\frac12\right)\\
&=y-2,\qquad 2\lt y\lt3.
\end{aligned}
```

第二段：

```math
\begin{aligned}
f_Y(y)
&=\int_1^2\frac{2(4-y)}{(3-x)^2}\,dx\\
&=2(4-y)\left[\frac1{3-x}\right]_1^2\\
&=4-y,\qquad 3\le y\lt4.
\end{aligned}
```

因此：

```math
\boxed{
f_Y(y)=
\begin{cases}
y-2,&2\lt y\lt3,\\
4-y,&3\le y\lt4,\\
0,&\text{其他}.
\end{cases}}
```

校验：$f_Y(y)$ 是以 $(2,0)$、$(3,1)$、$(4,0)$ 为顶点的三角形密度，其面积为 $2\times1/2=1$。由此还可重新验证

```math
P(Y\lt3)=\int_2^3(y-2)\,dy=\frac12.
```

### （3）已知总时间 $Y=3$，求 $P(X\le1.5\mid Y=3)$

这时需要反向的条件密度：

```math
f_{X\mid Y}(x\mid y)=\frac{f(x,y)}{f_Y(y)}
```

条件值 $y=3$ 时，第二问给出 $f_Y(3)=1$。联合支持区域要求 $1<x<2$，故

```math
f_{X\mid Y}(x\mid3)
=\frac{2(4-3)}{(3-x)^2}\cdot\frac1{f_Y(3)}
=\frac2{(3-x)^2},\qquad 1\lt x\lt2.
```

所求条件概率：

```math
\begin{aligned}
P(X\le1.5\mid Y=3)
&=\int_1^{1.5}\frac2{(3-x)^2}\,dx\\
&=2\left[\frac1{3-x}\right]_1^{1.5}\\
&=2\left(\frac23-\frac12\right)\\
&=\boxed{\frac13}.
\end{aligned}
```

## Key Formula｜通用逻辑链

```math
f_X(x)+f_{Y\mid X}(y\mid x)
\quad\Longrightarrow\quad
f(x,y)=f_X(x)f_{Y\mid X}(y\mid x)
```

```math
f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)\,dx
```

```math
f_{X\mid Y}(x\mid y)=\frac{f(x,y)}{f_Y(y)}
\qquad\text{（仅当 }f_Y(y)\gt0\text{）}.
```

最后把已知 $y$ 代入条件密度，对 $x$ 在所求事件内积分。对连续型的零概率单点条件 $Y=3$，此处的条件分布通过条件密度定义，不能套离散型条件概率的商式。

## Calculation Skeleton｜考试步骤

1. 由 $X\sim U(1,2)$ 写出 $f_X(x)=1$（$1<x<2$）。
2. 通过 $f=f_Xf_{Y\mid X}$ 求联合密度，且**取两个支持条件的交集**。
3. 求 $P(Y<3)$ 时给支持区域新增 $y<3$，画图或解不等式确定积分限。
4. 求 $f_Y(y)$ 时保留 $y$，对 $x$ 积分；上界为 $\min(2,y-1)$，务必**在 $y=3$ 处分段**。
5. 求反向条件概率时：计算 $f_Y(3)$、写 $f_{X\mid Y}(x\mid3)$、按目标区间积分。

## Mistake｜常见易错点

- 误解 $U(1,2)$，不知道均匀密度是 $1/(2-1)=1$。
- 求联合密度时只写 $x+1<y<4$，漏掉 $1<x<2$。
- 求 $f_Y(y)$ 时不分段，从头到尾使用同一积分上限。
- 忘记密度只在 $2<y<4$ 非零。
- 条件已从 $X$ 换为 $Y$，却仍直接使用 $f_{Y\mid X}$ 而不计算反向条件密度。

## Transfer｜与 A18、A20 对照

- A18、A20 由联合密度积分求边际、再除得条件密度。
- B5 先给出一个边际密度和一个条件密度，需相乘还原联合密度，再积分求另一边际密度，最后反向求条件概率。
- A20 的分界来自曲线不等式，B5 的分界来自两个上界 $2$ 和 $y-1$ 的交替起作用。

## Personal Summary｜个人总结

- 用户真实提问：“这个 U 是什么记号，还有这道题怎么做”。
- 这次首先要识别 $U(1,2)$ 是均匀分布，进而知道 $f_X(x)=1$；这是展开整道题的入口。
- 第二问的重点是：当求 $f_Y(y)$ 时固定 $y$，允许的 $x$ 满足 $1<x<\min(2,y-1)$，在 $y=3$ 切换积分上限。
- 尚未收到用户独立重做的结果，因此不记录为已掌握。下次优先检查是否能独立解释为什么在 $y=3$ 处分段。
