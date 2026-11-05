---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Joint Density, Marginal Density, Conditional Probability, Mixed Distribution, Independence]
tags: [past-quiz, comprehensive, curved-region, double-integral, mixed-distribution, independence, final-review-priority]
difficulty: hard
exam_priority: highest
status: review
source: [2026-11-04 to 2026-11-05 历年小测截图及本轮手写答题]
related:
  - Cards/Mistakes/Curved-Region-Double-Integral-Order-and-Limits.md
  - Cards/Concepts/Conditional-Distribution-CDF-vs-Density.md
  - Cards/Problems/A20-Marginal-Density-on-Curved-Region.md
created: 2026-11-05
updated: 2026-11-05
---

# 历年小测综合题一：抛物线联合密度（完整五问）

## Original Problem｜原题

设二维连续型随机变量 $(X,Y)$ 的联合概率密度为：

```math
f_{X,Y}(x,y)=
\begin{cases}
c,&y^2\lt x\lt4,\\
0,&\text{其他}.
\end{cases}
```

求：

1. 常数 $c$；
2. $Y$ 的边际密度 $f_Y(y)$；
3. $P(-0.5\lt Y\lt1.44\mid X=1)$；
4. 令 $T=1$（$Y\gt0$），$T=0$（$Y\le0$），求 $Z=YT$ 的分布函数并判断 $Z$ 的分布类型；
5. 令 $\xi=1$（$0\le Y\lt\sqrt X\lt2$），其他情况 $\xi=0$，判断 $\xi$ 与 $X$ 是否独立，说明理由。

## Standard Solution｜标准书写

### （1）归一化求 c

由 $y^2\lt x\lt4$，可得 $-2\lt y\lt2$。所以：

```math
1=\int_{-2}^{2}\int_{y^2}^{4}c\,dx\,dy
=c\int_{-2}^{2}(4-y^2)\,dy
=\frac{32c}{3}.
```

故 $c=3/32$。亦可换序写为 $\int_0^4\int_{-\sqrt x}^{\sqrt x}c\,dy\,dx$。

### （2）边际密度

```math
f_Y(y)=
\begin{cases}
\displaystyle\int_{y^2}^{4}\frac3{32}\,dx=\frac3{32}(4-y^2),&-2\lt y\lt2,\\
0,&\text{其他}.
\end{cases}
```

为后续条件概率，也求出：

```math
f_X(x)=
\begin{cases}
\displaystyle\int_{-\sqrt x}^{\sqrt x}\frac3{32}\,dy=\frac3{16}\sqrt x,&0\lt x\lt4,\\
0,&\text{其他}.
\end{cases}
```

### （3）条件密度与条件概率

由 $f_{Y\mid X}(y\mid x)=f_{X,Y}(x,y)/f_X(x)$：

```math
f_{Y\mid X}(y\mid x)=
\begin{cases}
\frac1{2\sqrt x},&0\lt x\lt4,\ -\sqrt x\lt y\lt\sqrt x,\\
0,&\text{其他 } y\text{（固定 }0\lt x\lt4\text{ 时）}.
\end{cases}
```

给定 $X=1$，实际条件支持区间为 $-1\lt y\lt1$，因此：

```math
P(-0.5\lt Y\lt1.44\mid X=1)
=\int_{-0.5}^{1}\frac12\,dy
=\frac34.
```

注意题给上限 $1.44$ 超出条件支持区间，上限必须截断到 $1$。

### （4）Z=YT 的分布函数与分布类型

由于 $Z=\max(Y,0)$，所以 $P(Z=0)=P(Y\le0)=1/2$；其中 $f_Y$ 关于 $0$ 对称。对 $0\le z\lt2$：

```math
F_Z(z)=P(Z\le z)
=\frac12+\int_0^z\frac3{32}(4-y^2)\,dy
=\frac12+\frac{3z}{8}-\frac{z^3}{32}.
```

完整分布函数：

```math
F_Z(z)=
\begin{cases}
0,&z\lt0,\\
\frac12+\frac{3z}{8}-\frac{z^3}{32},&0\le z\lt2,\\
1,&z\ge2.
\end{cases}
```

其在 $z=0$ 处发生大小为 $1/2$ 的跳跃，同时在 $(0,2)$ 内有连续变化，故 $Z$ 为**混合型分布**（离散质量与连续部分兼有）。

### （5）判断 xi 与 X 是否独立

由支持区域 $y^2\lt x\lt4$ 可知，几乎必然有 $\lvert Y\rvert\lt\sqrt X\lt2$；于是 $\xi$ 几乎必然等于 $Y$ 非负时取 $1$、否则取 $0$ 的指示变量。

由 $f_Y$ 关于 $0$ 对称，$P(\xi=1)=1/2$，$P(\xi=0)=1/2$。

对任意 $0\lt x\lt4$：

```math
P(\xi=1\mid X=x)
=\int_0^{\sqrt x}\frac1{2\sqrt x}\,dy
=\frac12=P(\xi=1).
```

且 $P(\xi=0\mid X=x)=1/2=P(\xi=0)$，所以 $\xi$ 与 $X$ **独立**。

**不能仅凭 $\xi$ 的表达式中出现 $X$ 就判断不独立**；要比较条件概率与边际概率。

## Personal Attempt & Errors｜本轮实际表现

- **（1）** 第一次交换二重积分次序时混用了上下限；在讲解后自己重新列出正确积分，得 $c=3/32$。不把它误写为首次独立正确。
- **（2）** 首次求 $f_Y$ 时将非零区域外也当作常数密度，误得常数 $3/8$；后来独立正确算出 $f_X(x)=3\sqrt x/16$，并在后续手稿写对 $f_Y$。
- **（3）** 多轮混淆边际密度/CDF、条件密度/CDF 以及积分变量；一度写错条件密度为 $1$、把 $Y$ 的整体范围 $(-2,2)$ 当成给定 $X=1$ 的范围，甚至以 $1.44$ 积分到支持区间外，得过错误结果 $0.975$；经讲解已标出截断到 $1$，但仍宜无提示复测。
- **（4）** 首先表示没有学过混合型分布；经过讲解，独立写出了正确的 $F_Z$ 分段与类型。此小问可记为本轮通过，但建议大考新变式复测。
- **（5）** 第一次判断为“不独立”，理由仅为 $\xi$ 的表达式出现 $X$；正确答案是独立，尚未独立复测。

## Exam Checklist｜期末快速检查

1. 联合密度只在指定区域非零；画区域，按切片确定积分限。
2. 求 $f_X$：对 $y$ 积分；求 $f_Y$：对 $x$ 积分，二者不是 CDF。
3. 给定 $X=x$ 后重新确定 $Y$ 的条件支持区间；区间概率只积分两区间的交集。
4. CDF 必须左侧 $0$、右侧 $1$；函数将正概率一整段压到某点时，CDF 可能跳跃。
5. 独立性只按分布判断，不按“表达式里有没有另一个变量”判断。

## Open-book Reference

- 教材第三章 §3.3：联合、边际、条件密度及二重积分区域；§3.4：独立性。
- 教材第二章 §2.5：一维随机变量函数的分布（第 4 小问可用分布函数法）。
- 对应本轮 PPT 的具体例题编号未再次核对，不凭空写例题编号。

## Final Review｜大考复测任务

请**整题限时独立重做**，尤其复测（2）（3）（5），并解释（4）为何不是纯连续型；随后用第二套历年题 $f(x,y)=cx^2y$，$x^2\lt y\lt1$ 做迁移训练。

## Personal Summary｜个人总结

这套题不断暴露了同一个核心问题：算式会写，但经常没有把密度的非零区域、条件支持区间和积分变量同步约束。第（4）问从没思路到成功独立解答；第（5）问不能凭表面函数依赖判断独立。大考应优先无提示验证这些区别，不可将听过讲解等同于完全掌握。
