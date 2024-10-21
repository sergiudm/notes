# 1. some terminologies

![[Pasted image 20240308172410.png|650]]

- ## linear combination of the previous output: $z_j^l=\sum\limits_{k} w_{jk}^la_k^{l-1}+b_j^l$ , where $w_{jk}^l$ denotes the $j$th row and the $k$th column of the matrix $w$.
	- ### vectorization :$z^l=w^{l-1}a^{l-1}+b^l$
- ## the activation value: $a^l=\sigma(z^l)$
- ## error of a neuron: $\delta_j^l\equiv\frac{\partial C}{\partial z_j^l}$
- ## cost function: $C$
- ## the number of layers: $L$


# 2. four equations
## $$ \delta_{j}^{L}=\frac{\partial C}{\partial a_j^L}\sigma'(z_j^L) \tag1$$
### vectorization : $$ \delta_j^L=\nabla_a C \odot \sigma'(z^L) \tag{1'}$$
## $$ \delta ^l = ((w^{l+1})^T \delta^{l+1}) \odot \sigma'(z^l) \tag2$$
## $$\frac{\partial C}{\partial b_j^l}=\delta_j^l\tag3$$
## $$ \frac{\partial C}{\partial w_{jk}^l}=a_k^{l-1} \delta_j^l\tag4$$
# 3. the algorithm 
![[Pasted image 20240308174024.png|700]]






