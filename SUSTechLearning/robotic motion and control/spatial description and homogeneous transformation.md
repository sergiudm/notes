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

### orientation
${}^A_B R$: 
$$
{}^A_B R = \begin{bmatrix}
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
\hat X_B \dot {}^A\hat X_A & \hat X_B \dot {}^A \hat Y_A & \hat X_B \dot {}^A\hat Z_A \\
\hat Y_B \dot {}^A\hat X_A & \hat Y_B \dot {}^A \hat Y_A & \hat Y_B \dot {}^A\hat Z_A \\
\hat Z_B \dot {}^A\hat X_A & \hat Z_B \dot {}^A \hat Y_A & \hat Z_B \dot {}^A\hat Z_A \\
\end{bmatrix}
$$

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
