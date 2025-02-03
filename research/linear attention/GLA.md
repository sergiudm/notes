Code: [flash-linear-attention/fla/models/gla/modeling_gla.py at main · fla-org/flash-linear-attention](https://github.com/fla-org/flash-linear-attention/blob/main/fla/models/gla/modeling_gla.py)
## Linear attention
$$
q_t, k_t, v_t = x_t W_Q, x_t W_K, x_t W_V,
$$
$$
o_t = \frac{\sum_{i=1}^t \phi(\boldsymbol{q}_t) \phi(\boldsymbol{k}_i)^\top \boldsymbol{v}_i}{\sum_{i=1}^t \phi(\boldsymbol{q}_t) \phi(\boldsymbol{k}_i)^\top} = \frac{\phi(\boldsymbol{q}_t) \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top \boldsymbol{v}_i}{\phi(\boldsymbol{q}_t) \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top}
$$
### Recurrent form
$$
\begin{aligned}
&\text{Letting } \boldsymbol{S}_t = \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top \boldsymbol{v}_i \text{ and } \boldsymbol{z}_t = \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top \text{ where } \\
&\boldsymbol{S}_t \in \mathbb{R}^{d \times d}, \boldsymbol{z}_t \in \mathbb{R}^{d \times 1}, \text{ we can rewrite the above as an RNN,} \\
&\boldsymbol{S}_t = \boldsymbol{S}_{t-1} + \phi(\boldsymbol{k}_t)^\top \boldsymbol{v}_t, \boldsymbol{z}_t = \boldsymbol{z}_{t-1} + \phi(\boldsymbol{k}_t)^\top, \boldsymbol{o}_t = \frac{\phi(\boldsymbol{q}_t) \boldsymbol{S}_t}{\phi(\boldsymbol{q}_t) \boldsymbol{z}_t}.
\end{aligned}
$$
#### Simplification
$$
\boldsymbol{S}_t = \boldsymbol{S}_{t-1} + \boldsymbol{k}_t^\top \boldsymbol{v}_t, \quad \boldsymbol{o}_t = \boldsymbol{q}_t \boldsymbol{S}_t
$$

## Gated Linear Attention
### Recurrent form
$$
\boldsymbol{S}_t = \boldsymbol{G}_t \odot \boldsymbol{S}_{t-1} + \boldsymbol{k}_t^\top \boldsymbol{v}_t

$$
Where $$
\boldsymbol{G}_t \in (0, 1)^{d_k \times d_v}
$$
