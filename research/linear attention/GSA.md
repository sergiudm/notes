Code [flash-linear-attention/fla/models/gsa/modeling_gsa.py at main · fla-org/flash-linear-attention](https://github.com/fla-org/flash-linear-attention/blob/main/fla/models/gsa/modeling_gsa.py)
![[Pasted image 20250205001955.png]]
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
We can write GSA as a two-pass GLA as shown below:
$$
\begin{aligned}
\{\boldsymbol{o}'_t\}_{t=1}^T &= \text{GLA}(\{\boldsymbol{q}_t, \boldsymbol{k}_t, 1 - \boldsymbol{\alpha}_t, \boldsymbol{\alpha}_t, \boldsymbol{1}\}_{t=1}^T) \\
\{\boldsymbol{o}_t\}_{t=1}^T &= \text{GLA}(\{\text{softmax}(\boldsymbol{o}'_t), 1 - \boldsymbol{\alpha}_t, \boldsymbol{v}_t, \boldsymbol{1}, \boldsymbol{\alpha}_t\}_{t=1}^T)
\end{aligned}
$$
Therefore, we can adapt GLA's hardware-efficient chunkwise training algorithm for GSA training.
![[Pasted image 20250205002005.png]]