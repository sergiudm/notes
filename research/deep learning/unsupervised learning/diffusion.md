## Model
### Encoder (forward process)
#### Diffusion kernel $q(z_t|x)$
$$
q(\mathbf{z}_t|\mathbf{x}) = \text{Norm}_{\mathbf{z}_t} \Big[ \sqrt{\alpha_t} \cdot \mathbf{x}, (1-\alpha_t)\mathbf{I} \Big].
$$
Where $q(\mathbf{z}_t|\mathbf{x}) = \text{Norm}_{\mathbf{z}_t} \Big[ \sqrt{\alpha_t} \cdot \mathbf{x}, (1 - \alpha_t)\mathbf{I} \Big]$ and 
#### Marginal distribution $q(z_t)$
$$
q(\mathbf{z}_t) = \int q(\mathbf{z}_t|\mathbf{x}) Pr(\mathbf{x})d\mathbf{x}
$$
#### Conditional distribution $q(\mathbf{z}_{t-1}|\mathbf{z}_t)$
$$
q(\mathbf{z}_{t-1}|\mathbf{z}_t) = \frac{q(\mathbf{z}_t|\mathbf{z}_{t-1})q(\mathbf{z}_{t-1})}{q(\mathbf{z}_t)}
$$
#### Conditional diffusion distribution $q(z_{t-1}|z_t,x)$
$$
\begin{aligned}
q(\mathbf{z}_{t-1}|\mathbf{z}_t, \mathbf{x}) &= \frac{q(\mathbf{z}_t|\mathbf{z}_{t-1}, \mathbf{x})q(\mathbf{z}_{t-1}|\mathbf{x})}{q(\mathbf{z}_t|\mathbf{x})} \\
&\propto q(\mathbf{z}_t|\mathbf{z}_{t-1})q(\mathbf{z}_{t-1}|\mathbf{x}) \\
&= \text{Norm}_{\mathbf{z}_t} \Big[ \sqrt{1-\beta_t} \cdot \mathbf{z}_{t-1}, \beta_t \mathbf{I} \Big] \text{Norm}_{\mathbf{z}_{t-1}} \Big[ \sqrt{\alpha_{t-1}} \cdot \mathbf{x}, (1-\alpha_{t-1})\mathbf{I} \Big] \\
&\propto \text{Norm}_{\mathbf{z}_{t-1}} \left[ \frac{1}{\sqrt{1-\beta_t}}\mathbf{z}_t, \frac{\beta_t}{1-\beta_t}\mathbf{I} \right] \text{Norm}_{\mathbf{z}_{t-1}} \Big[ \sqrt{\alpha_{t-1}} \cdot \mathbf{x}, (1-\alpha_{t-1})\mathbf{I} \Big]
\end{aligned}
$$
$$
q(\mathbf{z}_{t-1}|\mathbf{z}_t, \mathbf{x}) = \text{Norm}_{\mathbf{z}_{t-1}} \left[ \frac{(1-\alpha_{t-1})}{1-\alpha_t}\sqrt{1-\beta_t}\mathbf{z}_t + \frac{\sqrt{\alpha_{t-1}}\beta_t}{1-\alpha_t}\mathbf{x}, \frac{\beta_t(1-\alpha_{t-1})}{1-\alpha_t}\mathbf{I} \right]
$$
### Decoder (backward process)

## Training
### ELBO
### Diffusion loss function
#### Reparameterization of loss function
##### Reparameterization of target
##### Reparameterization of network
