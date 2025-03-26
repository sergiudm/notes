## Adjacent Link Transformations
![[Pasted image 20250326110236.png]]
$$
\begin{align*}
^{i-1}P &= ^{i-1}_{R}T \, ^{R}_{Q}T \, ^{Q}_{P}T \, ^{P}_{i}T \, ^{i}P, \\
or, ^{i-1}P &= ^{i-1}_{i}T \, ^{i}P
\end{align*}
$$
,
Where $^{i-1}_{i}T = ^{i-1}_{R}T \, ^{R}_{Q}T \, ^{Q}_{P}T \, ^{P}_{i}T$. 
Thus
$$
^{i-1}_{i}T = \begin{bmatrix}
c\theta_i & -s\theta_i & 0 & a_{i-1} \\
s\theta_i c\alpha_{i-1} & c\theta_i c\alpha_{i-1} & -s\alpha_{i-1} & -s\alpha_{i-1} d_i \\
s\theta_i s\alpha_{i-1} & c\theta_i s\alpha_{i-1} & c\alpha_{i-1} & c\alpha_{i-1} d_i \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
## Concatenating Link Transformations
The link transformations can be multiplied together to find the single transformation that relates frame {N} to frame {0}:
