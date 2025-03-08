## Model
### Encoder (forward pass)
#### Diffusion kernel $q(z_t|x)$
$$
q(\mathbf{z}_t|\mathbf{x}) = \text{Norm}_{\mathbf{z}_t} \Big[ \sqrt{\alpha_t} \cdot \mathbf{x}, (1-\alpha_t)\mathbf{I} \Big].
$$
Where $q(\mathbf{z}_t|\mathbf{x}) = \text{Norm}_{\mathbf{z}_t} \Big[ \sqrt{\alpha_t} \cdot \mathbf{x}, (1 - \alpha_t)\mathbf{I} \Big].$
#### Marginal distribution $q(z_t)$
#### Conditional distribution $q(z_t|z_{t-1})$
#### Conditional diffusion distribution $q(z_{t-1}|z_t,x)$

### Decoder (backward pass)

## Training
### ELBO
### Diffusion loss function
#### Reparameterization of loss function
##### Reparameterization of target
##### Reparameterization of network
