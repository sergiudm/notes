## Retention
$$
\begin{aligned}
\boldsymbol{s}_n &= A \boldsymbol{s}_{n-1} + K_n^\top v_n, \quad & A \in \mathbb{R}^{d \times d}, K_n \in \mathbb{R}^{1 \times d} \\
o_n &= Q_n \boldsymbol{s}_n = \sum_{m=1}^n Q_n A^{n-m} K_m^\top v_m, \quad & Q_n \in \mathbb{R}^{1 \times d}
\end{aligned}
$$
### The Parallel Representation of Retention
$$
\begin{aligned}
Q &= (X W_Q) \odot \Theta, \quad K = (X W_K) \odot \overline{\Theta}, \quad V = X W_V \\
\Theta_n &= e^{in\theta}, \quad D_{nm} = \begin{cases} \gamma^{n-m}, & n \geq m \\ 0, & n < m \end{cases} \\
\text{Retention}(X) &= (Q K^\top \odot D) V
\end{aligned}
$$
### The Recurrent Representation of Retention
$$
\begin{aligned}
S_n &= \gamma S_{n-1} + K_n^\top V_n \\
\text{Retention}(X_n) &= Q_n S_n, \quad n = 1, \cdots, |x|
\end{aligned}
$$
### The Chunkwise Recurrent Representation of Retention
$$
\begin{aligned}
Q_{[i]} &= Q_{Bi:B(i+1)}, \quad K_{[i]} = K_{Bi:B(i+1)}, \quad V_{[i]} = V_{Bi:B(i+1)} \\
R_i &= K_{[i]}^\top (V_{[i]} \odot \zeta) + \gamma^B R_{i-1}, \quad \zeta_{ij} = \gamma^{B-i-1} \\
\text{Retention}(X_{[i]}) &= \underbrace{(Q_{[i]} K_{[i]}^\top \odot D) V_{[i]}}_{\text{Inner-Chunk}} + \underbrace{(Q_{[i]} R_{i-1}) \odot \xi}_{\text{Cross-Chunk}}, \quad \xi_{ij} = \gamma^{i+1}
\end{aligned}
$$
