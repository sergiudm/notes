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
{}_B^AR=\begin{bmatrix}
	{}^A(\hat{x_B})_x & {}^A(\hat{x_B})_y & {}^A(\hat{x_B})_z \\
	{}^A(\hat{y_B})_x & {}^A(\hat{y_B})_y & {}^A(\hat{y_B})_z \\
	{}^A(\hat{z_B})_x & {}^A(\hat{z_B})_y & {}^A(\hat{z_B})_z \\
\end{bmatrix}
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

then
$$
{}^B\mathbb{P}={}^A\mathbb{P}+{}^A\mathbb{T}
$$
Where ${}^A\mathbb{T}$ is the translation vector from {A} to {B}

### Mapping involving rotated frames
For a position $\mathbb{P}$ in {A}, it's coordinate is ${}^A\mathbb{P}$
While in {B}, it's ${}^{B}\mathbb{P}$,
then
$$
{}^B\mathbb{P}={}^A\mathbb{P}R
$$
Where $R$ is the rotation matrix from {A} to {B}

