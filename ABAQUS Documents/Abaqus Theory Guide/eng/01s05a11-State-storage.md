# 1.5.4 State storage

### 1.5.4 State storage

**Products: **Abaqus/Standard  Abaqus/Explicit

Many of the constitutive models in Abaqus require tensors to be stored to define the state at a material calculation point. Such "material state tensors" are stored as their components in a local, orthonormal, system at the material calculation point. The orientation of that system with respect to the global ![](../graphics/stm_eqn00564.gif) spatial system is stored as a rotation from the global axis system. The purpose of this section is to define the manner in which such tensors are stored and updated.

Three types of local basis are used in Abaqus for material calculations. For isotropic materials in continuum elements the global, spatial, ![](../graphics/stm_eqn00564.gif) system is used---the material basis is fixed in time. For isotropic materials in structural surface elements (shells and membranes) the local system is defined by the standard Abaqus convention described in "Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide; and for beams and trusses it is defined with the 1-direction along the axis of the member and the 2- and 3-directions in material directions in the cross-section. Thus, with isotropic materials the material basis is always the same as the element basis, although for structural elements the material basis changes with time. For anisotropic materials the material basis must be defined by the user and rotates with the average rigid body spin of the material. In this case the material basis and the element basis are not the same.

We refer to this local material basis at time *t* as ![](../graphics/stm_eqn00565.gif), where the superscript ![](../graphics/stm_eqn00566.gif) indicates that the basis is associated with material calculations and ![](../graphics/stm_eqn00567.gif) means that the basis is taken at time *t*. In this section Latin subscripts (like the ![](../graphics/stm_eqn00568.gif) above) take the range 1&#8211;3, while Greek subscripts will take the range 1&#8211;2.

Any tensor associated with the material's state, ![](../graphics/stm_eqn00001.gif), say (such as the stress tensor ![](../graphics/stm_eqn00033.gif)), is stored in terms of its components along the material basis:

![](../graphics/stm_eqn00569.gif)

The increment from time *t* to time ![](../graphics/stm_eqn00438.gif) of local motion at the material calculation point is defined by the incremental deformation gradient,

![](../graphics/stm_eqn00570.gif)This matrix is calculated from the gradient interpolator of the finite element and the coordinates of the element's nodes at times *t* and ![](../graphics/stm_eqn00438.gif).

The polar decomposition of ![](../graphics/stm_eqn00434.gif) is

![](../graphics/stm_eqn00571.gif)where ![](../graphics/stm_eqn00433.gif) is the average rigid body rotation at the material point and ![](../graphics/stm_eqn00572.gif) is a pure stretch matrix:

![](../graphics/stm_eqn00573.gif)(here ![](../graphics/stm_eqn00574.gif) is a principal stretch ratio and ![](../graphics/stm_eqn00298.gif) is a principal stretch direction).

During an increment any material state tensor changes according to

![](../graphics/stm_eqn00575.gif)where ![](../graphics/stm_eqn00576.gif) is the change in ![](../graphics/stm_eqn00001.gif) caused by constitutive behavior and ![](../graphics/stm_eqn00433.gif) is the average incremental rigid body rotation of the material. Since material tensors are written in terms of their components in the material basis system, this update is computed as

![](../graphics/stm_eqn00577.gif)It is, therefore, necessary to project ![](../graphics/stm_eqn00433.gif) onto the material basis systems at the start and end of the increment to define the update of material tensor components:

![](../graphics/stm_eqn00578.gif)

For isotropic materials the ![](../graphics/stm_eqn00579.gif) have been chosen for geometric convenience only, so the ![](../graphics/stm_eqn00580.gif) are quite general.

For anisotropic materials the material basis system, ![](../graphics/stm_eqn00579.gif), rotates with the average rigid body rotation of the material, ![](../graphics/stm_eqn00581.gif), and so is updated by

![](../graphics/stm_eqn00582.gif)In this case we see that

![](../graphics/stm_eqn00583.gif)and so the update of a material tensor's components simplifies to

![](../graphics/stm_eqn00584.gif)However, since in this case the material basis system is not the same as the element basis system, ![](../graphics/stm_eqn00585.gif) (which is chosen for geometric convenience for element calculations), transformations must be done to change basis system. Specifically, at the start of the material calculation routines, the strain increments are rotated from the element basis into the material basis:

![](../graphics/stm_eqn00586.gif)Likewise, at the end of the material calculation routines, the stress increments are rotated back to the element basis for integration into the discretized approximation to the equilibrium equations:

![](../graphics/stm_eqn00587.gif)In addition, the material stiffness matrix,

![](../graphics/stm_eqn00588.gif)must also be rotated from the material basis to the element basis:

![](../graphics/stm_eqn00589.gif)For a shell or membrane only two-dimensional rotations are required---for example,

![](../graphics/stm_eqn00590.gif)since ![](../graphics/stm_eqn00591.gif) because both are unit vectors along the normal to the surface.
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide