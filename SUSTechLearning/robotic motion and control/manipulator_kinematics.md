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
$$
^{0}_{N}T = ^{0}_{1}T ^{1}_{2}T ^{2}_{3}T \dots ^{N-1}_{N}T.
$$
>Note:
> $^{0}_{N}T$ will be a function of all n joint variables. If the robot’s joint-position sensors are queried, the Cartesian position and orientation of the last link can be computed by $^{0}_{N}T$ .

## Actuator space, joint space, and Cartesian space
- joint space:
    - an $n \times 1$ vector of joint variables
- Cartesian space:
    - same as task space, or operational space
    - the matrix of joint variables that describes the position and orientation of the robot’s end effector
- actuator space:
    - The sensors that measure the position of the manipulator are often located at the actuators, so some computations must be performed to realize the joint vector as a function of a set of actuator values, or actuator vector.
## {B}, {S}, {W}, {T}, and {G}
- The Base Frame:
	- {B} is located at the base of the manipulator. It is merely another name for frame {0}. It is affixed to a nonmoving part of the robot, sometimes called link 0.
- The Station Frame:
	- {S} is located in a task-relevant location. 
	- As far as the user of this robot system is concerned, {S} is the universe frame, and all actions of the robot are performed relative to it. It is sometimes called the task frame, the world frame, or the universe frame.
- The Wrist Frame:
	- {W} is affixed to the last link of the manipulator.
- The Tool Frame:
	- {T } is affixed to the end of any tool the robot happens to be holding.
	- When the hand is empty, {T} is usually located with its origin between the fingertips of the robot.
- The Goal Frame:
	- {G} is a description of the location to which the robot is to move the tool.
	- At the end of the motion, the tool frame should be brought to coincidence with the goal frame.
	- {G} is always specified relative to the station frame.
![[Pasted image 20250326121611.png]]
