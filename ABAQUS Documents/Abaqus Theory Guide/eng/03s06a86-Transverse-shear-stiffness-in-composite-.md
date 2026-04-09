# 3.6.8 Transverse shear stiffness in composite shells and offsets from the midsurface

### 3.6.8 Transverse shear stiffness in composite shells and offsets from the midsurface

**Products: **Abaqus/Standard  Abaqus/Explicit
### Transverse shear stiffness

Abaqus supports element types S3R, S3RS, S4, S4R, S4RS, S4RSW, SC6R, SC8R, and S8R for the analysis of laminated composite shells. These elements are based on first-order transverse shear flexible theory in which the transverse shear strain is assumed to be constant through the thickness of the shell. This assumption necessitates the use of shear correction factors. The development of these factors also provides a basis for estimating interlaminar shear stresses in a composite section. This section describes the development of the transverse shear stiffness for element types S3R, S4, S4R, SC6R, SC8R, and S8R.Finite-strain shells

The transverse shear stiffness correction factors are easily shown to be ![](../graphics/stm_eqn04871.gif) for isotropic plates. We want to establish the equivalent factors for laminated plates and sandwich constructions. For this purpose we calculate the distribution of transverse shear stress through the thickness of the shell, for the case of unidirectional bending and assuming linear elastic response. Then the shear strain energy, expressed in terms of section forces and strains, is equated to the strain energy of this distribution of transverse shear stresses.

This method, outlined below, provides an approximate method for calculating interlaminar shear stresses and supplies reasonable estimates of transverse shear stiffness. In this calculation Abaqus assumes that the shell section directions are the principal bending directions (bending about one principal direction does not require a restraining moment about the other direction). For composite shells with orthotropic layers that are not symmetric about the shell midsurface, the shell section directions may not be the principal bending directions. In such cases the transverse shear stiffness and interlaminar shear stresses are less accurate approximations and will change if different shell section directions are used.

Consider a plate in the ![](../graphics/stm_eqn03043.gif) plane. Assume only bending and shear in the *x*-direction, without gradients in the *y*-direction. Then the membrane forces in the shell are zero: ![](../graphics/stm_eqn04872.gif), and ![](../graphics/stm_eqn04873.gif) for all response variables. In this case equilibrium within the section in the *x*-direction is

![](../graphics/stm_eqn04874.gif)

Moment equilibrium about the *y*-axis gives

![](../graphics/stm_eqn04875.gif)where ![](../graphics/stm_eqn04876.gif) is the transverse shear force per unit width in the plate and ![](../graphics/stm_eqn04877.gif) is the bending moment per unit width for bending about the *y*-axis.

For the bending behavior we assume the strain varies linearly across the section:

![](../graphics/stm_eqn04878.gif)where ![](../graphics/stm_eqn04879.gif) is the membrane strain of the reference surface ![](../graphics/stm_eqn04880.gif) and ![](../graphics/stm_eqn04881.gif) is the curvature of that surface.

If the response of the shell is linear elastic, any in-plane component of stress at a point through the shell section is given by

![](../graphics/stm_eqn04882.gif) where the plane stress elastic stiffness, ![](../graphics/stm_eqn04883.gif), is defined from the elasticity and orientation of the material at the particular layer of the shell. Greek subscripts take the range ![](../graphics/stm_eqn04884.gif).

Integrating through the thickness and inverting the resultant section stiffness provides the 6  6 section flexibility matrix, ![](../graphics/stm_eqn01154.gif):

![](../graphics/stm_eqn04885.gif)

We have already assumed that ![](../graphics/stm_eqn04886.gif). We now also assume that ![](../graphics/stm_eqn04887.gif); that is, that it is possible to have no bending in the *y*-direction without any restraining moments associated with the *y*-direction. This is clearly not the case for an unbalanced composite section, but we still use it as a simplifying assumption to obtain the shear correction factors. Thus,

![](../graphics/stm_eqn04888.gif)where ![](../graphics/stm_eqn04889.gif) is the fourth column of ![](../graphics/stm_eqn01154.gif). Combining this result with the elastic stiffness at a point through the shell thickness provides the in-plane stress components in terms of ![](../graphics/stm_eqn04877.gif) as

![](../graphics/stm_eqn04890.gif)where

![](../graphics/stm_eqn04891.gif) and

![](../graphics/stm_eqn04892.gif)

Combining the gradient of this equation in the *x*-direction with the equilibrium equations [Equation 3.6.8&#8211;1](03s06a86-Transverse-shear-stiffness-in-composite-.md) and [Equation 3.6.8&#8211;2](03s06a86-Transverse-shear-stiffness-in-composite-.md) yields a description of the variation of the transverse shear stress through the thickness of the plate:

![](../graphics/stm_eqn04893.gif)In calculating ![](../graphics/stm_eqn04894.gif) we have assumed that the elasticity and thickness of the composite section do not vary (or vary slowly) with position along the shell.

A laminated composite shell section consists of *N* layers ![](../graphics/stm_eqn04895.gif) with different values of (![](../graphics/stm_eqn04896.gif),![](../graphics/stm_eqn04897.gif)) at layer 1, (![](../graphics/stm_eqn04898.gif),![](../graphics/stm_eqn04899.gif)) at layer 2, ![](../graphics/stm_eqn04900.gif) (![](../graphics/stm_eqn04901.gif),![](../graphics/stm_eqn04902.gif)) at layer *N*. Layer *i* extends from ![](../graphics/stm_eqn04903.gif) to ![](../graphics/stm_eqn04904.gif) and its thickness is ![](../graphics/stm_eqn04905.gif). Integrating [Equation 3.6.8&#8211;6](03s06a86-Transverse-shear-stiffness-in-composite-.md) through the shell, using the boundary conditions ![](../graphics/stm_eqn04906.gif) at ![](../graphics/stm_eqn04907.gif), ![](../graphics/stm_eqn04908.gif) at ![](../graphics/stm_eqn04909.gif) and ![](../graphics/stm_eqn04906.gif) at ![](../graphics/stm_eqn04910.gif), gives the transverse shear stress in layer *i* as

![](../graphics/stm_eqn04911.gif) where

![](../graphics/stm_eqn04912.gif) and

![](../graphics/stm_eqn04913.gif)

The subscript ![](../graphics/stm_eqn04914.gif) is used instead of ![](../graphics/stm_eqn01197.gif) in this case because the result is associated with pure bending in the *x*-direction.

The variation of ![](../graphics/stm_eqn04915.gif) through the shell thickness is obtained using a similar procedure, based on pure bending in the *y*-direction.

These results provide the estimates of interlaminar shear stresses.

We define the shear flexibility of the section by matching the shear strain energy obtained by integrating the elastic strain energy density associated with transverse shear stress distribution obtained above:

![](../graphics/stm_eqn04916.gif)where ![](../graphics/stm_eqn04917.gif) is the shear flexibility of the section and ![](../graphics/stm_eqn04918.gif) is the continuum transverse shear flexibility within layer *i*. Here we introduce the assumption that the transverse shear flexibility within a layer is not coupled to the in-plane flexibility. This is usually the case for shell constructions.

Substituting the relations for ![](../graphics/stm_eqn04919.gif) and ![](../graphics/stm_eqn04920.gif) into the above equation and integrating defines the shear flexibility of the section as

![](../graphics/stm_eqn04921.gif)

![](../graphics/stm_eqn04922.gif)

![](../graphics/stm_eqn04923.gif)

The transverse shear stiffness of the section is then available as ![](../graphics/stm_eqn04924.gif). Notice that ![](../graphics/stm_eqn04925.gif) will be nonzero if any layer is anisotropic or orthotropic in a local system (since then ![](../graphics/stm_eqn04926.gif) will be nonzero).Small-strain shells

When the shell resultant forces at each increment are computed for pre-integrated sections, the transverse shear forces for small-strain shell elements S3RS, S4RS, and S4RSW are computed using the transverse shear stiffness derived for finite-strain shells. For numerically integrated sections the transverse shear behavior is based on a simplified stiffness for improved computational performance. For single or multilayer isotropic sections and single layer orthotropic sections, the transverse shear force converges to the proper thin and thick shell transverse shear solution and the transverse shear stress is assumed to have a constant distribution. The transverse shear stiffness is approximate for multilayer orthotropic sections, where the transverse shear stress distribution is assumed piecewise constant. Convergence to the proper transverse shear behavior for this case may not be obtained as shells become thick and principal material directions deviate from the principal section directions.
### Offset: reference surface versus midsurface

In Abaqus the geometry of the shell is defined by kinematic variables that exist at the nodes on the shell reference surface. The kinematics of the shell theory consist of measuring membrane strain on the reference surface and bending strain from the derivatives of the unit normal vector on the reference surface. The default reference surface is the shell midsurface. However, many situations arise in which it is more convenient to define the reference surface as offset from the midsurface. In this case we assume that the in-plane strain at any material point varies linearly across the section:

![](../graphics/stm_eqn04878.gif)where ![](../graphics/stm_eqn04927.gif) and ![](../graphics/stm_eqn04928.gif) represent the two orthogonal axes on the reference surface, ![](../graphics/stm_eqn04879.gif) is the membrane strain of the reference surface, ![](../graphics/stm_eqn04929.gif) is the distance to the reference surface measured from the midsurface, and ![](../graphics/stm_eqn04881.gif) is the curvature of that surface. The positive values of ![](../graphics/stm_eqn04929.gif) are in the positive normal direction. When ![](../graphics/stm_eqn04930.gif), the top surface of the shell is the reference surface, where *t* is the shell thickness. The bottom surface of the shell becomes the reference surface when ![](../graphics/stm_eqn04931.gif). When ![](../graphics/stm_eqn04932.gif), the midsurface represents the reference surface.

If the response of the shell is linear elastic, any in-plane component of stress at a point through the shell section, ![](../graphics/stm_eqn04933.gif), is given by

![](../graphics/stm_eqn04934.gif)where the plane stress elastic stiffness, ![](../graphics/stm_eqn04883.gif), is defined from the elasticity and orientation of the material at the particular layer of the shell. Greek subscripts take the range ![](../graphics/stm_eqn04884.gif).

The section force and moment resultants per unit length can then be defined as

![](../graphics/stm_eqn04935.gif)Integrating the above equations through the thickness leads to the resultant section stiffness, ![](../graphics/stm_eqn00147.gif):

![](../graphics/stm_eqn04936.gif)
### Reference

### Reference

"Shell section behavior,"  Section 29.6.4 of the Abaqus Analysis User's Guide