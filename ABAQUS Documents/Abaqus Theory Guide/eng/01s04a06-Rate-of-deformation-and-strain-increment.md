# 1.4.3 Rate of deformation and strain increment

### 1.4.3 Rate of deformation and strain increment

**Products: **Abaqus/Standard  Abaqus/Explicit

Many of the materials we need to model are path dependent, so usually the constitutive relationships are defined in rate form, which requires a definition of strain rate. The velocity of a material particle is

![](../graphics/stm_eqn00413.gif)where the partial differentiation with respect to time (*t*) means the rate of change of the spatial position, ![](../graphics/stm_eqn00117.gif), of a fixed material particle. Here, again, we take the Lagrangian viewpoint: we observe a material particle and follow it through the motion, rather than looking at a fixed point in space and watching the material flowing through this point. The Lagrangian point of view is used for the mechanical modeling capabilities in Abaqus because we are usually dealing with history-dependent materials and the Lagrangian perspective makes it easy to record and update the state of a material point since the mesh is glued to the material.

The velocity difference between two neighboring particles in the current configuration is

![](../graphics/stm_eqn00414.gif)where

![](../graphics/stm_eqn00415.gif)is the velocity gradient in the current configuration.

In "Deformation,"  Section 1.4.1, we introduced the definition of the deformation gradient matrix, ![](../graphics/stm_eqn00319.gif):

![](../graphics/stm_eqn00416.gif)so

![](../graphics/stm_eqn00417.gif)

We could also obtain the velocity difference directly by

![](../graphics/stm_eqn00418.gif)where

![](../graphics/stm_eqn00419.gif)because ![](../graphics/stm_eqn00420.gif) is defined as the velocity difference between two neighboring material particles and, having chosen these particles, the gauge length between them in the reference configuration, ![](../graphics/stm_eqn00272.gif), is the same throughout the motion and, so, has no time derivative.

Comparing the two expressions for ![](../graphics/stm_eqn00420.gif) in terms of the reference configuration gauge length ![](../graphics/stm_eqn00272.gif), we see that

![](../graphics/stm_eqn00421.gif)or

![](../graphics/stm_eqn00422.gif)

Now ![](../graphics/stm_eqn00423.gif) will be composed of a rate of deformation and a rate of rotation or spin. Since these are rate quantities, the spin can be treated as a vector; thus, we can decompose ![](../graphics/stm_eqn00423.gif) into a symmetric strain rate matrix and an antisymmetric rotation rate matrix, just as in small motion theory we decompose the infinitesimal displacement gradient into an infinitesimal strain and an infinitesimal rotation. The symmetric part of the decomposition is the strain rate (it is called the rate of deformation tensor in many textbooks and is also commonly denoted as ![](../graphics/stm_eqn00424.gif)) and is

![](../graphics/stm_eqn00425.gif)The antisymmetric part of the decomposition is the spin matrix,

![](../graphics/stm_eqn00426.gif)

These are particularly simple and familiar forms; for example, ![](../graphics/stm_eqn00118.gif) is identical to the elementary definition of "small strain" if we replace the particle velocity, ![](../graphics/stm_eqn00427.gif), with the displacement, ![](../graphics/stm_eqn00428.gif). In one dimension ![](../graphics/stm_eqn00118.gif) is

![](../graphics/stm_eqn00429.gif)which identifies ![](../graphics/stm_eqn00430.gif) as the rate of logarithmic strain,

![](../graphics/stm_eqn00431.gif)

This interpretation would also be correct if the principal directions of strain rotate along with the rigid body motion (because the identification can be applied to each principal value of the logarithmic strain matrix). In the general case, when the principal strain directions rotate independent of the material, ![](../graphics/stm_eqn00118.gif) is not integrable into a total strain measure. Nevertheless, the identification of ![](../graphics/stm_eqn00118.gif) with the rate of logarithmic strain in the particular case of nonrotating principal directions provides a useful interpretation of the logarithmic measure of strain as a "natural" strain if we think of ![](../graphics/stm_eqn00118.gif), as it is defined above as the symmetric part of the velocity gradient with respect to current spatial position, as a "natural" measure of strain rate.

The typical inelastic constitutive model requires as input a small but finite strain increment ![](../graphics/stm_eqn00432.gif), as well as vector and tensor valued state variables (such as the stress) that are written on the current configuration. In Abaqus/Explicit and for shell and membrane elements in Abaqus/Standard, a slightly different algorithm is used to calculate ![](../graphics/stm_eqn00433.gif). For most element types in Abaqus/Standard we approach this problem by first using the polar decomposition in the increment to define the change in the average material rotation over the increment, ![](../graphics/stm_eqn00433.gif), from the total deformation in the increment, ![](../graphics/stm_eqn00434.gif):

![](../graphics/stm_eqn00435.gif)All vectors and tensors associated with the material (whose values are available at the beginning of the increment from previous calculations) can now be rotated to the configuration at the end of the increment, solely to account for the rigid body rotation in the increment:

![](../graphics/stm_eqn00436.gif)for a vector, and

![](../graphics/stm_eqn00437.gif)for a tensor.

These rotated variables are now passed to the constitutive routines, which may provide further updates to them because of constitutive effects. These constitutive effects will be associated with deformation, which must be supplied in the form of the strain increment ![](../graphics/stm_eqn00432.gif). For this we proceed as follows.

Since we assume ![](../graphics/stm_eqn00433.gif) rotates the deformation basis---in the sense that it rotates the principal axes of deformation and, thus, provides a measure of average material rotation---we can define the velocity gradient ![](../graphics/stm_eqn00423.gif) at any time during the increment, referred to the fixed basis at ![](../graphics/stm_eqn00438.gif), as

![](../graphics/stm_eqn00439.gif)Then our integration of ![](../graphics/stm_eqn00118.gif) is the matrix ![](../graphics/stm_eqn00432.gif), on the basis at the end of the increment, and defined by

![](../graphics/stm_eqn00440.gif)Using [Equation 1.4.3&#8211;2](01s04a06-Rate-of-deformation-and-strain-increment.md), this is

![](../graphics/stm_eqn00441.gif)Since

![](../graphics/stm_eqn00442.gif)we can make use of the polar decomposition of the increment of deformation into a stretch on the axes at the start of the increment followed by rotation (![](../graphics/stm_eqn00443.gif)) to write

![](../graphics/stm_eqn00444.gif) so that the integrand in the definition of the increment of strain is

![](../graphics/stm_eqn00445.gif)

We now assume that the incremental stretch at any time in the increment written on the basis at the beginning of the increment, ![](../graphics/stm_eqn00446.gif), always has the same principal directions ![](../graphics/stm_eqn00295.gif), ![](../graphics/stm_eqn00296.gif), ![](../graphics/stm_eqn00297.gif), so that

![](../graphics/stm_eqn00447.gif)and, hence,

![](../graphics/stm_eqn00448.gif)and

![](../graphics/stm_eqn00449.gif)We can, thus, write

![](../graphics/stm_eqn00450.gif)and, hence,

![](../graphics/stm_eqn00451.gif)so that, finally, from [Equation 1.4.3&#8211;3](01s04a06-Rate-of-deformation-and-strain-increment.md),

![](../graphics/stm_eqn00452.gif)Thus, as long as we assume that the stretch at any time during the increment has the same principal directions as the total increment of stretch (on the fixed basis at the start of the increment), the logarithmic definition of incremental strain provides the required integral of the strain rate expressed as the rate of deformation. This assumption amounts to requiring that the components of stretch grow proportionally during the increment: that ![](../graphics/stm_eqn00453.gif), where *p* is any scalar that we take to grow monotonically from 0 to 1 during ![](../graphics/stm_eqn00454.gif). This assumption might be questionable if the increments are very large, but it is consistent with the levels of approximation used in the integration of the inelastic constitutive models. We, therefore, have a simple method for calculating the strain increment for use in this type of constitutive model without any additional loss of accuracy compared to what we already accept in the constitutive integration itself.
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide