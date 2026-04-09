# 6.6.3 Revolute joint

### 6.6.3 Revolute joint

**Products: **Abaqus/Standard  Abaqus/Explicit

A revolute joint is a joint between two nodes in which the rotations of the nodes differ by a relative rotation about an axis that is fixed in and, therefore, rotates with the joint. A simple example is a hinge.

A revolute joint is implemented in Abaqus/Standard as a multi-point constraint, defining the total rotation of the constrained ("slave") node (the first node of the MPC), ![](../graphics/stm_eqn08381.gif), as the total rotation of the "master node" (the second node of the MPC), ![](../graphics/stm_eqn08382.gif), followed by the relative rotation ![](../graphics/stm_eqn08383.gif), about the axis of the joint ![](../graphics/stm_eqn00001.gif):

![](../graphics/stm_eqn08384.gif)The joint axis, ![](../graphics/stm_eqn00001.gif), also rotates with the rotation of the master node:

![](../graphics/stm_eqn08385.gif)

The angular velocity of the slave node is

![](../graphics/stm_eqn08386.gif)and the virtual variations of the rotations are, likewise,

![](../graphics/stm_eqn08387.gif)Thus, the joint imposes three constraints (each component of the angular velocity of the slave node is constrained) but introduces an additional degree of freedom in the form of the relative rotation ![](../graphics/stm_eqn08383.gif). This means the joint provides a total of two constraints to the model if ![](../graphics/stm_eqn08383.gif) is not prescribed and three constraints if it is.

The virtual work contribution of the three nodes of the joint is

![](../graphics/stm_eqn08388.gif)where ![](../graphics/stm_eqn08389.gif) is the total moment at node *S*, ![](../graphics/stm_eqn08390.gif) is the total moment at node *M*, and ![](../graphics/stm_eqn08391.gif) is the moment in the joint. Applying the constraints ([Equation 6.6.3&#8211;1](06s06a154.md)), this is

![](../graphics/stm_eqn08392.gif)If there are no further constraints associated with the nodes of the joint, ![](../graphics/stm_eqn08393.gif) and ![](../graphics/stm_eqn08394.gif) are independent variations, so the constrained virtual work equation implies that

![](../graphics/stm_eqn08395.gif)and that

![](../graphics/stm_eqn08396.gif)

Because the revolute is implemented in this manner, the relative rotation in the joint ![](../graphics/stm_eqn08383.gif) appears as a degree of freedom in the model (degree of freedom 6 at the third node of the MPC). Thus, a moment, ![](../graphics/stm_eqn08391.gif), can be applied in the joint by specifying its value as a concentrated load; ![](../graphics/stm_eqn08383.gif) can be given a prescribed variation in time by specifying a boundary condition; or stiffness and/or damping can be associated with relative rotation of the joint by attaching a spring and/or dashpot to ground to this degree of freedom (a spring or dashpot to ground is used because the variable is a relative rotation).
### Reference

### Reference

"General multi-point constraints,"  Section 35.2.2 of the Abaqus Analysis User's Guide