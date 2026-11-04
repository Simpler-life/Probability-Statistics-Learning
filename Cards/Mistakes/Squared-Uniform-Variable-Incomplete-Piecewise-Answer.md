---
type: mistake
subject: Probability and Mathematical Statistics
chapter: Chapter 2
topic: [Function of Random Variable, CDF, PDF, Exam Writing]
tags: [squared-transform, uniform-distribution, incomplete-piecewise, repeated-error, cdf-vs-pdf, final-review-priority]
difficulty: easy
exam_priority: high
status: review
source: [2026-11-04 手写练习与本人确认的错因]
related:
  - Cards/Problems/Absolute-Value-of-Uniform-Variable-Piecewise-Density.md
  - Cards/Problems/B18-Continuous-CDF-to-Density.md
created: 2026-11-04
updated: 2026-11-04
---

# 平方变换：求出公式却没有写完所有分段

## Original Problem｜完整原题

设 $X\sim U(-2,2)$，令 $Y=X^2$。求 $Y$ 的取值范围、分布函数 $F_Y(y)$ 与概率密度函数 $f_Y(y)$。

## Context / Wrong Idea｜本次实际表现与错因

用户手写过程正确求出了 $0\le Y<4$，也正确算出在 $0\le y<4$ 内 $F_Y(y)=\sqrt y/2$，进而求导得到 $f_Y(y)=1/(4\sqrt y)$。

**本人明确指出的错因：**“没有直接写完所有情况”。

具体是最终未写完整的分段式：CDF 漏写 $y<0$ 时为 $0$ 和 $y\ge4$ 时为 $1$；PDF 只写了区间内的公式，没有补全“其他位置为 $0$”。而且 $1/(4\sqrt y)$ 在 $y=0$ 无定义，密度这一段应写 $0<y<4$。

这不是对平方变换思路或求导方法的全面不理解，是**考试答案完整性**问题。

## Correct Solution｜标准考试书写

由 $-2<X<2$ 得 $0\le Y<4$。当 $0\le y<4$ 时：

$$
F_Y(y)=P(-\sqrt y\le X\le\sqrt y)=\frac{\sqrt y}{2}.
$$

完整的分布函数应写为：

~~~math
F_Y(y)=
\begin{cases}
0,&y\lt 0,\\
\frac{\sqrt y}{2},&0\le y\lt 4,\\
1,&y\ge4.
\end{cases}
~~~

逐段求导，完整的密度函数应写为：

~~~math
f_Y(y)=
\begin{cases}
\frac1{4\sqrt y},&0\lt y\lt 4,\\
0,&\text{其他}.
\end{cases}
~~~

密度在 $y=0$ 的单点值不影响概率，但不能把 $y=0$ 写进 $1/(4\sqrt y)$ 的适用区间。

## Exam Warning｜交卷前检查清单

1. 先写出变换后随机变量的值域。
2. **CDF 三块检查：** 左侧 $0$、中间计算式、右侧 $1$。
3. **PDF 两块检查：** 有效区间公式、其他 $0$。
4. 核查分界点及分母是否为零。
5. 最终答案明确写成覆盖全部实数范围的分段形式。

## Final Review｜期末无提示复测

改为 $X\sim U(-3,3)$，$Y=X^2$，限时独立写出 $F_Y(y)$ 和 $f_Y(y)$ 的全部分段；此次重点是不要在写出有效区间公式后就结束答案。

开卷位置：教材 §2.5（纸质第 65 页起），PPT 第二章第 89—90 页通用步骤、第 93—95 页相关例题。

## Personal Summary｜个人总结

> “把这个放入GitHub，错因是没有直接写完所有情况。”

这次主要计算是对的；遗漏的是最后把 CDF、PDF 补成全定义域上的分段答案。以后遇到“求分布函数 / 密度函数”，必须额外检查两侧的情况，避免因为答案不完整丢分。

## 2026-11-04｜第二章综合抽查第 4 题：同类错误再次发生【反复易错】

**本轮新题：** $X\sim U(0,2)$，$Y=(X-1)^2$，求 $Y$ 的分布函数与密度函数。

**本次手写表现：** 能独立得到 $0\le Y<1$；算出有效区间内 $F_Y(y)=\sqrt y$，并求出有效区间内 $f_Y(y)=1/(2\sqrt y)$。但最后把分布函数写成“$0\le y<1$ 时为 $\sqrt y$，**其他为 $0$**”，误将 $y\ge1$ 的 CDF 写成 $0$。密度部分按支持区间外为 $0$ 的规则正确处理。

**明确错因：** 再次遗漏 CDF 完整分段，而且混淆了分布函数与密度函数在支持区间外的规则。这是同类错误第二次出现，不是变换和求导计算错误。

### 正确结果（GitHub 安全公式格式）

~~~math
F_Y(y)=
\begin{cases}
0,&y\lt0,\\
\sqrt y,&0\le y\lt1,\\
1,&y\ge1.
\end{cases}
~~~

~~~math
f_Y(y)=
\begin{cases}
\frac{1}{2\sqrt y},&0\lt y\lt1,\\
0,&\text{其他}.
\end{cases}
~~~

### 期末考试防错检查（必须做）

- **CDF：** 左 $0$、中间公式、右 $1$。检查极限 $F_Y(-\infty)=0$ 和 $F_Y(+\infty)=1$。
- **PDF：** 支持区间内用密度公式，区间外为 $0$（允许个别点的约定）。
- 绝对不能把 CDF 的“其他”笼统写为 $0$，除非该其他区域真的只包含左侧。
- 做完主体计算后 **再用 10 秒手写完整分段**；若忘记，先问“大于最大可能取值时，$P(Y\le y)$ 是多少？”

**复测标准：** 连续两道不同的变换题，无提示独立写出 CDF/PDF 全部分段且端点正确，才把此错因记为稳定修复。

### Personal Summary｜本人补充

> “这个放进GitHub，真的太容易错了。”

这不是单次笔误：前一题是 CDF/PDF 没写全，这一次更具体地把 CDF 的右端错误写成了 $0$。需要重点纠正“CDF 右端为 $1$，PDF 支持区间外为 $0$”的条件反射。
