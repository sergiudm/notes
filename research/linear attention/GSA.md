Code [flash-linear-attention/fla/models/gsa/modeling_gsa.py at main · fla-org/flash-linear-attention](https://github.com/fla-org/flash-linear-attention/blob/main/fla/models/gsa/modeling_gsa.py)
For each memory slot, the update rule is a simple gated RNN with a scalar data-dependent gating value $\alpha_i \in [0, 1]$,
$$
(\tilde{\mathbf{K}}_t)_i = \alpha_i (\tilde{\mathbf{K}}_{t-1})_i + (1 - \alpha_i) \boldsymbol{k}_t \in \mathbb{R}^d, \quad (\tilde{\mathbf{V}}_t)_i = \alpha_i (\tilde{\mathbf{V}}_{t-1})_i + (1 - \alpha_i) \boldsymbol{v}_t \in \mathbb{R}^d
$$
And these can be written in matrix form, which is reminiscent of HGRN 2.
$$
\begin{aligned}
\tilde{\mathbf{K}}_t &= \text{Diag}(\boldsymbol{\alpha}_t) \cdot \tilde{\mathbf{K}}_{t-1} + (1 - \boldsymbol{\alpha}_t) \otimes \boldsymbol{k}_t \in \mathbb{R}^{m \times d} \\
\tilde{\mathbf{V}}_t &= \text{Diag}(\boldsymbol{\alpha}_t) \cdot \tilde{\mathbf{V}}_{t-1} + (1 - \boldsymbol{\alpha}_t) \otimes \boldsymbol{v}_t \in \mathbb{R}^{m \times d} \\
\boldsymbol{o}_t &= \tilde{\mathbf{V}}_t^T \text{softmax}(\tilde{\mathbf{K}}_t^T \boldsymbol{q}_t) \in \mathbb{R}^d
\end{aligned}
$$
## GSA as two-pass GLA
