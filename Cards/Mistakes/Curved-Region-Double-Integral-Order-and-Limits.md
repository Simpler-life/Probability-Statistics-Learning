---
type: mistake
subject: Probability and Mathematical Statistics
chapter: Chapter 3
topic: [Joint Density, Double Integral, Region, Order of Integration, Marginal Density]
tags: [double-integral, integration-order, limits, curved-region, marginal-density, support-restriction, original-quiz, final-review-priority]
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

历年题完整题干另有求边际密度、条件概率、变量函数分布及独立性判断等小问；**本轮已练习第（1）、（2）问，第（2）问边际密度第一次做错，尚待复测。**

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

## 第（2）问：边际密度漏掉联合密度的非零区域【真实错误】

保持 $y$ 不动、对 $x$ 积分：

~~~math
f_Y(y)=\int_{y^2}^{4}f(x,y)\,dx,
\qquad -2\lt y\lt2.
~~~

手写先正确写出边际密度的全轴积分定义，但代入时把联合密度的常数 $3/32$ 误当成整个实数轴上都成立，**没有限制 $y^2\lt x\lt4$ 这一非零区域**，结果错误地得到常数 $3/8$。

这里的关键不是积分公式记错，而是 $f(x,y)$ **在区域外为零**。固定 $y$ 时，只有 $y^2\lt x\lt4$ 才贡献概率；当 $y$ 不在 $(-2,2)$ 内，整个积分为零。

正确的完整边际密度：

~~~math
f_Y(y)=
\begin{cases}
\frac{3}{32}(4-y^2),&-2\lt y\lt2,\\
0,&\text{其他}.
\end{cases}
~~~

考试写法：先写 $f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)\,dx$，随后对 $-2\lt y\lt2$ 改为 $\int_{y^2}^{4}\frac3{32}\,dx$，最后补全其他情况。

**验证：** 结果应随横向切片的长度 $4-y^2$ 变化，且积分为 1。若写成常数 $3/8$，在 $(-2,2)$ 上的总积分将为 $3/2$，不满足归一化。

**实际状态：** 第（1）问已重新独立算对 $c=3/32$；第（2）问首次作答错误，尚未独立复测通过。


## Exam Writing Checklist｜考场防错

1. 先画出非零密度区域 $D$，标注两条边界。
2. 看最右端微分：$dx\,dy$ 表示先横向对 $x$ 积分；$dy\,dx$ 表示先竖向对 $y$ 积分。
3. 固定外层变量，沿内层变量方向切片，找入点和出点。
4. **内层积分界限可以含外层变量，外层界限不能含内层变量。**
5. 交换积分次序必须重新写两层界限，不能只交换 $dx$ 与 $dy$。
6. 边际密度公式虽然写成全轴积分，但代入分段联合密度时必须缩到非零区域。
7. 边际密度只积分掉另外一个变量，并补全有效区间外为 $0$ 的分段。

## Open-Book Location

教材第三章 §3.3 二维连续型随机变量，找到联合密度归一化、按区域积分与边际密度例题；结合个人 GitHub 的 A20（抛物线边际密度）和 B4（三角区域事件积分）。本次未重新核验具体例题编号，不虚构页码。

## Final Review｜期末无提示复测

- **原题重做：** 在 $y^2\lt x\lt4$ 上不看答案写两种积分次序，计算 $c$，再独立写完整 $f_Y(y)$。
- **变式：** $D=\{(x,y):x^2\lt y\lt1\}$，写出 $dx\,dy$ 和 $dy\,dx$ 两种积分次序的上下限（先不要求计算）。
- 必须解释：为什么外层积分限不能再依赖内层变量。

## Personal Summary｜个人总结

> “怎么这个积分好像有点问题啊，但是这个先算后算不是应该是一样的，可以交换的吗？”

我的区域图画得基本正确，真正出错的是把“可以换序”理解成“上下限可以不变或随意组合”。以后先确定**切片方向和区域交点**，再写积分界限；换序要重新从区域出发。随后求边际密度时，又将联合密度常数误用于整个积分区域，得出错误的常数 $3/8$。两次错误都与“没有紧扣非零积分区域”有关。仍待无提示独立复测，状态保留为 review。
