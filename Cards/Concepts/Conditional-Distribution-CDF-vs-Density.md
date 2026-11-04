---
type: concept
subject: Probability and Mathematical Statistics
chapter: Chapter 3
status: review
exam_priority: high
---

# 条件分布函数与条件密度的区别

本次学习提问：条件密度的比值公式能否推广到条件分布函数？属于主动澄清，不是已确认的错题。

普通条件概率（分母正）：$P(A\mid B)=P(A\cap B)/P(B)$。

对于二维连续型随机变量，$f_X(x)>0$ 时：

$$
f_{Y\mid X}(y\mid x)=\frac{f_{X,Y}(x,y)}{f_X(x)}
$$

条件分布函数需要积分：

$$
F_{Y\mid X}(y\mid x)=\int_{-\infty}^{y}f_{Y\mid X}(t\mid x)\,dt
$$

而 $F_{X,Y}(x,y)/F_X(x)$ 在分母正时对应 $P(Y\le y\mid X\le x)$，不是 $P(Y\le y\mid X=x)$。

历年题 $f(x,y)=3/32$（$y^2<x<4$），固定 $X=1$，条件密度在 $-1<y<1$ 时为 $1/2$，区间外为 $0$，相应条件分布函数在 $y<-1$ 为 $0$，在 $-1\le y<1$ 为 $(y+1)/2$，在 $y\ge1$ 为 $1$。

考场提醒：先辨清条件 $X=x$ 与 $X\le x$，再区分条件密度与条件分布函数；CDF 写全左 0、右 1。教材第三章 §3.1—§3.3。
