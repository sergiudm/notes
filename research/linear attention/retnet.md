## Retention in a recurrent manner
$$
\begin{aligned}
\boldsymbol{s}_n &= A \boldsymbol{s}_{n-1} + K_n^\top v_n, \quad & A \in \mathbb{R}^{d \times d}, K_n \in \mathbb{R}^{1 \times d} \\
o_n &= Q_n \boldsymbol{s}_n = \sum_{m=1}^n Q_n A^{n-m} K_m^\top v_m, \quad & Q_n \in \mathbb{R}^{1 \times d}
\end{aligned}
$$
