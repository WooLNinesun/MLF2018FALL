---
export_on_save:
  phantomjs: "pdf"
---

# Machine Learning Foundations Homework #3

B04902083 莊翔旭

@import "./coursera.png"


## problem 2
PLA update $\Rightarrow$
$$
\begin{align*}
    w_{t+1}
    &\leftarrow w_t + [\![sign(w^Tx) \neq y]\!]yx\\
    &\leftarrow w_t + 1 \times
        \begin{cases}
            0                       & \quad\text{if } sign(w^Tx) = y\\
            yx = \nabla(-yw^Tx)     & \quad\text{if } sign(w^Tx) \neq y
        \end{cases}
\end{align*}
$$
So SGD $err(w) = max(0, −yw^Tx)$ with $\eta = 1$ in PLA.

<!-- pagebreak -->
## problem 3
$h_y(x)=\frac{exp(\mathbb{w}^T_y\mathbb{x})}{\sum_{k=1}^K exp(\mathbb{w}_k^T\mathbb{x})}$, and $max \bigg(\frac{1}{N} \prod_{n=1}^N h_{y_n}(\mathbb{x})\bigg)
\to min \bigg(-\frac{1}{N}\sum_{n=1}^N ln(h_{y_n}(\mathbb{x}_n))\bigg)$
$$
\begin{align*}
E_{in}
&= -\frac{1}{N}\sum_{n=1}^N ln(h_{y_n}(\mathbb{x}_n))\\
&= -\frac{1}{N}\sum_{n=1}^N ln\bigg(\frac{exp(\mathbb{w}^T_{y_n}\mathbb{x}_n)}{\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x})}\bigg)\\
&= -\frac{1}{N}\sum_{n=1}^N ln\bigg(exp(\mathbb{w}^T_{y_n}\mathbb{x}_n)\bigg) - ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg) - ln\bigg(exp(\mathbb{w}^T_{y_n}\mathbb{x}_n)\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg) - \mathbb{w}^T_{y_n}\mathbb{x}_n\\
\\\\
\frac{\partial E_{in}}{\partial \mathbb{w}_i}
&= \frac{\partial (\ \frac{1}{N}\sum_{n=1}^N ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg) - \mathbb{w}^T_{y_n}\mathbb{x}_n\ )}{\partial \mathbb{w}_i} \\
&= \frac{1}{N}\sum_{n=1}^N \frac{\partial (\ ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg) - \mathbb{w}^T_{y_n}\mathbb{x}_n\ )}{\partial \mathbb{w}_i} \\
&= \frac{1}{N}\sum_{n=1}^N \bigg( \frac{\partial (\ ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg)\ )}{\partial \mathbb{w}_i} - \frac{\partial (\ \mathbb{w}^T_{y_n}\mathbb{x}_n\ )}{\partial \mathbb{w}_i} \bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( \frac{\partial (\ ln\bigg(\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\bigg)\ )}{\partial \mathbb{w}_i} - [\![y_n=i]\!] \times \mathbb{x}_n\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( \frac{1}{\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)} \times \frac{\partial (\ \sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)\ )}{\partial \mathbb{w}_i} - [\![y_n=i]\!] \times \mathbb{x}_n\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( \frac{1}{\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)} \times exp(\mathbb{w}_i^T\mathbb{x}_n) \times \mathbb{x}_n - [\![y_n=i]\!] \times \mathbb{x}_n\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( \frac{exp(\mathbb{w}_i^T\mathbb{x}_n)}{\sum_{k=1}^Kexp(\mathbb{w}_k^T\mathbb{x}_n)} \times \mathbb{x}_n - [\![y_n=i]\!] \times \mathbb{x}_n\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( h_i(\mathbb{x}) \times \mathbb{x}_n - [\![y_n=i]\!] \times \mathbb{x}_n\bigg)\\
&= \frac{1}{N}\sum_{n=1}^N \bigg( (h_i(\mathbb{x}) - [\![y_n=i]\!]) \times \mathbb{x}_n\bigg)_\sharp\\
\end{align*}
$$

<!-- pagebreak -->
## problem 4
@import "./linechart1.png"
@import "./linechart3.png"

第一張圖可以注意到 GD 的 Error 很會就降下去了， SGD 的 Error 在尾端才有往下降的感覺。為了比較，在畫一張 SGD 在 $\eta = 0.002$ 的圖，可以發現這次 SGD 的 Error 比較早往下降。可以發現在 $\eta$ 很小的時候會機器學期的確會學的比較慢。

<!-- pagebreak -->
## problem 5
@import "./linechart2.png"
@import "./linechart4.png"

可以發現和第四題一樣的結論，且 Eins 和 Eout 不會差太多，表示和預期的一樣有學習到

## Bonus
