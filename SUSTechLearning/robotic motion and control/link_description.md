# Link Description
> links: a set of bodies connected in a chain by joints. These bodies are called links.

> Joints: a mechanism that allows two bodies to move relative to each other.


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
    - joint angle: $\theta_i$

## Convention for Affixing Frames to Links



