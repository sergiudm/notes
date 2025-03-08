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
$$
\begin{aligned}
Pr(\mathbf{z}_T) &= \text{Norm}_{\mathbf{z}_T}[\mathbf{0}, \mathbf{I}] \\
Pr(\mathbf{z}_{t-1}|\mathbf{z}_t, \phi_t) &= \text{Norm}_{\mathbf{z}_{t-1}}[\mathbf{f}_t[\mathbf{z}_t, \phi_t], \sigma_t^2\mathbf{I}] \\
Pr(\mathbf{x}|\mathbf{z}_1, \phi_1) &= \text{Norm}_{\mathbf{x}}[\mathbf{f}_1[\mathbf{z}_1, \phi_1], \sigma_1^2\mathbf{I}],
\end{aligned}
$$
Where $f_t[\mathbf z_t, \mathbf\phi_t]$ is a neural network that computes the mean of the normal distribution in the estimated mapping from $\mathbf{z}_t$ to the preceding latent variable $\mathbf{z}_{t−1}$.
## Training
$$
\begin{aligned}
&\text{To train the model, we maximize the log-likelihood of the training data } \{\mathbf{x}_i\} \text{ with} \\
&\text{respect to the parameters } \boldsymbol{\phi}\text{:} \\
&\hat{\boldsymbol{\phi}}_{1...T} = \underset{\boldsymbol{\phi}_{1...T}}{\text{argmax}} \left[ \sum_{i=1}^{I} \log[Pr(\mathbf{x}_i|\boldsymbol{\phi}_{1...T})] \right]. 
\end{aligned}
$$
Where $Pr(\mathbf{x}|\boldsymbol{\phi}_{1...T}) = \int Pr(\mathbf{x}, \mathbf{z}_{1...T}|\boldsymbol{\phi}_{1...T})d\mathbf{z}_{1...T}$ and $Pr(\mathbf{x}, \mathbf{z}_{1...T}|\boldsymbol{\phi}_{1...T}) = Pr(\mathbf{x}|\mathbf{z}_1, \phi_1) \prod_{t=2}^{T} Pr(\mathbf{z}_{t-1}|\mathbf{z}_t, \phi_t) \cdot Pr(\mathbf{z}_T)$.

### ELBO
$$
\text{ELBO}[\boldsymbol{\phi}_{1...T}] = \int q(\mathbf{z}_{1...T}|\mathbf{x}) \log \left[ \frac{Pr(\mathbf{x}, \mathbf{z}_{1...T}|\boldsymbol{\phi}_{1...T})}{q(\mathbf{z}_{1...T}|\mathbf{x})} \right] d\mathbf{z}_{1...T}
$$

### Diffusion loss function
$$
\begin{aligned}
L[\boldsymbol{\phi}_{1...T}] &= \sum_{i=1}^{I} \overbrace{\Big( -\log \big[ \text{Norm}_{\mathbf{x}_i} \left[ \mathbf{f}_1[\mathbf{z}_{i1}, \boldsymbol{\phi}_1], \sigma_1^2 \mathbf{I} \right] \big] \Big)}^{\text{reconstruction term}} \\
&+ \sum_{t=2}^{T} \frac{1}{2\sigma_t^2} \Big\Vert \overbrace{\frac{1 - \alpha_{t-1}}{1 - \alpha_t} \sqrt{1-\beta_t} \mathbf{z}_{it} + \frac{\sqrt{\alpha_{t-1}}\beta_t}{1-\alpha_t} \mathbf{x}_i}^{\text{target, mean of } q(\mathbf{z}_{t-1}|\mathbf{z}_t, \mathbf{x})} - \underbrace{\mathbf{f}_t[\mathbf{z}_{it}, \boldsymbol{\phi}_t]}_{\text{predicted } \mathbf{z}_{t-1}} \Big\Vert^2 \Big),
\end{aligned}
$$
#### Reparameterization of loss function

##### Reparameterization of target
##### Reparameterization of network
