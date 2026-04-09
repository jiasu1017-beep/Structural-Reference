# 3.4.1 Membrane elements

### 3.4.1 Membrane elements

**Products: **Abaqus/Standard  Abaqus/Explicit

Membrane elements are sheets in space that can carry membrane force but do not have any bending or transverse shear stiffness, so the only nonzero stress components in the membrane are those components parallel to the middle surface of the membrane: the membrane is in a state of plane stress.

At any time we use a local orthonormal basis system ![](../graphics/stm_eqn00022.gif), where ![](../graphics/stm_eqn00014.gif) and ![](../graphics/stm_eqn00015.gif) are in the surface of the membrane and ![](../graphics/stm_eqn00016.gif) is normal to the membrane. The basis system is defined by the standard convention used in Abaqus for a basis on a surface in space. In this section Greek indices take the range 1, 2, and Latin indices take the range 1, 2, 3. Greek indices are used to refer to components in the first two directions of the local orthonormal basis (in the surface of the membrane).
### Equilibrium

The virtual work contribution from the internal forces in a membrane element is

![](../graphics/stm_eqn03395.gif)where ![](../graphics/stm_eqn00033.gif) is the Cauchy stress, ![](../graphics/stm_eqn03396.gif) is the virtual rate of deformation (![](../graphics/stm_eqn03397.gif), where ![](../graphics/stm_eqn01597.gif) is the virtual velocity field), and *V* is the current volume of the membrane.

We assume that only the membrane stress components in the surface of the membrane are nonzero: ![](../graphics/stm_eqn03398.gif). Then [Equation 3.4.1&#8211;1](03s04a70.md) simplifies to

![](../graphics/stm_eqn03399.gif)where

![](../graphics/stm_eqn03400.gif)and ![](../graphics/stm_eqn03401.gif), where *t* is the current thickness of the element and *A* is its current area.
### Jacobian

The consistent Jacobian contribution from the element is

![](../graphics/stm_eqn03402.gif)Since we assume that ![](../graphics/stm_eqn03398.gif), the first term in the integrand is

![](../graphics/stm_eqn03403.gif)We also assume that there is no transverse shear strain of the element: ![](../graphics/stm_eqn03404.gif), and, hence, ![](../graphics/stm_eqn03405.gif). Thus, the second term in the integrand is

![](../graphics/stm_eqn03406.gif)We can write this out as

![](../graphics/stm_eqn03407.gif)
### Thickness change

In geometrically nonlinear analyses the cross-section thickness changes as a function of the membrane strain with a user-defined "effective section Poisson's ratio," ![](../graphics/stm_eqn01854.gif).

In plane stress ![](../graphics/stm_eqn03408.gif); linear elasticity gives

![](../graphics/stm_eqn03409.gif)Treating these as logarithmic strains,

![](../graphics/stm_eqn03410.gif)where *A* is the area on the membrane's reference surface. This nonlinear analogy with linear elasticity leads to the thickness change relationship:

![](../graphics/stm_eqn03411.gif)For ![](../graphics/stm_eqn03412.gif) the material is incompressible; for ![](../graphics/stm_eqn03413.gif) the section thickness does not change.
### Total deformation

The deformation gradient is ![](../graphics/stm_eqn03414.gif). Since we take ![](../graphics/stm_eqn00016.gif) normal to the current membrane surface and assume no transverse shear of the membrane,

![](../graphics/stm_eqn03415.gif)By the thickness change assumption above, the direct out-of-plane component of the deformation gradient is

![](../graphics/stm_eqn03416.gif)

To calculate the deformation gradient at the end of the increment, first we calculate the two tangent vectors at the end of the increment defined by the derivative of the position with respect to the reference coordinates:

![](../graphics/stm_eqn03417.gif)where ![](../graphics/stm_eqn03418.gif) is obtained by interpolation with the shape function derivatives from the nodal coordinates and the change of coordinate transformation ![](../graphics/stm_eqn03419.gif) is based on the reference geometry. The deformation gradient components are defined

![](../graphics/stm_eqn03420.gif)

To choose the element basis directions ![](../graphics/stm_eqn03421.gif), we do the following. Find any pair of in-plane orthonormal vectors ![](../graphics/stm_eqn03422.gif) (by the standard Abaqus projection). Then find the angle ![](../graphics/stm_eqn03423.gif) such that the element basis vectors ![](../graphics/stm_eqn03421.gif), defined

![](../graphics/stm_eqn03424.gif)satisfy the symmetry condition

![](../graphics/stm_eqn03425.gif)Using the definitions of ![](../graphics/stm_eqn03421.gif) in terms of ![](../graphics/stm_eqn03426.gif) in the above equation, the rotation angle ![](../graphics/stm_eqn03423.gif) is found to be

![](../graphics/stm_eqn03427.gif)where

![](../graphics/stm_eqn03428.gif)The deformation gradient then follows immediately.

For elastomers we work directly in terms of ![](../graphics/stm_eqn03429.gif) and ![](../graphics/stm_eqn03430.gif). For inelastic material models we need measures of incremental strain and average material rotation, which we compute from ![](../graphics/stm_eqn00434.gif) defined by ![](../graphics/stm_eqn03431.gif), where ![](../graphics/stm_eqn03432.gif) is the deformation gradient at the start of the current increment (at increment "*n*"):

![](../graphics/stm_eqn03433.gif)We can define the components of ![](../graphics/stm_eqn03434.gif) by

![](../graphics/stm_eqn03435.gif)and, hence, define ![](../graphics/stm_eqn03436.gif) by inversion.

The incremental strain and rotation are then defined from the polar decomposition ![](../graphics/stm_eqn03437.gif), where ![](../graphics/stm_eqn00433.gif) is a rotation matrix and ![](../graphics/stm_eqn00572.gif) is a pure stretch:

![](../graphics/stm_eqn03438.gif)(see "Deformation,"  Section 1.4.1). We find the ![](../graphics/stm_eqn00574.gif) and the corresponding eigenvectors ![](../graphics/stm_eqn03439.gif) by solving the eigenproblem for

![](../graphics/stm_eqn03440.gif)Since we assume no transverse shear in the membrane, the normal direction (along ![](../graphics/stm_eqn00016.gif)) is always a principal direction, so the eigenproblem is the ![](../graphics/stm_eqn03441.gif) problem

![](../graphics/stm_eqn03442.gif)The logarithmic strain increment is then

![](../graphics/stm_eqn03443.gif)and the average material rotation increment is defined from the polar decomposition of the increment:

![](../graphics/stm_eqn03444.gif)Due to the choice of the element basis directions, we can assume that

![](../graphics/stm_eqn03445.gif)
### Reference

### Reference

"Membrane elements,"  Section 29.1.1 of the Abaqus Analysis User's Guide