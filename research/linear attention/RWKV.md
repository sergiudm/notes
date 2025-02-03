![[Pasted image 20250203115908.png]]
![[Pasted image 20250203115922.png]]
$$
\begin{align*}
r_t &= W_r \cdot \left( \mu_r \odot x_t + (1 - \mu_r) \odot x_{t-1} \right), \\
k_t &= W_k \cdot \left( \mu_k \odot x_t + (1 - \mu_k) \odot x_{t-1} \right), \\
v_t &= W_v \cdot \left( \mu_v \odot x_t + (1 - \mu_v) \odot x_{t-1} \right),
\end{align*}

$$
$$
\begin{align*}
r'_t &= W'_r \cdot \left( \mu'_r \odot x_t + (1 - \mu'_r) \odot x_{t-1} \right), \\
k'_t &= W'_k \cdot \left( \mu'_k \odot x_t + (1 - \mu'_k) \odot x_{t-1} \right).
\end{align*}

$$
