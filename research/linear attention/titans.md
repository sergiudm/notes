Code [lucidrains/titans-pytorch: Unofficial implementation of Titans, SOTA memory for transformers, in Pytorch](https://github.com/lucidrains/titans-pytorch/tree/main)
## Long-term Memory
>A model that can encode the abstraction of the past history into its parameters

### Naive memory updates
$$
\mathcal{M}_{t} = \mathcal{M}_{t-1} - \theta_{t} \underbrace{\nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)}_{\text{Surprise}}
$$
Where $\ell\left(\mathcal{M}_{t-1} ; x_{t}\right)=\left\|\mathcal{M}_{t-1}\left(\mathbf{k}_{t}\right)-\mathbf{v}_{t}\right\|_{2}^{2}$.
- *Problem*: the gradient can become extremely small after several surprising steps, leading to stocking in a flat area(i.e., local minima),and missing information about some parts of the sequence.
### Memory update refined
$$
\begin{aligned}
\mathcal{M}_{t} &= \mathcal{M}_{t-1} + S_{t}, \\
S_{t} &= \eta_{t} \underbrace{S_{t-1}}_{\text{Past Surprise}} - \theta_{t} \underbrace{\nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)}_{\text{Momentary Surprise}}
\end{aligned}
$$
### Forgetting Mechanism


