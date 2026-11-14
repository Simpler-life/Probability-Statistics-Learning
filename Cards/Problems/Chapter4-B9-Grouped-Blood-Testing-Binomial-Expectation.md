---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 4
topic:
  - Mathematical Expectation
  - Binomial Distribution
  - Expected Cost
tags:
  - B9
  - Binomial Distribution
  - Expected Value
  - Group Testing
  - Formula Recall
difficulty: medium
exam_priority: high
status: review
source:
  - 黄炜等《概率论与数理统计（第二版）》习题四 B9
  - 2026-11-14 学习对话与本人手写解题照片
related: []
created: 2026-11-14
updated: 2026-11-14
---

# 习题四 B9：分组验血——已建立二项分布却忘用期望公式

## Source

黄炜等《概率论与数理统计（第二版）》习题四 B9。本卡记录本轮题目讲解及用户手写解答，重点保留实际思路与公式提取障碍。

## Problem

<img width="982" height="296" alt="image" src="https://github.com/user-attachments/assets/775e5063-8eda-4b73-9eed-8f652ac61264" />
<img width="974" height="228" alt="image" src="https://github.com/user-attachments/assets/8bf536b1-2e79-4eee-94ce-14779a76b54e" />


500 人需要检验是否患病，单人患病率为 20%。方案一是逐人化验，共 500 次；方案二把 500 人按每组 $k$ 人分组（$k>1$ 且 $500/k$ 为整数），每组先混合化验 1 次；若阳性，该组再逐人化验 $k$ 次；若阴性，该组无需进一步化验。比较平均化验次数，并选择合理分组大小。

按题目中的常规模型，假定各人患病情况相互独立，且混检能准确判断该组是否至少有一人患病。

## First Thought｜用户原始思路

用户在手写解答中：

1. 定义 $A$ 为单人患病，$P(A)=0.2$；$B$ 为一组混检阳性。
2. 正确得到 $P(B)=1-0.8^k$。
3. 设 $X$ 为阳性组数，写出了以组数 $500/k$、阳性概率 $1-0.8^k$ 为参数的二项分布概率式。
4. 设 $Y$ 为总化验次数，正确列出：

```math
Y=kX+\frac{500}{k}.
```

5. 正确推到：

```math
E(Y)=kE(X)+\frac{500}{k}.
```

**真实卡点**：已经知道 $X$ 服从二项分布，甚至写出了它的概率分布律，却没有及时调用二项分布的现成结论 $E(X)=np$，而是准备展开求和计算。这里是**已识别分布，但没提取出对应数字特征**，并不是不会建模或不会列二项分布。

## Mistake / Knowledge Gap

- 不是 $P(B)$、$X$ 的分布律、$Y=kX+500/k$ 算错。
- 核心缺口：忘记二项分布 $B(n,p)$ 的数学期望 $np$ 可以直接代入，不必从头对分布律求和。
- 目前没有进行无提示复测，不能标记为 mastered。

## Correct Solution｜沿用本人建模

一组全体健康的概率：

```math
P(\text{全组阴性})=0.8^k.
```

故阳性概率：

```math
p=P(B)=1-0.8^k.
```

总组数 $n=500/k$。不同组独立，令 $X$ 为阳性组数，则：

```math
X\sim \mathrm{Bin}\left(\frac{500}{k},1-0.8^k\right).
```

用户已写出其概率式：

```math
P(X=x)=
\binom{500/k}{x}
(1-0.8^k)^x
(0.8^k)^{500/k-x},
\quad x=0,1,\ldots,\frac{500}{k}.
```

**到这里应该立即停下，不再展开求和。** 因为：

```math
X\sim\mathrm{Bin}(n,p)\quad\Longrightarrow\quad E(X)=np.
```

直接有：

```math
E(X)=\frac{500}{k}(1-0.8^k).
```

根据本人已列出的线性关系：

```math
\begin{aligned}
Y&=kX+\frac{500}{k},\\
E(Y)&=kE(X)+\frac{500}{k}\\
&=k\frac{500}{k}(1-0.8^k)+\frac{500}{k}\\
&=\boxed{500(1-0.8^k)+\frac{500}{k}}.
\end{aligned}
```

方法一需要 500 次。对允许的分组大小 $k$（大于 1 且整除 500）比较方法二的期望：

| 每组人数 $k$ | 期望化验次数 $E(Y)$ |
| ---: | ---: |
| 2 | 430 |
| 4 | 420.2 |
| 5 | 436.16 |
| 10 | 约 496.31 |
| 20 | 约 519.24 |

其余可选整除数对应的期望更大，故**最优每组 $k=4$，平均约 420.2 次**，比逐人检验平均节省 79.8 次。注意：不是所有分组方案都优于逐人检验。

## Key Formula｜要形成条件反射

**二项分布的数字特征：**

```math
X\sim\mathrm{Bin}(n,p)
\quad\Longrightarrow\quad
E(X)=np,\qquad
\operatorname{Var}(X)=np(1-p).
```

可用指示变量理解：若 $X=I_1+\cdots+I_n$，每次是否发生记为 $I_i\in\{0,1\}$，则 $E(I_i)=p$，由期望线性性质：

```math
E(X)=\sum_{i=1}^n E(I_i)=np.
```

这也解释了为何不用重新计算求和：

```math
\sum_{x=0}^{n}x\binom{n}{x}p^x(1-p)^{n-x}.
```

**期望的线性性质：**

```math
E(aX+b)=aE(X)+b.
```

## Recognition｜考试时的三步自检

1. **随机变量是什么？** 本题 $X$ 是阳性组的个数，即独立重复试验中事件发生的次数。
2. **分布是什么？** 如果 $X$ 服从 $\mathrm{Bin}(n,p)$，标出 $n,p$。
3. **问题问什么数字特征？** 问平均个数就写 $E(X)=np$；问波动程度就想到 $\operatorname{Var}(X)=np(1-p)$。不要条件反射地从完整分布律开始求和。

**触发提醒**：一旦自己写出 $P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}$，下一行先写“$X\sim\mathrm{Bin}(n,p)$，所以 $E(X)=np$”，再继续算总成本。

## Alternative View｜与另一种建模对照

也可以令 $Z$ 为**一组**的化验次数，则：

```math
P(Z=1)=0.8^k,\qquad
P(Z=k+1)=1-0.8^k.
```

因此：

```math
E(Z)=1+k(1-0.8^k).
```

总共 $500/k$ 组，故：

```math
E(Y)=\frac{500}{k}E(Z)
=\frac{500}{k}+500(1-0.8^k).
```

这与用户的二项分布方法等价，但**不应因此替换用户本来正确的建模思路**。

## Transfer｜迁移练习

- 若每组发生额外检查的概率为 $p$，总共有 $n$ 组，每个阳性组额外花费 $c$，固定花费为 $b$，则总成本可写成 $Y=cX+b$，其中 $X\sim\mathrm{Bin}(n,p)$；立即得到 $E(Y)=cnp+b$。
- 复测时先给出“独立重复检查、求触发次数平均值”的新题，要求在**不展开二项求和**的情况下用 $np$ 求平均；再回到 B9 重做。
- 延伸问题：患病率从 20% 降低到 1% 时，直觉上合理的分组会变大（在可选 $k$ 内再做离散比较）。

## Personal Summary｜个人总结

- 我这次在 B9 手写过程中已经正确写出每组阳性概率、阳性组数的二项分布，以及总化验次数 $Y=kX+500/k$。
- 我真正没有想起的是：**既然已经判断 $X$ 服从二项分布，就可以直接用 $E(X)=np$，不用再把所有 $xP(X=x)$ 展开求和。**
- 下次看到“某件事在很多次独立试验中发生多少次”，不仅要识别二项分布，还要主动问：题目是不是在求**平均次数**？如果是，立刻考虑 $np$。
- 此刻我希望重点复习的是从“分布”快速调用“期望/方差”结论，而不是重做已经正确的建模步骤；尚未无提示复测。
