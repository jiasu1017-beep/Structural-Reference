# 4.3.9 Deformation plasticity

### 4.3.9 Deformation plasticity

**Product: **Abaqus/Standard

Deformation plasticity theory is provided in Abaqus/Standard to allow fully plastic analysis of ductile metals, usually under small-displacement conditions, for fracture mechanics applications. The model is based on the Ramberg-Osgood relationship. In this section the detailed constitutive model is defined. The procedure for obtaining fully plastic solutions generally consists of incremental loading until the response is fully plastic.

The model is termed deformation plasticity because the stress is defined by the total mechanical strain with no history dependence. There is no "unloading" criterion (to allow recovery of the initial elastic stiffness immediately after a strain reversal), so that the model is only useful as a plasticity model in cases of continuous flow. It is, in fact, a nonlinear elastic model; but at a limit state when all of a specimen or structure is responding plastically, this model is a useful equivalent representation of the plastic response because it has such a simple form.
### One-dimensional model

The basic one-dimensional model is

![](../graphics/stm_eqn05986.gif)where ![](../graphics/stm_eqn01110.gif) is the stress, ![](../graphics/stm_eqn00377.gif) is the mechanical strain, *E* is Young's modulus (defined as the slope of the stress-strain curve at zero stress), ![](../graphics/stm_eqn00904.gif) is the "yield" offset (in the sense that, when ![](../graphics/stm_eqn05987.gif), ![](../graphics/stm_eqn05988.gif)), and *n* is the hardening exponent for the "plastic" (nonlinear) term: ![](../graphics/stm_eqn05989.gif).

The material behavior described by this model is nonlinear at all stress levels, but for commonly used values of the hardening exponent (![](../graphics/stm_eqn05990.gif) or more) the nonlinearity becomes significant only at stress magnitudes approaching or exceeding ![](../graphics/stm_eqn05690.gif).
### Multiaxial generalization

A linear "elastic" relation is used to generalize the first term of [Equation 4.3.9&#8211;1](04s03a111.md); the nonlinear term is generalized to multiaxial stress states through the use of the Mises stress potential and associated flow law, giving the multiaxial model

![](../graphics/stm_eqn05991.gif)where

![](../graphics/stm_eqn00399.gif)

is the strain tensor,

![](../graphics/stm_eqn00033.gif)

is the stress tensor,

![](../graphics/stm_eqn05992.gif)

is the equivalent hydrostatic stress,

![](../graphics/stm_eqn05993.gif)

is the Mises equivalent stress,

![](../graphics/stm_eqn05994.gif)

is the stress deviator, and

![](../graphics/stm_eqn01854.gif)

is Poisson's ratio.

The linear part of the behavior may be compressible or incompressible depending on the value of Poisson's ratio, but the nonlinear part of the behavior is incompressible (because the flow is normal to the Mises stress potential). Since the model will generally be used for cases when the deformation is dominated by plastic flow, the use of selectively reduced integration elements or "hybrid" (mixed formulation) elements is recommended with this material model (except in plane stress).
### Strain energy density

The model is often used to obtain fully plastic solutions for fracture mechanics when the *J*-integral is needed. For evaluation of the *J*-integral the strain energy density is required. This is

![](../graphics/stm_eqn05995.gif)From [Equation 4.3.9&#8211;2](04s03a111.md) this may be obtained as

![](../graphics/stm_eqn05996.gif)
### Stress solution

During an analysis at each integration point the latest estimate of the kinematic solution is provided to the constitutive routines, which must provide the corresponding stress tensor calculated for the material model being used. Since this material model is nonlinear, we solve for the stresses by using the methods described below.The uniaxial case (the only nonzero stress component is one direct stress)

In this case

![](../graphics/stm_eqn05997.gif)where now ![](../graphics/stm_eqn05998.gif).

We solve [Equation 4.3.9&#8211;3](04s03a111.md) for ![](../graphics/stm_eqn01110.gif) using Newton's method. Writing ![](../graphics/stm_eqn05999.gif) as the correction to ![](../graphics/stm_eqn01110.gif), the Newton equations for [Equation 4.3.9&#8211;3](04s03a111.md) are

![](../graphics/stm_eqn06000.gif)

![](../graphics/stm_eqn06001.gif)As an initial guess we use ![](../graphics/stm_eqn06002.gif) if ![](../graphics/stm_eqn06003.gif) and ![](../graphics/stm_eqn06004.gif) (with the sign chosen as the same sign as ![](../graphics/stm_eqn00377.gif)) if ![](../graphics/stm_eqn06005.gif).

In this case the material stiffness matrix is

![](../graphics/stm_eqn06006.gif)All strain components defined by the kinematic solution

When all strain components are defined kinematically (that is, all cases except uniaxial and plane stress), projecting [Equation 4.3.9&#8211;2](04s03a111.md) onto ![](../graphics/stm_eqn06007.gif) gives

![](../graphics/stm_eqn06008.gif)a linear relationship for the volumetric behavior. Defining the deviatoric strain as

![](../graphics/stm_eqn06009.gif)and using [Equation 4.3.9&#8211;2](04s03a111.md), we find

![](../graphics/stm_eqn06010.gif)Defining the equivalent deviatoric strain as

![](../graphics/stm_eqn06011.gif)and using [Equation 4.3.9&#8211;4](04s03a111.md), we obtain the scalar equation

![](../graphics/stm_eqn06012.gif)This equation is solved for *q* using Newton's method:

![](../graphics/stm_eqn06013.gif)

![](../graphics/stm_eqn06014.gif)As for the uniaxial case we will use the starting guesses:

![](../graphics/stm_eqn06015.gif)and

![](../graphics/stm_eqn06016.gif)[Equation 4.3.9&#8211;6](04s03a111.md) can also be used to define

![](../graphics/stm_eqn06017.gif)so that [Equation 4.3.9&#8211;4](04s03a111.md) becomes

![](../graphics/stm_eqn06018.gif)Thus, once *q* is known, ![](../graphics/stm_eqn05748.gif) is defined; and, hence, ![](../graphics/stm_eqn00033.gif) is known as

![](../graphics/stm_eqn06019.gif)The material stiffness is defined as follows. From [Equation 4.3.9&#8211;7](04s03a111.md) we have

![](../graphics/stm_eqn06020.gif)and [Equation 4.3.9&#8211;6](04s03a111.md) gives

![](../graphics/stm_eqn06021.gif)and from [Equation 4.3.9&#8211;5](04s03a111.md),

![](../graphics/stm_eqn06022.gif)Using these results, [Equation 4.3.9&#8211;8](04s03a111.md) becomes

![](../graphics/stm_eqn06023.gif)Now

![](../graphics/stm_eqn06024.gif)

![](../graphics/stm_eqn06025.gif)and

![](../graphics/stm_eqn06026.gif)Combining these results, we obtain the material stiffness as

![](../graphics/stm_eqn06027.gif)Plane stress

For this case we obtain a solution for ![](../graphics/stm_eqn00033.gif) assuming that the material is fully incompressible. We then use this solution as a starting guess for a Newton loop to find ![](../graphics/stm_eqn00033.gif). Finally, we compute the corresponding material stiffness matrix.

Incompressible approximation:

In this case ![](../graphics/stm_eqn06028.gif) and ![](../graphics/stm_eqn06029.gif), so that ![](../graphics/stm_eqn06030.gif) is known and [Equation 4.3.9&#8211;6](04s03a111.md) can be solved as before for *q*. [Equation 4.3.9&#8211;7](04s03a111.md) then defines ![](../graphics/stm_eqn05748.gif), and the plane stress constraint requires that ![](../graphics/stm_eqn03408.gif), so

![](../graphics/stm_eqn06031.gif)and, hence, we obtain the initial estimate of the solution

![](../graphics/stm_eqn06032.gif)

![](../graphics/stm_eqn06033.gif)and

![](../graphics/stm_eqn06034.gif)Newton solution for the actual stresses:

[Equation 4.3.9&#8211;2](04s03a111.md) defines the stresses, where, for this case,

![](../graphics/stm_eqn06035.gif)

![](../graphics/stm_eqn06036.gif)and

![](../graphics/stm_eqn06037.gif)Therefore, [Equation 4.3.9&#8211;2](04s03a111.md) becomes

![](../graphics/stm_eqn06038.gif)These equations are solved using Newton's method:

![](../graphics/stm_eqn06039.gif)

![](../graphics/stm_eqn06040.gif)

![](../graphics/stm_eqn06041.gif)The material stiffness is directly available from [Equation 4.3.9&#8211;9](04s03a111.md) as

![](../graphics/stm_eqn06042.gif)
### Reference

### Reference

"Deformation plasticity,"  Section 23.2.13 of the Abaqus Analysis User's Guide