# 5.1.1 Small-sliding interaction between bodies

### 5.1.1 Small-sliding interaction between bodies

**Product: **Abaqus/Standard

In Abaqus/Standard a capability is included to model small-sliding contact of two bodies with respect to each other. With this formulation the contacting surfaces can undergo only relatively small sliding relative to each other, but arbitrary rotation of the bodies is permitted. Small-sliding contact is computationally less expensive than finite-sliding contact, which is described in "Finite-sliding interaction between deformable bodies,"  Section 5.1.2.

The small-sliding capability can be used to model the interaction between two deformable bodies or between a deformable body and a rigid body in two and three dimensions. With this approach one surface definition provides the "master" surface and the other surface definition provides the "slave" surface. A kinematic constraint that the slave surface nodes do not penetrate the master surface is then enforced. The contacting surfaces need not have matching meshes; however, the best accuracy is obtained when the meshes are initially matching. For initially nonmatching meshes, accuracy can be improved by judiciously specifying initial adjustments to ensure that all slave nodes that should initially be in contact are located on the master surface.

The small-sliding contact capability is implemented by means of four internal contact elements designed to handle the following kinematic constraints:

two-dimensional contact between a slave node and a deformable master surface,

two-dimensional contact between a slave node and a rigid master surface,

three-dimensional contact between a slave node and a deformable master surface, and

three-dimensional contact between a slave node and a rigid master surface.These elements are not accessible to the user, and Abaqus will automatically cover a slave surface with the appropriate element type, based on the nature of the corresponding master surface.
### Identification of tangent plane based on nearest neighbor interaction

Although four internal element types are used to model the various types of small-sliding contact interactions supported by Abaqus/Standard, all four formulations are based on the notion that a given slave node always interacts with the same subset of master surface nodes. This nodal subset is initially determined by the Abaqus analysis input file processor from the undeformed model definition, thus avoiding the need to "track" the slave node during the course of the analysis. This set of nearest-neighbor nodes to the point on the master surface closest to the slave node is used to parametrize a contact plane with which the slave node will interact during the analysis. This concept is illustrated next for the case of a two-dimensional slave node interacting with a first-order master surface. This formulation can be generalized to second order as well as three-dimensional situations, but this generalization will not be discussed here.

Consider the contact interaction of three nodes---102, 103, and 104---on the slave surface with a master surface made up of first-order element faces described by nodes 1, 2, and 3, as shown in [Figure 5.1.1&#8211;1](05s01a132.md).

Figure 5.1.1&#8211;1 Slave nodes interacting with a two-dimensional master surface.

![](../graphics/stmslave-2d-master-nls.png)

Before initiating the search for the nodal subset of the master surface nodes that will interact with each node on the slave surface, unit normal vectors are computed for all the nodes on the master surface. For example, the unit normal vector ![](../graphics/stm_eqn03520.gif) is computed by averaging the unit normal vectors of segments 1&#8211;2 and 2&#8211;3. The user can also specify the normal vector for each node on the master surface. Additional unit normal vectors are computed for each segment a distance ![](../graphics/stm_eqn07375.gif) from each end of the segment, where ![](../graphics/stm_eqn00377.gif) is a fraction and ![](../graphics/stm_eqn07376.gif) is the length of the segment; e.g., ![](../graphics/stm_eqn07377.gif). Currently the value of ![](../graphics/stm_eqn00377.gif) is set to 0.5, and the user cannot change this value. The unit normals computed are then used to define a smooth varying normal vector, ![](../graphics/stm_eqn07378.gif), at any point, ![](../graphics/stm_eqn02549.gif), on the master surface.

An "anchor" point on the master surface, ![](../graphics/stm_eqn07379.gif), is computed for each slave node so that the vector formed by the slave node and ![](../graphics/stm_eqn07379.gif) coincides with the normal vector ![](../graphics/stm_eqn07380.gif). Suppose that a search for the anchor point, ![](../graphics/stm_eqn07379.gif), of slave node 103 reveals that ![](../graphics/stm_eqn07379.gif) is on segment 1&#8211;2. Then, we find that

![](../graphics/stm_eqn07381.gif)where ![](../graphics/stm_eqn04123.gif) and ![](../graphics/stm_eqn07382.gif) are the coordinates of nodes 1 and 2, respectively, and ![](../graphics/stm_eqn07383.gif) is calculated so that ![](../graphics/stm_eqn07384.gif) coincides with ![](../graphics/stm_eqn07380.gif). Moreover, the contact plane tangent direction, ![](../graphics/stm_eqn01673.gif), at ![](../graphics/stm_eqn07379.gif) is chosen so that it is perpendicular to ![](../graphics/stm_eqn07380.gif); i.e.,

![](../graphics/stm_eqn07385.gif)where ![](../graphics/stm_eqn00553.gif) is a (constant) rotation matrix.

The small-sliding contact constraint is achieved by requiring that slave node 103 interact with the tangent plane whose current anchor point coordinates are, at any time, given by

![](../graphics/stm_eqn07386.gif)where ![](../graphics/stm_eqn07387.gif) and ![](../graphics/stm_eqn07388.gif), and whose current tangent direction is given by

![](../graphics/stm_eqn07389.gif)where ![](../graphics/stm_eqn07390.gif) and ![](../graphics/stm_eqn07391.gif). Since the above expressions for the point ![](../graphics/stm_eqn07392.gif) and the vector ![](../graphics/stm_eqn00427.gif) resulted from barycentric (affine) combinations of the points ![](../graphics/stm_eqn07393.gif) and ![](../graphics/stm_eqn07394.gif)---that is,

![](../graphics/stm_eqn07395.gif)the contact plane will be mapped properly under affine transformations such as translation, scaling (stretching), and rotation.

Next, suppose that a search for the anchor point of slave node 104 reveals that the anchor point is coincident to the master node 2. In this case the anchor point is chosen to be ![](../graphics/stm_eqn07382.gif), or in terms of the coordinates of the three master nodes 1, 2, and 3,

![](../graphics/stm_eqn07396.gif)where ![](../graphics/stm_eqn07397.gif), ![](../graphics/stm_eqn07398.gif), and ![](../graphics/stm_eqn07399.gif). The contact tangent direction at ![](../graphics/stm_eqn07382.gif) is simply

![](../graphics/stm_eqn07400.gif)However, we want to express ![](../graphics/stm_eqn01673.gif) in terms of the coordinates of the three nodes 1, 2, and 3 to be able to track the evolution of the tangent plane. To this end, we solve for the ![](../graphics/stm_eqn07401.gif) from the equation

![](../graphics/stm_eqn07402.gif)subject to the barycentric constraint

![](../graphics/stm_eqn07403.gif)The barycentric constraint ensures that the resulting expression for the contact plane tangent direction behaves properly under affine transformations such as translations and rotations.
### Contact formulation as a constrained variational principle

At each slave node that can come into contact with a master surface we construct a measure of overclosure ![](../graphics/stm_eqn07404.gif) (penetration of the node into the master surface) and measures of relative slip ![](../graphics/stm_eqn03479.gif). These kinematic measures are then used, together with appropriate Lagrange multiplier techniques, to introduce surface interaction theories for contact and friction, as described in "Contact pressure definition,"  Section 5.2.1, and "Coulomb friction,"  Section 5.2.3.

In two dimensions the overclosure ![](../graphics/stm_eqn07404.gif) along the unit contact normal ![](../graphics/stm_eqn00483.gif) between a slave point ![](../graphics/stm_eqn07405.gif) and a master line ![](../graphics/stm_eqn07406.gif), where ![](../graphics/stm_eqn01040.gif) parametrizes the line, is determined by finding the vector ![](../graphics/stm_eqn07407.gif) from the slave node to the line that is perpendicular to the tangent vector ![](../graphics/stm_eqn00427.gif) at ![](../graphics/stm_eqn00156.gif). Mathematically, we express the required condition as

![](../graphics/stm_eqn07408.gif)when

![](../graphics/stm_eqn07409.gif)

Similarly, in three dimensions the overclosure ![](../graphics/stm_eqn07404.gif) along the unit contact normal ![](../graphics/stm_eqn00483.gif) between a slave point ![](../graphics/stm_eqn07405.gif) and a master plane ![](../graphics/stm_eqn07410.gif), where ![](../graphics/stm_eqn07411.gif) parametrize the plane, is determined by finding the vector ![](../graphics/stm_eqn07407.gif) from the slave node to the plane that is perpendicular to the tangent vectors ![](../graphics/stm_eqn07412.gif) and ![](../graphics/stm_eqn07413.gif) at ![](../graphics/stm_eqn00156.gif). Mathematically, we express the required condition as

![](../graphics/stm_eqn07414.gif)when

![](../graphics/stm_eqn07415.gif)

If at a given slave node ![](../graphics/stm_eqn07416.gif), there is no contact between the surfaces at that node, and no further surface interaction calculations are needed. If ![](../graphics/stm_eqn07417.gif), the surfaces are in contact. The contact constraint ![](../graphics/stm_eqn07418.gif) is enforced by introducing a Lagrange multiplier, ![](../graphics/stm_eqn07419.gif), whose value provides the contact pressure at the point. To enforce the contact constraint, we need the first variation ![](../graphics/stm_eqn07420.gif); and for the Newton iterations, we need the second variation, ![](../graphics/stm_eqn07421.gif). Likewise, if frictional forces are to be transmitted across the contacting surfaces, the first variations of relative slip, ![](../graphics/stm_eqn07422.gif), and the second variations, ![](../graphics/stm_eqn07423.gif), are needed in the formulation. The derivation of some of these quantities is described next for all four small-sliding contact formulations.
### Formulation for two-dimensional small-sliding deformable contact

For the case of two-dimensional small-sliding deformable contact, a point on the contact line associated with a slave node ![](../graphics/stm_eqn07424.gif) is represented by the vector

![](../graphics/stm_eqn07425.gif)where, as described previously, the line's anchor point---![](../graphics/stm_eqn07392.gif)---and its tangent vector---![](../graphics/stm_eqn00427.gif)---are functions of the current master node coordinates, ![](../graphics/stm_eqn07426.gif). Hence, the vector ![](../graphics/stm_eqn00427.gif) is, in general, a nonunit vector. Linearization of [Equation 5.1.1&#8211;1](05s01a132.md) yields

![](../graphics/stm_eqn07427.gif)where ![](../graphics/stm_eqn07428.gif), ![](../graphics/stm_eqn07429.gif), and ![](../graphics/stm_eqn07430.gif).

Taking the dot product of [Equation 5.1.1&#8211;4](05s01a132.md) with ![](../graphics/stm_eqn00483.gif) results in the following expression for ![](../graphics/stm_eqn07420.gif):

![](../graphics/stm_eqn07431.gif)

Likewise, taking the dot product of [Equation 5.1.1&#8211;4](05s01a132.md) with the normalized tangent vector ![](../graphics/stm_eqn07432.gif) and setting ![](../graphics/stm_eqn07418.gif) results in the following expression for the variation in slip:

![](../graphics/stm_eqn07433.gif)

Suitable expressions for ![](../graphics/stm_eqn07421.gif) and ![](../graphics/stm_eqn07434.gif) can be derived by linearizing [Equation 5.1.1&#8211;4](05s01a132.md) and applying the techniques highlighted above. Since the resulting expressions do not provide additional insight into the understanding of this capability, they will not be presented here.
### Formulation for three-dimensional small-sliding deformable contact

The three-dimensional small-sliding deformable contact formulation is a straightforward generalization of the previous two-dimensional formulation. A point on the contact plane associated with a slave node ![](../graphics/stm_eqn07424.gif) is represented by the vector

![](../graphics/stm_eqn07435.gif)where the plane's anchor point---![](../graphics/stm_eqn07392.gif)---and its two tangent vectors---![](../graphics/stm_eqn07412.gif) and ![](../graphics/stm_eqn07413.gif)---are functions of the current master node coordinates ![](../graphics/stm_eqn07436.gif). Linearization of [Equation 5.1.1&#8211;2](05s01a132.md) yields

![](../graphics/stm_eqn07437.gif)where ![](../graphics/stm_eqn07438.gif) and ![](../graphics/stm_eqn07439.gif).

Taking the dot product of [Equation 5.1.1&#8211;7](05s01a132.md) with ![](../graphics/stm_eqn00483.gif) results in the following expression for ![](../graphics/stm_eqn07420.gif):

![](../graphics/stm_eqn07440.gif)

Likewise, taking the dot product of [Equation 5.1.1&#8211;7](05s01a132.md) with ![](../graphics/stm_eqn07441.gif) and setting ![](../graphics/stm_eqn07418.gif) results in the following expression for the variation of the first slip component:

![](../graphics/stm_eqn07442.gif)Similarly, taking the dot product of [Equation 5.1.1&#8211;7](05s01a132.md) with ![](../graphics/stm_eqn07443.gif) and setting ![](../graphics/stm_eqn07418.gif) results in the following expression for the variation of the second slip component:

![](../graphics/stm_eqn07444.gif)
### Formulation for two-dimensional small-sliding rigid contact

The formulation for two-dimensional small-sliding rigid contact follows from its deformable counterpart by exploiting the fact that the evolution of the contact plane is fully determined by the motion of the rigid body's reference node. [Figure 5.1.1&#8211;2](05s01a132.md) shows how the undeformed coordinates ![](../graphics/stm_eqn07379.gif) of the contact plane's anchor point are related vectorially to the undeformed coordinates of the rigid reference node, ![](../graphics/stm_eqn07445.gif), and the relative position vector ![](../graphics/stm_eqn00304.gif).We can express this relationship as

![](../graphics/stm_eqn07446.gif)

Figure 5.1.1&#8211;2 Rigid body reference geometry.

![](../graphics/stmrigid-body-ref-geom.png)

Suppose the rigid reference node undergoes a motion described by the displacement vector ![](../graphics/stm_eqn07447.gif) and the rotation vector ![](../graphics/stm_eqn07448.gif), then the current coordinates of the contact plane's anchor point are given by

![](../graphics/stm_eqn07449.gif)where ![](../graphics/stm_eqn00162.gif) is the orthogonal matrix that produces the rotation ![](../graphics/stm_eqn07448.gif) (see "Rotation variables,"  Section 1.3.1) and ![](../graphics/stm_eqn03949.gif) is the current position vector from the rigid reference node to the anchor point. The rotation matrix is also used to obtain the contact plane's current tangent and current normal as follows:

![](../graphics/stm_eqn07450.gif)where ![](../graphics/stm_eqn07451.gif) and ![](../graphics/stm_eqn07452.gif) are the initial contact tangent and normal at ![](../graphics/stm_eqn07379.gif), respectively, as shown in [Figure 5.1.1&#8211;2](05s01a132.md). By definition, a rigid surface cannot stretch; therefore, a point on the rigid contact line associated with a slave node ![](../graphics/stm_eqn07424.gif) is represented by the vector

![](../graphics/stm_eqn07453.gif)where---unlike the vector ![](../graphics/stm_eqn00427.gif) in [Equation 5.1.1&#8211;3](05s01a132.md)---the tangent ![](../graphics/stm_eqn00479.gif) is always a unit vector.

Linearization of [Equation 5.1.1&#8211;11](05s01a132.md) and [Equation 5.1.1&#8211;12](05s01a132.md) results in the following expressions for the first variations of the anchor coordinates and the contact plane's tangent:

![](../graphics/stm_eqn07454.gif)

Replacing ![](../graphics/stm_eqn00427.gif) by ![](../graphics/stm_eqn00479.gif) in [Equation 5.1.1&#8211;5](05s01a132.md), noting that ![](../graphics/stm_eqn07455.gif), and substituting for ![](../graphics/stm_eqn07456.gif) and ![](../graphics/stm_eqn07457.gif) from [Equation 5.1.1&#8211;13](05s01a132.md) results in the following expression for ![](../graphics/stm_eqn07420.gif):

![](../graphics/stm_eqn07458.gif)Similar manipulation of [Equation 5.1.1&#8211;6](05s01a132.md) yields the following expression for ![](../graphics/stm_eqn07459.gif):

![](../graphics/stm_eqn07460.gif)
### Formulation for three-dimensional small-sliding rigid contact

The three-dimensional small-sliding rigid contact formulation can also be derived from its deformable counterpart by generalizing some of the expressions that were introduced in the previous section. In particular, in this formulation the rigid reference node can undergo an arbitrary finite rotation described by the rotation vector ![](../graphics/stm_eqn07461.gif). Consequently, [Equation 5.1.1&#8211;13](05s01a132.md) for the variations of the anchor point coordinates and the contact plane's tangent generalize to

![](../graphics/stm_eqn07462.gif)where ![](../graphics/stm_eqn07463.gif) is the skew-symmetric matrix associated with the linearized rotation ![](../graphics/stm_eqn07464.gif), as explained in "Rotation variables,"  Section 1.3.1.

Replacing ![](../graphics/stm_eqn07465.gif) by ![](../graphics/stm_eqn04200.gif) in [Equation 5.1.1&#8211;8](05s01a132.md) through [Equation 5.1.1&#8211;10](05s01a132.md) and substituting for ![](../graphics/stm_eqn07456.gif) and ![](../graphics/stm_eqn07466.gif) from above results in the following expressions for ![](../graphics/stm_eqn07420.gif), ![](../graphics/stm_eqn07467.gif), and ![](../graphics/stm_eqn07468.gif):

![](../graphics/stm_eqn07469.gif)

![](../graphics/stm_eqn07470.gif)

![](../graphics/stm_eqn07471.gif)
### Reference

### Reference

"Contact formulations in Abaqus/Standard,"  Section 38.1.1 of the Abaqus Analysis User's Guide