Code [lucidrains/titans-pytorch: Unofficial implementation of Titans, SOTA memory for transformers, in Pytorch](https://github.com/lucidrains/titans-pytorch/tree/main)
## Learning to Memorize at Test Time
### Long-term Memory
>A model that can encode the abstraction of the past history into its parameters

#### Naive memory updates
$$
\mathcal{M}_{t} = \mathcal{M}_{t-1} - \theta_{t} \underbrace{\nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)}_{\text{Surprise}}
$$
Where $\ell\left(\mathcal{M}_{t-1} ; x_{t}\right)=\left\|\mathcal{M}_{t-1}\left(\mathbf{k}_{t}\right)-\mathbf{v}_{t}\right\|_{2}^{2}$.
- *Problem*: the gradient can become extremely small after several surprising steps, leading to stocking in a flat area(i.e., local minima),and missing information about some parts of the sequence.
#### Memory update refined
$$
\begin{aligned}
\mathcal{M}_{t} &= \mathcal{M}_{t-1} + S_{t}, \\
S_{t} &= \eta_{t} \underbrace{S_{t-1}}_{\text{Past Surprise}} - \theta_{t} \underbrace{\nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)}_{\text{Momentary Surprise}}
\end{aligned}
$$
#### Forgetting Mechanism
$$
\begin{aligned}
\mathcal{M}_{t} &= \left(1-\alpha_{t}\right) \mathcal{M}_{t-1}+S_{t}, \\
S_{t} &= \eta_{t} S_{t-1}-\theta_{t} \nabla \ell\left(\mathcal{M}_{t-1} ; x_{t}\right)
\end{aligned}
$$
#### Retrieving a Memory
Given an input $x_t$, we use a linear layer $W_Q$ to project the input, i.e. $\mathbf{q}_t = x_t W_Q$ and retrieve the corresponding (or useful) information from the memory $y_t$ text by:
$$
y_{t}=\mathcal{M}^{*}\left(\mathbf{q}_{t}\right)
$$
#### How to Parallelize the Long-term Memory Training
TBD
### Persistent Memory
$$
x_{\text {new }}=\left[\begin{array}{llll}
p_{1} & p_{2} & \ldots & p_{N_{p}}
\end{array}\right] \| x
$$
Where $\|$ is concatenation, and $\left[\begin{array}{llll}p_{1} & p_{2} & \ldots & p_{N_{p}}\end{array}\right]$ is a set of learnable but input-independent parameters.

## How to Incorporate Memory: three different variants of Titans
### Memory as a Context
given a long sequence $x \in \mathbb{R}^{N \times din}$, we first chunk the sequence into fixed-size segments $S^{(i)}$ for 𝑖 = 1,...,𝑁/𝐶. Given the incoming segment $S^{(t)}$
$$
\begin{aligned}
\tilde{S}^{(t)}&=\left[\begin{array}{llll}
p_{1} & p_{2} & \ldots & p_{N_{p}}
\end{array}\right]\left\|h_{t}\right\| S^{(t)} \\
y_{t}&=\operatorname{Attn}\left(\tilde{S}^{(t)}\right).
\end{aligned}
$$
Where $h_{t}=\mathcal{M}_{t-1}^{*}\left(\mathbf{q}_{t}\right)$ and $\mathbf{q}_{t}=S^{(t)} W_{Q}$ .
Finally, 
$$
\begin{aligned}
\mathcal{M}_{t} &= \mathcal{M}_{t-1}\left(y_{t}\right), \\
o_{t} &= y_{t} \otimes \mathcal{M}_{t}^{*}\left(y_{t}\right)
\end{aligned}
$$
Note that, in the above, we are updating the weight of $\mathcal{M}_{t-1}$ through forward pass.
### Gated Memory
$$
\begin{aligned}
\tilde{x} &=\left[\begin{array}{llll}
p_{1} & p_{2} & \ldots & p_{N_{p}}
\end{array}\right] \| x, \\
y &=\mathrm{SW}-\mathrm{Attn}^{*}(\tilde{x}), \\
o &=y \otimes \mathcal{M}(\tilde{x}),
\end{aligned}
$$
Where SW-Attn∗ is sliding window attention with prefix.
### Memory as a Layer
$$
\begin{aligned}
\tilde{x} &=\left[\begin{array}{llll}
p_{1} & p_{2} & \ldots & p_{N_{p}}
\end{array}\right] \| x, \\
y &=\mathcal{M}(\tilde{x}), \\
o &=\mathrm{SW}-\mathrm{Attn}\left(y\right),
\end{aligned}
$$
