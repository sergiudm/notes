Code: [flash-linear-attention/fla/models/gla/modeling_gla.py at main · fla-org/flash-linear-attention](https://github.com/fla-org/flash-linear-attention/blob/main/fla/models/gla/modeling_gla.py)
## Linear attention
$$
q_t, k_t, v_t = x_t W_Q, x_t W_K, x_t W_V,
$$
$$
o_t = \frac{\sum_{i=1}^t \phi(\boldsymbol{q}_t) \phi(\boldsymbol{k}_i)^\top \boldsymbol{v}_i}{\sum_{i=1}^t \phi(\boldsymbol{q}_t) \phi(\boldsymbol{k}_i)^\top} = \frac{\phi(\boldsymbol{q}_t) \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top \boldsymbol{v}_i}{\phi(\boldsymbol{q}_t) \sum_{i=1}^t \phi(\boldsymbol{k}_i)^\top}
$$
### Recurrent form
