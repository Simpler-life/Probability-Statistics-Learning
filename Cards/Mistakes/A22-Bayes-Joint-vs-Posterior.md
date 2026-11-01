---
type: mistake
subject: Probability and Mathematical Statistics
topic:
  - Total Probability
  - Bayes Formula
tags:
  - bayes
  - total-probability
  - conditional-probability
  - joint-probability
difficulty: medium
exam_priority: high
status: review
related: []
created: 2026-11-01
updated: 2026-11-01
---

# A22：把“来自某厂且为优质品”误当成“已知优质品后来自某厂”

## Original Problem｜完整原题

A22. 某公司从甲、乙、丙三家工厂购进同一型号产品，数量之比为 $6:5:4$。已知三家工厂产品的优质品率分别为 $85\%$、$90\%$、$80\%$。若从全部产品中随机取一件，发现是优质品，求该产品来自工厂甲、乙、丙的概率分别是多少，判断最有可能由哪家工厂生产。

## Context

我先算了：

```math
\frac{6}{15}\cdot0.85,
\qquad
\frac{5}{15}\cdot0.90,
\qquad
\frac{4}{15}\cdot0.80
```

但对这些量代表什么，以及为什么还需要再除一次总的优质品概率产生了混淆。

## Wrong Idea

我把：

```math
P(\text{甲})P(\text{优}\mid\text{甲})
```

误当成了：

```math
P(\text{甲}\mid\text{优})
```

实际上前者是联合概率：

```math
P(\text{甲}\cap\text{优})
```

而题目问的是“已经知道是优质品以后，来自甲厂的概率”，这是后验条件概率。

## Correct Idea

设：

- $A_1$：来自甲厂；
- $A_2$：来自乙厂；
- $A_3$：来自丙厂；
- $B$：抽到优质品。

先验概率：

```math
P(A_1)=\frac{6}{15}=\frac25
```

```math
P(A_2)=\frac{5}{15}=\frac13
```

```math
P(A_3)=\frac{4}{15}
```

条件优质率：

```math
P(B\mid A_1)=\frac{17}{20},
\qquad
P(B\mid A_2)=\frac9{10},
\qquad
P(B\mid A_3)=\frac45
```

三条“来源且优质”的联合概率分别为：

```math
P(A_1\cap B)
=
\frac25\cdot\frac{17}{20}
=
\frac{17}{50}
```

```math
P(A_2\cap B)
=
\frac13\cdot\frac9{10}
=
\frac3{10}
```

```math
P(A_3\cap B)
=
\frac4{15}\cdot\frac45
=
\frac{16}{75}
```

用全概率公式得到优质品的总概率：

```math
P(B)
=
\frac{17}{50}
+
\frac3{10}
+
\frac{16}{75}
=
\frac{51+45+32}{150}
=
\frac{128}{150}
=
\frac{64}{75}
```

再用贝叶斯公式。

甲厂：

```math
P(A_1\mid B)
=
\frac{\frac{17}{50}}{\frac{64}{75}}
=
\frac{51}{128}
```

乙厂：

```math
P(A_2\mid B)
=
\frac{\frac3{10}}{\frac{64}{75}}
=
\frac{45}{128}
```

丙厂：

```math
P(A_3\mid B)
=
\frac{\frac{16}{75}}{\frac{64}{75}}
=
\frac14
=
\frac{32}{128}
```

因此：

```math
\frac{51}{128}
>
\frac{45}{128}
>
\frac{32}{128}
```

最有可能来自甲厂。

## Key Mechanism

这类题的固定结构是：

```math
\text{先验概率}
\times
\text{条件概率}
=
\text{联合概率}
```

然后：

```math
\text{后验概率}
=
\frac{\text{对应联合概率}}{\text{证据的总概率}}
```

也就是：

```math
P(A_i\mid B)
=
\frac{P(A_i)P(B\mid A_i)}
{\sum_j P(A_j)P(B\mid A_j)}
```

## Trigger

看到题目出现：

- “来自多个来源”；
- “各来源比例不同”；
- “各来源合格率 / 优质率 / 命中率不同”；
- “已经发现某个结果，反推来自哪个来源”；

就要立刻想到：**全概率公式 + 贝叶斯公式**。

## Exam Warning

最容易混淆的三个量：

```math
P(A_i)
```

表示“来自第 $i$ 个来源”。

```math
P(B\mid A_i)
```

表示“已知来自第 $i$ 个来源，是优质品的概率”。

```math
P(A_i\mid B)
```

表示“已经知道是优质品，反推来自第 $i$ 个来源的概率”。

它们不能互换。

## Personal Summary｜个人总结

我这次已经会先用“来源比例 × 该厂优质率”去算，但我一开始没有分清这个结果到底是什么。现在我知道：

$P(\text{甲})P(\text{优}\mid\text{甲})$ 算出来的是“甲厂且优质”的联合概率，不是“已知优质以后来自甲厂”的概率。

真正的贝叶斯反推还要再除以所有来源产生优质品的总概率。以后看到“已经发现是某类产品，再问它来自哪里”，我要意识到条件方向已经反过来了。
