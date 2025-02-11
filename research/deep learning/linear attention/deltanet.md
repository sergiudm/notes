Code [flash-linear-attention/fla/layers/delta_net.py at main · fla-org/flash-linear-attention](https://github.com/fla-org/flash-linear-attention/blob/main/fla/layers/delta_net.py)
![[Pasted image 20250204232232.png]]
## Delta rule
$$
\boldsymbol{v}_{t}^{\mathrm{new}} = \beta_{t} \boldsymbol{v}_{t} + (1 - \beta_{t}) \boldsymbol{v}_{t}^{\mathrm{old}}, \qquad \boldsymbol{S}_{t} = \underbrace{\boldsymbol{S}_{t-1} - \boldsymbol{v}_{t}^{\mathrm{old}} \boldsymbol{k}_{t}^{\top}}_{\text{remove}} + \underbrace{\boldsymbol{v}_{t}^{\mathrm{new}} \boldsymbol{k}_{t}^{\top}}_{\text{write}}, \qquad
\boldsymbol{o}_t = \boldsymbol{S}_t \boldsymbol{q}_t
$$
Where $\boldsymbol{v}_{t}^{\mathrm{old}} = \boldsymbol{S}_{t-1} \boldsymbol{k}_{t}, \beta_t = \sigma(\mathbf{W}_{\beta} \boldsymbol{x}_t) \in (0, 1)$

>when $\beta_t = 1$, the old value is completely removed and $\boldsymbol{v}^{new}_t = \boldsymbol{v}_t$; when $\beta_t = 0$, the memory remains unmodified and we have $\boldsymbol{S}_t = \boldsymbol{S}_{t−1}$
>The method derives its name from the core principle of updating weights based on the “delta” (difference) between the prediction $\boldsymbol{S}_{t−1}\boldsymbol{k}_{t}$ and the target $\boldsymbol{v}_t$

This process can also be regarded as optimizing an online regression loss using a single step of SGD
$$
\mathcal{L}_t(\mathbf{S}) = \frac{1}{2} \| \mathbf{S}\boldsymbol{k}_t - \boldsymbol{v}_t \|^2, \quad \mathbf{S}_t = \mathbf{S}_{t-1} - \beta_t \nabla_{\mathbf{S}_{t-1}} \mathcal{L}_t(\mathbf{S}_{t-1}) = \mathbf{S}_{t-1} - \beta_t (\mathbf{S}_{t-1} \boldsymbol{k}_t - \boldsymbol{v}_t) \boldsymbol{k}_t^\top
$$
## Parallelizing DeltaNet Across the Sequence Dimension
$$
\begin{aligned}
\mathbf{S}_n &= \mathbf{S}_{n-1} (\mathbf{I} - \beta_n \boldsymbol{k}_n \boldsymbol{k}_n^\top) + \beta_n \boldsymbol{v}_n \boldsymbol{k}_n^\top \\
&= \left( \sum_{t=1}^{n-1} \boldsymbol{u}_t \boldsymbol{k}_t^\top \right) (\mathbf{I} - \beta_n \boldsymbol{k}_n \boldsymbol{k}_n^\top) + \beta_n \boldsymbol{v}_n \boldsymbol{k}_n^\top \\
&= \sum_{t=1}^{n-1} \boldsymbol{u}_t \boldsymbol{k}_t^\top - \left( \sum_{t=1}^{n-1} \boldsymbol{u}_t \boldsymbol{k}_t^\top \right) \beta_n \boldsymbol{k}_n \boldsymbol{k}_n^\top + \beta_n \boldsymbol{v}_n \boldsymbol{k}_n^\top \\
&= \sum_{t=1}^{n-1} \boldsymbol{u}_t \boldsymbol{k}_t^\top + \underbrace{\left( \beta_n \boldsymbol{v}_n - \beta_n \sum_{t=1}^{n-1} \boldsymbol{u}_t (\boldsymbol{k}_t^\top \boldsymbol{k}_n) \right)}_{\boldsymbol{u}_n} \boldsymbol{k}_n^\top \\
&= \sum_{t=1}^{n} \boldsymbol{u}_t \boldsymbol{k}_n^\top
\end{aligned}
$$




