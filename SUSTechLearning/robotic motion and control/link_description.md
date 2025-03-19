# Link Description
> links: a set of bodies connected in a chain by joints. These bodies are called links.

> Joints: a mechanism that allows two bodies to move relative to each other.

- Common lower-pair joints:
![[Pasted image 20250319115647.png]]
Mechanical-design considerations favor manipulators’ generally being constructed from joints that exhibit just *one degree of freedom*.

The links are numbered starting from the immobile base of the arm, which might be called link 0. The first moving body is link 1, and so on, out to the free end of the arm, which is link n.

> Joint axes: the axis of rotation of a joint.

Distance between two links: $d_i$:

$$
d_i = \left| \overrightarrow{O_i} - \overrightarrow{O_{i+1}} \right|
$$

### Link Parameters (Denavit–Hartenberg notation)
- link description
    - link length: $a$
    - link twist: $\alpha$
- Link-connection Description
    - link offset: $d_i$
    - joint angle (joint variable): $\theta_i$
![[Pasted image 20250319115739.png]]
## Convention for Affixing Frames to Links
### How to determine a frame{i} attached to link i
- Determine the z-axis:
	- Z is coincident with the direction of axis i.
- Determine the origin:
	- Origin is defined as the intersection of 
![[Pasted image 20250319115816.png]]

