Code [lucidrains/titans-pytorch: Unofficial implementation of Titans, SOTA memory for transformers, in Pytorch](https://github.com/lucidrains/titans-pytorch/tree/main)
## Long-term Memory
>A model that can encode the abstraction of the past history into its parameters
$$
\mathcal{M}_{t} = \mathcal{M}_{t-1} - \theta_{t} \underbrace{\nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)}_{\text{Surprise}}
$$

