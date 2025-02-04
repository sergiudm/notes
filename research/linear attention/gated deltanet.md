Code [NVlabs/GatedDeltaNet: Official PyTorch Implementation of Gated Delta Networks: Improving Mamba2 with Delta Rule](https://github.com/NVlabs/GatedDeltaNet/tree/main)
$$
\begin{equation}
S_{t}=S_{t-1}(\alpha_{t}(\mathbf{I}-\beta_{t}k_{t}k_{t}^{T}))+\beta_{t}v_{t}k_{t}^{T}
\end{equation}
$$
This formulation unifies the advantages of both gating mechanisms and the delta rule: the gating term enables adaptive memory management, while the delta update structure facilitates effective key-value association learning.