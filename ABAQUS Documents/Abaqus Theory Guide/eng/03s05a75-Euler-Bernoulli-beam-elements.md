# 3.5.3 Euler-Bernoulli beam elements

### 3.5.3 Euler-Bernoulli beam elements

**Product: **Abaqus/Standard

In these elements it is assumed that the internal virtual work rate is associated with axial strain and torsional shear only. Further, it is assumed that the cross-section does not deform in its plane or warp out of its plane, and that this cross-sectional plane remains normal to the beam axis. These are the classical assumptions of the Euler-Bernoulli beam theory, which provides satisfactory results for slender beams.

Let ![](../graphics/stm_eqn03804.gif) be material coordinates such that *S* locates points on the beam axis and ![](../graphics/stm_eqn03805.gif) measures distance in the cross-section. In addition, let ![](../graphics/stm_eqn03806.gif) be unit vectors normal to the beam axis in the current configuration: ![](../graphics/stm_eqn03807.gif). Then the position of a point of the beam in the current configuration is

![](../graphics/stm_eqn03808.gif)where ![](../graphics/stm_eqn03809.gif) is the point on the beam axis of the cross-section containing ![](../graphics/stm_eqn03810.gif). Then

![](../graphics/stm_eqn03811.gif)and so length on the fiber at ![](../graphics/stm_eqn03804.gif) is measured in the current configuration as

![](../graphics/stm_eqn03812.gif)Now since the beam is slender, we will neglect terms of second-order in *g* and *h*, the distance measuring material coordinates in the cross-section. Thus,

![](../graphics/stm_eqn03813.gif)
### Strain measures

The internal virtual work rate associated with axial stress is

![](../graphics/stm_eqn03814.gif)where ![](../graphics/stm_eqn03815.gif)and ![](../graphics/stm_eqn03816.gif) are any material stress and strain measures associated with axial deformation at the point ![](../graphics/stm_eqn03804.gif) of the beam, since strains are assumed to be small. For this purpose we will use Green's strain so that

![](../graphics/stm_eqn03817.gif)where ![](../graphics/stm_eqn03818.gif), the square of the ratio of current configuration length to reference configuration length in the axial direction on the fiber. From [Equation 3.5.3&#8211;1](03s05a75.md) and its equivalent in the reference configuration, we have

![](../graphics/stm_eqn03819.gif)Again, neglecting all but first-order terms in *g* and *h* because of the slenderness assumption, this becomes

![](../graphics/stm_eqn03820.gif)where

![](../graphics/stm_eqn03821.gif)This simplification allows us to write the internal virtual work rate associated with axial stress as

![](../graphics/stm_eqn03822.gif)where

![](../graphics/stm_eqn03823.gif)with

![](../graphics/stm_eqn03824.gif)and

![](../graphics/stm_eqn03825.gif)Now the cross-sectional base vectors ![](../graphics/stm_eqn03500.gif) and ![](../graphics/stm_eqn03501.gif) are assumed to remain normal to the beam axis, so

![](../graphics/stm_eqn03826.gif)Hence,

![](../graphics/stm_eqn03827.gif)So we have

![](../graphics/stm_eqn03828.gif)and

![](../graphics/stm_eqn03829.gif)

This defines the generalized strains associated with axial stretch. For torsional strain the internal virtual work rate is

![](../graphics/stm_eqn03830.gif)where

![](../graphics/stm_eqn03831.gif)and ![](../graphics/stm_eqn03741.gif) is the proportionality constant between shear strains and torsional strains (see "Beam element formulation,"  Section 3.5.2, for details). For computational simplicity the form of the torsional strains is taken to be

![](../graphics/stm_eqn03832.gif)where

![](../graphics/stm_eqn03833.gif)and

![](../graphics/stm_eqn03834.gif)This assumes a linear interpolation of rotation ![](../graphics/stm_eqn03835.gif) along the beam. Thus, the generalized strain measures for these beams are

![](../graphics/stm_eqn00377.gif)

axial strain,

![](../graphics/stm_eqn03836.gif) and ![](../graphics/stm_eqn03837.gif)

the beam curvature change measures, and

![](../graphics/stm_eqn03838.gif)

the torsional strain.With these measures, the internal virtual work rate can be written

![](../graphics/stm_eqn03839.gif)
### Internal virtual work rate Jacobian

For the Jacobian matrix of the overall Newton method, [Equation 2.1.1&#8211;3](02s01a13.md), the variation of this internal work rate with respect to nodal displacement variations must be formed. The constitutive theory is written as

![](../graphics/stm_eqn03840.gif)and so

![](../graphics/stm_eqn03841.gif)

![](../graphics/stm_eqn03842.gif)where ![](../graphics/stm_eqn03843.gif) is the section stiffness matrix obtained by integration over the cross-section. See "Beam element formulation,"  Section 3.5.2, for more information on section integration.
### First variations of strains

Taking the variations of the above strain definitions gives directly

![](../graphics/stm_eqn03844.gif)In these expressions we need ![](../graphics/stm_eqn03845.gif) and ![](../graphics/stm_eqn03846.gif) as well as ![](../graphics/stm_eqn03847.gif); these are now derived. From the expression for ![](../graphics/stm_eqn03848.gif), namely

![](../graphics/stm_eqn03849.gif)another ancillary vector ![](../graphics/stm_eqn03850.gif), normal to the tangent, is defined by

![](../graphics/stm_eqn03851.gif)so that

![](../graphics/stm_eqn03852.gif)In addition,

![](../graphics/stm_eqn03853.gif)so that

![](../graphics/stm_eqn03854.gif)Since ![](../graphics/stm_eqn03855.gif) form an orthonormal triad,

![](../graphics/stm_eqn03856.gif) because ![](../graphics/stm_eqn03857.gif). From the definition of ![](../graphics/stm_eqn03858.gif), it is straightforward to show that

![](../graphics/stm_eqn03859.gif)So

![](../graphics/stm_eqn03860.gif)and

![](../graphics/stm_eqn03861.gif)Thus,

![](../graphics/stm_eqn03862.gif)We can also write

![](../graphics/stm_eqn03863.gif)and

![](../graphics/stm_eqn03864.gif)Combining terms appropriately,

![](../graphics/stm_eqn03865.gif)Hence, from [Equation 3.5.3&#8211;2](03s05a75.md)

![](../graphics/stm_eqn03866.gif)In a similar manner one can show that

![](../graphics/stm_eqn03867.gif)The first variations of strain become

![](../graphics/stm_eqn03868.gif)so that

![](../graphics/stm_eqn03869.gif)In addition,

![](../graphics/stm_eqn03853.gif)so that

![](../graphics/stm_eqn03870.gif)since ![](../graphics/stm_eqn03871.gif) form an orthonormal triad,

![](../graphics/stm_eqn03872.gif)because

![](../graphics/stm_eqn03873.gif)
### Second variations of strains

The second variation of the axial strain is simply

![](../graphics/stm_eqn03874.gif)To compute the second variations of bending strain, we need expressions for ![](../graphics/stm_eqn03875.gif). These are obtained by approximating

![](../graphics/stm_eqn03876.gif)from which

![](../graphics/stm_eqn03877.gif)Using these expressions, the second variations of bending strains are written as

![](../graphics/stm_eqn03878.gif)and

![](../graphics/stm_eqn03879.gif)For the torsional strain contribution to the initial stress matrix, we approximate

![](../graphics/stm_eqn03880.gif)This matrix is again unsymmetric.
### Interpolation

In the virtual work equation the strains include second derivatives of displacement. For this reason continuity of rotation as well as displacement is needed so that the Hermitian polynomial interpolation functions are the minimum interpolation order needed. These are used here. The Hermite cubic is written in terms of the function value and its derivative at the ends of the interval:

![](../graphics/stm_eqn03881.gif)with node 1 at ![](../graphics/stm_eqn03882.gif) and node 2 at ![](../graphics/stm_eqn03450.gif).

These functions are used in Abaqus to interpolate the components of displacement ![](../graphics/stm_eqn02547.gif) and the initial position vector ![](../graphics/stm_eqn02550.gif), so that the elements are basically isoparametric. In addition, rotation of ![](../graphics/stm_eqn03883.gif) about the beam axis, ![](../graphics/stm_eqn03884.gif), is interpolated linearly. This interpolation is unsatisfactory for the user, because the nodal variables are

![](../graphics/stm_eqn03885.gif)The last four of these variables are difficult to work with; furthermore, making them the same in all elements sharing the same node causes excessive constraint of axial stretch in these elements, especially if the beam axis is not continuous through the node, as in a frame structure or "T" junction.

To avoid this difficulty, the following procedure is adopted. At a node the tangent to the beam axis is

![](../graphics/stm_eqn03886.gif)so

![](../graphics/stm_eqn03887.gif) Now suppose we store as degrees of freedom at the node,

![](../graphics/stm_eqn03888.gif)where ![](../graphics/stm_eqn03889.gif) is the rotation definition introduced above. Since the initial geometry and hence ![](../graphics/stm_eqn00553.gif), the initial direction of the beam axis, is known, ![](../graphics/stm_eqn03890.gif) where ![](../graphics/stm_eqn00162.gif) is the rotation matrix defined by ![](../graphics/stm_eqn03889.gif), and hence

![](../graphics/stm_eqn03891.gif) is defined by these variables and the initial geometry. Furthermore, ![](../graphics/stm_eqn03884.gif) is directly available from ![](../graphics/stm_eqn03889.gif) and ![](../graphics/stm_eqn00479.gif). Thus, the above set is a satisfactory set of nodal variables. To eliminate the unwanted axial strain constraint, in Abaqus the stretch ![](../graphics/stm_eqn03892.gif) at the node of each such element is taken as an internal variable, local to the element (a third internal node is created for this purpose, and so it is not shared with neighboring elements.)

It should be remarked that the above transformation ([Equation 3.5.3&#8211;3](03s05a75.md)) is nonlinear. This leads to some complications---for example, the d'Alembert forces no longer have the simple form ![](../graphics/stm_eqn03893.gif) rather, a matrix ![](../graphics/stm_eqn03894.gif) replaces ![](../graphics/stm_eqn03895.gif) where ![](../graphics/stm_eqn03896.gif) and ![](../graphics/stm_eqn03897.gif) use the transformation ([Equation 3.5.3&#8211;3](03s05a75.md)) and its appropriate time derivatives. The resulting Jacobian is nonsymmetric; Abaqus ignores the nonsymmetric terms.
### Integration

The cross-section integration has already been discussed in the context of the shear beams---it is the same for these beams. Along the beam axis, the integration schemes are as described below.

**Stiffness and internal forces**

Three Gauss points are used. Two Gauss points are not sufficient because the torsional strain is not independent.

**Mass and distributed loads**

Three Gauss points are used. Rotary inertia is not included in the mass, except for rotation of the section about the beam axis, where it is included to avoid singularity in perfectly straight beams.
### Reference

### Reference

"Beam modeling: overview,"  Section 29.3.1 of the Abaqus Analysis User's Guide