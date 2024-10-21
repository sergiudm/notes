## Fundamental results
### Insights of observability
we assume that the input signal u(t) and the output signal y(t) can be measured over a finite time interval and seek to deduce the initial state $x(t_0) = x_0$ by processing this information in some way.

### Definition of observability
A state $\mathbf{x_0} ∈ \mathbb{R^n}$ is **unobservable** if the zero-input response of the linear state equation (4.1) with initial state $x(t_0) = x_0$ is y(t) ≡ 0 for all $t ≥ t_0$. The state equation (4.1) is **observable** if the zero vector $\mathbf{0} \in \mathbb{R^n}$ is the only unobservable state. Therefore, a nonzero unobservable state is sometimes called indistinguishable from $\mathbf{0} \in \mathbb{R^n}$.

### Access the observability of a system
#### Theorem 1
![[Pasted image 20241021105638.png]]

#### Obsevability Gramian
![[Pasted image 20241021112039.png]]
##### Gramian and obvervability
![[Pasted image 20241021115019.png]]
How to obtain $x_0$ with zero-input response:
![[Pasted image 20241021115331.png]]
![[Pasted image 20241021115421.png]]
![[Pasted image 20241021115433.png]]
## Duality

