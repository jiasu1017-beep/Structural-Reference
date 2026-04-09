# 4.8.1 Viscoelasticity

### 4.8.1 Viscoelasticity

**Products: **Abaqus/Standard  Abaqus/Explicit

The basic hereditary integral formulation for linear isotropic viscoelasticity is

![](../graphics/stm_eqn07139.gif)Here ![](../graphics/stm_eqn02228.gif) and ![](../graphics/stm_eqn07140.gif) are the mechanical deviatoric and volumetric strains; *K* is the bulk modulus and *G* is the shear modulus, which are functions of the reduced time ![](../graphics/stm_eqn01399.gif); and ![](../graphics/stm_eqn07141.gif) denotes differentiation with respect to ![](../graphics/stm_eqn07142.gif).

The reduced time is related to the actual time through the integral differential equation

![](../graphics/stm_eqn07143.gif)where ![](../graphics/stm_eqn01111.gif) is the temperature and ![](../graphics/stm_eqn07144.gif) is the shift function. (Hence, if ![](../graphics/stm_eqn07145.gif), ![](../graphics/stm_eqn07146.gif).) A commonly used shift function is the Williams-Landel-Ferry (WLF) equation, which has the following form:

![](../graphics/stm_eqn07147.gif)where ![](../graphics/stm_eqn07148.gif) and ![](../graphics/stm_eqn07149.gif) are constants and ![](../graphics/stm_eqn07150.gif) is the "glass" transition temperature. This is the temperature at which, in principle, the behavior of the material changes from glassy to rubbery. If ![](../graphics/stm_eqn07151.gif), deformation changes will be elastic. ![](../graphics/stm_eqn07148.gif) and ![](../graphics/stm_eqn07149.gif) were once thought to be "universal" constants whose values were obtained at ![](../graphics/stm_eqn07150.gif), but these constants have been shown to vary slightly from polymer to polymer.

Abaqus allows the WLF equation to be used with any convenient temperature, other than the glass transition temperature, as the reference temperature. The form of the equation remains the same, but the constants are different. Namely,

![](../graphics/stm_eqn07152.gif)where ![](../graphics/stm_eqn05040.gif) is the reference temperature at which the relaxation data are given, and ![](../graphics/stm_eqn07153.gif) and ![](../graphics/stm_eqn07154.gif) are the calibration constants at the reference temperature. The "universal" constants ![](../graphics/stm_eqn07148.gif) and ![](../graphics/stm_eqn07149.gif) are related to ![](../graphics/stm_eqn07153.gif) and ![](../graphics/stm_eqn07154.gif) as follows:

![](../graphics/stm_eqn07155.gif)Other forms of ![](../graphics/stm_eqn07156.gif) are also used, such as a power series in ![](../graphics/stm_eqn07157.gif). Abaqus allows a general definition of the shift function with user subroutine UTRS.

The relaxation functions ![](../graphics/stm_eqn07158.gif) and ![](../graphics/stm_eqn07159.gif) can be defined individually in terms of a series of exponentials known as the Prony series:

![](../graphics/stm_eqn07160.gif)where ![](../graphics/stm_eqn07161.gif) and ![](../graphics/stm_eqn07162.gif) represent the long-term bulk and shear moduli. In general, the relaxation times ![](../graphics/stm_eqn07163.gif) and ![](../graphics/stm_eqn07164.gif) need not equal each other; however, Abaqus assumes that ![](../graphics/stm_eqn07165.gif). On the other hand, the number of terms in bulk and shear, ![](../graphics/stm_eqn07166.gif) and ![](../graphics/stm_eqn07167.gif), need not equal each other. In fact, in many practical cases it can be assumed that ![](../graphics/stm_eqn07168.gif). Hence, we now concentrate on the deviatoric behavior. The equations for the volumetric terms can be derived in an analogous way.

The deviatoric integral equation is

![](../graphics/stm_eqn07169.gif)We rewrite this equation in the form

![](../graphics/stm_eqn07170.gif)where ![](../graphics/stm_eqn07171.gif) is the instantaneous shear modulus, ![](../graphics/stm_eqn07172.gif) is the relative modulus of term *i*, and

![](../graphics/stm_eqn07173.gif)is the viscous (creep) strain in each term of the series. For finite element analysis this equation must be integrated over a finite increment of time. To perform this integration, we will assume that during the increment ![](../graphics/stm_eqn02228.gif) varies linearly with ![](../graphics/stm_eqn01399.gif); hence, ![](../graphics/stm_eqn07174.gif). To use this relation, we break up [Equation 4.8.1&#8211;2](04s08a128.md) into two parts:

![](../graphics/stm_eqn07175.gif)Now observe that

![](../graphics/stm_eqn07176.gif)Use of this expression and the approximation for ![](../graphics/stm_eqn07177.gif) during the increment yields

![](../graphics/stm_eqn07178.gif)The first and last integrals in this expression are readily evaluated, whereas from [Equation 4.8.1&#8211;2](04s08a128.md) follows that the second integral represents the viscous strain in the ![](../graphics/stm_eqn07179.gif) term at the beginning of the increment. Hence, the change in the ![](../graphics/stm_eqn07179.gif) viscous strain is

![](../graphics/stm_eqn07180.gif)If ![](../graphics/stm_eqn07181.gif) approaches zero, this expression can be approximated by

![](../graphics/stm_eqn07182.gif)The last form is used in the computations if ![](../graphics/stm_eqn07183.gif).

Hence, in an increment, [Equation 4.8.1&#8211;3](04s08a128.md) or [Equation 4.8.1&#8211;4](04s08a128.md) is used to calculate the new value of the viscous strains. [Equation 4.8.1&#8211;1](04s08a128.md) is then used subsequently to obtain the new value of the stresses.

The tangent modulus is readily derived from these equations by differentiating the deviatoric stress increment, which is

![](../graphics/stm_eqn07184.gif)with respect to the deviatoric strain increment ![](../graphics/stm_eqn07185.gif). Since the equations are linear, the modulus depends only on the reduced time step:

![](../graphics/stm_eqn07186.gif)

Finally, one needs a relation between the reduced time increment, ![](../graphics/stm_eqn07187.gif), and the actual time increment, ![](../graphics/stm_eqn00883.gif). To do this, we observe that ![](../graphics/stm_eqn07144.gif) varies very nonlinearly with temperature; hence, any direct approximation of ![](../graphics/stm_eqn07144.gif) is likely to lead to large errors. On the other hand, ![](../graphics/stm_eqn07156.gif) will generally be a smoothly varying function of temperature that is well approximated by a linear function of temperature over an increment. If we further assume that incrementally the temperature ![](../graphics/stm_eqn01111.gif) is a linear function of time *t*, one finds the relation

![](../graphics/stm_eqn07188.gif)or

![](../graphics/stm_eqn07189.gif)with

![](../graphics/stm_eqn07190.gif)This yields the relation

![](../graphics/stm_eqn07191.gif)This expression can also be written as

![](../graphics/stm_eqn07192.gif)
### Reduced states of stress

So far, we have discussed full triaxial stress states. If the stress state is reduced (i.e., plane stress or uniaxial stress), the equations derived here cannot be used directly because only the total stress state is reduced, not the individual terms in the series. Therefore, we use the following procedure.

For plane stress let the third component be the zero stress component. At the beginning of the increment we presumably know the volumetric elastic strain ![](../graphics/stm_eqn07193.gif), the volumetric viscous strain ![](../graphics/stm_eqn07194.gif), and the volumetric viscous strains ![](../graphics/stm_eqn07195.gif) associated with the Prony series. The total volumetric strain can be obtained by adding together the elastic volumetric strain and the volumetric viscous strain

![](../graphics/stm_eqn07196.gif)The deviatoric strain in the 3-direction follows from the relation ![](../graphics/stm_eqn07197.gif), which yields:

![](../graphics/stm_eqn07198.gif)The out-of-plane deviatoric stress at the end of the increment is

![](../graphics/stm_eqn07199.gif)Substituting [Equation 4.8.1&#8211;3](04s08a128.md) for ![](../graphics/stm_eqn07200.gif), letting ![](../graphics/stm_eqn07201.gif), and collecting terms gives

![](../graphics/stm_eqn07202.gif)The hydrostatic stress is derived similarly as

![](../graphics/stm_eqn07203.gif)We can write these equations in the form

![](../graphics/stm_eqn07204.gif)In the third direction the deviatoric stress minus the hydrostatic pressure is zero; hence,

![](../graphics/stm_eqn07205.gif)Since ![](../graphics/stm_eqn07206.gif), it follows that

![](../graphics/stm_eqn07207.gif)from which ![](../graphics/stm_eqn03570.gif) can be solved. One can then also calculate ![](../graphics/stm_eqn07208.gif) and ![](../graphics/stm_eqn07209.gif), and with [Equation 4.8.1&#8211;3](04s08a128.md) or [Equation 4.8.1&#8211;4](04s08a128.md) one can update the deviatoric viscous strains ![](../graphics/stm_eqn07210.gif). The volumetric strains ![](../graphics/stm_eqn07211.gif) are obtained with a relation similar to [Equation 4.8.1&#8211;3](04s08a128.md).

For uniaxial stress states a similar procedure is used. As before, ![](../graphics/stm_eqn07212.gif) follows from [Equation 4.8.1&#8211;5](04s08a128.md) and ![](../graphics/stm_eqn07213.gif) and ![](../graphics/stm_eqn07214.gif) follow from ![](../graphics/stm_eqn07215.gif):

![](../graphics/stm_eqn07216.gif)[Equation 4.8.1&#8211;6](04s08a128.md) and [Equation 4.8.1&#8211;7](04s08a128.md) can be used to calculate ![](../graphics/stm_eqn07217.gif) and ![](../graphics/stm_eqn06584.gif), which again leads to [Equation 4.8.1&#8211;8](04s08a128.md). Applying [Equation 4.8.1&#8211;9](04s08a128.md) for ![](../graphics/stm_eqn07218.gif)

![](../graphics/stm_eqn07219.gif)After this, one can follow the same procedure as for plane stress.
### Automatic time stepping procedure

To create an automatic time stepping procedure in Abaqus/Standard, we want to compare viscous strain rates at the beginning and the end of the increment. The strain rates in the individual terms at the beginning of the increment can be obtained directly by taking the limit of the incremental strain:

![](../graphics/stm_eqn07220.gif)A similar expression can be derived for the strain rate at the end of the increment:

![](../graphics/stm_eqn07221.gif)If we use these expressions to calculate a difference in estimated total viscous strain increment, one finds

![](../graphics/stm_eqn07222.gif)

This expression is readily evaluated. A similar expression can be calculated for volumetric strain ![](../graphics/stm_eqn07223.gif), and from these two quantities a suitable scalar measure can be constructed; for example,

![](../graphics/stm_eqn07224.gif)Comparison with the user-specified strain increment tolerance allows construction of an automatic time stepping scheme.
### Reference

### Reference

"Time domain viscoelasticity,"  Section 22.7.1 of the Abaqus Analysis User's Guide