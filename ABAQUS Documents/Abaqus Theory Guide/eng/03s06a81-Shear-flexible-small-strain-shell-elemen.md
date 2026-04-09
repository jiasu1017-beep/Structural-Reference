# 3.6.3 Shear flexible small-strain shell elements

### 3.6.3 Shear flexible small-strain shell elements

**Product: **Abaqus/Standard

This section discusses the formulation of the small-strain shear flexible elements in Abaqus/Standard, which are quadrilaterals (S4R5, S8R5, S9R5, and S8R), except for the 6-node triangle STRI65. The essential idea of these elements is that the position of a point in the shell reference surface---![](../graphics/stm_eqn00117.gif)---and the components of a vector ![](../graphics/stm_eqn00483.gif)---which is approximately normal to the reference surface---are interpolated independently. The kinematics of the shell theory then consist of measuring membrane strain on the reference surface from the derivatives of ![](../graphics/stm_eqn00117.gif) with respect to position on the surface and bending strain from the derivatives of ![](../graphics/stm_eqn00483.gif); the strain measures that are used for this purpose are approximations to Koiter-Sanders theory strains ([Budiansky and Sanders, 1963](07s01a01-References.md)). The transverse shear strains are measured as the changes in the projections of ![](../graphics/stm_eqn00483.gif) onto tangents to the shell's reference surface. For these element types the strain measures are suitable for large rotations but small strains, and the change in the shell's thickness caused by deformation is neglected.
### Notation

A typical piece of shell surface is shown in [Figure 3.6.3&#8211;1](03s06a81-Shear-flexible-small-strain-shell-elemen.md).

Figure 3.6.3&#8211;1 Shell reference surface.

![](../graphics/stmshell-ref-surf.png) Let (![](../graphics/stm_eqn04038.gif), ![](../graphics/stm_eqn04039.gif)) be a set of Gaussian surface coordinates on the shell reference surface. Since these coordinates are only needed locally at an integration point, we use the element's isoparametric coordinates as these coordinates. ![](../graphics/stm_eqn04083.gif) is the current position of a point on the interpolated reference surface, and ![](../graphics/stm_eqn04084.gif) is the initial position of the same point. The unit vector

![](../graphics/stm_eqn04085.gif)is the unit normal to the interpolated reference surface in the initial configuration. This vector gives a "sidedness" to the surface---one surface of the shell is the "top" surface (in the positive direction along ![](../graphics/stm_eqn00278.gif) from the shell's reference surface) and the other is the bottom surface. The vector corresponding to ![](../graphics/stm_eqn00278.gif) in the current configuration, ![](../graphics/stm_eqn00483.gif), will be made approximately normal to the reference surface in the current configuration by imposing the Kirchhoff constraint discretely.

In the rest of this section Greek indices will be used to indicate values associated with the (two-dimensional) reference surface and so will sum over the range 1, 2 under the summation convention.

First, we establish convenient directions for stress and strain output. These will be local material directions, indistinguishable (to the order of approximation) from corotational directions, since we assume strains are small. The standard convention used throughout Abaqus for such local directions on a surface is as follows.

It is most convenient to choose orthogonal directions. Define

![](../graphics/stm_eqn04086.gif)so long as ![](../graphics/stm_eqn04087.gif), where ![](../graphics/stm_eqn04088.gif) is a unit vector in the global *X*-direction; otherwise,

![](../graphics/stm_eqn04089.gif)where ![](../graphics/stm_eqn02234.gif) is a unit vector in the global *Z*-direction. Then define

![](../graphics/stm_eqn04090.gif)

Let

![](../graphics/stm_eqn04091.gif)so that the ![](../graphics/stm_eqn04092.gif) are locally defined distance measuring coordinates at each material point. The transformation

![](../graphics/stm_eqn04093.gif)transforms locally with respect to surface coordinates. Here

![](../graphics/stm_eqn04094.gif)

Stress and strain components are formed in the (![](../graphics/stm_eqn04095.gif), ![](../graphics/stm_eqn04096.gif)) directions.
### Surface measures

The following surface measures are defined. The metric of the deformed surface is

![](../graphics/stm_eqn04097.gif)and an approximation to the curvature tensor (the second fundamental form) is

![](../graphics/stm_eqn04098.gif)(this is only an approximation because ![](../graphics/stm_eqn00483.gif) is not exactly normal to the surface in the current configuration).

The corresponding measures associated with the original reference surface are the metric

![](../graphics/stm_eqn04099.gif)and the approximation to the curvature

![](../graphics/stm_eqn04100.gif)The vectors ![](../graphics/stm_eqn04101.gif) are defined from the derivatives of the interpolation functions and the "normals" at the nodes. These nodal normals are calculated as average values of the normals to the surfaces of all elements abutting the node. Abaqus determines if the surface is intended to be smooth at the node (the criterion is that the angle between the normals at the node should be less than 20). If the surface is not calculated as smooth, separate normals are set up in the different surface branches at the node. Thus, ![](../graphics/stm_eqn04102.gif) should be a reasonable approximation to the second fundamental form of the original reference surface.
### Displacements

The nodal variables for shell elements are the displacements of the shell's reference surface, ![](../graphics/stm_eqn04103.gif), and the normal direction, ![](../graphics/stm_eqn00483.gif). Since ![](../graphics/stm_eqn00483.gif) is defined to be a unit vector, only two independent values are needed to define ![](../graphics/stm_eqn00483.gif), so that this type of shell element needs only five degrees of freedom per node. In Abaqus this issue is addressed in two ways. At nodes in a smooth shell surface in those elements that naturally have five degrees of freedom per node, Abaqus stores the values of the projections of the change in ![](../graphics/stm_eqn00483.gif) projected onto two orthogonal directions in the shell surface at the start of the increment to define ![](../graphics/stm_eqn00483.gif). Otherwise, Abaqus stores the usual rotation triplet, ![](../graphics/stm_eqn00242.gif), at the node. This latter method leaves a redundant degree of freedom if the node is on a smooth surface. A small stiffness is introduced locally at the node to constrain this extra degree of freedom to a measure of the same rotation of the shell's reference surface.
### Interpolation

The same bipolynomial interpolation functions are used for all components of ![](../graphics/stm_eqn00428.gif), ![](../graphics/stm_eqn00141.gif), ![](../graphics/stm_eqn00278.gif), and ![](../graphics/stm_eqn00483.gif). The shear flexible shell elements in the library use bilinear interpolation (four nodes), fully biquadratic interpolation (nine nodes), and "serendipity" quadratics (eight nodes).
### Strains

The reference surface membrane strains are

![](../graphics/stm_eqn04104.gif)

The curvature change is

![](../graphics/stm_eqn04105.gif)

The transverse shears are

![](../graphics/stm_eqn04106.gif)where

![](../graphics/stm_eqn04107.gif)is a unit vector, tangent to the ![](../graphics/stm_eqn04092.gif) line in the current surface.

In addition to these strains, when six degrees of freedom are used at the nodes of the elements, the extra rotation degree of freedom is constrained with a penalty, as follows.

When such a node is the corner node of an element, define ![](../graphics/stm_eqn02571.gif), ![](../graphics/stm_eqn02572.gif), ![](../graphics/stm_eqn03519.gif), ![](../graphics/stm_eqn04095.gif), and ![](../graphics/stm_eqn04096.gif) in the element as above. Notice that these will be different in each element at the node, since the interpolated surface is not generally continuous. Then the strain to be penalized is defined as

![](../graphics/stm_eqn04108.gif)where

![](../graphics/stm_eqn04109.gif)is the rotated tangent direction, as defined by the rotation values at the node, and

![](../graphics/stm_eqn04110.gif)is the rotated tangent direction defined by the motion of the interpolated reference surface at the node.

At each midside node in the original configuration, define ![](../graphics/stm_eqn00278.gif) as the average surface normal for the elements of this surface branch at the nodes (there will be at most two such elements) and ![](../graphics/stm_eqn00553.gif) as the tangent to the edge. Then define

![](../graphics/stm_eqn04111.gif)as rotated values of ![](../graphics/stm_eqn00553.gif) and ![](../graphics/stm_eqn00278.gif), as defined by the rotation values at the node. The vector

![](../graphics/stm_eqn04112.gif)is then normal to ![](../graphics/stm_eqn00483.gif) and to the edge.

The strain to be penalized at these midside nodes is then defined as

![](../graphics/stm_eqn04113.gif)where

![](../graphics/stm_eqn04114.gif)is the tangent to the edge of the element in the current position of the reference surface.
### Penalties

The transverse shear strains are calculated at a set of reduced integration points and have the following stiffness associated with them:

![](../graphics/stm_eqn04115.gif)where the ![](../graphics/stm_eqn04116.gif) are the elastic moduli associated with transverse shear. The ![](../graphics/stm_eqn04116.gif) are defined directly by the user or are computed from the elastic moduli given for the layers of the shell. *h* is the shell thickness; ![](../graphics/stm_eqn04117.gif) is the value of reference surface area associated with this integration point in the numerical integration scheme; *q* is a numerical factor, currently set to ![](../graphics/stm_eqn04118.gif). (See [Hughes et al., 1977](07s01a01-References.md), for a discussion of such factors.) Transverse shears are always treated elastically: nonlinear material calculations in shells are based on plane stress theory, using the membrane and bending strains to define the strain on the surface parallel to the shell's reference surface at each integration point through the shell's thickness.

When rotation constraints are required at nodes that use six degrees of freedom, the penalty used is

![](../graphics/stm_eqn04119.gif)

This is the same as the transverse shear constraint, except that ![](../graphics/stm_eqn04117.gif) is here an area "assigned" to the node and the factor *k* is introduced. This (small) factor has been chosen based on numerical experiments, to be large enough to avoid singularities yet small enough to avoid adding significantly to the stiffness of the model.

These strain measures, with the interpolation specified above, give zero strain for any general rigid body motion

![](../graphics/stm_eqn04120.gif)where ![](../graphics/stm_eqn04121.gif), ![](../graphics/stm_eqn04122.gif), and ![](../graphics/stm_eqn04123.gif) are constant.
### First variations of strain

The first variations of the strains are

![](../graphics/stm_eqn04124.gif)where

![](../graphics/stm_eqn04125.gif) and at the midside nodes

![](../graphics/stm_eqn04126.gif)
### Second variations of strains

In forming the initial stress matrix we approximate by neglecting ![](../graphics/stm_eqn04127.gif), ![](../graphics/stm_eqn04128.gif), etc, to simplify the expressions and reduce the cost of forming the matrix. Numerical experiments have suggested that, at least for the problems tested, this does not significantly affect the convergence rate. With this approximation,

![](../graphics/stm_eqn04129.gif)

![](../graphics/stm_eqn04130.gif)

![](../graphics/stm_eqn04131.gif)

![](../graphics/stm_eqn04132.gif)and

![](../graphics/stm_eqn04133.gif)
### Internal virtual work rate

For these shell elements the internal virtual work rate is assumed to be

![](../graphics/stm_eqn04134.gif)where ![](../graphics/stm_eqn04135.gif), ![](../graphics/stm_eqn04136.gif), and ![](../graphics/stm_eqn04137.gif) are the transverse shear stiffness and the penalties defined above and *r* indicates the integration points at which transverse shears are calculated, ![](../graphics/stm_eqn04138.gif) indicates corner nodes at which six degrees of freedom are used, and ![](../graphics/stm_eqn04139.gif) indicates midside nodes at which six degrees of freedom are used. Here ![](../graphics/stm_eqn04140.gif) and ![](../graphics/stm_eqn04076.gif) are the strain and stress in the (![](../graphics/stm_eqn04092.gif), ![](../graphics/stm_eqn04141.gif)) material directions in a surface offset by a distance *z* from the reference surface. The usual Kirchhoff assumption is adopted:

![](../graphics/stm_eqn04142.gif)so that the first term above is

![](../graphics/stm_eqn04143.gif)

The thickness direction integrations are performed numerically in Abaqus. The integration scheme is a Simpson's rule, of user-chosen order. The shell can also be considered layered, with different properties at each layer and a different integration scheme assigned (by the user) to each layer.
### Pressure load stiffness

The load stiffness associated with pressure loading is often important in shells, especially in eigenvalue buckling estimates on elastic shells. In Abaqus/Standard the pressure load stiffness is implemented as a symmetric form, thus assuming that the pressure magnitude is constant over the surface and neglecting free edge effects. See [Hibbitt (1979)](07s01a01-References.md) and [Mang (1980)](07s01a01-References.md) for details.

The load stiffness is obtained in such a form as follows. The external virtual work associated with pressure is

![](../graphics/stm_eqn04144.gif)where ![](../graphics/stm_eqn00156.gif) is the pressure load per unit area, given in terms of the (externally prescribed) pressure magnitude, *p*, as

![](../graphics/stm_eqn04145.gif)

Thus,

![](../graphics/stm_eqn04146.gif)

The change in this term caused by change of displacement of the shell (the "load stiffness") is

![](../graphics/stm_eqn04147.gif)since we assume that pressure magnitude, *p*, is externally prescribed and has no dependence on position, ![](../graphics/stm_eqn00117.gif). Neglecting free edge effects, and assuming the magnitude *p* is uniform, results in the symmetric form

![](../graphics/stm_eqn04148.gif)

This is the pressure load stiffness provided in Abaqus.
### Reference

### Reference

"Shell elements: overview,"  Section 29.6.1 of the Abaqus Analysis User's Guide