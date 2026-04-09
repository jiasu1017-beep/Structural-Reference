# 5.2.3 Coulomb friction

### 5.2.3 Coulomb friction

**Products: **Abaqus/Standard  Abaqus/Explicit

An extended version of the classical isotropic Coulomb friction model is provided in Abaqus for use with all contact analysis cababilities. The extensions include an additional limit on the allowable shear stress, anisotropy, and the definition of a "secant" friction coefficient.

The standard Coulomb friction model assumes that no relative motion occurs if the equivalent frictional stress

![](../graphics/stm_eqn07681.gif)is less than the critical stress, ![](../graphics/stm_eqn07682.gif), which is proportional to the contact pressure, ![](../graphics/stm_eqn02386.gif), in the form

![](../graphics/stm_eqn07683.gif)where ![](../graphics/stm_eqn01087.gif) is the friction coefficient that can be defined as a function of the contact pressure, ![](../graphics/stm_eqn02386.gif); the slip rate, ![](../graphics/stm_eqn07684.gif); the average surface temperature at the contact point; and the average field variables at the contact point. Rate-dependent friction cannot be used in a static Riks analysis since velocity is not defined. In Abaqus it is possible to put a limit on the critical stress:

![](../graphics/stm_eqn07685.gif)where ![](../graphics/stm_eqn07686.gif) is user-specified. If the equivalent stress is at the critical stress ![](../graphics/stm_eqn07687.gif), slip can occur. If the friction is isotropic, the direction of the slip and the frictional stress coincide, which is expressed in the form

![](../graphics/stm_eqn07688.gif)where ![](../graphics/stm_eqn07689.gif) is the slip rate in direction ![](../graphics/stm_eqn07690.gif) and ![](../graphics/stm_eqn07691.gif) is the magnitude of the slip velocity,

![](../graphics/stm_eqn07692.gif)As will be shown later, the same laws can be used for anisotropic friction after some simple transformations.

The above behavior can be modeled in Abaqus/Standard in two different ways. By default, the condition of no relative motion is approximated by stiff elastic behavior. The stiffness is chosen such that the relative motion from the position of zero shear stress is bounded by a value ![](../graphics/stm_eqn07693.gif). (In the Abaqus Analysis User's Guide ![](../graphics/stm_eqn07693.gif) is referred to as the allowable maximum elastic slip.) The critical slip value, ![](../graphics/stm_eqn07693.gif), can be specified by the user. If it is not specified by the user, ![](../graphics/stm_eqn07693.gif) is, by default, set to 0.5% of the average length of all contact elements in the model. It is worth noting that this approximate implementation method can also be considered an implementation of a nonlocal friction model; that is, a friction model for which the Coulomb condition is not applied pointwise but weighted over a small area with a so-called mollifying function ([Zhong, 1989](07s01a01-References.md)). See [Oden and Pires (1983)](07s01a01-References.md) for further discussion of nonlocal friction models.

Optionally, the relative motion in the absence of slip can be made exactly zero with the use of a Lagrange multiplier formulation. Although this procedure appears attractive because of the exact sticking constraint, it has two disadvantages:

The additional Lagrange multipliers increase the cost of the analysis.

The presence of rigid constraints tends to slow or sometimes prevent convergence of the Newton solution scheme used in Abaqus/Standard. This is likely to occur in areas where contact conditions change.A special case of friction in Abaqus/Standard is so-called rough friction, where it is assumed that there is no bound on the shear stress; that is, no relative motion can occur as long as the surfaces are in contact. Rough friction is implemented with the Lagrange multiplier method.

In Abaqus/Explicit the relative motion in the absence of slip is always equal to zero if the kinematic contact algorithm is used with hard tangential surface behavior; at the end of each increment the positions of the nodes on the contact surfaces are adjusted so that the relative motion is zero. With the penalty contact algorithm in Abaqus/Explicit the relative motion in the absence of slip is equal to the friction force divided by the penalty stiffness.
### Elastic stick formulation

In the elastic stick formulation in Abaqus/Standard, the "elastic" tangential slip ![](../graphics/stm_eqn07694.gif) is defined as the *reversible* relative tangential motion from the point of zero shear stress. The elastic slip is related to the interface shear stress with the relation

![](../graphics/stm_eqn07695.gif)where ![](../graphics/stm_eqn01861.gif) is the (current) "stiffness in stick," which follows from the relation

![](../graphics/stm_eqn07696.gif)Since ![](../graphics/stm_eqn07682.gif) may be dependent on contact pressure, slip rate, average surface temperature at the contact point, and field variables, ![](../graphics/stm_eqn01861.gif) may change during the analysis. The behavior remains elastic as long as the equivalent stress does not exceed the critical stress; hence,

![](../graphics/stm_eqn07697.gif)Consistent linearization of this expression yields

![](../graphics/stm_eqn07698.gif)The contributions from the contact pressure are nonsymmetric for the second case. Since the slip rate is zero in the elastic stick formulation, derivatives with respect to the slip velocity are not needed.

The above expressions hold if the equivalent shear stress remains less than the critical stress. If the equivalent stress exceeds the critical stress, slip must be taken into consideration so that the condition ![](../graphics/stm_eqn07699.gif) is satisfied. Let the starting situation be characterized by the elastic slip ![](../graphics/stm_eqn07700.gif). The critical stress at the end of the increment follows from the contact pressure, ![](../graphics/stm_eqn02386.gif), and the slip rate, ![](../graphics/stm_eqn07701.gif).

Let the (as yet unknown) elastic slip at the end of the increment be ![](../graphics/stm_eqn07694.gif) and the slip increment be ![](../graphics/stm_eqn07702.gif). Consistency requires that

![](../graphics/stm_eqn07703.gif)and the shear stress at the end of the increment follows from the elasticity relation,

![](../graphics/stm_eqn07704.gif)The slip increment is related to the stress at the end of the increment with the backward difference approach:

![](../graphics/stm_eqn07705.gif)With these equations and the critical stress equality ![](../graphics/stm_eqn07706.gif) it is possible to solve for ![](../graphics/stm_eqn07694.gif), ![](../graphics/stm_eqn07702.gif), and ![](../graphics/stm_eqn07707.gif). Elimination of ![](../graphics/stm_eqn07694.gif) and ![](../graphics/stm_eqn07702.gif) from the above equations yields,

![](../graphics/stm_eqn07708.gif)or

![](../graphics/stm_eqn07709.gif)It is convenient to define the "elastic predictor strain"

![](../graphics/stm_eqn07710.gif)which simplifies the expression for the stress to

![](../graphics/stm_eqn07711.gif)Substitution in the critical stress equality yields

![](../graphics/stm_eqn07712.gif)where

![](../graphics/stm_eqn07713.gif)Substitution in the expression for ![](../graphics/stm_eqn07707.gif) and introduction of the normalized slip direction ![](../graphics/stm_eqn07714.gif) furnishes the final result

![](../graphics/stm_eqn07715.gif)Here ![](../graphics/stm_eqn07682.gif) is a function of the slip rate, which is obtained with

![](../graphics/stm_eqn07716.gif)where ![](../graphics/stm_eqn00883.gif) is the time increment in a static analysis. In the case of dynamics with the Hilber-Hughes-Taylor time integration operator, ![](../graphics/stm_eqn00883.gif) is scaled by the Hilber-Hughes-Taylor time integration operator parameters, ![](../graphics/stm_eqn01256.gif) and ![](../graphics/stm_eqn01219.gif).

For the iterative solution scheme this equation must be linearized. Some straightforward algebra yields

![](../graphics/stm_eqn07717.gif)With the expression for the equivalent slip the final result is

![](../graphics/stm_eqn07718.gif) In this case the unsymmetric terms may have a strong effect on the speed of convergence of the Newton scheme. Hence, use of the unsymmetric equations solver is strongly recommended for the analysis of problems in which sliding friction occurs. In the case of dynamics with the Hilber-Hughes-Taylor time integration operator, ![](../graphics/stm_eqn00883.gif) is scaled by the Hilber-Hughes-Taylor time integration operator parameters.
### Frictional stress due to forced sliding in static analysis

If the user specifies different velocities for two bodies in contact as a predefined field, it is assumed that the slip velocity follows from the prescribed motion and is independent of the displacement values. The frictional stresses then follow from

![](../graphics/stm_eqn07719.gif) where

![](../graphics/stm_eqn07720.gif) and

![](../graphics/stm_eqn07721.gif) ![](../graphics/stm_eqn07722.gif) are the tangential slip velocities derived from the user-defined fields (![](../graphics/stm_eqn07723.gif)).
### Friction contributions for complex eigenvalue extraction analysis

At the contact nodes at which the velocity differential is imposed, the linearized shear stress can be expressed in the following form:

![](../graphics/stm_eqn07724.gif)In the equation above the first term is generated by the friction forces acting in the direction perpendicular to the direction of slip. The third term exists if the friction coefficient depends on velocity. In the complex eigenvalue extraction analysis both terms contribute to the damping matrix. The second term contributes to the stiffness matrix.
### Viscous stick formulation for steady-state transport

For steady-state transport a viscous stick formulation is used. In this case the "viscous" tangential slip rate, ![](../graphics/stm_eqn07725.gif), is related to the interface shear stress by

![](../graphics/stm_eqn07726.gif) where ![](../graphics/stm_eqn07727.gif) is the "stick viscosity," which follows from the relation

![](../graphics/stm_eqn07728.gif) The allowable viscous slip is defined as a fraction of the relative tangential velocity

![](../graphics/stm_eqn07729.gif)where ![](../graphics/stm_eqn07730.gif) is a user-defined slip tolerance, ![](../graphics/stm_eqn07731.gif) is the angular spinning velocity, and ![](../graphics/stm_eqn03159.gif) is the radius of a point on the contact surface in the undeformed configuration.
### Exact stick formulation

In Abaqus/Standard Lagrange multipliers are used to enforce exact sticking conditions. A constraint term enforced with Lagrange multipliers ![](../graphics/stm_eqn07732.gif) is added to the virtual work statement:

![](../graphics/stm_eqn07733.gif)where ![](../graphics/stm_eqn07732.gif) is a Lagrange multiplier. By taking the rate of change of [Equation 5.2.3&#8211;4](05s02a137.md), the rate of virtual work is obtained:

![](../graphics/stm_eqn07734.gif)where the last term results from a nonlinear relation between nodal displacements and relative motion ![](../graphics/stm_eqn05225.gif). This term is nonzero only for contact with finite sliding (see "Finite-sliding interaction between deformable bodies,"  Section 5.1.2, and "Finite-sliding interaction between a deformable and a rigid body,"  Section 5.1.3).

To obtain a complete formulation, a relationship between ![](../graphics/stm_eqn07735.gif), ![](../graphics/stm_eqn07736.gif), and ![](../graphics/stm_eqn07707.gif) must be defined. For sticking conditions a suitable relation is

![](../graphics/stm_eqn07737.gif)with ![](../graphics/stm_eqn06810.gif) a reference stiffness selected internally in Abaqus. The reference stiffness can be considered to model a spring that is in parallel to the sticking constraint. Since the constraint prevents relative motion, the reference stiffness has no physical significance and is added only to eliminate zero terms on the diagonal of the stiffness matrix that could cause equation solver problems. The variational and rate forms of the equation for ![](../graphics/stm_eqn07707.gif) are readily obtained as

![](../graphics/stm_eqn07738.gif)Substitution in [Equation 5.2.3&#8211;5](05s02a137.md) yields

![](../graphics/stm_eqn07739.gif)

If the element is slipping, ![](../graphics/stm_eqn07735.gif) can take an arbitrary value. Consequently the terms involving ![](../graphics/stm_eqn07732.gif) in [Equation 5.2.3&#8211;4](05s02a137.md) and [Equation 5.2.3&#8211;5](05s02a137.md) vanish. With the backward difference method, the frictional stress is obtained as

![](../graphics/stm_eqn07740.gif)and the linearized form is

![](../graphics/stm_eqn07741.gif)The rate of virtual work can, hence, be written in the form

![](../graphics/stm_eqn07742.gif)Observe that for two-dimensional problems the term involving ![](../graphics/stm_eqn07743.gif) vanishes. In the case of dynamics with the Hilber-Hughes-Taylor time integration operator, ![](../graphics/stm_eqn00883.gif) is scaled by the Hilber-Hughes-Taylor time integration operator parameters.

To determine whether an element sticks or slips, the following tests are used. If the element is currently sticking, it is checked whether the magnitude of the frictional stress exceeds the critical value. Hence, if

![](../graphics/stm_eqn07744.gif)the state is changed to slipping.

If the element is slipping, the direction of slip is compared with the frictional stress ![](../graphics/stm_eqn07745.gif) applied at the start of the iteration. If at the end of the iteration

![](../graphics/stm_eqn07746.gif)the state is changed to sticking.
### Anisotropic friction

In anisotropic friction the friction coefficients in the two (principal) directions are different; hence, the critical shear stresses are different:

![](../graphics/stm_eqn07747.gif)The two critical shear stresses are at the extreme points of the friction ellipse, given by the equation

![](../graphics/stm_eqn07748.gif)This suggests definition of the scaled shear stresses,

![](../graphics/stm_eqn07749.gif)where ![](../graphics/stm_eqn07750.gif) is the average friction coefficient defined by

![](../graphics/stm_eqn07751.gif)Hence, the (scaled) equivalent frictional stress is defined by

![](../graphics/stm_eqn07752.gif)and the average critical stress

![](../graphics/stm_eqn07753.gif)where ![](../graphics/stm_eqn07686.gif) is the user-specified limiting shear stress, which is applied to the scaled shear stresses. No slip will occur if ![](../graphics/stm_eqn07754.gif), and slip can occur if ![](../graphics/stm_eqn07755.gif).

If slip occurs, it is assumed that the direction of slip is governed by an associated slip law:

![](../graphics/stm_eqn07756.gif)Hence, scaled rates of slip are defined by

![](../graphics/stm_eqn07757.gif)and the (scaled) equivalent slip rate

![](../graphics/stm_eqn07758.gif)As a result, the direction of the scaled slip and the scaled shear stress coincide:

![](../graphics/stm_eqn07759.gif)Since these equations have exactly the same structure as the equations for isotropic friction, the same solution algorithms can be used to get the incremental and linearized equations in terms of the scaled stress and slip. The actual stresses are readily obtained from the scaled stresses with [Equation 5.2.3&#8211;10](05s02a137.md), and the linearized equations are scaled with the same factors.

In the anisotropic elastic stick formulation, it is assumed that the stiffness in stick in terms of the *scaled* stress and slip is constant:

![](../graphics/stm_eqn07760.gif)hence, the scaled stress is related to the scaled elastic slip by the relation

![](../graphics/stm_eqn07761.gif)

In terms of the actual stress and strain in the ![](../graphics/stm_eqn07762.gif)- and ![](../graphics/stm_eqn07763.gif)-directions, this implies

![](../graphics/stm_eqn07764.gif)with

![](../graphics/stm_eqn07765.gif)Hence, the anisotropy in terms of the stiffness in stick is more pronounced than the anisotropy in terms of critical stress.
### Viscous damping

In addition to the friction models described above, Abaqus allows for the definition of a "viscous" shear stress ![](../graphics/stm_eqn07766.gif) that is proportional to the relative tangential velocity ![](../graphics/stm_eqn07722.gif). This viscous damping in the tangential direction occurs if

damping in the contact direction is included and the tangent fraction is nonzero; or

contact controls are used to stabilize rigid body modes automatically in multi-body contact analysis. The viscous damping stress is proportional to the tangential damping coefficient ![](../graphics/stm_eqn07767.gif), which is a function of the overclosure as follows:

![](../graphics/stm_eqn07768.gif)where ![](../graphics/stm_eqn07769.gif) is the value of the tangential damping coefficient at zero overclosure and ![](../graphics/stm_eqn02098.gif) is the fraction of the overclosure interval ![](../graphics/stm_eqn07645.gif) over which the damping coefficient is equal to ![](../graphics/stm_eqn07769.gif).

The virtual work contribution associated with the viscous shear stress is

![](../graphics/stm_eqn07770.gif)The contribution to the stiffness matrix for the Newton solution is given by the linearized form of the virtual work contribution:

![](../graphics/stm_eqn07771.gif)where

![](../graphics/stm_eqn07772.gif)

In static analysis the velocity is defined as the displacement increment divided by the time increment. Therefore, ![](../graphics/stm_eqn07773.gif), and the stiffness contribution reduces to

![](../graphics/stm_eqn07774.gif)

The previous expression also applies to dynamics with the backward Euler time integration operator. In the case of dynamics with the Hilber-Hughes-Taylor time integration operator, ![](../graphics/stm_eqn07775.gif) is defined by the dynamic time integration operator and the stiffness contribution can be written as

![](../graphics/stm_eqn07776.gif)where ![](../graphics/stm_eqn01256.gif) and ![](../graphics/stm_eqn01219.gif) are the Hilber-Hughes-Taylor time integration operator parameters. Viscous damping cannot be used in a Riks analysis since velocity is not defined.
### Reference

### Reference

"Frictional behavior,"  Section 37.1.5 of the Abaqus Analysis User's Guide