---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Functions of Random Variables, Continuous Random Variables, Distribution Function]
tags: [absolute-value, uniform-distribution, piecewise-CDF, change-of-variable, first-attempt-wrong, final-review-priority]
difficulty: medium
exam_priority: high
status: review
source:
  - "2026-11-04 小测冲刺：§2.5 教学例题，参考老师 PPT Example 30"
related:
  - Cards/Problems/B18-Continuous-CDF-to-Density.md
created: 2026-11-04
updated: 2026-11-04
---

# 均匀分布取绝对值｜非对称区间与分段分布

## Source

小测冲刺复习 §2.5 时讲解的例题，老师 PPT 第二章 PDF 第 95 页附近的 Example 30：$X\sim U(-1,2)$，令 $Y=|X|$，求 $Y$ 的密度函数。

**用户明确反馈：**“把这道题放入GitHub，我第一次做错了。”

## Problem｜完整题意

设

```math
X\sim U(-1,2),\qquad Y=|X|.
$$

求 $Y$ 的概率密度函数 $f_Y(y)$。

## First Thought / Attempt

用户确认第一次做错，但**尚未提供第一次手写解法及具体错误步骤**；不把下列“常见陷阱”擅自记成用户实际错误。

## Tested Knowledge

- 一维连续型随机变量函数的分布：先确定 $Y$ 的范围，再从 $F_Y(y)=P(Y\le y)$ 求分布函数。
- 非单调变换 $|X|$：一个 $y$ 值可能来自 $x=y$ 和 $x=-y$。
- 原始取值范围 $-1\lt X\lt 2$ 不对称，导致分段点为 $y=1$。
- 求出连续型 CDF 后，对各可导区间求导得到 PDF；有限个端点的密度值可以任取。

## Correct Solution｜规范考试写法

由 $X\sim U(-1,2)$，知

```math
f_X(x)=
\begin{cases}
\frac13,&-1\lt x\lt 2,\\
0,&\text{其他}.
\end{cases}
```

并且 $0\le Y\lt 2$。令 $F_Y(y)=P(Y\le y)$。

当 $y\lt 0$ 时，$F_Y(y)=0$。

当 $0\le y\lt 1$ 时，原分布支持区间覆盖 $[-y,y]$，故

```math
F_Y(y)=P(-y\le X\le y)=\frac{2y}{3}.
$$

当 $1\le y\lt 2$ 时，左侧边界已超出 $X$ 的支持区间，只能取 $-1\lt X\le y$，故

$$
F_Y(y)=P(-1\lt X\le y)=\frac{y+1}{3}.
$$

当 $y\ge2$ 时，$F_Y(y)=1$。综上，

```math
F_Y(y)=
\begin{cases}
0,&y\lt 0,\\
\frac{2y}{3},&0\le y\lt 1,\\
\frac{y+1}{3},&1\le y\lt 2,\\
1,&y\ge2.
\end{cases}
```

逐段求导得

```math
f_Y(y)=
\begin{cases}
\frac23,&0\lt y\lt 1,\\
\frac13,&1\lt y\lt 2,\\
0,&\text{其他}.
\end{cases}
```

$y=0,1,2$ 等有限个点的密度值不会改变概率，取值可按分段约定设置。

## Fast Recognition｜看到题时怎么做

1. **先写原支持区间** $-1\lt X\lt 2$，求出 $Y$ 的值域 $[0,2)$。
2. 写 $F_Y(y)=P(|X|\le y)=P(-y\le X\le y)$（$y\ge0$）。
3. 对 $[-y,y]$ 与 $(-1,2)$ **取交集**；在 $y=1$ 时左边界换挡，在 $y=2$ 后概率为 $1$。
4. 写完整分段 CDF，最后才求导得 PDF，检查 $\int_0^2 f_Y(y)\,dy=1$。

## Common Traps｜此题潜在陷阱（不是已证实的用户错误）

- 把 $X$ 的支持区间忽略，误将 $F_Y(y)=2y/3$ 沿用到 $y\ge1$。
- 认为 $|X|$ 是单调函数，直接套单支反函数密度公式。
- 忘记写 $y\lt 0$ 与 $y\ge2$ 的两端分段。
- 只给最终密度，缺少用等价事件求 CDF 的书写依据。

## Exam Focus / Transfer

- 优先核对教材 §2.5（纸质第 65 页起）和老师 PPT 第二章 PDF 第 89—90 页的一般求解步骤、第 93—95 页的绝对值例题。
- 大考无提示复测：$X\sim U(-2,3)$，$Y=|X|$；先找分界点，再独立写 $F_Y$ 与 $f_Y$。
- 对照 B18：B18 是**已知分段 CDF 再求参数与密度**；本题先由**原始支持区间和变换**推导出分段 CDF。

## Personal Summary｜个人总结

\gt  “把这道题放入GitHub，我第一次做错了。”

此次确认该例题第一次做错，应作为期末重点回访题。具体哪一步错了还未提供，不能虚构首次错误过程。已提供过完整讲解，但尚无本人的无提示独立重做记录，因此状态保留为 `review`，下次优先检查“为什么必须在 $y=1$ 处分段”以及标准解答的完整书写。
