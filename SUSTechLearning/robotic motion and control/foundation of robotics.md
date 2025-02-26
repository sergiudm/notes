## Introduction
### Analysis
#### Zero-order analysis: (forward)kinematics & inverse kinematics
> Kinematics: given a robot manipulator (arm) with a specific configuration(joint angles), find the position and orientation of the robot arm end-effector (tip)

>Inverse kinematics: given desired position and orientation of the end-effector, find the set of possible joint angles which support such position and orientation

Eg. 1
Forward:
$$
\begin{align*}
p_x=l_1cos(\theta_1)+l_2cos(\theta_2) \\
p_y=l_1sin(\theta_1)+l_2sin(\theta_2)
\end{align*}
$$
Inverse:
$$
\begin{align*}
\theta_1 = f_1(p_x,p_y)\\
\theta_2 = f_2(p_x,p_y)
\end{align*}
$$
##### Joint space and cartesian space
> Joint space:
> Cartesian space: task space

#### First-order analysis: velocity relationships between the joint space and cartesian space
Forward, 
Given
$$
\begin{bmatrix}
\dot{\theta_1} \\
\dot{\theta_2}\\
\vdots \\
\dot{\theta_n}
\end{bmatrix}
$$
, find 
$$
\begin{bmatrix}
\dot{p_x}\\
\dot{p_y}
\end{bmatrix}
$$
And 
$$
\begin{bmatrix}
\dot{\omega_x}\\
\dot{\omega_y}
\end{bmatrix}
$$
Eg.

