Link [RWKV-LM/RWKV-v1/src/model.py at main · BlinkDL/RWKV-LM](https://github.com/BlinkDL/RWKV-LM/blob/main/RWKV-v1/src/model.py)
## Architecture
![[Pasted image 20250203120937.png]]
>• R: The Receptance vector acts as the receiver of past information. 
>• W: The Weight signifies the positional weight decay vector, a trainable parameter within the model. 
>• K: The Key vector performs a role analogous to K in traditional attention mechanisms. 
>• V: The Value vector functions similarly to V in conventional attention processes.
## Token shift
### Time mixing
$$
\begin{align*}
r_t &= W_r \cdot \left( \mu_r \odot x_t + (1 - \mu_r) \odot x_{t-1} \right), \\
k_t &= W_k \cdot \left( \mu_k \odot x_t + (1 - \mu_k) \odot x_{t-1} \right), \\
v_t &= W_v \cdot \left( \mu_v \odot x_t + (1 - \mu_v) \odot x_{t-1} \right),
\end{align*}

$$
### Channel mixing
$$
\begin{align*}
r'_t &= W'_r \cdot \left( \mu'_r \odot x_t + (1 - \mu'_r) \odot x_{t-1} \right), \\
k'_t &= W'_k \cdot \left( \mu'_k \odot x_t + (1 - \mu'_k) \odot x_{t-1} \right).
\end{align*}

$$
## WKVOperator
$$
wkv_t = \frac{
\sum_{i=1}^{t-1} e^{-(t-1-i)w + k_i} \odot v_i + e^{u + k_t} \odot v_t
}{
\sum_{i=1}^{t-1} e^{-(t-1-i)w + k_i} + e^{u + k_t}
}
$$
## Output Gating
### post the WKV operator
$$
o_t = W_o \cdot (\sigma(r_t) \odot wkv_t)
$$
### In the channel-mixing block
$$
o'_t = \sigma(r'_t) \odot (W'_v \cdot \max(k'_t, 0)^2)
$$

