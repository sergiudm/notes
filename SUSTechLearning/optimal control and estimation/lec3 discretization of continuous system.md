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
