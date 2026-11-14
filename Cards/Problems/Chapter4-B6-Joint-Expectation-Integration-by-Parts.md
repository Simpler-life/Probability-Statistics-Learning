---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 4
topic:
  - Mathematical Expectation
  - Joint Probability Density
  - Integration by Parts
tags:
  - B6
  - Double Integral
  - Marginal Density
  - Exponential Distribution
  - Tabular Integration
difficulty: medium
exam_priority: high
status: learning
source:
  - 黄炜等《概率论与数理统计（第二版）》习题四 B6
  - 2026-11-14 学习对话（数学计算与积分方法复盘）
related: []
created: 2026-11-14
updated: 2026-11-14
---

# 习题四 B6：二维期望、分部积分与表格积分法

## Source

黄炜等《概率论与数理统计（第二版）》习题四 B6。本卡根据本轮对话中的题干与求解展开；关注重点是无穷积分的数学处理。

## Problem

设二维随机变量 $(X,Y)$ 的联合概率密度为：

```math
f(x,y)=
\begin{cases}
\dfrac{2}{x}e^{-2x},&0\lt x\lt +\infty,\quad 0\lt y\lt x,\\
0,&\text{其他}.
\end{cases}
```

求 $E(X)$、$E(3X-1)$ 和 $E(XY)$。

**积分区域**：

```math
D=\{(x,y):0\lt x\lt +\infty,\ 0\lt y\lt x\}.
```

固定 $x$ 后，内层变量 $y$ 的上下限为 $0,x$；不是 $0,+\infty$。

## Tested Knowledge

- 联合密度积分求期望：$E[g(X,Y)]=\iint_D g(x,y)f(x,y)\,dx\,dy$（相关期望存在时）。
- 边际密度：$f_X(x)=\int f(x,y)\,dy$。
- 期望的线性性质：$E(aX+b)=aE(X)+b$。
- 两次分部积分与表格积分法（连续分部积分的压缩写法）。
- 识别指数分布及其期望，但不能用“认出分布”代替需要掌握的积分运算。

## Recognition

见到 $x^n e^{-ax}$（$n$ 为非负整数，$a\gt 0$）：

1. 多项式 $x^n$ 连续求导最终为 $0$；
2. 指数函数 $e^{-ax}$ 可连续积分；
3. 适合连续分部积分或表格积分法；
4. 无穷上限下，需要证明边界项 $x^k e^{-ax}\to0$。

## First Thought / Knowledge Gap

- 用户追问：“这个最后一步为什么就是直接得到1/2啊”，指 $E(X)=\int_0^\infty 2xe^{-2x}\,dx$ 的最后一步。
- 在 $E(XY)$ 的计算中，用户再次表示：“我还是不懂这个积分怎么求，你还是分布积分吧”，要求展开分部积分过程。
- 用户主动联想到：“我感觉好像这积分可以用什么表格法吗”。
- 目前没有用户独立手写的计算过程，**不能推断已掌握**，也不能虚构具体计算失误。

## Correct Solution

### 1. 求 $E(X)$

先对 $y$ 积分：

```math
\begin{aligned}
E(X)
&=\int_0^\infty\int_0^x
x\frac{2}{x}e^{-2x}\,dy\,dx\\
&=\int_0^\infty 2xe^{-2x}\,dx.
\end{aligned}
```

**必须展开的分部积分：**

取 $u=x$、$dv=2e^{-2x}\,dx$，得 $du=dx$、$v=-e^{-2x}$。所以：

```math
\begin{aligned}
E(X)
&=\left[-xe^{-2x}\right]_0^\infty
+\int_0^\infty e^{-2x}\,dx\\
&=0+\left[-\frac12e^{-2x}\right]_0^\infty\\
&=\frac12.
\end{aligned}
```

第一项为零是由于 $\lim_{x\to\infty}x/e^{2x}=0$，且 $x=0$ 时为零。

**快捷识别（验证）**：

```math
f_X(x)=\int_0^x\frac2x e^{-2x}\,dy=2e^{-2x},
\quad x\gt 0.
```

即 $X\sim\mathrm{Exp}(2)$（率参数 $\lambda=2$），故 $E(X)=1/2$。

### 2. 求 $E(3X-1)$

```math
E(3X-1)=3E(X)-1=\frac12.
```

线性性质不要求两个随机变量独立。

### 3. 求 $E(XY)$：先化成一元积分

```math
\begin{aligned}
E(XY)
&=\int_0^\infty\int_0^x
xy\frac2x e^{-2x}\,dy\,dx\\
&=\int_0^\infty 2e^{-2x}
\left[\frac{y^2}{2}\right]_0^x\,dx\\
&=\int_0^\infty x^2e^{-2x}\,dx.
\end{aligned}
```

记 $I=\int_0^\infty x^2e^{-2x}\,dx$。

#### 方法 A：普通分部积分，两次完成

**第一次：** 取 $u=x^2$、$dv=e^{-2x}\,dx$，则

```math
du=2x\,dx,\qquad v=-\frac12e^{-2x}.
```

因此：

```math
\begin{aligned}
I
&=\left[-\frac12x^2e^{-2x}\right]_0^\infty
+\int_0^\infty xe^{-2x}\,dx\\
&=\int_0^\infty xe^{-2x}\,dx.
\end{aligned}
```

**第二次：** 取 $u=x$、$dv=e^{-2x}\,dx$，则

```math
du=dx,\qquad v=-\frac12e^{-2x}.
```

于是：

```math
\begin{aligned}
I
&=\left[-\frac12xe^{-2x}\right]_0^\infty
+\frac12\int_0^\infty e^{-2x}\,dx\\
&=0+\frac12\left[-\frac12e^{-2x}\right]_0^\infty\\
&=\frac14.
\end{aligned}
```

这里两次产生的边界项都为 $0$，因为 $x^2/e^{2x}\to0$ 和 $x/e^{2x}\to0$。

#### 方法 B：表格积分法（列表分部积分法）

**记法**：左列连续求导；右列连续积分；从第一行开始，按右下斜线相乘，符号依次为 $+,-,+,\ldots$。左列为 $0$ 时停止。

| 符号（该行斜乘） | 左列：连续求导 | 右列：连续积分 |
| :---: | :---: | :---: |
| $+$ | $x^2$ | $e^{-2x}$ |
| $-$ | $2x$ | $-\frac12e^{-2x}$ |
| $+$ | $2$ | $\frac14e^{-2x}$ |
| — | $0$ | $-\frac18e^{-2x}$ |

斜乘的三项分别是：

- 第一项：$+\ x^2\cdot(-\frac12e^{-2x})$
- 第二项：$-\ 2x\cdot(\frac14e^{-2x})$
- 第三项：$+\ 2\cdot(-\frac18e^{-2x})$

因此：

```math
\begin{aligned}
\int x^2e^{-2x}\,dx
&=-\frac12x^2e^{-2x}
-\frac12xe^{-2x}
-\frac14e^{-2x}+C\\
&=-e^{-2x}\left(\frac{x^2}{2}+\frac{x}{2}
+\frac14\right)+C.
\end{aligned}
```

**最后别忘了代入定积分上下限：**

```math
\begin{aligned}
I
&=\left[
-e^{-2x}\left(\frac{x^2}{2}+\frac{x}{2}
+\frac14\right)\right]_0^\infty\\
&=0-\left(-\frac14\right)\\
&=\frac14.
\end{aligned}
```

**表格法的本质**不是新公式，而是把多次分部积分集中写出来。检查时要防止“表格交替符号”和“指数积分自带负号”混淆；两种负号都需要保留。

### 三问结果

```math
\boxed{
E(X)=\frac12,\qquad
E(3X-1)=\frac12,\qquad
E(XY)=\frac14
}
```

## Calculation Skeleton

1. 写明非零区域 $D$，先积 $y$（$0$ 到 $x$）。
2. 化成 $\int_0^\infty 2xe^{-2x}\,dx$ 或 $\int_0^\infty x^2e^{-2x}\,dx$。
3. 做分部积分时选多项式求导、指数函数积分。
4. 若使用表格法，左导右积，斜乘、符号交替、列到左边变 $0$。
5. 无穷积分边界必须解释（指数增长快于任意固定次幂）。
6. 写结果时切记 $E(XY)$ **一般不能**拆成 $E(X)E(Y)$；独立时才可这样用。

## Key Formula

分部积分：

```math
\int u\,dv=uv-\int v\,du.
```

对于非负整数 $n$、$a\gt 0$：

```math
\int_0^\infty x^n e^{-ax}\,dx
=\frac{n!}{a^{n+1}}.
```

这个公式可以由连续分部积分得到。本题 $n=2,a=2$，所以积分为 $2!/2^3=1/4$。**现阶段应能推导，不应只记结果。**

## Transfer

- $\int_0^\infty x^3e^{-x}\,dx$：多一次多项式求导，可以用表格法。
- $\int x^2\sin x\,dx$：同样适合表格法（右侧连续积分为三角函数循环）。
- 有非矩形定义域的二维期望题，先弄清内外积分界限再处理一元积分。

## Similar Problems

- 复测：不用 Gamma 公式，完整推导 $\int_0^\infty x^2e^{-2x}\,dx$，同时写普通分部积分与表格法。
- 迁移：独立计算 $\int_0^\infty x^3e^{-2x}\,dx$，检查斜乘正负号和无穷边界。

## Personal Summary｜个人总结

- 我的真实疑问是：看到 $\int_0^\infty 2xe^{-2x}\,dx$，我不理解为什么答案可以直接写成 $1/2$；看到 $\int_0^\infty x^2e^{-2x}\,dx$，我也不想只套 Gamma 公式，而是需要看到每次分部积分。
- 我主动想到这种积分“好像可以用什么表格法”，因此这张卡重点保存表格法的左右两列、斜乘、交替符号和代上下限全过程。
- 当前应重点复盘：分部积分中 $dv=e^{-2x}dx$ 积分后为何产生 $-\frac12$；表格法的负号如何组合；为什么无穷上限的边界项为 $0$。
- **掌握状态：尚未经过本人无提示独立重做，暂记 learning，不冒称已经掌握。**
