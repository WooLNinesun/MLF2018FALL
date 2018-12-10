---
export_on_save:
  phantomjs: "pdf"
---

# Machine Learning Foundations Homework #1

B04902083 莊翔旭

@import "./coursera.png"

## problem 2

題目可以轉換成 N+1 ~ N+L 有多少個偶數:
$$
\begin{align*}
&\frac{1}{L} * ( \text{N+1 ~ N+L 有多少個偶數} )\\
= &\frac{1}{L} * ( ( \text{1 ~ N+L 有多少個偶數} ) - ( \text{1 ~ N 有多少個偶數} ) )\\
= &\frac{1}{L} * ( \frac{\lfloor N+L \rfloor}{2} - \frac{\lfloor N \rfloor}{2} )
\end{align*}
$$

## problem 3

$$
\begin{align*}
\mathbb{E}_f \Big\{ E_{OTS}(\mathcal{A}(\mathcal{D}), f) \Big\}
&= \frac{1}{2^L}\sum_{i = 1}^{2^L}\frac{1}{L}\sum_{l = 1}^{L}[\![ g(X_{N+l}) \neq f_i(X_{N+l}) ]\!]\\
&= \frac{1}{2^L}\frac{1}{L}\sum_{l = 1}^{L}\sum_{i = 1}^{2^L}[\![ g(X_{N+l}) \neq f_i(X_{N+l}) ]\!]\\
&= \frac{1}{2^L}\frac{1}{L}\sum_{l = 1}^{L}2^{L-1} \quad (\because 對和錯各佔一半)\\
&= \frac{1}{2} \Rightarrow 常數，和演算法無關
\end{align*}
$$

<!-- pagebreak -->

## problem 4

μ = 0.8

> what is the probability of ν ≤ 0.1?
> 
> $C^0_{10} * 0.2^{10} + C^1_{10} * 0.8 * 0.2^9 = 0.2^{10} + 10 * 0.8 * 0.2^9 = 4.2 * 10^{-6}$

> what is the probability of ν ≥ 0.9?
>
> $C^0_{10} * 0.8^{10} + C^1_{10} * 0.2 * 0.8^9 = 0.8^{10} + 10 * 0.2 * 0.8^9 = 0.376$

## problem 5

題目可以轉換成拿到只有 A 和 D 的機率，每個骰子的機率都一樣，所以是 $(\frac{2}{4})^5 = \frac{1}{32}$

## problem 6

| number| 1  | 2  | 3  | 4  | 5  | 6  |
|-------|----|----|----|----|----|----|
| green | AD | BD | AD | BC | AC | BC |

總共有 AC, BC, AD, BD 四種組合，然後考慮到 ABCD 各個重複計算 $(\frac{2}{4})^5 * 4 - (\frac{1}{4})^5 * 4 = \frac{31}{256}$

比較之後可以觀察到單一數字都是綠色的機率都是 $\frac{1}{32}$，但是它們在一起計算會互相影響，不是獨立事件

## problem 7

* average number of updates:  40.476
@import "./histogram.png"

## Bonus
