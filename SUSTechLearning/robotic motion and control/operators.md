## Translational operators
>Definieion:
A translation moves a point *in space* a finite distance along a given vector direction

e.g.
$$
{}^AP_2={}^AP_1+{}^AQ
$$
in matrix form:
$$
{}^AP_2 = D(Q)_q {}^AP_1
$$
where 
$$
D(Q)_q = \begin{bmatrix} 1 & 0 & 0 & q_x \\ 0 & 1 & 0 & q_y \\ 0 & 0 & 1 & q_z \\ 0 & 0 & 0 & 1 \end{bmatrix}
$$
$q_x, q_y, q_z$ are the components of the translation vector $Q$ in the frame $A$

## Rotational operators
Usually, when a rotation matrix is shown as an operator, no sub- or superscripts
appear, because it is not viewed as relating two frames.
$$
{}^AP_2 = R {}^AP_1
$$
where $R$ is a rotation matrix.

## Transformation operators
A frame has another interpretation as a transformation operator that rotates and translates a vector ${}^AP_1$ to a new position ${}^AP_2$.
$$
{}^AP_2 = T {}^AP_1
$$
where $T$ is a transformation matrix.

>**Key Insight of a Homogeneous Transform**:
1. It is a description of a frame. ${}^A_B\mathbf T$ describes the frame {B} relative to the frame
{A}. Specifically, the columns of ${}^A_BR$ are unit vectors defining the directions of
the principal axes of {B}, and APBORG locates the position of the origin of {B}.
2. It is a transform mapping. ${}^A_B T$ maps ${}^BP$ → ${}^AP$.
3. It is a transform operator. T operates on ${}^AP_1$ to create ${}^AP_2$.

>**Remark on Rotational Matrices**:
1. There are only 3 independent parameters in a 3×3 rotation matrix.
2. The determinant of a rotation matrix is always +1(proper matrix).
3. The inverse of a rotation matrix is its transpose(orthogonal matrix).
4. Rotations are not commutative.(i.e. ${}^A_BR {}^B_CR \neq {}^B_CR {}^A_BR$)

**Cayley's Formula**:
For any proper orthogonal matrix $R$, there exists a skew-symmetric matrix $S$ such that
$$
R = (I + S)(I - S)^{-1}
$$
where 
$$
S=-S^T=\begin{bmatrix}
 0 & -s_z & s_y \\ 
 s_z & 0 & -s_x \\ 
 -s_y & s_x & 0 \end{bmatrix}
$$
.Therefore, any 3 × 3 rotation
matrix can be specified by just three parameters.

## Transformation Arithmetic
### Compound Transformations
$$
{}^A_C T = {}^A_B T {}^B_C T
$$
$$
{}^A_B T
= \begin{bmatrix}
{}^A_BR {}^B_CR & {}^A_BR {}^B_CP_{CORG} + {}^AP_{BORG}
\\ 0 & 1
\end{bmatrix}
$$
### Inverse Transformations
$$
{}^A_B T^{-1} = {}^B_A T=
\begin{bmatrix}
{}^A_BR^T & -{}^A_BR^T {}^AP_{BORG}
\\ 0 & 1
\end{bmatrix}
