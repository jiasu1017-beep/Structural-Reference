# 3.2.5 Continuum elements with incompatible modes

### 3.2.5 Continuum elements with incompatible modes

**Products: **Abaqus/Standard  Abaqus/Explicit

The lower-order quadrilateral continuum elements in Abaqus of type CPS4I, CPE4I, CAX4I, CPEG4I, and C3D8I, as well as the related hybrid elements, are enhanced by incompatible modes to improve the bending behavior. In addition to the displacement degrees of freedom, incompatible deformation modes are added internal to the elements. The primary effect of these degrees of freedom is to eliminate the so-called parasitic shear stresses that are observed in regular displacement elements if they are loaded in bending.

In addition, these degrees of freedom eliminate artificial stiffening due to Poisson's effect in bending. In regular displacement elements the linear variation of the axial stress due to bending is accompanied by a linear variation of the stress perpendicular to the bending direction, which leads to incorrect stresses and an overestimation of the stiffness. The incompatible modes prevent such a stress from occurring.

In the nonhybrid elements (except CPS4I) additional incompatible modes are added to prevent locking of the elements for approximately incompressible material behavior. For fully incompressible material behavior, hybrid elements must be used. In these elements pressure degrees of freedom are added to enforce a linear pressure variation inside the element. In the hybrid elements the additional incompatible modes used to prevent locking are not included.

The incompatible mode elements perform almost as well as second-order elements in many situations if the elements have an approximately rectangular shape. The performance is considerably less if the elements have a parallelogram shape. For trapezoidal element shapes the performance is not much better than the performance of regular displacement elements.

Because of the internal degrees of freedom (4 for CPS4I; 5 for CPE4I, CAX4I, and CPEG4I; and 13 for C3D8I) the elements are somewhat more expensive than regular displacement elements. However, the additional degrees of freedom do not substantially increase the wavefront size since they can be eliminated immediately. In addition, it is not necessary to use selectively reduced integration, which partially offsets the cost of the additional degrees of freedom.

The geometrically linear incompatible mode formulation used in Abaqus is related to the work presented by [Simo and Rifai (1990)](07s01a01-References.md). Simo's formulation is very similar to much earlier work done by [Wilson et al. (1973)](07s01a01-References.md) and [Taylor et al. (1976)](07s01a01-References.md). The nonlinear formulation is based on work by [Simo and Armero (1992)](07s01a01-References.md).
### Geometrically linear formulation

As discussed in the paper by Simo, the incompatible mode formulation can be derived in a rigorous way from the general Hu-Washizu variational principle. In this discussion we will not present this derivation but use only the key results of Simo's work.

In the incompatible mode formulation, the displacement gradient ![](../graphics/stm_eqn02963.gif) is augmented with an additional, incompatible displacement gradient field ![](../graphics/stm_eqn02964.gif):

![](../graphics/stm_eqn02965.gif)The incompatible displacement gradient ![](../graphics/stm_eqn02964.gif) is chosen internal to an element. The field cannot be selected arbitrarily. It must be independent of the regular displacement gradient.

![](../graphics/stm_eqn02966.gif)which can also be expressed in the form

![](../graphics/stm_eqn02967.gif)In addition, it must be orthogonal to any constant gradient field, which yields the condition

![](../graphics/stm_eqn02968.gif)If these conditions are violated, the element does not pass the patch test.

The last condition is used to obtain a suitable general form of the incompatible modes. We describe the incompatible field as a transformation of a parametric gradient field ![](../graphics/stm_eqn02969.gif):

![](../graphics/stm_eqn02970.gif)where ![](../graphics/stm_eqn00479.gif) is the parametric transformation at the center of the element

![](../graphics/stm_eqn02971.gif)![](../graphics/stm_eqn02972.gif) is the Jacobian of the parametric transformation at the location ![](../graphics/stm_eqn02973.gif), and ![](../graphics/stm_eqn02974.gif) is the Jacobian at the center of the element. For planar elements the Jacobian can be written as

![](../graphics/stm_eqn02975.gif)where *h* is the thickness; for axisymmetric elements it is

![](../graphics/stm_eqn02976.gif)where *r* is the radius; and for three-dimensional elements it is

![](../graphics/stm_eqn02977.gif)Substitution of [Equation 3.2.5&#8211;2](03s02a63-Continuum-elements-with-incompatible-mod.md) in [Equation 3.2.5&#8211;1](03s02a63-Continuum-elements-with-incompatible-mod.md) allows us to create a simple condition for ![](../graphics/stm_eqn02969.gif):

![](../graphics/stm_eqn02978.gif)

For two-dimensional elements this yields

![](../graphics/stm_eqn02979.gif)and for three-dimensional elements,

![](../graphics/stm_eqn02980.gif)This makes it possible to write ![](../graphics/stm_eqn02981.gif) as a simple polynomial in ![](../graphics/stm_eqn02973.gif). The principal contribution to ![](../graphics/stm_eqn02981.gif) can be written in the form

![](../graphics/stm_eqn02982.gif)where ![](../graphics/stm_eqn02983.gif) are vectorial degrees of freedom and ![](../graphics/stm_eqn02984.gif) are vectors and the summation *i* extends over the parametric coordinates. In two-dimensional elements ![](../graphics/stm_eqn02985.gif) and ![](../graphics/stm_eqn02986.gif) are vectors of the form

![](../graphics/stm_eqn02987.gif)and in three-dimensional elements

![](../graphics/stm_eqn02988.gif)The principal contribution to the incompatible displacement gradient hence becomes

![](../graphics/stm_eqn02989.gif)

With the addition of these terms, parasitic shear and Poisson's effect in bending are eliminated. Note that the vectors ![](../graphics/stm_eqn02983.gif) in ![](../graphics/stm_eqn02964.gif) appear in a similar form as the nodal displacement vectors ![](../graphics/stm_eqn02990.gif) in ![](../graphics/stm_eqn02991.gif),

![](../graphics/stm_eqn02992.gif)and can be treated similar to displacement degrees of freedom.

For approximately incompressible material behavior, bilinear patterns in the hydrostatic stress can still be observed in all elements except CPS4I. These patterns can be eliminated by the introduction of additional incompatible modes of the form

![](../graphics/stm_eqn02993.gif)where ![](../graphics/stm_eqn02994.gif) are additional scalar degrees of freedom. For two-dimensional elements a single term ![](../graphics/stm_eqn02995.gif) is added with

![](../graphics/stm_eqn02996.gif)In the three-dimensional elements four additional terms ![](../graphics/stm_eqn02994.gif) are added with

![](../graphics/stm_eqn02997.gif)Thus, the incompatible displacement gradient ![](../graphics/stm_eqn02964.gif) takes the final form

![](../graphics/stm_eqn02998.gif)

The symmetric part of the incompatible displacement gradient contributes to incompatible strains:

![](../graphics/stm_eqn02999.gif)The skew-symmetric part plays no role in the geometrically linear formulation.
### Geometrically nonlinear formulation

Since we want to use a formulation that can be used for any material model, we want to express the incompatible modes as a modification of the deformation gradient ![](../graphics/stm_eqn00319.gif). The most obvious approach is to add the incompatible modes to the deformation gradient:

![](../graphics/stm_eqn03000.gif)This approach has been used successfully by Simo and Armero. Elements formulated on this basis satisfy the large-strain patch test; i.e., any patch of elements will be able to represent homogeneous deformations exactly. However, once the elements become distorted due to deformation, the patch test will no longer be satisfied in an incremental sense; that is, subsequent homogeneous deformations will not be represented exactly. This turns out to be a fatal flaw in the formulation for problems involving large distortions in compression.

Satisfaction of the instantaneous patch test requires the addition of an incompatible deformation rate tensor to the standard rate of deformation:

![](../graphics/stm_eqn03001.gif)To obtain an approximate relation of this type, we write the total deformation gradient as the product of a series of incremental deformation gradients:

![](../graphics/stm_eqn03002.gif)Principal incompatible modes are then added to the incremental deformation gradient:

![](../graphics/stm_eqn03003.gif)

Similar to [Equation 3.2.5&#8211;2](03s02a63-Continuum-elements-with-incompatible-mod.md) the principal incompatible modes are described as a transformation of the parametric gradient field ![](../graphics/stm_eqn03004.gif):

![](../graphics/stm_eqn03005.gif)where ![](../graphics/stm_eqn03006.gif) is the parametric transformation at the center of the element in the state at the start of the increment,

![](../graphics/stm_eqn03007.gif)![](../graphics/stm_eqn02972.gif) is the Jacobian of the parametric transformation at the location ![](../graphics/stm_eqn02973.gif); and ![](../graphics/stm_eqn02974.gif) is the Jacobian at the centroid at the start of the increment. Note that ![](../graphics/stm_eqn02972.gif) is evaluated based on the deformation caused by the displacement degrees of freedom only and does not include the volume change due to the incompatible modes.

The incremental parametric gradient field ![](../graphics/stm_eqn03004.gif) has exactly the same form as in the linear formulation,

![](../graphics/stm_eqn03008.gif)which yields the principal incremental incompatible deformation gradient

![](../graphics/stm_eqn03009.gif)Bilinear volumetric terms are added to the principal terms in a multiplicative way:

![](../graphics/stm_eqn03010.gif)

The variation in the gradient of the position with respect to the current state is obtained from the fundamental relation

![](../graphics/stm_eqn03011.gif)with

![](../graphics/stm_eqn03012.gif)

This allows us to write for ![](../graphics/stm_eqn03013.gif)

![](../graphics/stm_eqn03014.gif)The integral of the principal incompatible modes over the element volume at the start of the increment is, hence, equal to

![](../graphics/stm_eqn03015.gif)Note that the integral will vanish if the incremental deformation is *homogeneous*; that is, ![](../graphics/stm_eqn03016.gif), since in that case the integral can be written as

![](../graphics/stm_eqn03017.gif)Hence, the *incremental* patch test will be satisfied. The rate of the gradient of the position with respect to the current state is obtained similar to the variation

![](../graphics/stm_eqn03018.gif)with

![](../graphics/stm_eqn03019.gif)

For a finite-strain increment we use the midincrement approach proposed by Hughes and Winget. This yields

![](../graphics/stm_eqn03020.gif)The second variation is obtained in the usual way. Since the regular deformation gradient and the principal incompatible modes are purely displacement based, the initial stress stiffness terms are readily obtained as

![](../graphics/stm_eqn03021.gif)where ![](../graphics/stm_eqn03022.gif) is the gradient of the velocity and ![](../graphics/stm_eqn03023.gif) is the gradient of the displacement variation including the primary incompatible modes. Further, ![](../graphics/stm_eqn03024.gif) is the rate of deformation, and ![](../graphics/stm_eqn03025.gif) is the variation in the deformation.

The additional bilinear modes appear in the first variation only as variations (the values ![](../graphics/stm_eqn03026.gif) themselves do not appear); hence, the contributions to the second variation can be neglected.
### Reference

### Reference

"Solid (continuum) elements,"  Section 28.1.1 of the Abaqus Analysis User's Guide