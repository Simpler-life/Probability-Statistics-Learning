---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic:
  - 二维连续型随机变量
  - 边际密度函数
  - 条件密度函数
  - 非矩形积分区域
tags:
  - A20
  - Joint-PDF
  - Marginal-PDF
  - Conditional-PDF
  - Integration-Region
difficulty: medium
exam_priority: high
status: learning
source:
  - 用户提供的 A20 题目截图（教材页码未核实）
related:
  - A18-Continuous-Joint-Density-and-Conditional-Density.md
created: 2026-11-01
updated: 2026-11-01
---

# A20｜曲线区域上的边际密度、条件密度与条件概率

## Source

用户提供的 A20 原题截图。以下完整誊写题目与三问。

## Problem｜完整原题

**A20.** 设二维连续型随机变量 $(X,Y)$ 的联合密度函数为

```math
f(x,y)=
\begin{cases}
\dfrac54 x, & y^2\lt x\lt 1,\\
0, & \text{其他}.
\end{cases}
```

（1）求 $Y$ 的边际密度函数 $f_Y(y)$；

（2）求条件密度函数 $f_{X\mid Y}(x\mid y)$；

（3）求 $P(X>\frac12\mid Y=\frac12)$。

## Tested Knowledge

- 将联合密度的支持区域 $D=\{(x,y):y^2<x<1\}$ 转换为积分限。
- 求边际密度：保留哪个变量，就对另一个变量积分。
- 用联合密度与条件变量的边际密度之比求条件密度。
- 固定条件值后，取事件区间与支持区间的交集积分。

## Recognition｜积分区域首先分析

条件 $y^2<x<1$ 表明：$0<x<1$，并且 $-\sqrt{x}<y<\sqrt{x}$；也等价于 $-1<y<1$，并且 $y^2<x<1$。

因此：

- 固定 $y$，水平切片的积分限：$x$ 从 $y^2$ 到 $1$（要求 $-1<y<1$）。
- 固定 $x$，竖直切片的积分限：$y$ 从 $-\sqrt{x}$ 到 $\sqrt{x}$（要求 $0<x<1$）。

## First Thought｜个人真实问题

用户在 A20 中明确要求：“这道题呢，总结一下边际密度函数的求法。”学习重点是从非矩形区域确定边际密度的积分限。

## Attempt

目前没有用户独立手写的计算过程，不虚构尝试或错误。

## Correct Solution｜完整解答

### （1）求 $Y$ 的边际密度

对 $x$ 积分，保留 $y$：

```math
f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)\,dx.
```

当 $-1<y<1$ 时，有 $y^2<x<1$，故：

```math
\begin{aligned}
f_Y(y)
&=\int_{y^2}^1\frac54 x\,dx\\
&=\frac54\left[\frac{x^2}{2}\right]_{y^2}^1\\
&=\frac58(1-y^4).
\end{aligned}
```

最终：

```math
\boxed{
f_Y(y)=
\begin{cases}
\dfrac58(1-y^4), & -1\lt y\lt 1,\\
0, & \text{其他}.
\end{cases}
}
```

检查归一化：

```math
\int_{-1}^1\frac58(1-y^4)\,dy
=\frac58\left(2-\frac25\right)=1.
```

### （2）求 $X$ 关于 $Y=y$ 的条件密度

在 $-1<y<1$ 时，$f_Y(y)>0$，可以使用：

```math
f_{X\mid Y}(x\mid y)=\frac{f(x,y)}{f_Y(y)}.
```

代入第一问结果：

```math
\frac{\frac54x}{\frac58(1-y^4)}
=\frac{2x}{1-y^4}.
```

因此：

```math
\boxed{
f_{X\mid Y}(x\mid y)=
\begin{cases}
\dfrac{2x}{1-y^4}, & y^2\lt x\lt1,\ -1\lt y\lt1,\\
0, & \text{其他 }x\text{（给定 }-1\lt y\lt1\text{）}.
\end{cases}
}
```

校验（给定有效 $y$）：

```math
\int_{y^2}^1\frac{2x}{1-y^4}\,dx
=\frac{1-y^4}{1-y^4}=1.
```

### （3）计算 $P(X>\frac12\mid Y=\frac12)$

条件 $Y=\frac12$ 对应 $y^2=\frac14$，故 $X$ 的支持区间为 $\frac14<x<1$。再结合事件 $X>\frac12$，实际积分限为 $\frac12<x<1$。

代入条件密度：

```math
f_{X\mid Y}\left(x\mid\frac12\right)
=\frac{2x}{1-(\frac12)^4}
=\frac{32x}{15},\quad \frac14\lt x\lt 1.
```

所以：

```math
\begin{aligned}
P\left(X\gt\frac12\mid Y=\frac12\right)
&=\int_{\frac12}^1\frac{32x}{15}\,dx\\
&=\frac{16}{15}\left[x^2\right]_{\frac12}^1\\
&=\frac{16}{15}\left(1-\frac14\right)\\
&=\boxed{\frac45}.
\end{aligned}
```

## Calculation Skeleton｜边际密度函数通法

**核心口诀：求谁的边际密度，就留下谁，对另一个变量积分。积分限由联合密度的非零区域决定。**

| 目标 | 固定哪个变量 | 积掉哪个变量 | 本题积分区间 |
| --- | --- | --- | --- |
| $f_Y(y)$ | $y$ | $x$ | $y^2<x<1$，$-1<y<1$ |
| $f_X(x)$ | $x$ | $y$ | $-\sqrt{x}<y<\sqrt{x}$，$0<x<1$ |

一般公式：

```math
f_X(x)=\int_{-\infty}^{+\infty}f(x,y)\,dy,
\qquad
f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)\,dx.
```

标准作答顺序：

1. **画或分析支持区域** $D=\{(x,y):f(x,y)\ne0\}$。
2. **确定保留变量的范围**（本题 $Y$ 的范围是 $-1<y<1$）。
3. **固定保留变量，寻找积分变量的上下限**。
4. **积分并写成分段函数**，支持区域外密度为 $0$。
5. **校验**边际密度在其支持区间的积分是否为 $1$。

### 与 A18 的区别

A18 是矩形区域 $0<x<1,0<y<2$，所以求 $f_Y(y)$ 时积分上下限是常数 $0$ 到 $1$。

A20 是曲线区域 $y^2<x<1$，所以求 $f_Y(y)$ 时，积分下限是随 $y$ 变化的 $y^2$，上限是 $1$。

**易混点：** 积分上下限可以包含未被积掉的变量。例如 $\int_{y^2}^1 f(x,y)\,dx$ 合法，因为此时 $y$ 当作固定参数。

## Key Formula｜适用条件

对于具有联合密度的二维连续型随机变量，可通过对另一变量积分得到边际密度。在条件变量的边际密度为正的地方，条件密度由联合密度除以条件变量的边际密度得到。对连续型条件 $Y=y$（单点概率为零）不直接使用除以 $P(Y=y)$ 的普通事件概率商式。

## Transfer｜迁移与练习

如果本题改成求 $f_X(x)$，要先将 $y^2<x$ 改写成 $-\sqrt{x}<y<\sqrt{x}$，再对 $y$ 积分：

```math
f_X(x)=
\begin{cases}
\displaystyle\int_{-\sqrt{x}}^{\sqrt{x}}\frac54x\,dy
=\frac52x^{3/2},&0\lt x\lt1,\\
0,&\text{其他}.
\end{cases}
```

这是额外迁移练习，并非 A20 原题要求的小问。

## Personal Summary｜个人总结

- 用户本轮关注点是：“这道题呢，总结一下边际密度函数的求法。”
- 与 A18 的矩形区域相比，这次需理解非矩形支持区域的切片方法：求 $f_Y(y)$ 时固定 $y$，沿 $x$ 方向从 $y^2$ 积到 $1$。
- 仍待用户独立验证：若改求 $f_X(x)$，能否从 $y^2<x$ 自己写出 $-\sqrt{x}<y<\sqrt{x}$。
- 未确认能够独立完整重做，保持 status 为 learning。
