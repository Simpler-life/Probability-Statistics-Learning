---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Normal Distribution, Sum of Independent Random Variables, Convolution]
tags: [A35, normal-distribution, convolution, gaussian-integral, completion-of-square]
difficulty: medium
exam_priority: high
status: learning
source: [教材习题 A35（用户提供题图）, 2026-11-07 ChatGPT 学习讨论]
related: [B27-Gaussian-Density-Normalization-and-Tail-Probability.md, ../Concepts/Gaussian-Integral-Geometric-Intuition.md]
created: 2026-11-07
updated: 2026-11-07
---

# A35（第 1 问）｜两个独立标准正态变量之和：正态可加性与卷积法

## Problem｜题目

设随机变量 $`X`$ 与 $`Y`$ 相互独立，且都服从标准正态分布。**（1）令 $`Z=X+Y`$，求 $`Z`$ 的密度函数。**

原题还包含第（2）（3）问关于 $`\min`$、$`\max`$ 的概率，本卡仅记录用户指定的**第（1）问两种解法**。

## Recognition｜识别

已知 $`X,Y`$ 独立，且

$$
X\sim N(0,1),\qquad Y\sim N(0,1),\qquad Z=X+Y.
$$

**考试优先选方法一**，但方法二（卷积）更通用，可以解释为什么结果依旧是正态分布。

## Method 1｜直接利用独立正态变量的可加性

若 $`X\sim N(\mu_1,\sigma_1^2)`$、$`Y\sim N(\mu_2,\sigma_2^2)`$ **且相互独立**，则

$$
X+Y\sim N(\mu_1+\mu_2,\ \sigma_1^2+\sigma_2^2).
$$

本题的均值之和为 $`0+0=0`$，方差之和为 $`1+1=2`$，所以

$$
Z\sim N(0,2).
$$

注意：正态分布记号的**第二个参数是方差**，不是标准差；此时 $`\sigma=\sqrt2`$。

正态分布密度通式：

$$
f_Z(z)=\frac{1}{\sqrt{2\pi}\sigma}
\exp\left[-\frac{(z-\mu)^2}{2\sigma^2}\right].
$$

代入 $`\mu=0`$、$`\sigma^2=2`$、$`\sigma=\sqrt2`$：

$$
\boxed{f_Z(z)=\frac{1}{2\sqrt{\pi}}e^{-z^2/4}},\qquad z\in\mathbb{R}.
$$

## Method 2｜用卷积公式逐步推导

### ① 写出卷积

两个**独立、具有密度**的随机变量之和的密度满足

$$
f_Z(z)=\int_{-\infty}^{+\infty} f_X(x)f_Y(z-x)\,dx.
$$

这里用 $`z-x`$，因为当 $`Z=z`$ 且 $`X=x`$ 时，$`Y=z-x`$。

两者均为标准正态，因此

$$
f_X(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2},
\qquad
f_Y(y)=\frac{1}{\sqrt{2\pi}}e^{-y^2/2}.
$$

代入：

$$
\begin{aligned}
f_Z(z)
&=\int_{-\infty}^{+\infty}
\frac{1}{\sqrt{2\pi}}e^{-x^2/2}
\frac{1}{\sqrt{2\pi}}e^{-(z-x)^2/2}\,dx\\
&=\frac{1}{2\pi}\int_{-\infty}^{+\infty}
e^{-[x^2+(z-x)^2]/2}\,dx.
\end{aligned}
$$

### ② 对指数中的二次式配方

$$
\begin{aligned}
x^2+(z-x)^2
&=2x^2-2zx+z^2\\
&=2\left(x-\frac z2\right)^2+\frac{z^2}{2}.
\end{aligned}
$$

于是

$$
-\frac{x^2+(z-x)^2}{2}
=-\left(x-\frac z2\right)^2-\frac{z^2}{4}.
$$

再代回卷积积分，把与积分变量 $`x`$ 无关的 $`e^{-z^2/4}`$ 提出来：

$$
f_Z(z)=\frac{e^{-z^2/4}}{2\pi}
\int_{-\infty}^{+\infty}
e^{-(x-z/2)^2}\,dx.
$$

### ③ 换元并使用高斯积分

令 $`u=x-z/2`$，则 $`du=dx`$。由于是整个实数轴上的积分，平移后积分上下限仍为 $`-\infty`$ 到 $`+\infty`$：

$$
\begin{aligned}
\int_{-\infty}^{+\infty}e^{-(x-z/2)^2}\,dx
&=\int_{-\infty}^{+\infty}e^{-u^2}\,du\\
&=\sqrt{\pi}.
\end{aligned}
$$

这是经典的**高斯积分**。$`e^{-u^2}`$ 不存在初等函数形式的原函数，不能按普通不定积分硬算；高斯积分的证明可通过平方后使用极坐标完成，见关联概念卡。

### ④ 化简得到结果

$$
\begin{aligned}
f_Z(z)
&=\frac{e^{-z^2/4}}{2\pi}\sqrt{\pi}\\
&=\boxed{\frac{1}{2\sqrt{\pi}}e^{-z^2/4}},
\qquad z\in\mathbb R.
\end{aligned}
$$

和方法一完全一致。

## Calculation Skeleton｜考试速写

**方法一（最省时）：**

$$
X,Y\text{ 独立且都服从 }N(0,1)
\Longrightarrow Z=X+Y\sim N(0,2)
\Longrightarrow
f_Z(z)=\frac{e^{-z^2/4}}{2\sqrt{\pi}}.
$$

**方法二（卷积核心三行）：**

$$
\begin{aligned}
f_Z(z)&=\frac1{2\pi}\int_{-\infty}^{+\infty}
e^{-[x^2+(z-x)^2]/2}\,dx\\
&=\frac{e^{-z^2/4}}{2\pi}\int_{-\infty}^{+\infty}
e^{-(x-z/2)^2}\,dx\\
&=\frac{e^{-z^2/4}}{2\pi}\sqrt\pi
=\frac{e^{-z^2/4}}{2\sqrt\pi}.
\end{aligned}
$$

## Common Traps

1. **方差而非标准差相加**：$`Z`$ 的方差为 $`2`$，标准差为 $`\sqrt2`$。
2. **卷积公式需要独立性**：一般不能直接把边缘密度相乘。
3. **配方时保留常数项**：$`x^2+(z-x)^2=2(x-z/2)^2+z^2/2`$；漏掉最后一项会得到错误密度。
4. **$`z`$ 是外部参数，$`x`$ 才是积分变量**：$`e^{-z^2/4}`$ 可提出积分号。
5. **高斯积分的系数**：$`\int_{\mathbb R}e^{-u^2}\,du=\sqrt\pi`$，而 $`\int_{\mathbb R}e^{-u^2/2}\,du=\sqrt{2\pi}`$，不能混淆。

## Related

- [B27｜高斯型密度、归一化和尾概率](B27-Gaussian-Density-Normalization-and-Tail-Probability.md)
- [高斯积分的几何直觉](../Concepts/Gaussian-Integral-Geometric-Intuition.md)

## My Questions

- 用户问：“我不可以直接使用卷积公式吗，但是用了之后我不会算了”。
- 尚未提交完整的卷积手写步骤，不能断言具体在哪一个等号算错。

## Personal Summary｜个人总结

- 本轮明确希望**保留第一问的正态可加性与卷积两种方法**。
- 卷积积分的主要练习点是：展开平方、配方、提出常数、换元为高斯积分。
- 尚未独立复做验证，不标记为 mastered。
