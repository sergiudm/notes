# Euler method
Substitute $\dot{\mathbf{x}}(t) \approx \frac{\mathbf{x}[k+1] - \mathbf{x}[k]}{\Delta t}$ into SSM
We get:
$$
\frac{\mathbf{x}[k+1] - \mathbf{x}[k]}{\Delta t} = A\mathbf{x}[k] + B\mathbf{u}[k]
$$
, that is:
$$
\mathbf{x}[k+1] = \left( I + \Delta t A \right) \mathbf{x}[k] + \Delta t B \mathbf{u}[k]
$$
So $A_d = I + \Delta t A, \quad B_d = \Delta t B, \quad C_c=C, \quad D_c=D$

# ZOH method
During $\Delta t$ ,  $\mathbf{u}(t) = \mathbf{u}[k]$ . The solution of SSM is:
$$
\mathbf{x}(t_{k+1}) = e^{A\Delta t} \mathbf{x}(t_k) + \int_{0}^{\Delta t} e^{A\tau} B \mathbf{u}[k] d\tau
$$

Thus $A_d = e^{A\Delta t}, \quad B_d = \int_{0}^{\Delta t} e^{A\tau} B d\tau, \quad C_c=C, \quad D_c=D$
