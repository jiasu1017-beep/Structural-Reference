# 3.6.4 Triangular facet shell elements

### 3.6.4 Triangular facet shell elements

**Product: **Abaqus/Standard

Element type STRI3 in Abaqus/Standard is a facet shell---a plate element used to approximate a shell. The element has three nodes, each with six degrees of freedom. The strains are based on thin plate theory, using a small-strain approximation. Arbitrary rigid body rotations are accounted for exactly by formulating the deformation of the element in a local coordinate system that rotates with the element. The element also satisfies the patch test, so that it will produce reliable results with appropriate meshes.

The bending of the element is based on a discrete Kirchhoff approach to plate bending, using Batoz's interpolation functions ([Batoz et al., 1980](07s01a01-References.md)). This formulation satisfies the Kirchhoff constraints all around the boundary of the triangle and provides linear variation of curvature throughout the element. However, the membrane strains are assumed constant within the element. In addition, a curved shell is approximated by this element as a set of facets formed by the planes defined by the three nodes of each element. For these reasons it is necessary to use a reasonably well refined mesh in most applications.
### Kinematics

A local orthonormal basis system, ![](../graphics/stm_eqn04149.gif) and ![](../graphics/stm_eqn04150.gif), is defined in the plane of each element in the reference configuration, using the standard Abaqus convention. ![](../graphics/stm_eqn04151.gif) and ![](../graphics/stm_eqn04152.gif) measure distance along ![](../graphics/stm_eqn04149.gif) and ![](../graphics/stm_eqn04150.gif) in the reference configuration.

Figure 3.6.4&#8211;1 Triangular facet shell in the reference configuration.

![](../graphics/stmtrifacetshellfig.png)The membrane strains are then defined as

![](../graphics/stm_eqn04153.gif)where

![](../graphics/stm_eqn04154.gif)is the metric in the current configuration, and

![](../graphics/stm_eqn04155.gif)is the metric in the reference configuration.

Here ![](../graphics/stm_eqn00117.gif) and ![](../graphics/stm_eqn00141.gif) are the spatial coordinates of a point in the current and reference configurations, respectively. Curvature changes are defined incrementally. To account for large rigid body rotations we use a local coordinate system that rotates with the plane defined by the three nodes of the element. The basis vectors chosen for this local system are ![](../graphics/stm_eqn04156.gif) and ![](../graphics/stm_eqn04157.gif). Since the membrane strains are assumed to be small, these vectors will be approximately orthonormal. The components of incremental rotation of the normal to the plate are defined as ![](../graphics/stm_eqn04158.gif) about ![](../graphics/stm_eqn04159.gif) and ![](../graphics/stm_eqn04160.gif) about ![](../graphics/stm_eqn04161.gif). The incremental displacement of the reference surface of the plate along the normal to the plane of its nodes is defined as ![](../graphics/stm_eqn04162.gif). (Note that ![](../graphics/stm_eqn04162.gif) will be zero at the nodes at all times because the plane containing ![](../graphics/stm_eqn04159.gif) and ![](../graphics/stm_eqn04161.gif) always passes through the nodes.) The Kirchhoff constraints are, approximately,

![](../graphics/stm_eqn04163.gif)and

![](../graphics/stm_eqn04164.gif)

[Batoz (1980)](07s01a01-References.md) assumes that ![](../graphics/stm_eqn04158.gif) and ![](../graphics/stm_eqn04165.gif) vary quadratically over the element and that ![](../graphics/stm_eqn04162.gif) is defined independently along each of the three sides of the element as a cubic function. The Kirchhoff constraints are then imposed at the corners and at the middle of each element edge along the direction of the edge to give

![](../graphics/stm_eqn04166.gif)and

![](../graphics/stm_eqn04167.gif)where ![](../graphics/stm_eqn04168.gif) is the array

![](../graphics/stm_eqn04169.gif)

In the above expressions ![](../graphics/stm_eqn04170.gif) and ![](../graphics/stm_eqn04171.gif) are interpolation functions that are defined by [Batoz (1980)](07s01a01-References.md), and the incremental rotation components at the nodes, ![](../graphics/stm_eqn04172.gif), are defined as

![](../graphics/stm_eqn04173.gif)where

![](../graphics/stm_eqn04174.gif)and ![](../graphics/stm_eqn04175.gif) are the increments of the rotational degrees of freedom at the node *N*, ![](../graphics/stm_eqn00162.gif) is the rotation matrix defined by ![](../graphics/stm_eqn04176.gif), and ![](../graphics/stm_eqn00278.gif) is the normal to the plane of the element's nodes at the beginning of the increment. Finally, the incremental curvature change measures are defined as

![](../graphics/stm_eqn04177.gif)

The three membrane strains and three curvature strains complete the basic kinematic description of the element, except that the use of six degrees of freedom per node introduces a spurious rotation at each node (only two incremental rotations at each node appear in the above equations---the rotation about the normal to the plane of the element's nodes does not enter). To deal with this problem, we define a generalized strain to be penalized with a small stiffness at each node as

![](../graphics/stm_eqn04178.gif)where

![](../graphics/stm_eqn04179.gif)and *j*, *k* are the node numbers in cyclic order forming the two sides of the triangle at the node *i*.
### First variations of strain

The first variations of strain are

![](../graphics/stm_eqn04180.gif)where

![](../graphics/stm_eqn04181.gif)and in ![](../graphics/stm_eqn04182.gif),

![](../graphics/stm_eqn04183.gif)

Also, for the "strain" used to introduce the extra stiffness at the nodes to avoid singularity caused by the component of rotation about the normal,

![](../graphics/stm_eqn04184.gif)
### Second variations of strain

The second variations of strain are

![](../graphics/stm_eqn04185.gif)where

![](../graphics/stm_eqn04186.gif)and

![](../graphics/stm_eqn04187.gif)Here ![](../graphics/stm_eqn04188.gif) and ![](../graphics/stm_eqn04189.gif) are coordinates in the plane of the element, normalized so that the nodes of the element are at (0,0), (1,0) and (0,1).
### Internal virtual work rate

The internal virtual work rate is defined as

![](../graphics/stm_eqn04190.gif)where ![](../graphics/stm_eqn04191.gif) is the strain at a point, *f*, away from the reference surface; ![](../graphics/stm_eqn04076.gif) are the stress components at *f*; *h* is the shell thickness; and ![](../graphics/stm_eqn04192.gif) is the penalty stiffness used to constrain the spurious rotation.

The formulation now proceeds as for the shell elements described in "Shear flexible small-strain shell elements,"  Section 3.6.3, using a 3-point integration scheme in the plane of the element.
### Reference

### Reference

"Shell elements: overview,"  Section 29.6.1 of the Abaqus Analysis User's Guide