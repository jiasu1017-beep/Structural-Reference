# 5.1.3 Finite-sliding interaction between a deformable and a rigid body

### 5.1.3 Finite-sliding interaction between a deformable and a rigid body

**Product: **Abaqus/Standard

Abaqus/Standard provides two formulations for modeling the interaction between a deformable body and an arbitrarily shaped rigid body that may move during the history being modeled. The first is a small-sliding formulation in which the contacting surfaces can only undergo relatively small sliding relative to each other, but arbitrary rotation of the surfaces is permitted. This formulation is discussed in "Small-sliding interaction between bodies,"  Section 5.1.1. The second is a finite-sliding formulation where separation and sliding of finite amplitude and arbitrary rotation of the surfaces may arise. This formulation is discussed in this section.

The finite-sliding rigid contact capability is implemented by means of a family of contact elements that Abaqus automatically generates based on the data associated with the user-specified contact pairs. At each integration point these elements construct a measure of overclosure (penetration of the point on the surface of the deforming body into the rigid surface) and measures of relative shear sliding. These kinematic measures are then used, together with appropriate Lagrange multiplier techniques, to introduce surface interaction theories (contact and friction). A library of interaction theories is provided in Abaqus---these may be thought of as a library of "surface constitutive models." In this section we discuss only the kinematics of the interacting surfaces. The surface constitutive models are described in Chapter 4, "Mechanical Constitutive Theories."

Let ![](../graphics/stm_eqn01047.gif) be a point on the deforming mesh, with current coordinates ![](../graphics/stm_eqn07559.gif). Let ![](../graphics/stm_eqn07560.gif) be the "rigid body reference node"---the node that defines the position of the rigid body---with current coordinates ![](../graphics/stm_eqn07561.gif). Let ![](../graphics/stm_eqn07562.gif) be the closest point on the surface of the rigid body to ![](../graphics/stm_eqn01047.gif) at which the normal to the surface of the rigid body, ![](../graphics/stm_eqn00483.gif), passes through ![](../graphics/stm_eqn01047.gif). Define ![](../graphics/stm_eqn03949.gif) as the vector from ![](../graphics/stm_eqn07560.gif) to ![](../graphics/stm_eqn07562.gif). The geometry described by these quantities is shown in [Figure 5.1.3&#8211;1](05s01a134.md).

Figure 5.1.3&#8211;1 Rigid surface interface geometry.

![](../graphics/stmrigidsurf-geom.png)

Let ![](../graphics/stm_eqn07404.gif) be the distance from ![](../graphics/stm_eqn07562.gif) to ![](../graphics/stm_eqn01047.gif) along ![](../graphics/stm_eqn07563.gif): the "overclosure" of the surfaces. From the definitions introduced above,

![](../graphics/stm_eqn07564.gif)

Then if ![](../graphics/stm_eqn07565.gif) there is no contact between the surfaces at ![](../graphics/stm_eqn01047.gif), and no further surface interaction calculations need be done at this point. Here ![](../graphics/stm_eqn07566.gif) is the clearance below which contact occurs. For a "hard" surface ![](../graphics/stm_eqn07567.gif), but Abaqus/Standard also allows a "softened" surface to be introduced in which ![](../graphics/stm_eqn07566.gif) may be nonzero (although ![](../graphics/stm_eqn07566.gif) is usually very small compared to other dimensions). If ![](../graphics/stm_eqn07568.gif) the surfaces are in contact. To enforce the contact constraint we will need the first variation of ![](../graphics/stm_eqn07404.gif), ![](../graphics/stm_eqn07420.gif), and its second variation, ![](../graphics/stm_eqn07421.gif). These quantities are now derived.

Let ![](../graphics/stm_eqn07569.gif), ![](../graphics/stm_eqn07570.gif) be locally orthogonal, distance measuring surface coordinates on the surface at ![](../graphics/stm_eqn07562.gif). The ![](../graphics/stm_eqn07569.gif) measure distance along the tangents ![](../graphics/stm_eqn01706.gif) to the surface at ![](../graphics/stm_eqn07562.gif): these tangents are constructed according to the standard Abaqus convention for such tangents to a surface in space. As the point ![](../graphics/stm_eqn01047.gif) and the rigid body move, the projected point ![](../graphics/stm_eqn07562.gif) will move along. The movement consists of two parts: movement due to motion of the rigid body and motion relative to the body

![](../graphics/stm_eqn07571.gif)where ![](../graphics/stm_eqn03583.gif) is the "slip" of point ![](../graphics/stm_eqn07562.gif). The normal ![](../graphics/stm_eqn00483.gif) will also change due to rotation of the rigid surface and due to slip along the surface

![](../graphics/stm_eqn07572.gif)The linearized form of the contact equation, thus, becomes

![](../graphics/stm_eqn07573.gif)For "hard" contact ![](../graphics/stm_eqn03803.gif) exactly, and for soft contact we will assume ![](../graphics/stm_eqn03803.gif) as well. The linearized kinematic equation, thus, becomes

![](../graphics/stm_eqn07574.gif)This equation can be split into normal and tangential components, which yields the contact equation,

![](../graphics/stm_eqn07575.gif)and the slip equations,

![](../graphics/stm_eqn07576.gif)

To obtain the second variation of ![](../graphics/stm_eqn07404.gif), it will again be assumed that ![](../graphics/stm_eqn03803.gif). In addition, it will be assumed that ![](../graphics/stm_eqn07577.gif), which is accurate for relatively "hard" contact. It then directly follows that

![](../graphics/stm_eqn07578.gif)and from the linearized kinematic equation follows

![](../graphics/stm_eqn07579.gif)where we have used ![](../graphics/stm_eqn07580.gif). The first term corresponds to a second-order variation on the vector ![](../graphics/stm_eqn03949.gif) for rigid body rotations around point ![](../graphics/stm_eqn07560.gif) and is given by (see "Rotation variables,"  Section 1.3.1):

![](../graphics/stm_eqn07581.gif)The second term in the expression for the second variation is obtained with the previously used expression for the "slip" along the surface:

![](../graphics/stm_eqn07582.gif)The third term follows from the expression for the rigid body rotation:

![](../graphics/stm_eqn07583.gif)Finally, the fourth term is obtained by differentiation along the surface coordinates:

![](../graphics/stm_eqn07584.gif)where

![](../graphics/stm_eqn07585.gif)is the surface curvature matrix.

Substitution of the last four expressions in the expression for the second variation yields

![](../graphics/stm_eqn07586.gif)

![](../graphics/stm_eqn07587.gif)As in the first variation, one can split the second variation into a normal and tangential components. For the normal component one finds

![](../graphics/stm_eqn07588.gif)

![](../graphics/stm_eqn07589.gif)and for the tangential components,

![](../graphics/stm_eqn07590.gif)The expression involving ![](../graphics/stm_eqn07591.gif) can be simplified somewhat. Observe that ![](../graphics/stm_eqn07592.gif); hence,

![](../graphics/stm_eqn07593.gif)Similarly

![](../graphics/stm_eqn07594.gif)If the local surface coordinate system is created by projection of a tangential Cartesian ![](../graphics/stm_eqn07595.gif)&#8211;![](../graphics/stm_eqn07596.gif) system onto the surface, it is readily established that the last terms vanish. Hence, we will assume that the last term in the second variation is zero. The final result is obtained by substitution of the expressions for the first-order variation of the slip in the expressions for the second variation. After some reordering and with ![](../graphics/stm_eqn07597.gif) this furnishes

![](../graphics/stm_eqn07598.gif)

![](../graphics/stm_eqn07599.gif)

![](../graphics/stm_eqn07600.gif)

![](../graphics/stm_eqn07601.gif)

![](../graphics/stm_eqn07602.gif)

![](../graphics/stm_eqn07603.gif)The first two terms of the expression for ![](../graphics/stm_eqn07421.gif) will only need to be included if slip occurs, whereas the expression for ![](../graphics/stm_eqn07604.gif) only needs to be taken into account if frictional forces are transmitted.

For dynamic applications we need the velocity and acceleration terms ![](../graphics/stm_eqn07605.gif) and ![](../graphics/stm_eqn07606.gif) to calculate impact forces and impulses correctly. These terms are

![](../graphics/stm_eqn07607.gif)(this is the same form as the first variation of ![](../graphics/stm_eqn07404.gif)); and

![](../graphics/stm_eqn07608.gif)
### Reference

### Reference

"Contact formulations in Abaqus/Standard,"  Section 38.1.1 of the Abaqus Analysis User's Guide