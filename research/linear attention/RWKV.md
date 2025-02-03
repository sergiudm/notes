Link [RWKV-LM/RWKV-v1/src/model.py at main · BlinkDL/RWKV-LM](https://github.com/BlinkDL/RWKV-LM/blob/main/RWKV-v1/src/model.py)
## RWKV
![[Pasted image 20250203120937.png]]
>• R: The Receptance vector acts as the receiver of past information. 
>• W: The Weight signifies the positional weight decay vector, a trainable parameter within the model. 
>• K: The Key vector performs a role analogous to K in traditional attention mechanisms. 
>• V: The Value vector functions similarly to V in conventional attention processes.
### Token shift
#### Time mixing
$$
\begin{align*}
r_t &= W_r \cdot \left( \mu_r \odot x_t + (1 - \mu_r) \odot x_{t-1} \right), \\
k_t &= W_k \cdot \left( \mu_k \odot x_t + (1 - \mu_k) \odot x_{t-1} \right), \\
v_t &= W_v \cdot \left( \mu_v \odot x_t + (1 - \mu_v) \odot x_{t-1} \right),
\end{align*}

$$
#### Channel mixing
$$
\begin{align*}
r'_t &= W'_r \cdot \left( \mu'_r \odot x_t + (1 - \mu'_r) \odot x_{t-1} \right), \\
k'_t &= W'_k \cdot \left( \mu'_k \odot x_t + (1 - \mu'_k) \odot x_{t-1} \right).
\end{align*}

$$
### WKVOperator
$$
wkv_t = \frac{
\sum_{i=1}^{t-1} e^{-(t-1-i)w + k_i} \odot v_i + e^{u + k_t} \odot v_t
}{
\sum_{i=1}^{t-1} e^{-(t-1-i)w + k_i} + e^{u + k_t}
}
$$
### Output Gating
#### post the WKV operator
$$
o_t = W_o \cdot (\sigma(r_t) \odot wkv_t)
$$
#### In the channel-mixing block
$$
o'_t = \sigma(r'_t) \odot (W'_v \cdot \max(k'_t, 0)^2)
$$

## RWKV v 5
Code [RWKV-LM/RWKV-v5/src/model.py at main · BlinkDL/RWKV-LM](https://github.com/BlinkDL/RWKV-LM/blob/main/RWKV-v5/src/model.py)
### Time mixing
$$
\begin{aligned}
\square_t &= \text{lerp}_\square(x_t, x_{t-1}) W_\square, \quad \square \in \{r, k, v, g\} \\
w &= \exp(-\exp(\omega)) \\
wkv_t &= \text{diag}(u) \cdot k_t^\top \cdot v_t + \sum_{i=1}^{t-1} \text{diag}(w)^{t-1-i} \cdot k_i^\top \cdot v_i \in \mathbb{R}^{(D/h) \times (D/h)} \\
o_t &= \text{concat}(\text{SiLU}(g_t) \odot \text{LayerNorm}(r_t \cdot wkv_t)) W_o \in \mathbb{R}^D
\end{aligned}
$$
Where **l**inear int**erp**olation, $\text{lerp}_\square(a, b) = a + (b - a) \odot \mu_\square$ and $\mu_{\square} \in \mathbb{R}^D$ is a learnable vector.
### Channel mixing
$$
\begin{aligned}
r'_t &= \text{lerp}_{r'}(x'_t, x'_{t-1}) W_{r'} \in \mathbb{R}^D \\
k'_t &= \text{lerp}_{k'}(x'_t, x'_{t-1}) W_{k'} \in \mathbb{R}^{3.5D} \\
v'_t &= \text{ReLU}(k'_t)^2 W_{v'} \in \mathbb{R}^D \\
o'_t &= \sigma(r'_t) \odot v'_t \in \mathbb{R}^D
\end{aligned}
$$
## RWKV v 6
### Time mixing
#### Token shift
$$
\begin{aligned}
\text{lora}_\square(x) &= \lambda_\square + \text{tanh}(x A_\square) B_\square \\
\text{ddlerp}_\square(a, b) &= a + (b - a) \odot \text{lora}_\square(a + (b - a) \odot \mu_x)
\end{aligned}
$$
#### Time mixing

