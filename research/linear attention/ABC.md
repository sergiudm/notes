$$
\begin{aligned}
\tilde{\mathbf{K}}_t &= \tilde{\mathbf{K}}_{t-1} + \boldsymbol{\phi}_t \otimes \boldsymbol{k}_t \in \mathbb{R}^{m \times d}, \quad \tilde{\mathbf{V}}_t = \tilde{\mathbf{V}}_{t-1} + \boldsymbol{\phi}_t \otimes \boldsymbol{v}_t \in \mathbb{R}^{m \times d}, \quad \boldsymbol{o}_t = \tilde{\mathbf{V}}_t^T f(\tilde{\mathbf{K}}_t^T \boldsymbol{q}_t) \in \mathbb{R}^d \\
\text{where} \\
&\boldsymbol{\alpha}_i = \exp{(\mathbf{W}_{\phi} \boldsymbol{x}_i)} \in \mathbb{R}^m, \quad \boldsymbol{\phi}_i = \frac{\boldsymbol{\alpha}_i}{\sum_{j=1}^i \boldsymbol{\alpha}_j} \in (0, 1)^m
\end{aligned}
$$
## ABC as two-pass linear attention
Denote the linear attention operator that computes $\boldsymbol{o}_i$ from $\boldsymbol{q}_i, \boldsymbol{k}_i$ and $\boldsymbol{v}_i$ by $\{\boldsymbol{o}_i\}_{i=1}^T = \text{LA}(\{\boldsymbol{q}_i, \boldsymbol{k}_i, \boldsymbol{v}_i\}_{i=1}^T)$. The ABC operations can be written as
$$
\begin{aligned}
\{\boldsymbol{o}'_i\}_{i=1}^T &= \text{LA}(\{\boldsymbol{q}_i, \boldsymbol{k}_i, \boldsymbol{\phi}_i\}_{i=1}^T), \\
\{\boldsymbol{o}_i\}_{i=1}^T &= \text{LA}(\{\text{softmax}(\boldsymbol{o}'_i), \boldsymbol{\phi}_i, \boldsymbol{v}_i\}_{i=1}^T),
\end{aligned}
$$
where $\boldsymbol{o}'_i \in \mathbb{R}^m, \boldsymbol{o}_i \in \mathbb{R}^d$. Therefore, ABC can enjoy hardware-efficient linear-time chunkwise training.