# 4.6.3 Anisotropic hyperelastic material behavior

### 4.6.3 Anisotropic hyperelastic material behavior

**Products: **Abaqus/Standard  Abaqus/Explicit

The constitutive behavior of hyperelastic materials is discussed in "Hyperelastic material behavior,"  Section 4.6.1, in the context of isotropic response. However, many materials of industrial and technological interest exhibit anisotropic elastic behavior due to the presence of preferred directions in their microstructure. Examples of such materials include common engineering materials (such as fiber-reinforced composites, reinforced rubber, and wood) as well as soft biological tissues (such as those found in arterial walls and heart tissues). Under large deformations these materials exhibit highly anisotropic and nonlinear elastic behavior due to rearrangements in their microstructure, such as reorientation of the fiber directions with deformation. The simulation of these nonlinear effects requires constitutive models formulated within the framework of anisotropic hyperelasticity.

Hyperelastic materials are described in terms of a "strain energy potential," which defines the strain energy stored in the material per unit of reference volume (volume in the initial configuration) as a function of the deformation at that point in the material. Two distinct formulations are used for the representation of the strain energy potential of anisotropic hyperelastic materials: strain-based and invariant-based.
### Strain-based formulation

In this case the strain energy function is expressed directly in terms of the components of a suitable strain tensor, such as the Green strain tensor (see "Strain measures,"  Section 1.4.2):

![](../graphics/stm_eqn06978.gif)where ![](../graphics/stm_eqn06979.gif) is Green's strain, ![](../graphics/stm_eqn06980.gif) is the right Cauchy-Green strain tensor, ![](../graphics/stm_eqn00319.gif) is the deformation gradient, and ![](../graphics/stm_eqn00064.gif) is the identity matrix. Without loss of generality, the strain energy function can be written in the form

![](../graphics/stm_eqn06981.gif)where ![](../graphics/stm_eqn06982.gif) is the modified Green strain tensor, ![](../graphics/stm_eqn06983.gif) is the distortional part of the right Cauchy-Green strain, and ![](../graphics/stm_eqn06984.gif) is the volume change.

The underlying assumption in models based on the strain-based formulation is that the preferred materials directions are initially aligned with an orthogonal coordinate system  in the reference (stress-free) configuration. These directions may become nonorthogonal only after deformation. Examples of this form of strain energy function include the generalized Fung-type form (see ["Generalized Fung form](04s06a125.md)," below).

From [Equation 4.6.3&#8211;1](04s06a125.md) the variation of ![](../graphics/stm_eqn06985.gif) is given as

![](../graphics/stm_eqn06986.gif)Using the principle of virtual work, the variation of the strain energy potential can be written as

![](../graphics/stm_eqn06987.gif)(see [Equation 4.6.1&#8211;7](04s06a123.md)).

For a compressible material the strain variations are arbitrary, so this equation defines the stress components for such a material as

![](../graphics/stm_eqn06988.gif)and

![](../graphics/stm_eqn06989.gif)

When the material response is almost incompressible, the pure displacement formulation, in which the strain invariants are computed from the kinematic variables of the finite element model, can behave poorly. One difficulty is that from a numerical point of view the stiffness matrix is almost singular because the effective bulk modulus of the material is so large compared to its effective shear modulus, thus causing difficulties with the solution of the discretized equilibrium equations. Similarly, in Abaqus/Explicit the high bulk modulus increases the dilatational wave speed, thus reducing the stable time increment substantially. To avoid such problems, Abaqus/Standard offers a "mixed" formulation for such cases (refer to "Hyperelastic material behavior,"  Section 4.6.1).
### Invariant-based formulation

Using the continuum theory of fiber-reinforced composites (Spencer, [1984](07s01a01-References.md)), the strain energy function can be expressed directly in terms of the invariants of the deformation tensor and fiber directions. For example, consider a composite material that consists of an isotropic hyperelastic matrix reinforced with ![](../graphics/stm_eqn06990.gif) families of fibers. The directions of the fibers in the reference configuration are characterized by a set of unit vectors ![](../graphics/stm_eqn06991.gif), (![](../graphics/stm_eqn06992.gif)). Assuming that the strain energy depends not only on deformation, but also on the fiber directions, the following form is postulated:

![](../graphics/stm_eqn06993.gif)The strain energy of the material must remain unchanged if both matrix and fibers in the reference configuration undergo a rigid body rotation. Then, following Spencer ([1984](07s01a01-References.md)), the strain energy can be expressed as an isotropic function of an irreducible set of scalar invariants that form the integrity basis of the tensor ![](../graphics/stm_eqn00162.gif) and the vectors ![](../graphics/stm_eqn06991.gif):

![](../graphics/stm_eqn06994.gif) where ![](../graphics/stm_eqn06995.gif) and ![](../graphics/stm_eqn06996.gif) are the first and second deviatoric strain invariants; ![](../graphics/stm_eqn02113.gif) is the volume ratio (or third strain invariant); and ![](../graphics/stm_eqn06997.gif) and ![](../graphics/stm_eqn06998.gif) are the *pseudo-invariants* of ![](../graphics/stm_eqn06999.gif), ![](../graphics/stm_eqn06991.gif), and ![](../graphics/stm_eqn07000.gif), defined as

![](../graphics/stm_eqn07001.gif)The terms ![](../graphics/stm_eqn07002.gif) are geometrical constants (independent of deformation) equal to the cosine of the angle between the directions of any two families of fibers in the reference configuration,

![](../graphics/stm_eqn07003.gif)

Unlike in the case of the strain-based formulation, in the invariant-based formulation the fiber directions need not be orthogonal in the initial configuration. An example of the invariant-based energy function is the form proposed by [Holzapfel, Gasser, and Ogden (2000)](07s01a01-References.md) for arterial walls (see ["Holzapfel-Gasser-Ogden form](04s06a125.md)," below).

From [Equation 4.6.3&#8211;4](04s06a125.md) the variation of ![](../graphics/stm_eqn06985.gif) is given as

![](../graphics/stm_eqn07004.gif)

Using the principle of virtual work ([Equation 4.6.3&#8211;3](04s06a125.md)) and after some lengthy derivations, the stress components for a compressible material are found to be given as

![](../graphics/stm_eqn07005.gif)and

![](../graphics/stm_eqn07006.gif)where ![](../graphics/stm_eqn07007.gif) and ![](../graphics/stm_eqn07008.gif).
### Particular forms of the strain energy potential

Several particular forms of the strain energy potential are available in Abaqus. The incompressible or almost incompressible models make up:

the generalized Fung form and

the Holzapfel-Gasser-Ogden form.In addition, Abaqus provides a general capability to support user-defined forms of the strain energy potential via two sets of user subroutines: one for strain-based and one for invariant-based formulations.Generalized Fung form

The generalized Fung strain energy potential in Abaqus is based on the two-dimensional exponential form proposed by [Fung et al. (1979)](07s01a01-References.md), suitably generalized to arbitrary three-dimensional states following [Humphrey (1995)](07s01a01-References.md). It has the following form:

![](../graphics/stm_eqn07009.gif)where *U* is the strain energy per unit of reference volume, *c* and *D* are temperature-dependent material parameters, ![](../graphics/stm_eqn07010.gif) is the elastic volume ratio, and ![](../graphics/stm_eqn07011.gif) is defined as

![](../graphics/stm_eqn07012.gif)where ![](../graphics/stm_eqn07013.gif) is a dimensionless symmetric fourth-order tensor of anisotropic material constants that can be temperature dependent and ![](../graphics/stm_eqn07014.gif) are the components of the modified Green strain tensor.

The elastic volume ratio, ![](../graphics/stm_eqn07010.gif), relates the total volume ratio, *J*, and the thermal volume ratio, ![](../graphics/stm_eqn07015.gif):

![](../graphics/stm_eqn07016.gif)![](../graphics/stm_eqn07015.gif) is given by

![](../graphics/stm_eqn07017.gif)where ![](../graphics/stm_eqn07018.gif) are the principal thermal expansion strains that are obtained from the temperature and the thermal expansion coefficients.

The initial deviatoric elasticity tensor, ![](../graphics/stm_eqn07019.gif), and bulk modulus, ![](../graphics/stm_eqn07020.gif), are given by

![](../graphics/stm_eqn07021.gif)

Abaqus supports two forms of the generalized Fung model: anisotropic and orthotropic. The number of independent components ![](../graphics/stm_eqn07013.gif) that must be specified depends on the level of anisotropy of the material: 21 for the fully anisotropic case and 9 for the orthotropic case.