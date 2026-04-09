# 6.6.4 Universal joint

### 6.6.4 Universal joint

**Products: **Abaqus/Standard  Abaqus/Explicit

A universal joint is a joint between two nodes containing orthogonal hinges that provide two axes of relative rotation in the joint.

A universal joint is implemented in Abaqus/Standard as a multi-point constraint, defining the total rotation of the constrained ("slave") node (the first node of the MPC), ![](../graphics/stm_eqn08381.gif), as the total rotation of the "master node" (the second node of the MPC), ![](../graphics/stm_eqn08397.gif), followed by two relative rotations: ![](../graphics/stm_eqn08398.gif) about the first axis of the joint ![](../graphics/stm_eqn05355.gif), then ![](../graphics/stm_eqn08399.gif) about the second axis of the joint ![](../graphics/stm_eqn05349.gif) (which is orthogonal to ![](../graphics/stm_eqn05355.gif)):

![](../graphics/stm_eqn08400.gif)The first joint axis, ![](../graphics/stm_eqn05355.gif), rotates with the rotation of the master node:

![](../graphics/stm_eqn08401.gif)The second joint axis has this rotation plus the rotation about the first joint axis:

![](../graphics/stm_eqn08402.gif)

The angular velocity of the slave node is

![](../graphics/stm_eqn08403.gif)and the virtual variations of the rotations are, likewise,

![](../graphics/stm_eqn08404.gif)Thus, the joint imposes three constraints (each component of the angular velocity of the slave node is constrained) but introduces two additional degrees of freedom in the form of the relative rotations ![](../graphics/stm_eqn08398.gif) and ![](../graphics/stm_eqn08399.gif). This means the joint provides a total of one constraint to the model if ![](../graphics/stm_eqn08398.gif) and ![](../graphics/stm_eqn08399.gif) are not prescribed or up to three constraints if they are.

The virtual work contribution of the joint is

![](../graphics/stm_eqn08405.gif)where ![](../graphics/stm_eqn08389.gif) is the total moment at node *S*, ![](../graphics/stm_eqn08390.gif) is the total moment at node *M*, and ![](../graphics/stm_eqn05299.gif) and ![](../graphics/stm_eqn05300.gif) are the moments in the joint hinges. Applying the constraints ([Equation 6.6.4&#8211;1](06s06a155.md)), this is

![](../graphics/stm_eqn08406.gif)If there are no further constraints associated with the nodes of the joint, ![](../graphics/stm_eqn08393.gif), ![](../graphics/stm_eqn08407.gif) and ![](../graphics/stm_eqn08408.gif) are independent variations, so that the constrained virtual work equation implies that

![](../graphics/stm_eqn08409.gif)

![](../graphics/stm_eqn08410.gif)and

![](../graphics/stm_eqn08411.gif)

Because the universal joint is implemented in this manner, the relative rotations in the joint, ![](../graphics/stm_eqn08398.gif) and ![](../graphics/stm_eqn08399.gif), appear as degrees of freedom in the model (degree of freedom 6 at the third and fourth nodes of the MPC). Moments ![](../graphics/stm_eqn05299.gif) and ![](../graphics/stm_eqn05300.gif) can, therefore, be applied in the joint by specifying their values as concentrated loads; ![](../graphics/stm_eqn08398.gif) and ![](../graphics/stm_eqn08399.gif) can be given prescribed variations in time by specifying boundary conditions; or stiffness and/or damping can be associated with relative rotations of the joint by attaching springs and/or dashpots to ground to these degrees of freedom (springs or dashpots to ground are used because the variables are relative rotations).
### Reference

### Reference

"General multi-point constraints,"  Section 35.2.2 of the Abaqus Analysis User's Guide