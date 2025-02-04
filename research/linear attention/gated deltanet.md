Code [NVlabs/GatedDeltaNet: Official PyTorch Implementation of Gated Delta Networks: Improving Mamba2 with Delta Rule](https://github.com/NVlabs/GatedDeltaNet/tree/main)
![[Pasted image 20250205003408.png]]
## Memory update rule
$$
\begin{equation}
S_{t}=S_{t-1}(\alpha_{t}(\mathbf{I}-\beta_{t}k_{t}k_{t}^{T}))+\beta_{t}v_{t}k_{t}^{T}
\end{equation}
$$
This formulation unifies the advantages of both gating mechanisms and the delta rule: the gating term enables adaptive memory management, while the delta update structure facilitates effective key-value association learning.
### Extended WY representation
$$
\begin{align*}
S_{t+1} &= S_{t}(\alpha_{t+1}(I-\beta_{t+1}k_{t+1}k_{t+1}^{T}))+\beta_{t+1}v_{t+1}k_{t+1}^{T} \\
&= \alpha_{t+1}(\sum_{i=1}^{t}\frac{\gamma_{t}}{\gamma_{i}}u_{i}k_{i}^{T})-\alpha_{t+1}\beta_{t+1}(\sum_{i=1}^{t}\frac{\gamma_{t}}{\gamma_{i}}u_{i}k_{i}^{T}k_{i}k_{t+1}^{T})+\beta_{t+1}v_{t+1}k_{t+1}^{T} \\
&= \sum_{i=1}^{t}\frac{\gamma_{t+1}}{\gamma_{i}}u_{i}k_{i}^{T}+\beta_{t+1}(v_{t+1}-\sum_{i=1}^{t}\frac{\gamma_{t+1}}{\gamma_{i}}u_{i}k_{i}^{T}k_{i}k_{t+1})k_{t+1}^{T} \\
&= \sum_{i=1}^{t}\frac{\gamma_{t+1}}{\gamma_{i}}u_{i}k_{i}^{T}+\frac{\gamma_{t+1}}{\gamma_{t+1}}u_{t+1}k_{t+1}^{T} \\
&= \sum_{i=1}^{t+1}\frac{\gamma_{t+1}}{\gamma_{i}}u_{i}k_{i}^{T}
\end{align*}
$$
