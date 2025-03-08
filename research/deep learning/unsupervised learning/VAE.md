>Goal: given a dataset $X$, learn the distribution of its element, that is, $Pr (x)$ where $x \in X$.
>The params ($\phi$) of $Pr (x|\phi)$ are in neural networks.

It's the pro version of parameter estimation
## Generation
### Nonlinear latent variable model

## Training![[Screenshot 2025-03-09 at 3.08.36 AM.png]]
### ELBO
$$
\log \left[ \int q(\mathbf{z}) \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z})}d\mathbf{z} \right] \geq \int q(\mathbf{z}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z})} \right] d\mathbf{z}
$$
$$
\text{ELBO}[\boldsymbol{\theta}, \phi] = \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z}
$$
$$
\begin{aligned}
\text{ELBO}[\boldsymbol{\theta}, \phi] &= \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{z}|\mathbf{x}, \phi)Pr(\mathbf{x}|\phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \int q(\mathbf{z}|\boldsymbol{\theta}) \log[Pr(\mathbf{x}|\phi)] d\mathbf{z} + \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{z}|\mathbf{x}, \phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \log[Pr(\mathbf{x}|\phi)] + \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{z}|\mathbf{x}, \phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \log[Pr(\mathbf{x}|\phi)] - D_{KL} \Big[ q(\mathbf{z}|\boldsymbol{\theta}) || Pr(\mathbf{z}|\mathbf{x}, \phi) \Big]
\end{aligned}
$$
Thus, The KL distance will be zero, and the bound will be tight when $q(z|θ) = P r(z|x, ϕ)$.
In VAE:
$$
\begin{aligned}
\text{ELBO}[\boldsymbol{\theta}, \phi] &= \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{x}|\mathbf{z}, \phi)Pr(\mathbf{z})}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \int q(\mathbf{z}|\boldsymbol{\theta}) \log[Pr(\mathbf{x}|\mathbf{z}, \phi)] d\mathbf{z} + \int q(\mathbf{z}|\boldsymbol{\theta}) \log \left[ \frac{Pr(\mathbf{z})}{q(\mathbf{z}|\boldsymbol{\theta})} \right] d\mathbf{z} \\
&= \int q(\mathbf{z}|\boldsymbol{\theta}) \log[Pr(\mathbf{x}|\mathbf{z}, \phi)] d\mathbf{z} - D_{KL} \Big[ q(\mathbf{z}|\boldsymbol{\theta}) || Pr(\mathbf{z}) \Big]
\end{aligned}
$$

the first term measures the average agreement $Pr(x|z, ϕ)$ of the latent variable and the data. This measures the reconstruction accuracy. The second term measures the degree to which the auxiliary distribution $q(z|θ)$ matches the prior.

In practice:
$$
\text{ELBO}[\boldsymbol{\theta}, \phi] \approx \log[Pr(\mathbf{x}|\mathbf{z}^{*}, \phi)] - D_{KL} \Big[ q(\mathbf{z}|\mathbf{x}, \boldsymbol{\theta}) || Pr(\mathbf{z}) \Big]
$$
And 
$$
q(\mathbf{z}|\mathbf{x}, \boldsymbol{\theta}) = \text{Norm}_{\mathbf{z}} \Big[ \mathbf{g}_{\mu}[\mathbf{x}, \boldsymbol{\theta}], \mathbf{g}_{\Sigma}[\mathbf{x}, \boldsymbol{\theta}] \Big]
$$
## VAE algorithm
we aim to build a model that computes the evidence lower bound for a point $\mathbf{x}$.
![[Screenshot 2025-03-09 at 2.32.54 AM.png]]

### The reparameterization trick
![[Screenshot 2025-03-09 at 3.08.36 AM.png]]

