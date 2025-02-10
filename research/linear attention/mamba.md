Code [state-spaces/mamba: Mamba SSM architecture](https://github.com/state-spaces/mamba)
## Mamba
![[Pasted image 20250210102001.png]]
### Selective State Space Models
$$
\begin{aligned}
&\textbf{Algorithm:} \text{ SSM + Selection (S6)} \\
&\textbf{Input: } x: (\text{B, L, D}) \\
&\textbf{Output: } y: (\text{B, L, D}) \\
&1: \quad \boldsymbol{A}: (\text{D, N}) \leftarrow \text{Parameter}  \qquad \triangleright \text{Represents structured } N \times N \text{ matrix} \\
&2: \quad \boldsymbol{B}: (\text{B, L, N}) \leftarrow s_{\boldsymbol{B}}(x) \\
&3: \quad \boldsymbol{C}: (\text{B, L, N}) \leftarrow s_{\boldsymbol{C}}(x) \\
&4: \quad \boldsymbol{\Delta}: (\text{B, L, D}) \leftarrow \tau_{\boldsymbol{\Delta}}(\text{Parameter} + s_{\boldsymbol{\Delta}}(x)) \\
&5: \quad \overline{\boldsymbol{A}}, \overline{\boldsymbol{B}}: (\text{B, L, D, N}) \leftarrow \text{discretize}(\boldsymbol{\Delta}, \boldsymbol{A}, \boldsymbol{B}) \\
&6: \quad y \leftarrow \text{SSM}(\overline{\boldsymbol{A}}, \overline{\boldsymbol{B}}, \boldsymbol{C})(x) \qquad \triangleright \text{Time-varying: recurrence (} scan \text{) only}  \\
&7: \quad \textbf{return } y
\end{aligned}
$$
