# 3.2.6 Triangular, tetrahedral, and wedge elements

### 3.2.6 Triangular, tetrahedral, and wedge elements

**Products: **Abaqus/Standard  Abaqus/Explicit

The library of solid elements in Abaqus includes first- and second-order triangles, tetrahedra, and wedge elements for planar, axisymmetric, and three-dimensional analysis.

Hybrid versions of these elements are provided for use with incompressible and nearly incompressible constitutive models (see "Hybrid incompressible solid element formulation,"  Section 3.2.3, for a detailed discussion of the formulation used). However, these hybrid forms should be used only to fill in regions in meshes made of brick elements; otherwise, too many constraint variables may be introduced.

Second-order tetrahedra are not suitable for the analysis of contact problems: a constant pressure on an element face produces zero equivalent loads at the corner nodes. In contact problems this makes the contact condition at the corners indeterminate, with failure of the solution likely because of excessive gap chatter. The same argument holds true for contact on triangular faces of a wedge element.
### Interpolation

The interpolation is defined in terms of the element coordinates *g*, *h*, and *r* shown in [Figure 3.2.6&#8211;1](03s02a64-Triangular-tetrahedral-and-wedge-element.md). Since Abaqus is a Lagrangian code for most applications, these are also material coordinates. They each span a range from 0 to 1 in an element but satisfy the constraint that ![](../graphics/stm_eqn03027.gif) for triangles and wedges and ![](../graphics/stm_eqn03028.gif) for tetrahedra. The node numbering convention used in Abaqus for these elements is also shown in [Figure 3.2.6&#8211;1](03s02a64-Triangular-tetrahedral-and-wedge-element.md). Corner nodes are numbered first, and then the midside nodes for second-order elements. The interpolation functions are as follows.

First-order triangle (3 nodes):

![](../graphics/stm_eqn03029.gif)

Second-order triangle (6 nodes):

![](../graphics/stm_eqn03030.gif)

First-order tetrahedron (4 nodes):

![](../graphics/stm_eqn03031.gif)

Second-order tetrahedron (10 nodes):

![](../graphics/stm_eqn03032.gif)

Figure 3.2.6&#8211;1 Isoparametric master elements.

![](../graphics/stmtritet-iso-master-nls.png)

First-order wedge (6 nodes):

![](../graphics/stm_eqn03033.gif)

Second-order wedge (15 nodes):

![](../graphics/stm_eqn03034.gif)

Second-order variable 15&#8211;18 node wedge (assuming all 18 nodes are defined):

![](../graphics/stm_eqn03035.gif)where

![](../graphics/stm_eqn03036.gif)

![](../graphics/stm_eqn03037.gif)

![](../graphics/stm_eqn03038.gif)
### Integration

The first-order triangle and tetrahedron are constant stress elements and use a single integration point for the stiffness calculation when used in stress/displacement applications. A lumped mass matrix is used for both elements, with the total mass divided equally over the nodes. For heat transfer applications a three-point integration scheme is used for the conductivity and heat capacity matrices of the first-order triangle, with the integration points midway between the vertices and the centroid of the element; and a four-point integration scheme is used for the first-order tetrahedron. Distributed loads are integrated with two and three points for first-order triangles and tetrahedrons, respectively.

The three-point scheme is also used for the stiffness of the second-order triangle when it is used in stress/displacement applications. The mass matrix is integrated with a six-point scheme that integrates fourth-order polynomials exactly ([Cowper, 1973](07s01a01-References.md)). Distributed loads are integrated using three points. The heat transfer versions of the element use the six-point scheme for the conductivity and heat capacity matrices.

For stress/displacement applications the second-order tetrahedron uses 4 integration points for its stiffness matrix and 15 integration points for its consistent mass matrix. For heat transfer applications the conductivity and heat capacity matrices are integrated using 15 integration points. The first-order wedge uses 2 integration points for its stiffness matrix but 6 integration points for its lumped mass matrix. The second-order wedge uses 9 integration points for its stiffness matrix but 18 integration points for its consistent mass matrix. The integration schemes used for the second-order tetrahedra and wedge elements can be found in [Stroud (1971)](07s01a01-References.md).
### Reference

### Reference

"Solid (continuum) elements,"  Section 28.1.1 of the Abaqus Analysis User's Guide