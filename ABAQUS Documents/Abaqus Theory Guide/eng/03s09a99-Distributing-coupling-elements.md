# 3.9.8 Distributing coupling elements

### 3.9.8 Distributing coupling elements

**Products: **Abaqus/Standard  Abaqus/Explicit

The distributing coupling elements provide a means to connect a reference node to a group of coupling nodes in a way that distributes loads according to weight factors that are prescribed individually at each coupling node. The element distributes forces and moments at the reference node as a coupling node&#8211;force distribution only. The formulation presented here is also used for the surface-based distributing coupling and in fastener constraints. This section defines this load distribution relationship and the resultant element development for the case when the default continuum coupling method is used.

The reference node has displacement ![](../graphics/stm_eqn05493.gif) and rotation ![](../graphics/stm_eqn05494.gif) degrees of freedom. The coupling nodes have only displacement ![](../graphics/stm_eqn05495.gif) degrees of freedom active in this element. Each coupling node has a weight factor ![](../graphics/stm_eqn05496.gif) assigned, which determines the proportion of load carried by the element that is transmitted through the coupling node. Weight factors are dimensionless, and their magnitude is significant only in a relative sense. Hereafter, normalized weights are used:

![](../graphics/stm_eqn05497.gif)
### Load distribution

Let ![](../graphics/stm_eqn05498.gif) and ![](../graphics/stm_eqn05499.gif) be the load and moment applied to the reference node. The statically admissible force distribution ![](../graphics/stm_eqn03432.gif) among the coupling nodes satisfies

![](../graphics/stm_eqn05500.gif)where ![](../graphics/stm_eqn05501.gif) and ![](../graphics/stm_eqn05502.gif) are the positions of the reference and coupling nodes, respectively. For an arbitrary number of coupling nodes there is no unique solution to [Equation 3.9.8&#8211;1](03s09a99-Distributing-coupling-elements.md).

The force distribution adopted in Abaqus has the property that the linearized motion of the reference node is compatible with the coupling node group motion in an average sense. This compatibility can be described by considering the momentum of a moving coupling node group in a case where weight factors are considered as masses. In this case the reference node motion is identical to that of a point on a rigid body occupying the position of the reference node, where the center of mass of the rigid body is the center of mass of the coupling nodes and the rigid body moves with the same linear and angular momentum as the coupling node group. Since the element mass is distributed this way, the dynamic behavior of the element also has this property.

![](../graphics/stm_eqn05503.gif)where

![](../graphics/stm_eqn05504.gif)and the coupling node arrangement inertia tensor is

![](../graphics/stm_eqn05505.gif)where ![](../graphics/stm_eqn00064.gif) is the second-order identity tensor. This force distribution is recognized to be equivalent to the classic bolt-pattern force distribution when the weight factors are interpreted as bolt cross-section areas.
### Constraint expression

The load distribution results in the following linearized constraint on node motions:

![](../graphics/stm_eqn05506.gif)where ![](../graphics/stm_eqn05507.gif).
### Finite motion

Finite displacement and rotation terms take the form of a constraint on the motion of the reference node as a function of the coupling-node finite incremental motions. A measure of the finite rotation of the coupling node arrangement is developed first and is based on the mid-increment position of the coupling nodes, defined as

![](../graphics/stm_eqn05508.gif)and the mid-increment inertia tensor is

![](../graphics/stm_eqn05509.gif)The mid-increment "spin" is then

![](../graphics/stm_eqn05510.gif)

The finite incremental rotation tensor ![](../graphics/stm_eqn00433.gif) is deduced from the above expression according to the [Hughes and Winget (1980)](07s01a01-References.md) formula,

![](../graphics/stm_eqn05511.gif)

This orthogonal tensor yields an incremental finite-rotation vector ![](../graphics/stm_eqn05512.gif). From this rotation description comes the constraint expressions for finite displacement and rotation:

![](../graphics/stm_eqn05513.gif)
### Virtual work contribution

The virtual work expression for the attached structure is augmented with the contribution of the constraint

![](../graphics/stm_eqn05514.gif)where ![](../graphics/stm_eqn05515.gif) is the augmented virtual work expression, ![](../graphics/stm_eqn04709.gif) is the virtual work expression for the attached structure, and ![](../graphics/stm_eqn05516.gif) and ![](../graphics/stm_eqn05517.gif) are the respective Lagrange multiplier variables for force and moment.
### Initial stress stiffness terms

The initial stress stiffness terms are derived from a suitable approximation of the exact virtual work expression shown in [Equation 3.9.8&#8211;2](03s09a99-Distributing-coupling-elements.md). This approximation is based on an assumption of infinitesimal incremental motions, ![](../graphics/stm_eqn05518.gif) and ![](../graphics/stm_eqn05519.gif), that implies

![](../graphics/stm_eqn05520.gif)An approximate virtual work expression is obtained:

![](../graphics/stm_eqn05521.gif)

![](../graphics/stm_eqn05522.gif)This expression yields the following initial stress stiffness terms:

![](../graphics/stm_eqn05523.gif)
### Mass

The distributing coupling elements also distribute masses to each coupling node according to the weight distribution. A prescribed element mass of *M* is distributed to the cloud nodes according to

![](../graphics/stm_eqn05524.gif)where ![](../graphics/stm_eqn05525.gif) is the cloud node mass. Masses are distributed only to the cloud nodes; no mass is associated with the reference node.
### References

### References

"Distributing coupling elements,"  Section 32.4 of the Abaqus Analysis User's Guide

"Coupling constraints,"  Section 35.3.2 of the Abaqus Analysis User's Guide