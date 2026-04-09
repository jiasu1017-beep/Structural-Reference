# 4.6.1 Hyperelastic material behavior

### 4.6.1 Hyperelastic material behavior

**Products: **Abaqus/Standard  Abaqus/Explicit

The constitutive behavior of a hyperelastic material is defined as a total stress&#8211;total strain relationship, rather than as the rate formulation that has been discussed in the context of history-dependent materials in previous sections of this chapter. Therefore, the basic development of the formulation for hyperelasticity is somewhat different. Furthermore, hyperelastic materials are often incompressible or very nearly so; hence, mixed ("hybrid") formulations can be used effectively. In this section the hyperelastic model provided in Abaqus is defined, and the mixed variational principles used in Abaqus/Standard to treat the fully incompressible case and the almost incompressible case are introduced.
### Definitions and basic kinematic results

We first introduce some definitions and basic kinematic results that will be used in this section. Some of these items have already been discussed in Chapter 1, "Introduction and Basic Equations": they are repeated here for convenience.

Writing the current position of a material point as ![](../graphics/stm_eqn00117.gif) and the reference position of the same point as ![](../graphics/stm_eqn00141.gif), the deformation gradient is

![](../graphics/stm_eqn06705.gif)Then *J*, the total volume change at the point, is

![](../graphics/stm_eqn06706.gif)For simplicity, we define

![](../graphics/stm_eqn06707.gif)as the deformation gradient with the volume change eliminated.

We then introduce the deviatoric stretch matrix (the left Cauchy-Green strain tensor) of ![](../graphics/stm_eqn02953.gif) as

![](../graphics/stm_eqn06708.gif)so that we can define the first strain invariant as

![](../graphics/stm_eqn06709.gif)where ![](../graphics/stm_eqn00064.gif) is a unit matrix, and the second strain invariant as

![](../graphics/stm_eqn06710.gif)The variations of ![](../graphics/stm_eqn06711.gif), ![](../graphics/stm_eqn06712.gif), ![](../graphics/stm_eqn06713.gif), ![](../graphics/stm_eqn06714.gif), and *J* will be required during the remainder of the development. We first define some variations of basic kinematic quantities that will be needed to write these results.

The gradient of the displacement variation with respect to current position is written as

![](../graphics/stm_eqn06715.gif)

The virtual rate of deformation is the symmetric part of ![](../graphics/stm_eqn03092.gif):

![](../graphics/stm_eqn06716.gif)which we decompose into the virtual rate of change of volume per current volume (the "virtual volumetric strain rate"),

![](../graphics/stm_eqn06717.gif)and the virtual deviatoric strain rate,

![](../graphics/stm_eqn06718.gif)

The virtual rate of spin of the material is the antisymmetric part of ![](../graphics/stm_eqn03092.gif):

![](../graphics/stm_eqn06719.gif)

The variations of ![](../graphics/stm_eqn06711.gif), ![](../graphics/stm_eqn06712.gif), ![](../graphics/stm_eqn06713.gif), ![](../graphics/stm_eqn06714.gif), and *J* are obtained directly from their definitions above in terms of these quantities as

![](../graphics/stm_eqn06720.gif)where

![](../graphics/stm_eqn06721.gif)

![](../graphics/stm_eqn06722.gif)where

![](../graphics/stm_eqn06723.gif)

![](../graphics/stm_eqn06724.gif)

![](../graphics/stm_eqn06725.gif)and

![](../graphics/stm_eqn06726.gif)

The Cauchy ("true") stress components are defined from the strain energy potential as follows. From the virtual work principal the internal energy variation is

![](../graphics/stm_eqn06727.gif)where ![](../graphics/stm_eqn00033.gif) are the components of the Cauchy ("true") stress, *V* is the current volume, and ![](../graphics/stm_eqn01828.gif) is the reference volume.

We decompose the stress into the equivalent pressure stress,

![](../graphics/stm_eqn06728.gif)and the deviatoric stress,

![](../graphics/stm_eqn06729.gif)so that the internal energy variation can be written

![](../graphics/stm_eqn06730.gif)

For isotropic, compressible materials the strain energy, *U*, is a function of ![](../graphics/stm_eqn06713.gif), ![](../graphics/stm_eqn06714.gif), and *J*:

![](../graphics/stm_eqn06731.gif)so that

![](../graphics/stm_eqn06732.gif)Hence, using [Equation 4.6.1&#8211;3](04s06a123.md), [Equation 4.6.1&#8211;4](04s06a123.md), and [Equation 4.6.1&#8211;5](04s06a123.md),

![](../graphics/stm_eqn06733.gif)

Since the variation of the strain energy potential is, by definition, the internal virtual work per reference volume, ![](../graphics/stm_eqn06734.gif), we have

![](../graphics/stm_eqn06735.gif)

For a compressible material the strain variations are arbitrary, so this equation defines the stress components for such a material as

![](../graphics/stm_eqn06736.gif)and

![](../graphics/stm_eqn06737.gif)

When the material response is almost incompressible, the pure displacement formulation, in which the strain invariants are computed from the kinematic variables of the finite element model, can behave poorly. One difficulty is that from a numerical point of view the stiffness matrix is almost singular because the effective bulk modulus of the material is so large compared to its effective shear modulus, thus causing difficulties with the solution of the discretized equilibrium equations. Similarly, in Abaqus/Explicit the high bulk modulus increases the dilatational wave speed, thus reducing the stable time increment substantially. Another problem is that, unless reduced-integration techniques are used, the stresses calculated at the numerical integration points show large oscillations in the pressure stress values, because---in general---the elements cannot respond accurately and still have small volume changes at all numerical integration points. To avoid such problems, Abaqus/Standard offers a "mixed" formulation for such cases. The concept is to introduce a variable, ![](../graphics/stm_eqn06738.gif), that is used in place of the volume change, *J*, in the definition of the strain energy potential. The internal energy integral, ![](../graphics/stm_eqn06739.gif), is augmented with the constraint that ![](../graphics/stm_eqn06740.gif), imposed by the use of a Lagrange multiplier, ![](../graphics/stm_eqn06422.gif), and integrated over the volume:

![](../graphics/stm_eqn06741.gif)Taking the variation of this definition,

![](../graphics/stm_eqn06742.gif)Since ![](../graphics/stm_eqn06743.gif) is an independent variation in this expression, the Lagrange multiplier is

![](../graphics/stm_eqn06744.gif)and its variation is

![](../graphics/stm_eqn06745.gif)where

![](../graphics/stm_eqn06746.gif)These results allow us to write the augmented internal energy variation as

![](../graphics/stm_eqn06747.gif)which implies that continuity of the![](../graphics/stm_eqn06748.gif) interpolation across elements is not required.

This augmented formulation can be used for any value of compressibility except fully incompressible behavior. For most element types ![](../graphics/stm_eqn06748.gif) is interpolated independently in each element: Abaqus uses constant ![](../graphics/stm_eqn06738.gif) in most first-order elements and linear variation of ![](../graphics/stm_eqn06738.gif) with respect to position in second-order elements. The only element type where continuity of the ![](../graphics/stm_eqn06738.gif) interpolation across elements is enforced is C3D4H: a first-order tetrahedron with a linear interpolation of ![](../graphics/stm_eqn06738.gif) continuous across elements.

When the material is fully incompressible, *U* is a function of the first and second strain invariants---![](../graphics/stm_eqn06713.gif) and ![](../graphics/stm_eqn06714.gif)---only, and we write the internal energy in the augmented form,

![](../graphics/stm_eqn06749.gif)where ![](../graphics/stm_eqn06422.gif) is again a Lagrange multiplier introduced to impose the constraint ![](../graphics/stm_eqn06750.gif) in such a way that the variation of ![](../graphics/stm_eqn06751.gif) can be taken with respect to all kinematic variables, thus giving

![](../graphics/stm_eqn06752.gif)The Lagrange multiplier ![](../graphics/stm_eqn06422.gif) is interpolated in the same way as ![](../graphics/stm_eqn06738.gif) is interpolated in the augmented formulation for almost incompressible behavior; that is, ![](../graphics/stm_eqn06422.gif) is assumed to be constant in most first-order elements and to vary linearly with respect to position in second-order elements. The only exception is element type C3D4H, which is a first-order tetrahedron with a linear interpolation of ![](../graphics/stm_eqn06422.gif) continuous across elements.
### Rate of change of the internal virtual work

The rate of change of the internal virtual work is required for use in the Newton method, which is generally used in Abaqus/Standard to solve the nonlinear equilibrium equations (after discretization by finite elements). It will also be used when we extend the elasticity model to viscoelastic behavior for small (linearized) vibrations about a predeformed state.

When the pure displacement formulation is used for the compressible case, the deviatoric stress components, ![](../graphics/stm_eqn00522.gif), are defined by [Equation 4.6.1&#8211;8](04s06a123.md), from which we can show that

![](../graphics/stm_eqn06753.gif)where the "effective deviatoric elasticity" of the material, ![](../graphics/stm_eqn06754.gif), is defined as

![](../graphics/stm_eqn06755.gif)and the deviatoric stress rate-volumetric strain rate coupling term, ![](../graphics/stm_eqn06756.gif), is

![](../graphics/stm_eqn06757.gif)

From [Equation 4.6.1&#8211;9](04s06a123.md) it can be shown that

![](../graphics/stm_eqn06758.gif)where *K* is the effective bulk modulus of the material,

![](../graphics/stm_eqn06759.gif)Thus,

![](../graphics/stm_eqn06760.gif)since

![](../graphics/stm_eqn06761.gif)

For the mixed formulation introduced for almost incompressible materials, the rate of change of the augmented variation of internal energy, [Equation 4.6.1&#8211;10](04s06a123.md), is

![](../graphics/stm_eqn06762.gif)where

![](../graphics/stm_eqn06763.gif)

![](../graphics/stm_eqn06764.gif)

![](../graphics/stm_eqn06765.gif)and

![](../graphics/stm_eqn06766.gif)in which

![](../graphics/stm_eqn06767.gif)

For the case of incompressible materials the rate of change of the augmented variation of internal energy is similarly obtained from [Equation 4.6.1&#8211;11](04s06a123.md) as

![](../graphics/stm_eqn06768.gif)
### Particular forms of the strain energy potential

Several particular forms of the strain energy potential are available in Abaqus. The incompressible or almost incompressible models make up:

the polynomial form and its particular cases---the reduced polynomial form, the neo-Hookean form, the Mooney-Rivlin form, and the Yeoh form;

the Ogden form;

the Arruda-Boyce form; and

the Van der Waals form.In addition, a hyperelastic model for highly compressible, elastic materials is offered.Polynomial form and particular cases

Given isotropy and additive decomposition of the deviatoric and volumetric strain energy contributions in the presence of incompressible or almost incompressible behavior, we can write the potential, in general, as

![](../graphics/stm_eqn06769.gif)Setting ![](../graphics/stm_eqn06770.gif) and expanding ![](../graphics/stm_eqn06771.gif) in a Taylor series, we arrive at

![](../graphics/stm_eqn06772.gif)This form is the polynomial representation of the strain energy in Abaqus. The parameter *N* can take values up to six; however, values of *N* greater than 2 are rarely used when both the first and second invariants are taken into account. ![](../graphics/stm_eqn06773.gif) and ![](../graphics/stm_eqn06774.gif) are temperature-dependent material parameters. The value of *N* and tables giving the ![](../graphics/stm_eqn06773.gif) and ![](../graphics/stm_eqn06774.gif) values as functions of temperature are specified by the user. The elastic volume strain, ![](../graphics/stm_eqn06775.gif), follows from the total volume strain, *J*, and the thermal volume strain, ![](../graphics/stm_eqn06776.gif), with the relation

![](../graphics/stm_eqn06777.gif)and ![](../graphics/stm_eqn06776.gif) follows from the linear thermal expansion, ![](../graphics/stm_eqn06778.gif), with

![](../graphics/stm_eqn06779.gif)where ![](../graphics/stm_eqn06778.gif) follows from the temperature and the isotropic thermal expansion coefficient defined by the user.

The ![](../graphics/stm_eqn06774.gif) values determine the compressibility of the material: if all the ![](../graphics/stm_eqn06774.gif) are zero, the material is taken as fully incompressible. If ![](../graphics/stm_eqn06780.gif), all ![](../graphics/stm_eqn06774.gif) must be zero.

Regardless of the value of *N*, the initial shear modulus, ![](../graphics/stm_eqn06781.gif) and the bulk modulus, ![](../graphics/stm_eqn06782.gif) depend only on the polynomial coefficients of order ![](../graphics/stm_eqn05955.gif):

![](../graphics/stm_eqn06783.gif)

If ![](../graphics/stm_eqn05955.gif), so that only the linear terms in the deviatoric strain energy are retained, the Mooney-Rivlin form is recovered:

![](../graphics/stm_eqn06784.gif)The Mooney-Rivlin form can be viewed as an extension of the neo-Hookean form (discussed below) in that it adds a term that depends on the second invariant of the left Cauchy-Green tensor. In some cases this form will give a more accurate fit to the experimental data than the neo-Hookean form; in general, however, both models give similar accuracy since they use only linear functions of the invariants. These functions do not allow representation of the "upturn" at higher strain levels in the stress-strain curve.

Particular forms of the polynomial model can also be obtained by setting specific coefficients to zero. If all ![](../graphics/stm_eqn06773.gif) with ![](../graphics/stm_eqn06785.gif) are set to zero, the reduced polynomial form is obtained:

![](../graphics/stm_eqn06786.gif)Following [Yeoh (1993)](07s01a01-References.md) the justification for reducing the general polynomial series expansion by omitting the dependence on the second invariant arises from the following observations. The sensitivity of the strain energy function to changes in the second invariant is generally much smaller than the sensitivity to changes in the first invariant. In addition, the ![](../graphics/stm_eqn06714.gif)-dependence is difficult to measure, so it might be preferable to neglect it rather than to calculate it based on potentially inaccurate measurements. Finally, it appears that omitting the dependence on the second invariant if data for only a particular mode of deformation are known might enhance the prediction for other deformation states. This conjecture is supported by investigating the so-called reduced stresses in the presence of almost incompressible behavior:

![](../graphics/stm_eqn06787.gif)where the ![](../graphics/stm_eqn06788.gif), ![](../graphics/stm_eqn06789.gif) represent the principal Cauchy ("true") stresses. If the derivatives with respect to ![](../graphics/stm_eqn06714.gif) are omitted and different stress states---uniaxial, biaxial, and planar---are considered, the reduced stresses have the same form regardless of the stress state.

Measurements of the ![](../graphics/stm_eqn06714.gif)-dependence of carbon-black reinforced rubber vulcanizates confirming these findings can be found in [Kawabata, Yamashita, et al. (1995)](07s01a01-References.md). The paper of [Kaliske and Rothert (1997)](07s01a01-References.md) also supports the notion that often the prediction of general deformation states based on a uniaxial measurement can be enhanced only by ignoring the ![](../graphics/stm_eqn06714.gif)-dependence.

In this context it is worth noting that the mathematical structure of the Arruda-Boyce model can be viewed as a fifth-order reduced polynomial, where the five coefficients ![](../graphics/stm_eqn06790.gif) are implicit nonlinear functions of the two parameters ![](../graphics/stm_eqn01087.gif) and ![](../graphics/stm_eqn06791.gif) in the Arruda-Boyce form. However, the Arruda-Boyce model offers a physical interpretation of the parameters, which the general fifth-order reduced polynomial fails to provide.

The Yeoh form ([Yeoh, 1993](07s01a01-References.md)) can be viewed as a special case of the reduced polynomial with ![](../graphics/stm_eqn06792.gif):

![](../graphics/stm_eqn06793.gif)Typically, if ![](../graphics/stm_eqn06794.gif), the second coefficient will be negative and one to two orders of magnitude smaller [i.e., ![](../graphics/stm_eqn06795.gif) is ![](../graphics/stm_eqn06796.gif) to ![](../graphics/stm_eqn06797.gif)], while the third coefficient ![](../graphics/stm_eqn06798.gif) is again one to two orders of magnitude smaller but positive [i.e., ![](../graphics/stm_eqn06798.gif) is ![](../graphics/stm_eqn06799.gif) to ![](../graphics/stm_eqn06800.gif)]. These magnitudes will create the typical S-shape of the stress-strain behavior of rubber; at low strains ![](../graphics/stm_eqn06801.gif) represents the initial shear modulus, which softens at moderate strains due to the effect of the negative second coefficient ![](../graphics/stm_eqn06795.gif) and is followed by an upturn at large strains due to the positive third coefficient ![](../graphics/stm_eqn06798.gif). Thus, the Yeoh model often provides an accurate fit over a large strain range.

If the reduced-polynomial strain-energy function is simplified further by setting ![](../graphics/stm_eqn05955.gif), the neo-Hookean form is obtained:

![](../graphics/stm_eqn06802.gif)This form is the simplest hyperelastic model and often serves as a prototype for elastomeric materials in the absence of accurate material data. It also has some theoretical relevance since the mathematical representation is analogous to that of an ideal gas: the neo-Hookean potential represents the Helmholtz free energy of a molecular network with Gaussian chain-length distribution (see [Treloar, 1975](07s01a01-References.md)).

The user can request that Abaqus calculate the ![](../graphics/stm_eqn06773.gif) and ![](../graphics/stm_eqn06774.gif) values from measurements of nominal stress and strain in simple experiments. The basis of this calculation is described in "Fitting of hyperelastic and hyperfoam constants,"  Section 4.6.2.Ogden form

The Ogden strain energy potential is expressed in terms of the principal stretches. In Abaqus the following formulation is used:

![](../graphics/stm_eqn06803.gif)where

![](../graphics/stm_eqn06804.gif)Hence, the first part of Ogden's strain energy function depends only on ![](../graphics/stm_eqn06713.gif) and ![](../graphics/stm_eqn06714.gif). Ogden's energy function cannot be written explicitly in terms of ![](../graphics/stm_eqn06713.gif) and ![](../graphics/stm_eqn06714.gif). It is, however, possible to obtain closed-form expressions for the derivatives of *U* with respect to ![](../graphics/stm_eqn06713.gif) and ![](../graphics/stm_eqn06714.gif).

The value of *N* and tables giving the ![](../graphics/stm_eqn06805.gif) and ![](../graphics/stm_eqn01123.gif) values as functions of temperature are specified by the user. If ![](../graphics/stm_eqn05962.gif), ![](../graphics/stm_eqn06806.gif), and ![](../graphics/stm_eqn06807.gif), the Mooney-Rivlin model is obtained. If ![](../graphics/stm_eqn05955.gif) and ![](../graphics/stm_eqn06806.gif), Ogden's model degenerates to the neo-Hookean material model. In the Ogden form the initial shear modulus, ![](../graphics/stm_eqn06808.gif), depends on all coefficients:

![](../graphics/stm_eqn06809.gif)and the initial bulk modulus, ![](../graphics/stm_eqn06810.gif), depends on ![](../graphics/stm_eqn06811.gif) as before. The user can request that Abaqus calculate the ![](../graphics/stm_eqn06805.gif) and ![](../graphics/stm_eqn01123.gif) values from measurements of nominal stress and strain.Arruda-Boyce form

The hyperelastic Arruda-Boyce potential has the following form:

![](../graphics/stm_eqn06812.gif)where

![](../graphics/stm_eqn06813.gif)The deviatoric part of the strain energy density comes from [Arruda and Boyce (1993)](07s01a01-References.md). This model is also known as the eight-chain model, since it was developed starting out from a representative volume element where eight springs emanate from the center of a cube to its corners. The values of the coefficients ![](../graphics/stm_eqn06814.gif) arise from a series expansion of the inverse Langevin function, which arises in the statistical treatment of non-Gaussian chains. The series expansion is truncated after the fifth term. The coefficient ![](../graphics/stm_eqn06791.gif) is referred to as the locking stretch. Approximately at this stretch the slope of the stress-strain curve will rise significantly. The initial shear modulus, ![](../graphics/stm_eqn06808.gif), is related to ![](../graphics/stm_eqn01087.gif) with the expression

![](../graphics/stm_eqn06815.gif) A typical value of ![](../graphics/stm_eqn06791.gif) is 7, for which ![](../graphics/stm_eqn06816.gif).

The initial bulk modulus is obtained as ![](../graphics/stm_eqn06817.gif). To the deviatoric part of the strain energy density we add a simplified representation of the volumetric strain energy density, which requires only one material parameter, so that all material parameters can be estimated easily even with limited knowledge of the material behavior. This volumetric representation has been used successfully by [Kaliske and Rothert (1997)](07s01a01-References.md) and provides sufficient accuracy for most engineering elastomeric materials.

The Arruda-Boyce potential depends on the first invariant only. The physical interpretation is that the eight chains are stretched equally under the action of a general deformation state. The first invariant, ![](../graphics/stm_eqn06818.gif), directly represents this elongation.

When the Arruda-Boyce form is chosen, the user can specify the coefficients as functions of temperature; alternatively, Abaqus can perform a fit of the test data specified by the user to determine the coefficients.Van der Waals form

The hyperelastic Van der Waals potential, also known as the Kilian model, has the following form:

![](../graphics/stm_eqn06819.gif)where

![](../graphics/stm_eqn06820.gif)The name "Van der Waals" draws on the analogy in the thermodynamic interpretation of the equations of state for rubber and gas. While the neo-Hookean model can be compared with an ideal gas in that it starts out from a Gaussian network with no mutual interaction between the "quasi-particles" (Kilian, 1981), the Van der Waals strain energy potential is analogous to the equations of state of a real gas. This introduces two additional material parameters: the locking stretch, ![](../graphics/stm_eqn06791.gif), and the global interaction parameter, *a*. (Similarly, the Van der Waals equation for a real gas introduces two parameters to account for excluded volume and modified exchange of momentum between the particles.)

The locking stretch, ![](../graphics/stm_eqn06791.gif), accounts for finite extendability of the non-Gaussian chain network. In contrast to the Arruda-Boyce model the mathematical structure of the Van der Waals potential is such that the strain energy tends to infinity as the locking stretch, ![](../graphics/stm_eqn06791.gif), is reached; more precisely, as ![](../graphics/stm_eqn06821.gif). Thus, the Van der Waals potential cannot be used at stretches larger than the locking stretch.

The global interaction parameter, *a*, models the interaction between the chains; it is difficult to estimate. Kilian et al. (1986) point out that, given Mooney-Rivlin coefficients and a locking stretch ![](../graphics/stm_eqn06791.gif), a suitable value for the global interaction parameter is

![](../graphics/stm_eqn06822.gif)where ![](../graphics/stm_eqn01087.gif) is the initial shear modulus at low strains and ![](../graphics/stm_eqn06823.gif) is the second Mooney-Rivlin parameter. Given a positive initial shear modulus, ![](../graphics/stm_eqn01087.gif), and locking stretch, ![](../graphics/stm_eqn06791.gif), too large a positive interaction parameter, *a*, will lead to Drucker instability in the tensile range. Realistic values of the global interaction parameter, *a*, will contribute to the characteristic S-shape of tensile stress-strain curves of rubber in the middle strain range before the final upturn as the locking stretch is approached, without causing instability.

The parameter ![](../graphics/stm_eqn01219.gif) represents a linear mixture parameter combining both invariants ![](../graphics/stm_eqn06713.gif) and ![](../graphics/stm_eqn06714.gif) into ![](../graphics/stm_eqn06824.gif); for ![](../graphics/stm_eqn06825.gif), the Van der Waals potential will be dependent on the first invariant only. Admissible values for this parameter are ![](../graphics/stm_eqn06826.gif).

When the Van der Waals potential is chosen, the user can specify the coefficients as functions of temperature; alternatively, the parameters can be fitted from user-defined test data. The data fitting procedure will not necessarily yield a value of ![](../graphics/stm_eqn01219.gif) between zero and one. If during the curve fitting procedure the parameter ![](../graphics/stm_eqn01219.gif) leaves the admissible range, the curve fitting procedure is aborted and restarted with a fixed value of ![](../graphics/stm_eqn06825.gif). Alternatively, the curve fitting procedure can be used with a user-defined value of ![](../graphics/stm_eqn01219.gif).Strain energy potential for highly compressible elastomers

While the previous forms are intended for incompressible or almost incompressible materials, the elastic foam energy function is designed for describing highly compressible elastomers ([Storkers, 1986](07s01a01-References.md)). This energy function has the form

![](../graphics/stm_eqn06827.gif)where

![](../graphics/stm_eqn06828.gif)The volumetric and the deviatoric contributions are coupled in this expression, which can be demonstrated clearly by writing the expression in the form

![](../graphics/stm_eqn06829.gif)Series expansion of the last two terms in terms of ![](../graphics/stm_eqn06830.gif) shows that the first-order terms vanish and that the coefficients of the second-order terms are equal to ![](../graphics/stm_eqn06831.gif). Hence, a stable material is obtained if ![](../graphics/stm_eqn06832.gif). For each term in the energy function, the coefficient ![](../graphics/stm_eqn01120.gif) determines the degree of compressibility. ![](../graphics/stm_eqn01120.gif) is related to the Poisson's ratio, ![](../graphics/stm_eqn06833.gif), by the expressions

![](../graphics/stm_eqn06834.gif)Thus, if ![](../graphics/stm_eqn01120.gif) is the same for all terms, we have a single effective Poisson's ratio, ![](../graphics/stm_eqn01854.gif). The value of *N* and tables giving the ![](../graphics/stm_eqn06805.gif), ![](../graphics/stm_eqn01123.gif), and ![](../graphics/stm_eqn06833.gif) values as functions of temperature are specified by the user for the hyperfoam material model. The Poisson's ratio is valid for finite values of the logarithmic principal strains ![](../graphics/stm_eqn06835.gif); ![](../graphics/stm_eqn06836.gif) in uniaxial tension. For ![](../graphics/stm_eqn06837.gif) there is no Poisson's effect. The initial shear modulus, ![](../graphics/stm_eqn06808.gif), again follows from

![](../graphics/stm_eqn06809.gif)and the initial bulk modulus follows from

![](../graphics/stm_eqn06838.gif)

If Poisson's ratio is constant and known, Abaqus can calculate the ![](../graphics/stm_eqn06805.gif) and ![](../graphics/stm_eqn01123.gif) from measurements of nominal stress and stretch as before. If Poisson's ratio depends on the level of straining, Abaqus can also calculate the ![](../graphics/stm_eqn01120.gif) from the nominal lateral strains.Subroutine UHYPER

Abaqus/Standard also allows other forms of strain energy potentials to be defined for isotropic materials via user subroutine UHYPER by programming the first and second derivatives of *U* with respect to ![](../graphics/stm_eqn06713.gif), ![](../graphics/stm_eqn06714.gif), and *J* in that subroutine.
### References

### References

"Hyperelastic behavior of rubberlike materials,"  Section 22.5.1 of the Abaqus Analysis User's Guide

"Hyperelastic behavior in elastomeric foams,"  Section 22.5.2 of the Abaqus Analysis User's Guide