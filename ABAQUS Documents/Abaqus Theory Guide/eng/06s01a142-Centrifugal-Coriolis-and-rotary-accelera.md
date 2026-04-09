# 6.1.1 Centrifugal, Coriolis, and rotary acceleration forces

### 6.1.1 Centrifugal, Coriolis, and rotary acceleration forces

**Product: **Abaqus/Standard

Many of the elements in Abaqus allow centrifugal, Coriolis, and rotary acceleration forces to be included. This section defines these load types.

It is assumed that the model (or that part of it to which these forces are applied) is described in a coordinate system that is rotating with an angular velocity, ![](../graphics/stm_eqn00242.gif), and/or an angular (rotary) acceleration, ![](../graphics/stm_eqn07872.gif). Let ![](../graphics/stm_eqn07873.gif) be a right-handed set of unit, orthogonal vectors that form a basis for this system. Then, ![](../graphics/stm_eqn07874.gif) and ![](../graphics/stm_eqn07875.gif).

If the angular velocity is cast as

![](../graphics/stm_eqn07876.gif)where ![](../graphics/stm_eqn01091.gif) is the magnitude of ![](../graphics/stm_eqn00242.gif) and ![](../graphics/stm_eqn00483.gif) is the unit axis of rotation, the rotary acceleration is

![](../graphics/stm_eqn07877.gif)where the term ![](../graphics/stm_eqn07878.gif) represents the effect of the motion of the axis of rotation (precessional motion);

![](../graphics/stm_eqn07879.gif) is the magnitude of the rotary acceleration; and ![](../graphics/stm_eqn07880.gif) is the axis of rotary acceleration. If ![](../graphics/stm_eqn07881.gif), then ![](../graphics/stm_eqn07882.gif) and ![](../graphics/stm_eqn07883.gif). In component form

![](../graphics/stm_eqn07884.gif)and

![](../graphics/stm_eqn07885.gif)

Let ![](../graphics/stm_eqn01672.gif) be a point on the axis of rotation. The position of a material particle, ![](../graphics/stm_eqn00117.gif), can be written

![](../graphics/stm_eqn07886.gif)where ![](../graphics/stm_eqn07887.gif), ![](../graphics/stm_eqn07888.gif), are the coordinates of the point in the rotating basis system. Taking time derivatives,

![](../graphics/stm_eqn07889.gif)and

![](../graphics/stm_eqn07890.gif)

We assume that the origin of the rotating system, ![](../graphics/stm_eqn01195.gif), is fixed, so that

![](../graphics/stm_eqn07891.gif)With this simplification

![](../graphics/stm_eqn07892.gif)and

![](../graphics/stm_eqn07893.gif)

The virtual work contribution from the d'Alembert forces is

![](../graphics/stm_eqn07894.gif)where ![](../graphics/stm_eqn07342.gif) is the mass density of the body in its reference configuration, where its volume is ![](../graphics/stm_eqn01828.gif) and ![](../graphics/stm_eqn04502.gif) is a virtual variational field. For the part of the body described in the rotating system, the acceleration, ![](../graphics/stm_eqn07895.gif), is given by [Equation 6.1.1&#8211;1](06s01a142.md), while ![](../graphics/stm_eqn07896.gif) only, since ![](../graphics/stm_eqn00242.gif) and ![](../graphics/stm_eqn07872.gif) are prescribed and ![](../graphics/stm_eqn01672.gif) is fixed. Thus,

![](../graphics/stm_eqn07897.gif)

Simplifying,

![](../graphics/stm_eqn07898.gif)

The terms in ![](../graphics/stm_eqn07899.gif) can be identified as follows. The first term,

![](../graphics/stm_eqn07900.gif)is the usual "consistent mass matrix" term associated with acceleration of the material particles with respect to the rotating system.

Writing the angular velocity of the rotating basis system as its components in that system, ![](../graphics/stm_eqn07901.gif), gives the second term as

![](../graphics/stm_eqn07902.gif)where ![](../graphics/stm_eqn00168.gif) is the alternator tensor. This term is the Coriolis force term and arises whenever there is velocity in the rotating system, which can happen in dynamic analysis or in quasi-static cases in which a constant velocity has been introduced (for example, by defining an initial velocity).

The third term is, likewise, rewritten as

![](../graphics/stm_eqn07903.gif)This term is the centrifugal load term.

Similarly, the fourth term is rewritten as

![](../graphics/stm_eqn07904.gif)This term is the rotary acceleration load term.

In Abaqus/Standard the centrifugal load, Coriolis, and rotary acceleration terms contribute to the "load stiffness matrix." The centrifugal load term has a symmetric load stiffness matrix,

![](../graphics/stm_eqn07905.gif)the Coriolis term has an antisymmetric "load damping matrix,"

![](../graphics/stm_eqn07906.gif)and the rotary acceleration term has an antisymmetric load stiffness matrix,

![](../graphics/stm_eqn07907.gif)
### Reference

### Reference

"Distributed loads,"  Section 34.4.3 of the Abaqus Analysis User's Guide