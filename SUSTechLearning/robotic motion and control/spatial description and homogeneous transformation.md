## Description of position, orientation, and frame
### Position vector
$$
\mathbb{P}=\begin{bmatrix}
p_x \\
p_y \\
P_z
\end{bmatrix}
$$
### Orientation vector
Given {A}, the orientation of the 3D object can be described by {B}, i.e. by three unit vectors along its principal axes, in relation to {A}:
$$
{}^{A}{x_B},\space {}^{A}{y_B},\space{}^{A}{z_B},
$$
Where
$$
{}^Ax_B=\begin{bmatrix}
	{}^A(\hat{x_B})_x \\
	{}^A(\hat{x_B})_y \\
	{}^A(\hat{x_B})_z \\
\end{bmatrix}
$$
$$
{}^Ay_B=\begin{bmatrix}
	{}^A(\hat{y_B})_x \\
	{}^A(\hat{y_B})_y \\
	{}^A(\hat{y_B})_z \\
\end{bmatrix}
$$
$$
{}^Az_B=\begin{bmatrix}
	{}^A(\hat{z_B})_x \\
	{}^A(\hat{z_B})_y \\
	{}^A(\hat{z_B})_z \\
\end{bmatrix}
$$
$$
{}_B^AR=\begin{bmatrix}
{}^A\hat{x_B} {}^A\hat{y_B} {}^A\hat{z_B} 
\end{bmatrix}
$$
## Homogeneous transformation: changing description from frame to frame
### Mapping involving translated frames
For a position $\mathbb{P}$ in {A}, it's coordinate is ${}^A\mathbb{P}$
While in {B}, it's ${}^{B}\mathbb{P}$,
