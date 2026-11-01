---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic:
  - Continuous Random Variables
  - Normal Distribution
tags:
  - B27
  - Gaussian Integral
  - Density Normalization
  - Standard Normal Distribution
difficulty: medium
exam_priority: high
status: learning
source:
  - 教材 B27 原题照片（用户提供）
related:
  - Gaussian-Integral-Geometric-Intuition.md
created: 2026-11-01
updated: 2026-11-01
---

# B27｜高斯型概率密度：归一化常数与正态分布尾概率

## Source

用户提供的教材习题 B27 照片。下方**完整保留 B27 原题文字和全部两个小问**；不包括照片里相邻的 B28。

## Problem｜完整原题

**B27.** 设随机变量 \(X\) 的密度函数为

\[
f(x)=a\cdot e^{-x^2},\qquad -\infty<x<+\infty.
\]

（1）求常数 \(a\)；（2）求 \(P\left\{X>\frac12\right\}\)。

## Tested Knowledge

1. 概率密度函数非负、总积分为 \(1\)；
2. 高斯积分及其适用范围；
3. 识别正态分布 \(N(\mu,\sigma^2)\)；
4. 用 \(Z=(X-\mu)/\sigma\) 标准化，通过 \(\Phi\) 写出尾概率。

## Recognition

看到全实数轴上的 \(e^{-x^2}\) 型密度：
- 求常数 → 先用归一化条件；
- 求非全轴区间概率 → 优先识别正态分布，不要硬求 \(e^{-x^2}\) 的初等原函数。

## First Thought｜本轮真实问题

用户一开始说“这个 B27 我不会积分”，随后明确指出：“我不能理解这个积分为什么是这样做的，这一点也不形象，跟我之前学的各种换元法不一样。”

这是对**推导方法与几何直觉**的不理解，不等同于已经证实某一步数学计算错误。

## Attempt

没有提供完整的本人手写解法；不可编造尝试或错误步骤。

## Mistake / Knowledge Gap

- 高斯积分 \(\int_{-\infty}^{+\infty}e^{-x^2}\,dx=\sqrt{\pi}\) 与熟悉的一元换元法之间缺少直觉连接；
- 对“平方积分 → 二重积分 → 极坐标 / 圆环”的升维过程仍有疑问；
- 第二问是否已能独立进行正态标准化，尚未验证。

## Correct Solution

### （1）求 \(a\)

概率密度满足：

\[
\int_{-\infty}^{+\infty}f(x)\,dx=1.
\]

由高斯积分公式：

\[
\int_{-\infty}^{+\infty}e^{-x^2}\,dx=\sqrt{\pi}.
\]

故：

\[
a\sqrt{\pi}=1,\qquad
\boxed{a=\frac1{\sqrt{\pi}}}.
\]

**为什么高斯积分是 \(\sqrt{\pi}\)？** 见关联的 Concept Card：把积分平方，转换为曲面 \(z=e^{-(x^2+y^2)}\) 下的体积，再用同心圆薄环 \(2\pi r\,dr\) 积分。

### （2）求 \(P\left\{X>\frac12\right\}\)

先写为概率密度曲线下方的面积：

\[
P\left(X>\frac12\right)=
\frac1{\sqrt{\pi}}\int_{1/2}^{+\infty}e^{-x^2}\,dx.
\]

它不是全轴积分，不能直接等于 \(\sqrt{\pi}\)。比较正态密度：

\[
\frac{1}{\sqrt{2\pi}\sigma}
\exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right).
\]

由指数部分和系数得：

\[
\mu=0,\qquad \sigma^2=\frac12,\qquad
X\sim N\left(0,\frac12\right).
\]

令 \(Z=(X-\mu)/\sigma\sim N(0,1)\)，注意标准差为 \(\sigma=1/\sqrt{2}\)：

\[
\begin{aligned}
P\left(X>\frac12\right)
&=P\left(Z>\frac{1/2}{1/\sqrt2}\right)\\
&=P\left(Z>\frac1{\sqrt2}\right)\\
&=1-\Phi\left(\frac1{\sqrt2}\right).
\end{aligned}
\]

因此：

\[
\boxed{P\left(X>\frac12\right)
=1-\Phi\left(\frac1{\sqrt2}\right)
\approx0.23975}.
\]

其中 \(\Phi(t)=P(Z\le t)\) 为标准正态分布函数。

## Calculation Skeleton｜考试写法

\[
\begin{aligned}
&1=a\int_{-\infty}^{+\infty}e^{-x^2}\,dx=a\sqrt\pi\\
&\Rightarrow a=1/\sqrt\pi,\\
&X\sim N(0,1/2),\\
&P(X>1/2)=1-\Phi(1/\sqrt2).
\end{aligned}
\]

## Key Formula

对于 \(c>0\)：

\[
\int_{-\infty}^{+\infty}e^{-cx^2}\,dx
=\sqrt{\frac{\pi}{c}}.
\]

若 \(X\sim N(\mu,\sigma^2)\) 且 \(\sigma>0\)：

\[
P(X>x)=1-\Phi\left(\frac{x-\mu}{\sigma}\right).
\]

## Transfer

- 遇到 Gaussian 型密度的归一化常数，直接想到高斯积分；
- 遇到正态分布的区间或尾概率，标准化而非求原函数；
- 注意 \(N(\mu,\sigma^2)\) 第二个参数是方差，标准化除以 \(\sigma\)，不是 \(\sigma^2\)。

## Similar Problems

- 将本题换为 \(f(x)=ae^{-4x^2}\)，重新求 \(a\)。
- 将第二问换为 \(P(X<0)\)，利用关于 \(0\) 的对称性直接得 \(1/2\)。

## Personal Summary｜个人总结

> “这个 B27 我不会积分。”
>
> “我不能理解这个积分为什么是这样做的，这一点也不形象，跟我之前学的各种换元法不一样。”

当前实际学习状态：已接受“从密度总积分等于 1 开始”和“第二问用正态分布标准化”的讲解，但是否能够独立重做尚未确认；高斯积分升维证明的直觉仍需练习。不要标记为 mastered。
