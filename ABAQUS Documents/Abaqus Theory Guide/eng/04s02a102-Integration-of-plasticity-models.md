# 4.2.2 Integration of plasticity models

### 4.2.2 Integration of plasticity models

**Products: **Abaqus/Standard  Abaqus/Explicit

The plasticity models provided in Abaqus have been described in general terms in "Plasticity models: general discussion,"  Section 4.2.1. The only rate equations are the evolutionary rule for the hardening, the flow rule, and the strain rate decomposition. The simplest operator that provides unconditional stability for integration of rate equations is the backward Euler method: applying this method to the flow rule ([Equation 4.2.1&#8211;5](04s02a101.md)) gives

![](../graphics/stm_eqn05561.gif)and applying it to the hardening evolution equations, [Equation 4.2.1&#8211;6](04s02a101.md), gives

![](../graphics/stm_eqn05562.gif)

In these equations and throughout the remainder of this section any quantity not specifically associated with a time point is taken at the end of the increment (at time ![](../graphics/stm_eqn00438.gif)). The strain rate decomposition, [Equation 4.2.1&#8211;2](04s02a101.md), is integrated over a time increment as

![](../graphics/stm_eqn05563.gif)where ![](../graphics/stm_eqn00432.gif) is defined by the central difference operator:

![](../graphics/stm_eqn05564.gif)

We integrate the total values of each strain measure as the sum of the value of that strain at the start of the increment, rotated to account for rigid body motion during the increment, and the strain increment. The rotation to account for rigid body motion during the increment is defined approximately using the algorithm of [Hughes and Winget (1980)](07s01a01-References.md). This integration allows the strain rate decomposition to be integrated into

![](../graphics/stm_eqn05565.gif)

From a computational viewpoint the problem is now algebraic: we must solve the integrated equations of the constitutive model for the state at the end of the increment. The set of equations that define the algebraic problem are the strain decomposition, [Equation 4.2.2&#8211;3](04s02a102.md); the elasticity, [Equation 4.2.1&#8211;3](04s02a101.md); the integrated flow rule, [Equation 4.2.2&#8211;1](04s02a102.md); the integrated hardening laws, [Equation 4.2.2&#8211;2](04s02a102.md); and for rate independent models, the yield constraints

![](../graphics/stm_eqn05566.gif)for active systems (systems in which ![](../graphics/stm_eqn05554.gif) have ![](../graphics/stm_eqn05567.gif)).

We assume that the flow surface is sufficiently smooth so that its (second) derivatives with respect to stress and the hardening parameters are well-defined. This is generally true for the models in Abaqus: the exceptions occur at corners or vertices of the surfaces. These special cases are handled individually when they arise.

For some plasticity models the algebraic problem can be solved in closed form. For other models it is possible to reduce the problem to a one variable or a two variable problem that can then be solved to give the entire solution. For example, the Mises yield surface---which is generally used for isotropic metals, together with linear, isotropic elasticity---is a case for which the integrated problem can be solved exactly or in one variable (see "Isotropic elasto-plasticity,"  Section 4.3.2).

For other rate-independent models with a single yield system the algebraic problem is considered to be a problem in the components of ![](../graphics/stm_eqn05568.gif). Once these have been found---the elasticity---together with the integrated strain rate decomposition---define the stress. The flow rule then defines ![](../graphics/stm_eqn00851.gif) and the hardening laws define the increments in the hardening variables.

We now derive the equations for the Newton solution of the integrated problem for the case of rate-independent plasticity with a single yield system. The rate-dependent problem with a single yield system is solved in a similar way. For the particular cases of multiple, independent, yield systems (concrete and jointed material) particular techniques are used for this algebraic solution, taking advantage of the simplifications available in those particular models. The concrete model and its integration are described in "An inelastic constitutive model for concrete,"  Section 4.5.1, and the jointed material model is described in "Constitutive model for jointed materials,"  Section 4.5.4.

During the solution, the elasticity relationship and the integrated strain rate decomposition are satisfied exactly, so that

![](../graphics/stm_eqn05569.gif)where ![](../graphics/stm_eqn05570.gif) is the correction to the stress, ![](../graphics/stm_eqn05571.gif) is the correction to the plastic strain increments, and

![](../graphics/stm_eqn05572.gif)is the tangent elasticity matrix.

The hardening laws are also satisfied exactly (because the increments of the hardening parameters are defined from these laws) so that

![](../graphics/stm_eqn05573.gif)where ![](../graphics/stm_eqn01344.gif) is the correction to ![](../graphics/stm_eqn05574.gif) and ![](../graphics/stm_eqn05575.gif) is the correction to ![](../graphics/stm_eqn00851.gif).

This set of equations can be rewritten

![](../graphics/stm_eqn05576.gif)where

![](../graphics/stm_eqn05577.gif)and

![](../graphics/stm_eqn05578.gif)

The flow rule is not satisfied exactly until the solution has been found, so it gives the Newton equations

![](../graphics/stm_eqn05579.gif)

Using [Equation 4.2.2&#8211;5](04s02a102.md) and [Equation 4.2.2&#8211;6](04s02a102.md) allows these equations to be rewritten as

![](../graphics/stm_eqn05580.gif)where

![](../graphics/stm_eqn05581.gif)and

![](../graphics/stm_eqn05582.gif)

Likewise, the yield condition is not satisfied exactly during the Newton iteration, so

![](../graphics/stm_eqn05583.gif)

Using [Equation 4.2.2&#8211;5](04s02a102.md) and [Equation 4.2.2&#8211;6](04s02a102.md) in this equation gives

![](../graphics/stm_eqn05584.gif)where

![](../graphics/stm_eqn05585.gif)

We now eliminate ![](../graphics/stm_eqn05575.gif) between [Equation 4.2.2&#8211;7](04s02a102.md) and [Equation 4.2.2&#8211;8](04s02a102.md). Taking [Equation 4.2.2&#8211;7](04s02a102.md) along ![](../graphics/stm_eqn05586.gif) and using [Equation 4.2.2&#8211;8](04s02a102.md) gives

![](../graphics/stm_eqn05587.gif)where

![](../graphics/stm_eqn05588.gif)

Using this equation in [Equation 4.2.2&#8211;7](04s02a102.md) then gives

![](../graphics/stm_eqn05589.gif)where

![](../graphics/stm_eqn05590.gif)which is a set of linear equations solved for the ![](../graphics/stm_eqn05571.gif). The solution is then updated and the Newton loop continued until the flow equation and yield constraint are satisfied.

The solution for rate-dependent plasticity models with a single yield function is developed in the same way, the only differences being the lack of a yield constraint and the identification of ![](../graphics/stm_eqn00851.gif) with time.
### Tangent matrix

The tangent matrix for the material, ![](../graphics/stm_eqn05591.gif), is required when Abaqus/Standard is being used for implicit time integration and Newton's method is being used to solve the equilibrium equations. The matrix is obtained directly by taking variations of the integrated equations with respect to all solution parameters, and then solving for the relationship between ![](../graphics/stm_eqn00033.gif) and ![](../graphics/stm_eqn00399.gif). The procedure closely follows the derivation used above for the Newton solution: the result is the tangent matrix

![](../graphics/stm_eqn05592.gif)where

![](../graphics/stm_eqn05593.gif)
### Reference

### Reference

"Inelastic behavior,"  Section 23.1.1 of the Abaqus Analysis User's Guide