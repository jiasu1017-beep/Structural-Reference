# 3.9.6 Flexible joint element

### 3.9.6 Flexible joint element

**Product: **Abaqus/Standard

The JOINTC elements in Abaqus/Standard provide for flexible joints between two nodes. This section defines the kinematic variables used in these elements.
### Kinematics

A JOINTC element consists of two nodes, referred to here as nodes 1 and 2. Each node has six degrees of freedom: displacements ![](../graphics/stm_eqn00428.gif) and rotations ![](../graphics/stm_eqn00152.gif). A local orientation is defined for the element by the user. In a large-displacement analysis that local system rotates with the first node of the element.

Figure 3.9.6&#8211;1 JOINTC geometry.

![](../graphics/stmjointcgeom-nls.png)We define the local system by its unit, orthogonal base vectors, ![](../graphics/stm_eqn00008.gif), for ![](../graphics/stm_eqn00338.gif). Then at any time in the analysis

![](../graphics/stm_eqn05455.gif)where ![](../graphics/stm_eqn05456.gif) is the rotation matrix defined by the rotation at the first node of the element.

The relative displacements in the element are then

![](../graphics/stm_eqn05457.gif)with first variations

![](../graphics/stm_eqn05458.gif)where ![](../graphics/stm_eqn05459.gif) is a linearized rotation field (see "Rotation variables,"  Section 1.3.1), and second variations

![](../graphics/stm_eqn05460.gif)

The relative rotation about the local *3*-axis is defined as

![](../graphics/stm_eqn05461.gif)with ![](../graphics/stm_eqn05462.gif) and ![](../graphics/stm_eqn05463.gif) defined by cyclic permutation of the local direction indices.

These rotation measures define only relative angular rotations for small relative rotations. They are simple to compute, increase monotonically for relative rotations up to 180, and are taken as suitable for use in the elements for these reasons.

The first variation of ![](../graphics/stm_eqn05464.gif) is

![](../graphics/stm_eqn05465.gif)and its second variation is

![](../graphics/stm_eqn05466.gif)

The relative translational velocities in the element are taken as

![](../graphics/stm_eqn05467.gif)and the relative angular velocity about the local *3*-axis is taken as

![](../graphics/stm_eqn05468.gif)
### Virtual work

The virtual work contribution of the element is

![](../graphics/stm_eqn05469.gif)We assume that the behavior of the joint is defined by

![](../graphics/stm_eqn05470.gif)

The contribution to the operator matrix for the Newton solution is

![](../graphics/stm_eqn05471.gif)where ![](../graphics/stm_eqn05472.gif) is defined by the dynamic time integration operator.
### Reference

### Reference

"Flexible joint elements,"  Section 32.3 of the Abaqus Analysis User's Guide