---
type: mistake
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Normal Distribution, Total Probability, Bayes Formula, Binomial Distribution]
tags: [B24, normal-standardization, total-probability, bayes, independence]
difficulty: hard
exam_priority: high
status: review
source: [教材第二章习题 B24；用户上传照片]
related: [Cards/Concepts/Distribution-Function-and-Density.md]
created: 2026-11-01
updated: 2026-11-01
---

# B24｜条件故障概率不能忽略；元件独立性需要核查

## Original Problem｜完整原题

B24. 设系统电压（单位：V）在小于 200、在区间 $[200,240]$ 上和超过 240 这三种情况下，系统中某种电子元件不能正常工作的概率分别为 0.1、0.001、0.2。设系统电压 $X$ 服从 $N(220,25^2)$。

（1）求该电子元件不能正常工作的概率 $\alpha$；

（2）若该电子元件不能正常工作，求此时系统电压超过 240 V 的概率 $\beta$；

（3）设该系统有 3 个这种元件，且若至少有 2 个正常时系统才运行正常，求该系统运行正常的概率 $\theta$。

## Context / Wrong Idea

最初助教误读题目，把“电压落在 $[200,240]$ 外的概率 0.4238”误当成电子元件不能正常工作的概率，遗漏题目明确给出的**三个条件故障率**。这是助教错误，用户正确指出：“不正常工作还要乘上概率吧”，并要求“你重新读题呢”。

## Correct Solution

令 $A$ 为电子元件不能正常工作，$B_1=\{X<200\}$、$B_2=\{200\le X\le240\}$、$B_3=\{X>240\}$。

$$
Z=\frac{X-220}{25}\sim N(0,1).
$$

由 $\Phi(0.8)=0.7881$、$\Phi(-0.8)=1-\Phi(0.8)$：

$$
P(B_1)=P(B_3)=0.2119,\qquad P(B_2)=0.5762.
$$

（1）全概率公式：

$$
\begin{aligned}
\alpha=P(A)
&=0.1P(B_1)+0.001P(B_2)+0.2P(B_3)\\
&=0.1(0.2119)+0.001(0.5762)+0.2(0.2119)\\
&=0.0641462.
\end{aligned}
$$

（2）贝叶斯公式：

$$
\beta=P(B_3\mid A)
=\frac{0.2P(B_3)}{P(A)}
=\frac{0.2(0.2119)}{0.0641462}
\approx0.6607.
$$

（3）**独立性警告**：题目并未说明三个元件的联合工作规律，仅凭各区间中单个元件的故障概率不能严格唯一确定 $\theta$。

若**额外假定三元件的工作状态无条件相互独立**，每个正常概率 $p=1-\alpha=0.9358538$，则：

$$
\theta=\binom32p^2(1-p)+p^3\approx0.9882.
$$

但如果三元件共享同一随机系统电压，且只在**给定电压区间时条件独立**，应该计算：

$$
\theta=\sum_{i=1}^3 P(B_i)\left[3(1-q_i)^2q_i+(1-q_i)^3\right],
\quad(q_1,q_2,q_3)=(0.1,0.001,0.2).
$$

这与“无条件独立”的二项分布结果通常不同。因此不能将 0.9882 写成原题无额外条件下的必然答案。

## Trigger / Exam Warning

“在三种情况下故障率分别为……”意味着条件概率；先算电压区间概率，再按条件故障率加权。已知故障反求电压区间用 Bayes。多个元件出现时必须检查**独立性（尤其是否共享环境随机变量）**。

## Personal Summary｜个人总结

我先问负标准正态值是不是用 $1-\Phi(0.8)$ 查表；看到题目给三个故障概率，我反问“不正常工作还要乘上概率吧”，再要求助教重新读题。我的判断正确：要对各电压区间概率乘条件故障率，再相加。第三问的二项分布需要写出独立性前提；不能只看到“3 个、至少 2 个”就无条件套公式。
