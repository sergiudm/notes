>Goal: given a dataset $X$, learn the distribution of its element, that is, $Pr (x)$ where $x \in X$.
>The params ($\phi$) of $Pr (x|\phi)$ are in neural networks.

It's the pro version of parameter estimation
## Generation
### Nonlinear latent variable model

## Training
### ELBO
$$
\log \left[ \int q(\mathbf{z}) \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z})}d\mathbf{z} \right] \geq \int q(\mathbf{z}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}|\phi)}{q(\mathbf{z})} \right] d\mathbf{z}
$$
