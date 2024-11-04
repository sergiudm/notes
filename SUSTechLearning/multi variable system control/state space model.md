## State equations
![[Pasted image 20240914211818.png]]
### How to select state variables
![[Pasted image 20240914211924.png]]

### Find A, B, C, D from ODE
#### Theory
![[Pasted image 20240914212038.png]]
![[Pasted image 20240914212052.png]]
##### Including derivatives of $u(t)$:
![[Pasted image 20240914212200.png]]
Strategy:
![[Pasted image 20240914212256.png]]

##### Degree of numerator = denominator:
![[Pasted image 20240914212428.png]]
Strategy:
![[Pasted image 20240914212449.png]]
In addition, $D=b_n$
##### Multiple input/output systems
![[Pasted image 20241104115429.png]]
a:
![[Pasted image 20241104115508.png]]
![[Pasted image 20241104115611.png]]
b:
![[Pasted image 20241104115538.png]]![[Pasted image 20241104115549.png]]
#### Practice
##### When can we use CCF?
- 1. Coefficient of $y^{(n)}$ and $u(t)$ are both $1$
- 2.  $x_n=x_{n-1}'$
When `1` is not satisfied:
![[Pasted image 20241104104624.png]]

![[Pasted image 20241104104648.png]]
>[!attention] 
> The 'B' matrix has to change
> ![[Pasted image 20241104104903.png]]

When `2` is not satisfied:
![[Pasted image 20241104105441.png]]
>[!attention] 
> 'A' has to change
> ![[Pasted image 20241104105542.png]]

##### Multi input/output
![[Pasted image 20241104113731.png]]
![[Pasted image 20241104113744.png]]
![[Pasted image 20241104113804.png]]

### Block diagram and state space model
Similar to `Simulink `

