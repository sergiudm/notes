## Notation
### position
 a point ${}^A P$ is represented as a vector and
can equivalently be thought of as a position in space.
Individual elements of a vector are given the subscripts x, y, and z:
$$
{}^AP = \begin{bmatrix}
p_x \\
p_y \\
p_z
\end{bmatrix}
$$

### orientation ${}^A_B \mathbf R$: 
$$
{}^A_B \mathbf R = \begin{bmatrix}
{}^A\hat X_B & {}^A \hat Y_B & {}^A\hat Z_B
\end{bmatrix}
$$
where ${}^AX_B$, ${}^AY_B$, and ${}^AZ_B$ are the unit vectors of the coordinate system {B} in the coordinate system {A}.

$$
\begin{bmatrix}
{}^A\hat X_B & {}^A \hat Y_B & {}^A\hat Z_B
\end{bmatrix}
=
\begin{bmatrix}
\hat X_B \hat X_A & \hat 
\end{bmatrix}
$$
because the columns of ${}^A_B R$ are the unit vectors of {B} written in {A}, the rows of ${}^A_B R$ are the unit vectors of {A} written in {B}.

### frame
A frame is depicted by three arrows representing unit
vectors defining the principal axes of the frame.
$$
\{B\} = \{{}^A_B \mathbf R, {}^A \mathbf P_{BORG}\}
$$
where $P_{BORG}$ is the origin of frame {B} in frame {A}.

## mapping
### Mappings Involving Translated Frames
$$
{}^A P = {}^B P + {}^A P_{BORG}
$$
### Mappings Involving Rotated Frames
$$
{}^A P = {}^A_B R {}^B P
$$
This  implements a mapping—that is, it changes the description of a
vector—from ${}^BP$, which describes a point in space relative to {B}, into ${}^AP$, which is
a description of the same point, but expressed relative to {A}.

### Mappings Involving General Frames
$$
{}^A P = {}^A_B R {}^B P + {}^A P_{BORG}
$$
#### Homogeneous Transformation
$$
\begin{bmatrix}
{}^A P \\
1
\end{bmatrix}
=
\begin{bmatrix}
{}^A_B R & {}^A P_{BORG} \\
0 & 1
\end{bmatrix}
$$
