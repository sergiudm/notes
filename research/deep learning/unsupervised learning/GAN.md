the discriminator parameters $\phi$ are manipulated to minimize the loss function, and the generative parameters $\theta$ are manipulated to maximize the loss function.
$$
\begin{aligned}
L[\boldsymbol{\phi}] = \sum_j - \log \Big[ 1 - \text{sig} \big[ \mathbf{g}[\mathbf{z}_j, \boldsymbol{\theta}], \boldsymbol{\phi} \big] \Big] - \sum_i \log \Big[ \text{sig} \big[ \mathbf{f}[\mathbf{x}_i, \boldsymbol{\phi}] \big] \Big] \\
L[\boldsymbol{\theta}] = \sum_j \log \Big[ 1 - \text{sig} \big[ \mathbf{g}[\mathbf{z}_j, \boldsymbol{\theta}], \boldsymbol{\phi} \big] \Big]
\end{aligned}
$$

