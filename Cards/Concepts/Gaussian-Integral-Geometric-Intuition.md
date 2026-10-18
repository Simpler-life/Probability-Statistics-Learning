---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic:
  - Continuous Random Variables
  - Gaussian Integral
tags:
  - Gaussian Integral
  - Probability Density
  - Polar Coordinates
  - Integration
difficulty: medium
exam_priority: medium
status: learning
source:
  - "教材习题 B27；2026-10-18 学习答疑"
related: []
created: 2026-10-18
updated: 2026-10-18
---

# 高斯积分：为什么一维积分平方后变成二重积分？

## One Sentence

计算 $\int_{-\infty}^{+\infty}e^{-x^2}\,dx$ 的技巧，不是强行找原函数，而是**将积分平方，利用旋转对称性把二维高斯曲面下的体积按同心圆环累加**。

## Intuition｜直觉

先把 $y=e^{-x^2}$ 想象成一座二维平面上的对称“小山”，其曲线下方的面积记为 $I$。

将 $I$ 乘以另一个相同的 $I$（只是积分变量换名为 $y$），得到一个二重积分。它代表三维曲面

$$
z=e^{-(x^2+y^2)}
$$

下方的总体积。这座曲面的高度只取决于到原点的距离 $r$，与方向无关。因此，不必沿直角坐标网格切分整个平面，可以把底面按**同心圆薄环**划分：

- 半径为 $r$ 的薄环周长为 $2\pi r$；
- 厚度为 $dr$，薄环面积近似为 $2\pi r\,dr$；
- 该薄环上的高度为 $e^{-r^2}$；
- 微小体积为 $e^{-r^2}\,2\pi r\,dr$。

这样，一次看似复杂的二重积分重新变成了普通的换元积分；新增的 $r$ 正好与 $-r^2$ 的导数相配。

## Why

普通初等换元法难以计算 $\int e^{-x^2}\,dx$：它没有初等函数表示的原函数；但全实数轴上的定积分仍有精确值。利用对称性是计算这一广义积分的捷径。

## Key Formula

**高斯积分：**

$$
\int_{-\infty}^{+\infty}e^{-x^2}\,dx=\sqrt{\pi}
$$

**推广（$a>0$）：**

$$
\int_{-\infty}^{+\infty}e^{-ax^2}\,dx=\sqrt{\frac{\pi}{a}}
$$

**由偶函数性质得到：**

$$
\int_0^{+\infty}e^{-ax^2}\,dx=\frac12\sqrt{\frac{\pi}{a}}
$$

## Conditions

- 参数 $a>0$，使高斯积分收敛。
- 平方后转为二重积分，因被积函数非负，可由 Tonelli 定理交换或合并积分（初等课程中可从非负二重积分理解）。
- 极坐标面积微元为 $dx\,dy=r\,dr\,d\theta$；整个平面对应 $r\in[0,+\infty)$、$\theta\in[0,2\pi)$。
- 原积分 $I>0$，因此由 $I^2=\pi$ 取正平方根。

## Key Mechanism｜推导与图像对应

设：

$$
I=\int_{-\infty}^{+\infty}e^{-x^2}\,dx
$$

引入仅用于区分第二份积分的变量 $y$：

$$
\begin{aligned}
I^2
&=\left(\int_{-\infty}^{+\infty}e^{-x^2}\,dx\right)
\left(\int_{-\infty}^{+\infty}e^{-y^2}\,dy\right)\\
&=\iint_{\mathbb R^2}e^{-(x^2+y^2)}\,dx\,dy
\end{aligned}
$$

这里的 $I^2$ 不是“同一个平面上面积变面积”，而是两个积分的乘积，等价于二维底面上的累积体积。

把整座旋转对称的山按薄圆环相加：

$$
\begin{aligned}
I^2
&=\int_0^{+\infty}e^{-r^2}(2\pi r)\,dr\\
&=2\pi\left[-\frac12e^{-r^2}\right]_0^{+\infty}\\
&=\pi
\end{aligned}
$$

因此：

$$
I=\sqrt\pi
$$

**为什么会出现 $\pi$？** 不是指数函数本身“藏有圆周率”，而是升维后出现圆形对称性，圆环周长 $2\pi r$ 带来了 $\pi$。

## Typical Example｜教材 B27

已知概率密度：

$$
f(x)=ae^{-x^2},\quad -\infty<x<+\infty
$$

密度函数总积分为 $1$：

$$
a\sqrt{\pi}=1
$$

所以：

$$
a=\frac1{\sqrt\pi}
$$

第二问求 $P(X>1/2)$，无需计算无法初等表示的尾部积分。识别

$$
X\sim N\left(0,\frac12\right)
$$

并标准化，得：

$$
P\left(X>\frac12\right)
=1-\Phi\left(\frac1{\sqrt2}\right)
\approx0.23975
$$

## Exam Focus

- 识别 $e^{-ax^2}$ 且积分区间为整个实数轴时，可直接用高斯积分公式（$a>0$）。
- 识别偶函数，正半轴积分为全轴的一半。
- 概率密度常数由 $\int f(x)\,dx=1$ 确定。
- 对不规则尾区间，优先识别正态分布并标准化，而非硬找原函数。

## Common Traps

- 忘记极坐标的雅可比因子 $r$。
- 误以为 $e^{-x^2}$ 有简单的初等原函数。
- 把 $N(\mu,\sigma^2)$ 的第二个参数误作标准差。
- 以为“平方积分”是普通换元步骤；实际上先利用乘积把问题升到二维，再用极坐标体现对称性。

## My Questions

- 尚未确认完全理解：为什么两个一元积分的乘积能解释成三维曲面下的体积？
- 希望将“平方、升维、同心圆环、换元”与自己熟悉的换元积分建立直觉联系。

## Personal Summary｜个人总结

> 我不能理解这个积分为什么是这样做的，这一点也不形象，跟我之前学的各种换元法不一样。

学习记录（**尚不能据此认定已掌握**）：
- 在 B27 中，看到 $e^{-x^2}$ 不知道如何积分。
- 对“先平方引入 $y$，再用二重积分和极坐标”感到跳跃，尤其是该做法与传统一元换元法之间的联系。
- 目前尝试用“三维小山”和“同心圆薄环的体积累加”来建立直觉。
- 下一步应通过具体的简单可分离函数（例如常数函数在矩形区域上）解释“两个一元积分的乘积 = 二重积分”，再回到高斯积分。
