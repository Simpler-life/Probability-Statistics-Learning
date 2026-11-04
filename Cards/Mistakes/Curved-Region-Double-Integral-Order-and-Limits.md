---
type: mistake
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Joint Density, Double Integral, Region, Order of Integration, Marginal Density]
tags: [double-integral, integration-order, limits, curved-region, original-quiz, final-review-priority]
difficulty: medium
exam_priority: high
status: review
source:
  - 2026-11-04 历年小测原题及本人手写解答截图
related:
  - Cards/Problems/A20-Marginal-Density-on-Curved-Region.md
  - Cards/Problems/B4-Triangular-Region-Joint-Density-Integration.md
created: 2026-11-04
updated: 2026-11-04
---

# 历年小测｜曲线区域二重积分换序与上下限

## Original Problem｜原题与本轮练习范围

设二维连续型随机变量 $(X,Y)$ 的联合密度为

~~~math
f(x,y)=
\begin{cases}
c,&y^2\lt x\lt4,\\
0,&\text{其他}.
\end{cases}
~~~

历年题完整题干另有求边际密度、条件概率、变量函数分布及独立性判断等小问；**本轮实际练习的是第（1）问求 $c$，接下来才要求 $f_Y(y)$**。

## Attempt / Wrong Idea｜真实首次作答

用户先画了开口向右的抛物线 $x=y^2$ 与直线 $x=4$ 围成的区域，图形思路基本正确。

但手写积分混用了两种次序：把 $x$ 的界限 $y^2,4$ 放在外层，而在内层使用 $y$ 的常数界限 $-2,2$，相当于试图写成下面这样：

~~~math
\int_{y^2}^{4}\int_{-2}^{2}c\,dy\,dx.
~~~

这并不是对所给区域的有效积分写法：外层 $dx$ 的界限不能依赖已在内层积分掉的 $y$；并且当固定 $x$ 时，$y$ 不能始终从 $-2$ 到 $2$。

用户实际疑问：“怎么这个积分好像有点问题啊，但是这个先算后算不是应该是一样的，可以交换的吗？”

**错误类型：** 知道二重积分可以交换次序，但误以为交换次序时可以保留或拼接原有上下限；根本问题是“同一区域的两种切片”没有区分清楚，而非多项式积分运算能力差。

## Correct Idea｜同一区域的两种正确写法

原始区域为

~~~math
D=\{(x,y):y^2\lt x\lt4\}.
~~~

### 方法 A：先积 $x$，后积 $y$（横切）

固定 $y$：$y^2\lt x\lt4$。要存在这样的 $x$，须 $y^2\lt4$，因此 $-2\lt y\lt2$。

~~~math
1=\int_{-2}^{2}\int_{y^2}^{4}c\,dx\,dy
=c\int_{-2}^{2}(4-y^2)\,dy
=\frac{32}{3}c.
~~~

### 方法 B：先积 $y$，后积 $x$（竖切）

从 $y^2\lt x$ 得 $-\sqrt{x}\lt y\lt\sqrt{x}$，对应 $0\lt x\lt4$。

~~~math
1=\int_0^4\int_{-\sqrt{x}}^{\sqrt{x}}c\,dy\,dx
=2c\int_0^4\sqrt{x}\,dx
=\frac{32}{3}c.
~~~

两种写法对**同一块区域**积分，因此结果相同：

~~~math
\boxed{c=\frac{3}{32}}.
~~~

## Transfer｜第（2）问边际密度（留待本人无提示作答）

保持 $y$ 不动、对 $x$ 积分：

~~~math
f_Y(y)=\int_{y^2}^{4}f(x,y)\,dx,
\qquad -2\lt y\lt2.
~~~

考试时必须补写密度支持区间外为 $0$，且不应再对 $y$ 积分。此处只记方法，**不把第（2）问误记为用户已经独立解对**。

## Exam Writing Checklist｜考场防错

1. 先画出非零密度区域 $D$，标注两条边界。
2. 看最右端微分：$dx\,dy$ 表示先横向对 $x$ 积分；$dy\,dx$ 表示先竖向对 $y$ 积分。
3. 固定外层变量，沿内层变量方向切片，找入点和出点。
4. **内层积分界限可以含外层变量，外层界限不能含内层变量。**
5. 交换积分次序必须重新写两层界限，不能只交换 $dx$ 与 $dy$。
6. 边际密度只积分掉另外一个变量，并补全有效区间外为 $0$ 的分段。

## Open-Book Location

教材第三章 §3.3 二维连续型随机变量，找到联合密度归一化、按区域积分与边际密度例题；结合个人 GitHub 的 A20（抛物线边际密度）和 B4（三角区域事件积分）。本次未重新核验具体例题编号，不虚构页码。

## Final Review｜期末无提示复测

- **原题重做：** 在 $y^2\lt x\lt4$ 上不看答案写两种积分次序，计算 $c$，再独立写完整 $f_Y(y)$。
- **变式：** $D=\{(x,y):x^2\lt y\lt1\}$，写出 $dx\,dy$ 和 $dy\,dx$ 两种积分次序的上下限（先不要求计算）。
- 必须解释：为什么外层积分限不能再依赖内层变量。

## Personal Summary｜个人总结

> “怎么这个积分好像有点问题啊，但是这个先算后算不是应该是一样的，可以交换的吗？”

我的区域图画得基本正确，真正出错的是把“可以换序”理解成“上下限可以不变或随意组合”。以后先确定**切片方向和区域交点**，再写积分界限；换序要重新从区域出发。仍待无提示独立复测，状态保留为 review。
