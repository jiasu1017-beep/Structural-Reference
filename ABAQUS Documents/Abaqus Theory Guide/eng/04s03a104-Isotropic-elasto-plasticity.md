# 4.3.2 Isotropic elasto-plasticity

### 4.3.2 Isotropic elasto-plasticity

**Products: **Abaqus/Standard  Abaqus/Explicit

This material model is very commonly used for metal plasticity calculations, either as a rate-dependent or as a rate-independent model, and has a particularly simple form. Because of this simplicity the algebraic equations associated with integrating the model are easily developed in terms of a single variable, and the material stiffness matrix can be written explicitly. This results in particularly efficient code. In this section these equations are developed.

For simplicity of notation all quantities not explicitly associated with a time point are assumed to be evaluated at the end of the increment.

The Mises yield function with associated flow means that there is no volumetric plastic strain; since the elastic bulk modulus is quite large, the volume change will be small. Thus, we can define the volume strain as

![](../graphics/stm_eqn05605.gif)and, hence, the deviatoric strain is

![](../graphics/stm_eqn05606.gif)
### Material model definition

The strain rate decomposition is

![](../graphics/stm_eqn05607.gif)Using the standard definition of corotational measures, this can be written in integrated form as

![](../graphics/stm_eqn05608.gif)

The elasticity is linear and isotropic and, therefore, can be written in terms of two temperature-dependent material parameters. For the purpose of this development it is most appropriate to choose these parameters as the bulk modulus, *K*, and the shear modulus, *G*. These are computed readily from the user's input of Young's modulus, *E*, and Poisson's ratio, ![](../graphics/stm_eqn01854.gif), as

![](../graphics/stm_eqn05609.gif)and

![](../graphics/stm_eqn05610.gif)

The elasticity can be written in volumetric and deviatoric components as follows.

Volumetric:

![](../graphics/stm_eqn05611.gif)where

![](../graphics/stm_eqn05612.gif)is the equivalent pressure stress.

Deviatoric:

![](../graphics/stm_eqn05613.gif)where ![](../graphics/stm_eqn00522.gif) is the deviatoric stress,

![](../graphics/stm_eqn05614.gif)

The flow rule is

![](../graphics/stm_eqn05615.gif)where

![](../graphics/stm_eqn05616.gif)

![](../graphics/stm_eqn05617.gif)and ![](../graphics/stm_eqn05618.gif) is the (scalar) equivalent plastic strain rate.

The plasticity requires that the material satisfy a uniaxial-stress plastic-strain strain-rate relationship. If the material is rate independent, this is the yield condition:

![](../graphics/stm_eqn05619.gif)where ![](../graphics/stm_eqn05620.gif) is the yield stress and is defined by the user as a function of equivalent plastic strain (![](../graphics/stm_eqn05621.gif)) and temperature (![](../graphics/stm_eqn01111.gif)).

If the material is rate dependent, the relationship is the uniaxial flow rate definition:

![](../graphics/stm_eqn05622.gif)where *h* is a known function. For example, the rate-dependent material model offers an overstress power law model of the form

![](../graphics/stm_eqn05623.gif)where ![](../graphics/stm_eqn05624.gif) and ![](../graphics/stm_eqn05625.gif) are user-defined temperature-dependent material parameters and ![](../graphics/stm_eqn05620.gif) is the static yield stress.

Integrating this relationship by the backward Euler method gives

![](../graphics/stm_eqn05626.gif)

This equation can be inverted (numerically, if necessary) to give *q* as a function of ![](../graphics/stm_eqn05621.gif) at the end of the increment.

Thus, both the rate-independent model and the integrated rate-dependent model give the general uniaxial form

![](../graphics/stm_eqn05627.gif)where ![](../graphics/stm_eqn05628.gif) for the rate-independent model and ![](../graphics/stm_eqn05629.gif) is obtained by inversion of [Equation 4.3.2&#8211;6](04s03a104.md) for the rate-dependent model.

[Equation 4.3.2&#8211;1](04s03a104.md) to [Equation 4.3.2&#8211;7](04s03a104.md) define the material behavior. In any increment when plastic flow is occurring (which is determined by evaluating *q* based on purely elastic response and finding that its value exceeds ![](../graphics/stm_eqn05285.gif)), these equations must be integrated and solved for the state at the end of the increment. As in the general discussion in "Metal plasticity models,"  Section 4.3.1, the integration is done by applying the backward Euler method to the flow rule ([Equation 4.3.2&#8211;4](04s03a104.md)), giving

![](../graphics/stm_eqn05630.gif)

Combining this with the deviatoric elasticity ([Equation 4.3.2&#8211;3](04s03a104.md)) and the integrated strain rate decomposition ([Equation 4.3.2&#8211;1](04s03a104.md)) gives

![](../graphics/stm_eqn05631.gif)

Using the integrated flow rule ([Equation 4.3.2&#8211;8](04s03a104.md)), together with the Mises definition of the flow direction, ![](../graphics/stm_eqn00483.gif) (in [Equation 4.3.2&#8211;4](04s03a104.md)), this becomes

![](../graphics/stm_eqn05632.gif)

For simplicity of notation we write

![](../graphics/stm_eqn05633.gif)so that this equation is

![](../graphics/stm_eqn05634.gif)

Taking the inner product of this equation with itself gives

![](../graphics/stm_eqn05635.gif)where

![](../graphics/stm_eqn05636.gif)

The Mises equivalent stress, *q*, must satisfy the uniaxial form defined in [Equation 4.3.2&#8211;7](04s03a104.md), so that from [Equation 4.3.2&#8211;11](04s03a104.md),

![](../graphics/stm_eqn05637.gif)

This is a nonlinear equation for ![](../graphics/stm_eqn05638.gif) in the general case when ![](../graphics/stm_eqn05629.gif) depends on the equivalent plastic strain (that is, when the material is rate-dependent, or when there is nonzero work hardening). (It is linear in ![](../graphics/stm_eqn05639.gif) for rate-independent perfect plasticity.) We solve it by Newton's method:

![](../graphics/stm_eqn05640.gif)

![](../graphics/stm_eqn05641.gif)and we iterate until convergence is achieved.

Once ![](../graphics/stm_eqn05642.gif) is known, the solution is fully defined: using [Equation 4.3.2&#8211;5](04s03a104.md),

![](../graphics/stm_eqn05643.gif)and so, from [Equation 4.3.2&#8211;10](04s03a104.md),

![](../graphics/stm_eqn05644.gif)From [Equation 4.3.2&#8211;4](04s03a104.md),

![](../graphics/stm_eqn05645.gif)and thus, from [Equation 4.3.2&#8211;6](04s03a104.md),

![](../graphics/stm_eqn05646.gif)

For cases where three direct strain components are provided by the kinematic solution (that is, all but plane stress and uniaxial stress cases), [Equation 4.3.2&#8211;2](04s03a104.md) defines

![](../graphics/stm_eqn05647.gif)so that the solution is then fully defined.Plane stress

For plane stress ![](../graphics/stm_eqn02690.gif) is not defined by the kinematics but by the plane stress constraint

![](../graphics/stm_eqn05648.gif)

This additional equation (or equivalently ![](../graphics/stm_eqn05649.gif)) must be solved along with the yield condition and [Equation 4.3.2&#8211;9](04s03a104.md). The predicted third strain component

![](../graphics/stm_eqn05650.gif)where

![](../graphics/stm_eqn05651.gif)and

![](../graphics/stm_eqn05652.gif)serves as an initial guess toward the final value of ![](../graphics/stm_eqn05653.gif) that enables (with the correct plastic straining) the plane stress condition to be satisfied.Uniaxial stress

For cases with only one direct strain component defined by the kinematic solution (uniaxial deformation), we require

![](../graphics/stm_eqn05654.gif)so that

![](../graphics/stm_eqn05655.gif)
### Material stiffness

For this simple plasticity model the material stiffness matrix can be derived without the need for matrix inversion (as was needed in the general case described in "Integration of plasticity models,"  Section 4.2.2), as follows.

Taking the variation of [Equation 4.3.2&#8211;10](04s03a104.md) with respect to all quantities at the end of the increment gives

![](../graphics/stm_eqn05656.gif)

Now, from [Equation 4.3.2&#8211;5](04s03a104.md),

![](../graphics/stm_eqn05657.gif)and, from [Equation 4.3.2&#8211;11](04s03a104.md),

![](../graphics/stm_eqn05658.gif)

Combining these last two results,

![](../graphics/stm_eqn05659.gif)where

![](../graphics/stm_eqn05660.gif)

From the definition of ![](../graphics/stm_eqn05661.gif) (see [Equation 4.3.2&#8211;11](04s03a104.md)),

![](../graphics/stm_eqn05662.gif)and, hence,

![](../graphics/stm_eqn05663.gif)

Combining these results with [Equation 4.3.2&#8211;14](04s03a104.md) gives

![](../graphics/stm_eqn05664.gif)where ![](../graphics/stm_eqn05665.gif), ![](../graphics/stm_eqn05666.gif) is the fourth-order unit tensor, and

![](../graphics/stm_eqn05667.gif)

For all cases where three direct strains are defined by the kinematic solution, the material stiffness is completed by

![](../graphics/stm_eqn05668.gif)so since

![](../graphics/stm_eqn05669.gif)and

![](../graphics/stm_eqn05670.gif)we have

![](../graphics/stm_eqn05671.gif)Plane stress

For the plane stress case the material stiffness matrix is found by imposing

![](../graphics/stm_eqn05672.gif)on the general material stiffness matrix obtained for the plane strain case.Uniaxial stress

For the uniaxial stress case the material stiffness matrix is available directly from the variation of [Equation 4.3.2&#8211;13](04s03a104.md) as

![](../graphics/stm_eqn05673.gif)
### Reference

### Reference

"Classical metal plasticity,"  Section 23.2.1 of the Abaqus Analysis User's Guide