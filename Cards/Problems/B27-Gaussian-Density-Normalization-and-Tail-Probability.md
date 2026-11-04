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
  - final-review-priority
  - no-independent-solution
  - integration-knowledge-gap
difficulty: medium
exam_priority: high
status: learning
source:
  - 教材 B27 原题照片（用户提供）
related:
  - Gaussian-Integral-Geometric-Intuition.md
created: 2026-11-01
updated: 2026-11-04
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

## 2026-11-04｜小测冲刺再次卡住【大考高优先级・尚未独立掌握】

- 本轮看到全轴高斯积分 $\int_{-\infty}^{+\infty} e^{-x^2}\,dx=\sqrt{\pi}$ 时，再次追问“哪里有这个公式啊，我发现我又不会积分了，怎么办啊”。
- 对老师教材/PPT 中可查到的推导或结论位置感到不确定，并担心考试遇到复杂积分；**没有提交本轮 B27 的独立书面解答**，不能判定已掌握。
- 备选快速方法：将 $ae^{-x^2}$ 与正态密度形式比较，由指数匹配得 $\mu=0,\sigma^2=1/2$，再由归一化系数得 $a=1/\sqrt\pi$；第二问写 $1-\Phi(1/\sqrt2)$。不要强行寻找 $e^{-x^2}$ 的初等原函数。
- 参考位置：教材 §2.4 正态分布，纸质第 58—60 页附近；往年 PPT 第二章 PDF 第 66 页正态分布定义、第 71—73 页正态积分标准化和查表。**本轮核查未证实 PPT 里单独列出全轴高斯积分公式**，不可误写为“老师 PPT 直接给出该公式”。
- **当前判断：** `status: learning`，大考优先级高，须独立重做并验证对正态参数、标准差与方差的区分。

### 大考复测任务（先做，后看答案）

1. 在没有公式提示时求 $f(x)=ae^{-x^2}$ 的 $a$，尝试两种思路：归一化/识别正态密度；明确每个公式的依据。
2. 独立计算 $P(X>1/2)$，写出标准化过程、$\sigma=1/\sqrt2$，结果保留为 $1-\Phi(1/\sqrt2)$。
3. 改为 $f(x)=ae^{-4x^2}$，复测参数匹配；另练习普通换元积分与二重积分区域，区分“特例公式”与“基本积分能力”。

### Personal Summary｜本轮新增真实困惑

> “哪里有这个公式啊，我发现我又不会积分了，怎么办啊，小测要是也考到这种难的积分，我又不会……”

本轮尚未独立作答 B27。真正需要修补的是高斯型函数识别、何时可查标准正态表，以及常见积分方法的边界；不用把“暂时不理解高斯积分证明”误判为必然无法完成概率题。此前 Personal Summary 保留。
