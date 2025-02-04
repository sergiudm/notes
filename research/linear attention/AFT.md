Code [An Attention Free Transformer](https://nn.labml.ai/transformers/aft/index.html)
![[Pasted image 20250204150004.png]]
$$
Y = f(X); \ Y_t = \sigma_q(Q_t) \odot \frac{\sum_{t'=1}^T \exp(K_{t'} + w_{t, t'}) \odot V_{t'}}{\sum_{t'=1}^T \exp(K_{t'} + w_{t, t'})}
$$
Where $Q = XW^Q, K = XW^K, V = XW^V$
$w \in \mathbb{R}^{T \times T}$ is the learned pair-wise position biases