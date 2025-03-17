# linearization and Taylor expansion
## Jacobian matrix
### Definition
The Jacobian matrix is a matrix of all first-order partial derivatives of a vector-valued function. It is used to represent the rate of change of a vector-valued function with respect to a vector.

For a vector-valued function $\mathbf{f}(\mathbf{x})$, the Jacobian matrix is defined as:
$$
\mathbf{J}(\mathbf{x})=\begin{bmatrix}
    \frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} & \cdots & \frac{\partial f_1}{\partial x_n} \\
    \frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2} & \cdots & \frac{\partial f_2}{\partial x_n} \\
    \vdots & \vdots & \ddots & \vdots \\
    \frac{\partial f_m}{\partial x_1} & \frac{\partial f_m}{\partial x_2} & \cdots & \frac{\partial f_m}{\partial x_n}
\end{bmatrix}
$$
where $\mathbf{f}(\mathbf{x})=\begin{bmatrix} f_1 \\ f_2 \\ \vdots \\ f_m \end{bmatrix}$, $\mathbf{x}=\begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}$.

> *e.g.*
> let $\mathbf{f}(\mathbf{x})=\begin{bmatrix} 2x_1+e^{x_2} \\ \log x_3 + \frac{1}{x_2} \end{bmatrix}$, then
> $$
> \mathbf{J}(\mathbf{x})=\begin{bmatrix}
>     2 & e^{x_2} & 0 \\
>     0 & -\frac{1}{x_2^2} & \frac{1}{x_3}
> \end{bmatrix}
> $$

## Hessian matrix
### Definition
The Hessian matrix is a square matrix of second-order partial derivatives of a scalar-valued function. It is used to represent the rate of change of the gradient of a scalar-valued function with respect to a vector.

For a scalar-valued function $f(\mathbf{x})$, the Hessian matrix is defined as:
$$
\mathbf{H}(\mathbf{x})=\begin{bmatrix}
    \frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1\partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1\partial x_n} \\
    \frac{\partial^2 f}{\partial x_2\partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2\partial x_n} \\
    \vdots & \vdots & \ddots & \vdots \\
    \frac{\partial^2 f}{\partial x_n\partial x_1} & \frac{\partial^2 f}{\partial x_n\partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2}
\end{bmatrix}
$$
where $f(\mathbf{x})$ is a scalar-valued function, $\mathbf{x}=\begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}$.

## Taylor expansion

### Taylor expansion of a $\mathbb{R}^m\rightarrow\mathbb{R}$ function
For a scalar-valued function $\mathbf{f}(\mathbf{x})$, the Taylor expansion of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$ is:
$$
\mathbf{f}(\mathbf{x})=\mathbf{f}(\mathbf{x}_0)+\nabla \mathbf{f}(\mathbf{x}_0)(\mathbf{x}-\mathbf{x}_0)+\frac{1}{2}(\mathbf{x}-\mathbf{x}_0)^T\mathbf{H}_{\mathbf{f}(\mathbf{x}_0)}(\mathbf{x}-\mathbf{x}_0)+\cdots

$$
where $\nabla \mathbf{f}(\mathbf{x}_0)$ is the gradient vector of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$, $\mathbf{H}_{\mathbf{f}(\mathbf{x}_0)}$ is the Hessian matrix of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$.

### Taylor expansion of a $\mathbb{R}\rightarrow\mathbb{R}^n$ function
For a vector-valued function $\mathbf{f}(\mathbf{x})$, the Taylor expansion of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$ is:
$$
\mathbf{f}(\mathbf{x})=\mathbf{f}(\mathbf{x}_0)+\mathbf{f}'(\mathbf{x}_0)(\mathbf{x}-\mathbf{x}_0)+\mathbf{f}''(\mathbf{x}_0)(\mathbf{x}-\mathbf{x}_0)^2+\cdots
$$

where $\mathbf{f}'(\mathbf{x}_0)$ is the element-wise gradient

### Taylor expansion of a $\mathbb{R}^m\rightarrow\mathbb{R}^n$ function
For a vector-valued function $\mathbf{f}(\mathbf{x})$, the Taylor expansion of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$ is:
$$
\mathbf{f}(\mathbf{x})=\mathbf{f}(\mathbf{x}_0)+\mathbf{J}(\mathbf{x}_0)(\mathbf{x}-\mathbf{x}_0)+\frac{1}{2}(\mathbf{x}-\mathbf{x}_0)^T\mathbf{H}_{\mathbf{f}(\mathbf{x}_0)}(\mathbf{x}-\mathbf{x}_0)+\cdots
$$
where $\mathbf{J}(\mathbf{x}_0)$ is the Jacobian matrix of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$, $\mathbf{H}_{\mathbf{f}(\mathbf{x}_0)}$ is the Hessian matrix of $\mathbf{f}(\mathbf{x})$ at $\mathbf{x}_0$.



