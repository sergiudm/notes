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

## Gated Linear Attention Layer
### Recurrent form
$$
\boldsymbol{S}_t = \boldsymbol{G}_t \odot \boldsymbol{S}_{t-1} + \boldsymbol{k}_t^\top \boldsymbol{v}_t

$$
Where 
$$
\boldsymbol{G}_t \in (0, 1)^{d_k \times d_v}
$$
#### Parameterization of $G_t$
$$
\boldsymbol{S}_t = (\boldsymbol{\alpha}_t^\top \boldsymbol{1}) \odot \boldsymbol{S}_{t-1} + \boldsymbol{k}_t^\top \boldsymbol{v}_t = \text{Diag}(\boldsymbol{\alpha}_t) \boldsymbol{S}_{t-1} + \boldsymbol{k}_t^\top \boldsymbol{v}_t
$$
### Parallel form
$$
\boldsymbol{S}_t = \sum_{i=1}^t \left( \left( \prod_{j=i+1}^t \boldsymbol{\alpha}_j^\top \boldsymbol{1} \right) \odot \boldsymbol{k}_i^\top \boldsymbol{v}_i \right)
$$
$$
\begin{aligned}
&\text{Letting } \boldsymbol{b}_t := \prod_{j=1}^t \boldsymbol{\alpha}_j, \text{ we can rewrite the above as } \\
&\boldsymbol{o}_t = \boldsymbol{q}_t \boldsymbol{S}_t = \boldsymbol{q}_t \sum_{i=1}^t \left( \left( \frac{\boldsymbol{b}_t}{\boldsymbol{b}_i} \right)^\top \boldsymbol{1} \right) \odot \boldsymbol{k}_i^\top \boldsymbol{v}_i \\
&= \sum_{i=1}^t (\boldsymbol{q}_t \odot \boldsymbol{b}_t) \left( \frac{\boldsymbol{k}_i}{\boldsymbol{b}_i} \right)^\top \boldsymbol{v}_i
\end{aligned}
$$
where the division is element-wise
$$
\mathbf{O} = \left( \underbrace{(\mathbf{Q} \odot \mathbf{B}) \left( \frac{\mathbf{K}}{\mathbf{B}} \right)^\top}_{\mathbf{P}} \odot \mathbf{M} \right) \mathbf{V}
$$
Where $\mathbf{B} \in (0,1)^{L \times d}$

To prevent the explode of  $\frac{K}{B}$
$$
\mathbf{P}_{ij} = \sum_{k=1}^d \mathbf{Q}_{ik} \mathbf{K}_{jk} \text{exp}(\log \mathbf{B}_{ik} - \log \mathbf{B}_{jk}), \quad i \geq j,
$$
where $k$ denotes feature indices

## Multi-head GLA layer
$$
\begin{aligned}
\boldsymbol{S}^h_t &= \left( (\boldsymbol{\alpha}^h_t)^\top \boldsymbol{1} \right) \odot \boldsymbol{S}^h_{t-1} + \boldsymbol{k}^{h \top}_t \boldsymbol{v}^h_t \in \mathbb{R}^{d'_k \times d'_v}, \\
\boldsymbol{o}^h_t &= \boldsymbol{q}^h_t \boldsymbol{S}^h_t \in \mathbb{R}^{1 \times d'_v}, \\
\boldsymbol{o}'_t &= \text{concat}(\text{LN}(\boldsymbol{o}^1_t), ..., \text{LN}(\boldsymbol{o}^H_t)) \in \mathbb{R}^{1 \times d_v}, \\
\boldsymbol{r}_t &= \text{Swish}(\boldsymbol{x}_t \boldsymbol{W}_r + \boldsymbol{b}_r) \in \mathbb{R}^{1 \times d_v}, \\
\boldsymbol{y}_t &= (\boldsymbol{r}_t \odot \boldsymbol{o}'_t) \boldsymbol{W}_O \in \mathbb{R}^{1 \times d}.
\end{aligned}
$$

## GLA block
$$
\begin{aligned}
\mathbf{Y}^{(l)} &= \text{GLA}(\text{LN}(\mathbf{X}^{(l)})) + \mathbf{X}^{(l)} \\
\mathbf{X}^{(l+1)} &= \text{SwiGLU}(\text{LN}(\mathbf{Y}^{(l)})) + \mathbf{X}^{(l)}
\end{aligned}
$$
Where 
$$
\text{SwiGLU}(\mathbf{Z}) = (\text{Swish}(\mathbf{Z} \mathbf{W}_1) \odot \mathbf{Z} \mathbf{W}_2) \mathbf{W}_3
$$

