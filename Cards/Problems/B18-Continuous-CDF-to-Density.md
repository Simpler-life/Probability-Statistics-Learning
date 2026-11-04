---
type: problem
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Continuous Random Variable, Distribution Function, Density]
tags: [B18, CDF, PDF, continuity, differentiation, final-review-priority, first-attempt-gap, boundary-derivative]
difficulty: medium
exam_priority: high
status: review
source: [教材第二章习题 B18；用户上传照片]
related: [Cards/Concepts/Distribution-Function-and-Density.md]
created: 2026-11-01
updated: 2026-11-04
---

# B18｜分布函数反求密度

## Original Problem｜完整原题

B18. 设连续型随机变量 $X$ 的分布函数为：

$$
F(x)=
\begin{cases}
0,&x<0,\\
ax^2,&0\le x<1,\\
bx,&1\le x<2,\\
1,&x\ge2.
\end{cases}
$$

（1）求常数 $a,b$；（2）求 $X$ 的密度函数 $f(x)$；（3）求 $P\{0.5<X<1.5\}$。

## First Thought

用户原话：“这个 B18 怎么反求密度函数啊，直接求导吗？”

## Correct Solution

（1）连续型随机变量的 CDF 连续，在 $x=1,2$ 接起来：$a=b$、$2b=1$，故 $a=b=\frac12$。

（2）在可导点逐段求导：

$$
f(x)=
\begin{cases}
0,&x<0,\\
x,&0\le x<1,\\
\frac12,&1\le x<2,\\
0,&x\ge2.
\end{cases}
$$

$F$ 在 $x=1$ 不可导，但密度在单点取值不影响积分概率，以上为合法版本。

（3）优先用分布函数相减：

$$
P(0.5<X<1.5)=F(1.5)-F(0.5)=\frac34-\frac18=\frac58.
$$

也可分段积分：

$$
\int_{0.5}^{1}x\,dx+\int_1^{1.5}\frac12\,dx=\frac58.
$$

## Exam Warning

先求未知参数再求导；密度函数可有跳跃，不等于分布函数必须处处可导；遇分段积分需按断点拆开。

## Personal Summary｜个人总结

我先想到“直接求导”，正确方向是 $f=F'$，但要先由连续性求 $a,b$，再分段求导。单个分界点的密度值不影响概率。

## 2026-11-04｜小测冲刺独立复测：首问无思路、分界点导数出错【大考重点复查】

- **首次遇到第（1）问时明确表示没有思路**：“我不知道这个第一问怎么写，好像没有对应的公式啊。”经提示才理解连续型随机变量的 CDF 必须连续，用 $x=1,2$ 的衔接条件求 $a=b=1/2$。
- 第（2）问独立写对了密度分段表达式，但在中间步骤把 $F'(1)$ 误写为 $0$。**纠正：** $F'_-(1)=1$、$F'_+(1)=1/2$，因此 $F'(1)$ 不存在；密度在单点的取值可任意规定，不影响积分概率。
- 第（3）问独立用 $F(1.5)-F(0.5)=5/8$ 算对，书写合格。
- **当前判断：** 后两问能独立计算，但首问依赖提醒，分界点的可导性判断曾错。保留 `status: review`，列入大考重点回访，不能标为 `mastered`。

### 大考复测任务（先做，后看答案）

1. 给出类似 B18 的分段 CDF，**不提供提示**，自行找出所有连接点并写出连续性方程，求参数。
2. 区分 $F$ 连续、$F$ 可导、$f$ 连续三件事，尤其核查分界点的左右导数。
3. 限时写出分段密度，再选最快方式算区间概率；注意区间端点和单点质量。

### Personal Summary｜本轮新增真实理解与错误

> “我不知道这个第一问怎么写，好像没有对应的公式啊。”
>
> “必须连续吗，那密度函数是不是可以不连续？”

经过讲解，已能完成密度分段和概率计算，但曾写错 $F'(1)$。大考时第一眼先识别“连续型 CDF 含未知参数 → 连续性列方程”，而不是着急求导。此段为本轮补充，保留上方原有 Personal Summary。
