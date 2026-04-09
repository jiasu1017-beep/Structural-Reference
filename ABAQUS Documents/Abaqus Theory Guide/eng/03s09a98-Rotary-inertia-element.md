# 3.9.7 Rotary inertia element

### 3.9.7 Rotary inertia element

**Products: **Abaqus/Standard  Abaqus/Explicit

The MASS and ROTARYI elements allow the inertia of a rigid body to be introduced at a node. In this section the formulation used with these elements is defined.

It is assumed that the node at which the mass and rotary inertia are introduced is the center of mass of the body. We refer to the node as the rigid body reference node, *C*. Let the local principal axes of inertia of the body be ![](../graphics/stm_eqn00008.gif), ![](../graphics/stm_eqn00338.gif). Let ![](../graphics/stm_eqn03949.gif) be the vector between *C* and some point in the rigid body with current coordinates ![](../graphics/stm_eqn00117.gif), so that

![](../graphics/stm_eqn05473.gif)where ![](../graphics/stm_eqn05474.gif) are local coordinates in the rigid body. The mass of the rigid body is the integral of the mass density ![](../graphics/stm_eqn05475.gif) over the body

![](../graphics/stm_eqn05476.gif)Since *C* is assumed to be the center of mass of the body,

![](../graphics/stm_eqn05477.gif)Since the ![](../graphics/stm_eqn00008.gif) are the principal axes of the body,

![](../graphics/stm_eqn05478.gif)Let ![](../graphics/stm_eqn03733.gif), ![](../graphics/stm_eqn03734.gif), and ![](../graphics/stm_eqn05479.gif) be the second moments of inertia of the body about its principal axes ![](../graphics/stm_eqn00014.gif), ![](../graphics/stm_eqn00015.gif), and ![](../graphics/stm_eqn00016.gif); then

![](../graphics/stm_eqn05480.gif)The rotary inertia tensor is written

![](../graphics/stm_eqn05481.gif)

For a rigid body the velocity of any point in the body is given by

![](../graphics/stm_eqn05482.gif) where ![](../graphics/stm_eqn03952.gif) is the angular velocity of the body. Taking a second time derivative, the acceleration is

![](../graphics/stm_eqn05483.gif)

The local or strong form of the equilibrium equations represents the balance of linear momentum and balance of angular momentum; these two equilibrium equations are

![](../graphics/stm_eqn05484.gif)The variational or weak form of equilibrium is

![](../graphics/stm_eqn05485.gif)The internal or d'Alembert force contribution is

![](../graphics/stm_eqn05486.gif)where ![](../graphics/stm_eqn05487.gif) is the variation of the position of a point in the body. Here ![](../graphics/stm_eqn05488.gif) is the variation of the position of the rigid body reference node, and ![](../graphics/stm_eqn03959.gif) is the variation of the rotation of the rigid body reference node. The external loading contribution is

![](../graphics/stm_eqn05489.gif)Introducing component expressions relative to the principal axes of inertia, the rotational contribution to the weak form becomes

![](../graphics/stm_eqn05490.gif)

When the inertia of a rigid body is used with implicit time integration, the Jacobian contribution of ![](../graphics/stm_eqn05491.gif) is required: this is

![](../graphics/stm_eqn05492.gif)
### Reference

### Reference

"Rotary inertia,"  Section 30.2.1 of the Abaqus Analysis User's Guide