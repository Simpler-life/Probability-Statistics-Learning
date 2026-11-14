---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 4
topic:
  - Mathematical Expectation
  - Joint Probability Density
  - Double Integral
  - Polar Coordinates
tags:
  - B11
  - Uniform Distribution
  - Circular Region
  - Integration Bounds
  - Polar Coordinates
difficulty: medium
exam_priority: high
status: review
source:
  - 黄炜等《概率论与数理统计（第二版）》习题四 B11（题意据本轮讨论整理）
  - 2026-11-14 学习对话：本人补充的两处初始错误
related: []
created: 2026-11-14
updated: 2026-11-14
---

# 习题四 B11：圆形区域内均匀取点——积分区域与极坐标

## Source

习题四 B11，按本轮讨论的题意记录。

## Problem

半径为 $r>0$ 的圆形屏幕上，目标出现的位置 $A=(X,Y)$ 在圆内均匀分布。以圆心为原点，求：

1. $E(X)$ 与 $E(Y)$。
2. 目标到圆心的平均距离 $E(\sqrt{X^2+Y^2})$。

圆内均匀分布的联合概率密度为：

```math
f(x,y)=
\begin{cases}
\dfrac1{\pi r^2},&x^2+y^2\le r^2,\\
0,&\text{其他}.
\end{cases}
```

非零区域必须明确写成：

```math
D=\{(x,y):x^2+y^2\le r^2\}.
```

## First Thought / Actual Mistakes｜本人真实错误

### 错误 1：将圆形积分区域写成正方形

我在第一问最开始把范围写为：

```math
-r\lt x\lt r,\qquad -r\lt y\lt r.
```

**问题：** 这只表达了坐标各自可能落在 $[-r,r]$ 内，二者独立取遍这个区间对应的是边长 $2r$ 的**正方形**，而非圆盘。圆外、正方形内的点也被错误包含。

正确的联合约束是 $x^2+y^2\le r^2$；若先对 $y$ 积分，则在固定 $x$ 时：

```math
-r\le x\le r,\qquad
-\sqrt{r^2-x^2}\le y\le \sqrt{r^2-x^2}.
```

**检查方法：** 画出区域，固定外层变量画一条竖线/横线，内层上下界必须随外层变量变化。不能因为 $x$、$y$ 各自的取值范围都在 $[-r,r]$，就把联合支持集当作矩形。

**细节：** 如果使用全平面密度 $f(x,y)$，写成 $\int_{-r}^{r}\int_{-r}^{r}xf(x,y)\,dy\,dx$ 在形式上也可以，因为圆外 $f=0$；**错误在于把整个正方形都当作密度为 $1/(\pi r^2)$ 的区域**。这两者一定要区分。

### 错误 2：第二问一开始不会极坐标积分

我当时不知道如何将“圆内到圆心的距离的期望”转换为极坐标二重积分，特别需要记住：

```math
x=\rho\cos\theta,\quad
y=\rho\sin\theta,\quad
\sqrt{x^2+y^2}=\rho,\quad
dx\,dy=\rho\,d\rho\,d\theta.
```

从直角坐标变到极坐标时，**面积微元多一个 $\rho$**，否则最终平均距离会算错。

## Correct Solution｜标准完整解法

### （1）直角坐标积分求 $E(X)$ 和 $E(Y)$

圆形区域上 $f=1/(\pi r^2)$。按竖切方式（先 $y$ 后 $x$）：

```math
\begin{aligned}
E(X)
&=\frac1{\pi r^2}
\int_{-r}^{r}
\int_{-\sqrt{r^2-x^2}}^{\sqrt{r^2-x^2}}
x\,dy\,dx\\
&=\frac1{\pi r^2}
\int_{-r}^{r}2x\sqrt{r^2-x^2}\,dx\\
&=0.
\end{aligned}
```

最后一步用到：$2x\sqrt{r^2-x^2}$ 为奇函数，积分区间 $[-r,r]$ 关于原点对称。

同理，改为先 $x$ 后 $y$：

```math
\begin{aligned}
E(Y)
&=\frac1{\pi r^2}
\int_{-r}^{r}
\int_{-\sqrt{r^2-y^2}}^{\sqrt{r^2-y^2}}
y\,dx\,dy\\
&=\frac1{\pi r^2}
\int_{-r}^{r}2y\sqrt{r^2-y^2}\,dy\\
&=0.
\end{aligned}
```

也可以直接利用圆盘与均匀密度关于坐标轴对称得到 $E(X)=E(Y)=0$。但**本次应练会把积分式正确写出来**，不能只用对称性跳过曾经写错的积分上下界。

### （2）极坐标求平均距离

令距离随机变量：

```math
R=\sqrt{X^2+Y^2}.
```

按二维期望定义：

```math
E(R)=\frac1{\pi r^2}\iint_D\sqrt{x^2+y^2}\,dx\,dy.
```

换元：

```math
x=\rho\cos\theta,\qquad
y=\rho\sin\theta,
```

圆盘区域变为：

```math
0\le \rho\le r,\qquad 0\le\theta\le2\pi.
```

**不能漏面积雅可比因子：**

```math
dx\,dy=\rho\,d\rho\,d\theta.
```

所以：

```math
\begin{aligned}
E(R)
&=\frac1{\pi r^2}
\int_0^{2\pi}\int_0^r
\underbrace{\rho}_{\text{距离}}
\underbrace{\rho}_{\text{面积微元}}
\,d\rho\,d\theta\\
&=\frac1{\pi r^2}
\int_0^{2\pi}\left[\frac{\rho^3}{3}\right]_0^r\,d\theta\\
&=\frac1{\pi r^2}\cdot\frac{r^3}{3}\cdot2\pi\\
&=\boxed{\frac{2r}{3}}.
\end{aligned}
```

### （1）的极坐标替代写法

也能与第二问使用同一种积分区域：

```math
\begin{aligned}
E(X)
&=\frac1{\pi r^2}\int_0^{2\pi}\int_0^r
(\rho\cos\theta)\,\rho\,d\rho\,d\theta\\
&=\frac1{\pi r^2}
\left(\int_0^r\rho^2\,d\rho\right)
\left(\int_0^{2\pi}\cos\theta\,d\theta\right)=0,\\
E(Y)
&=\frac1{\pi r^2}\int_0^{2\pi}\int_0^r
(\rho\sin\theta)\,\rho\,d\rho\,d\theta=0.
\end{aligned}
```

### 最终结果

```math
\boxed{E(X)=0,\quad E(Y)=0,\quad
E\left(\sqrt{X^2+Y^2}\right)=\frac{2r}{3}.}
```

## Why the Mean Distance Is Not $r/2$

圆内“面积均匀”不等于“距离均匀”。到圆心距离不超过 $t$（$0\le t\le r$）的概率是面积之比：

```math
P(R\le t)=\frac{\pi t^2}{\pi r^2}
=\frac{t^2}{r^2}.
```

故 $R$ 的密度：

```math
f_R(t)=\frac{2t}{r^2},\qquad 0\le t\le r.
```

再验证：

```math
E(R)=\int_0^r t\frac{2t}{r^2}\,dt=\frac{2r}{3}.
```

圆外缘的环带面积较大，落在较大半径附近的机会更多。

## Recognition｜下次看到这类题的判断顺序

1. **先画密度非零区域**：本题圆盘 $x^2+y^2\le r^2$，不等于正方形。
2. 直角坐标：固定 $x$，$y$ 上下界从圆的方程解出；或反过来固定 $y$。
3. 看到圆盘、$\sqrt{x^2+y^2}$、$x^2+y^2$，优先考虑极坐标。
4. 极坐标“三件套”：被积函数换成 $\rho$ 表达式；区域变成 $0\le\rho\le r$、$0\le\theta\le2\pi$；面积微元乘 $\rho$。
5. 最后利用对称性或结果数量级检查：平均距离应在 $0$ 到 $r$ 之间，而且圆内面积均匀使其大于 $r/2$。

## Calculation Skeleton｜考试手写模板

- 先写 $D=\{x^2+y^2\le r^2\}$ 及 $f(x,y)=1/(\pi r^2)$（在 $D$ 内）。
- $E(X)$ 直角坐标：外层 $x:-r\to r$，内层 $y:-\sqrt{r^2-x^2}\to\sqrt{r^2-x^2}$，然后奇函数积分为 $0$。
- $E(Y)$ 同理交换 $x,y$。
- 距离期望：$\sqrt{x^2+y^2}\to\rho$，$dx\,dy\to\rho\,d\rho\,d\theta$，径向 $0\to r$，角度 $0\to2\pi$。
- 得 $2r/3$。

## Similar Problems / Retest

- **复测一（纠错）**：没有提示时，把半径 $r$ 的圆盘写成两种正确次序的直角坐标累次积分，解释为什么不能用常数密度覆盖整个 $[-r,r]^2$。
- **复测二（极坐标）**：独立写出 $E(\sqrt{X^2+Y^2})$ 的极坐标积分，从区域、被积函数、雅可比因子到计算全部完成。
- **迁移**：把圆盘换成圆环 $a\le\sqrt{x^2+y^2}\le b$，尝试求到圆心的平均距离。

## Personal Summary｜个人总结

- **我的第一处真实错误**：最开始把第一问的积分范围写成 $-r<x<r$ 和 $-r<y<r$，把圆形的二维联合区域错误地当成了矩形来处理。
- **我的第二处真实困难**：第二问的极坐标我一开始不会，不知道如何设置半径与角度的积分范围，也需要特别练习面积微元的 $\rho$ 因子。
- 我希望复习时优先检查：**是否先根据图形确定二维积分区域**，以及**是否把积分区域、被积函数、面积微元三者都换为极坐标**。
- 尚未进行不看答案的独立复测，暂不标记掌握。
