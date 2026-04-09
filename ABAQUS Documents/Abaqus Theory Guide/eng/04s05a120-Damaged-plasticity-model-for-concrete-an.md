# 4.5.2 Damaged plasticity model for concrete and other quasi-brittle materials

### 4.5.2 Damaged plasticity model for concrete and other quasi-brittle materials

**Products: **Abaqus/Standard  Abaqus/Explicit

This section describes the concrete damaged plasticity model provided in Abaqus for the analysis of concrete and other quasi-brittle materials. The material library in Abaqus also includes other constitutive models for concrete based on the smeared crack approach. These are the smeared crack model in Abaqus/Standard, described in "An inelastic constitutive model for concrete,"  Section 4.5.1, and the brittle cracking model in Abaqus/Explicit, described in "A cracking model for concrete and other brittle materials,"  Section 4.5.3.

The concrete damaged plasticity model is primarily intended to provide a general capability for the analysis of concrete structures under cyclic and/or dynamic loading. The model is also suitable for the analysis of other quasi-brittle materials, such as rock, mortar and ceramics; but it is the behavior of concrete that is used in the remainder of this section to motivate different aspects of the constitutive theory. Under low confining pressures, concrete behaves in a brittle manner; the main failure mechanisms are cracking in tension and crushing in compression. The brittle behavior of concrete disappears when the confining pressure is sufficiently large to prevent crack propagation. In these circumstances failure is driven by the consolidation and collapse of the concrete microporous microstructure, leading to a macroscopic response that resembles that of a ductile material with work hardening.

Modeling the behavior of concrete under large hydrostatic pressures is out of the scope of the plastic-damage model considered here. The constitutive theory in this section aims to capture the effects of irreversible damage associated with the failure mechanisms that occur in concrete and other quasi-brittle materials under fairly low confining pressures (less than four or five times the ultimate compressive stress in uniaxial compression loading). These effects manifest themselves in the following macroscopic properties:

different yield strengths in tension and compression, with the initial yield stress in compression being a factor of 10 or more higher than the initial yield stress in tension;

softening behavior in tension as opposed to initial hardening followed by softening in compression;

different degradation of the elastic stiffness in tension and compression;

stiffness recovery effects during cyclic loading; and

rate sensitivity, especially an increase in the peak strength with strain rate.

The plastic-damage model in Abaqus is based on the models proposed by Lubliner et al. ([1989](07s01a01-References.md)) and by Lee and Fenves ([1998](07s01a01-References.md)). The model is described in the remainder of this section. An overview of the main ingredients of the model is given first, followed by a more detailed discussion of the different aspects of the constitutive model.
### Overview

The main ingredients of the inviscid concrete damaged plasticity model are summarized below.Strain rate decomposition

An additive strain rate decomposition is assumed for the rate-independent model:

![](../graphics/stm_eqn05834.gif)where ![](../graphics/stm_eqn00118.gif) is the total strain rate, ![](../graphics/stm_eqn05527.gif) is the elastic part of the strain rate, and ![](../graphics/stm_eqn05528.gif) is the plastic part of the strain rate.Stress-strain relations

The stress-strain relations are governed by scalar damaged elasticity:

![](../graphics/stm_eqn06481.gif)where ![](../graphics/stm_eqn06482.gif) is the initial (undamaged) elastic stiffness of the material; ![](../graphics/stm_eqn06483.gif) is the degraded elastic stiffness; and *d* is the scalar stiffness degradation variable, which can take values in the range from zero (undamaged material) to one (fully damaged material). Damage associated with the failure mechanisms of the concrete (cracking and crushing) therefore results in a reduction in the elastic stiffness. Within the context of the scalar-damage theory, the stiffness degradation is isotropic and characterized by a single degradation variable, *d*. Following the usual notions of continuum damage mechanics, the effective stress is defined as

![](../graphics/stm_eqn06484.gif)The Cauchy stress is related to the effective stress through the scalar degradation relation:

![](../graphics/stm_eqn06485.gif)For any given cross-section of the material, the factor ![](../graphics/stm_eqn06486.gif) represents the ratio of the effective load-carrying area (i.e., the overall area minus the damaged area) to the overall section area. In the absence of damage, ![](../graphics/stm_eqn06487.gif), the effective stress ![](../graphics/stm_eqn06488.gif) is equivalent to the Cauchy stress, ![](../graphics/stm_eqn00033.gif). When damage occurs, however, the effective stress is more representative than the Cauchy stress because it is the effective stress area that is resisting the external loads. It is, therefore, convenient to formulate the plasticity problem in terms of the effective stress. As discussed later, the evolution of the degradation variable is governed by a set of hardening variables, ![](../graphics/stm_eqn06489.gif), and the effective stress; that is, ![](../graphics/stm_eqn06490.gif).Hardening variables

Damaged states in tension and compression are characterized independently by two hardening variables, ![](../graphics/stm_eqn06491.gif) and ![](../graphics/stm_eqn06492.gif), which are referred to as equivalent plastic strains in tension and compression, respectively. The evolution of the hardening variables is given by an expression of the form

![](../graphics/stm_eqn06493.gif) as described later in this section.

Microcracking and crushing in the concrete are represented by increasing values of the hardening variables. These variables control the evolution of the yield surface and the degradation of the elastic stiffness. They are also intimately related to the dissipated fracture energy required to generate micro-cracks. Yield function

The yield function, ![](../graphics/stm_eqn06494.gif), represents a surface in effective stress space, which determines the states of failure or damage. For the inviscid plastic-damage model

![](../graphics/stm_eqn06495.gif)The specific form of the yield function is described later in this section.Flow rule

Plastic flow is governed by a flow potential *G* according to the flow rule:

![](../graphics/stm_eqn06496.gif)where ![](../graphics/stm_eqn05794.gif) is the nonnegative plastic multiplier. The plastic potential is defined in the effective stress space. The specific form of the flow potential for the concrete damaged plasticity model is discussed later in this section. The model uses nonassociated plasticity, therefore requiring the solution of nonsymmetric equations.Summary

In summary, the elastic-plastic response of the concrete damaged plasticity model is described in terms of the effective stress and the hardening variables:

![](../graphics/stm_eqn06497.gif)where ![](../graphics/stm_eqn05794.gif) and *F* obey the Kuhn-Tucker conditions: ![](../graphics/stm_eqn06498.gif) The Cauchy stress is calculated in terms of the stiffness degradation variable, ![](../graphics/stm_eqn06499.gif), and the effective stress as

![](../graphics/stm_eqn06500.gif)

The constitutive relations for the elastic-plastic response, [Equation 4.5.2&#8211;1](04s05a120.md), are decoupled from the stiffness degradation response, [Equation 4.5.2&#8211;2](04s05a120.md), which makes the model attractive for an effective numerical implementation. The inviscid model summarized here can be extended easily to account for viscoplastic effects through the use of a viscoplastic regularization by permitting stresses to be outside the yield surface.
### Damage and stiffness degradation

The evolution equations of the hardening variables ![](../graphics/stm_eqn06501.gif) and ![](../graphics/stm_eqn06492.gif) are conveniently formulated by considering uniaxial loading conditions first and then extended to multiaxial conditions. Uniaxial conditions

It is assumed that the uniaxial stress-strain curves can be converted into stress versus plastic strain curves of the form

![](../graphics/stm_eqn06502.gif) where the subscripts *t* and *c* refer to tension and compression, respectively; ![](../graphics/stm_eqn06503.gif) and ![](../graphics/stm_eqn06504.gif) are the equivalent plastic strain rates, ![](../graphics/stm_eqn06505.gif) and ![](../graphics/stm_eqn06506.gif) are the equivalent plastic strains, ![](../graphics/stm_eqn01111.gif) is the temperature, and ![](../graphics/stm_eqn06507.gif) are other predefined field variables.

Under uniaxial loading conditions the effective plastic strain rates are given as

![](../graphics/stm_eqn06508.gif)In the remainder of this section we adopt the convention that ![](../graphics/stm_eqn05858.gif) is a positive quantity representing the magnitude of the uniaxial compression stress; that is, ![](../graphics/stm_eqn06509.gif).

As shown in [Figure 4.5.2&#8211;1](04s05a120.md), when the concrete specimen is unloaded from any point on the strain softening branch of the stress-strain curves, the unloading response is observed to be weakened: the elastic stiffness of the material appears to be damaged (or degraded). The degradation of the elastic stiffness is significantly different between tension and compression tests; in either case, the effect is more pronounced as the plastic strain increases. The degraded response of concrete is characterized by two independent uniaxial damage variables, ![](../graphics/stm_eqn06510.gif) and ![](../graphics/stm_eqn06511.gif), which are assumed to be functions of the plastic strains, temperature, and field variables:

![](../graphics/stm_eqn06512.gif)

Figure 4.5.2&#8211;1 Response of concrete to uniaxial loading in tension (a) and compression (b).

![](../graphics/cconcretedamaged-uniaxial.png)The uniaxial degradation variables are increasing functions of the equivalent plastic strains. They can take values ranging from zero, for the undamaged material, to one, for the fully damaged material.

If ![](../graphics/stm_eqn06513.gif) is the initial (undamaged) elastic stiffness of the material, the stress-strain relations under uniaxial tension and compression loading are, respectively:

![](../graphics/stm_eqn06514.gif)Under uniaxial loading cracks propagate in a direction transverse to the stress direction. The nucleation and propagation of cracks, therefore, causes a reduction of the available load-carrying area, which in turn leads to an increase in the effective stress. The effect is less pronounced under compressive loading since cracks run parallel to the loading direction; however, after a significant amount of crushing, the effective load-carrying area is also significantly reduced. The effective uniaxial cohesion stresses, ![](../graphics/stm_eqn06515.gif) and ![](../graphics/stm_eqn06516.gif) , are given as

![](../graphics/stm_eqn06517.gif)The effective uniaxial cohesion stresses determine the size of the yield (or failure) surface.Uniaxial cyclic conditions

Under uniaxial cyclic loading conditions the degradation mechanisms are quite complex, involving the opening and closing of previously formed micro-cracks, as well as their interaction. Experimentally, it is observed that there is some recovery of the elastic stiffness as the load changes sign during a uniaxial cyclic test. The stiffness recovery effect, also known as the "unilateral effect," is an important aspect of the concrete behavior under cyclic loading. The effect is usually more pronounced as the load changes from tension to compression, causing tensile cracks to close, which results in the recovery of the compressive stiffness.

The concrete damaged plasticity model assumes that the reduction of the elastic modulus is given in terms of a scalar degradation variable, *d*, as

![](../graphics/stm_eqn06518.gif)where ![](../graphics/stm_eqn06513.gif) is the initial (undamaged) modulus of the material.

This expression holds both in the tensile (![](../graphics/stm_eqn06519.gif)) and compressive (![](../graphics/stm_eqn06520.gif)) sides of the cycle. The stiffness reduction variable, *d*, is a function of the stress state and the uniaxial damage variables, ![](../graphics/stm_eqn06510.gif) and ![](../graphics/stm_eqn06511.gif). For the uniaxial cyclic conditions, Abaqus assumes that

![](../graphics/stm_eqn06521.gif)where ![](../graphics/stm_eqn06522.gif) and ![](../graphics/stm_eqn06523.gif) are functions of the stress state that are introduced to represent stiffness recovery effects associated with stress reversals. They are defined according to

![](../graphics/stm_eqn06524.gif)where

![](../graphics/stm_eqn06525.gif)The weight factors ![](../graphics/stm_eqn06526.gif) and ![](../graphics/stm_eqn06527.gif), which are assumed to be material properties, control the recovery of the tensile and compressive stiffness upon load reversal. To illustrate this, consider the example in [Figure 4.5.2&#8211;2](04s05a120.md), where the load changes from tension to compression. Assume that there was no previous compressive damage (crushing) in the material; that is, ![](../graphics/stm_eqn06528.gif) and ![](../graphics/stm_eqn06529.gif). Then

![](../graphics/stm_eqn06530.gif)In tension (![](../graphics/stm_eqn06531.gif)), ![](../graphics/stm_eqn06532.gif); thus, ![](../graphics/stm_eqn06533.gif) as expected. In compression (![](../graphics/stm_eqn06534.gif)), ![](../graphics/stm_eqn06535.gif), and ![](../graphics/stm_eqn06536.gif). If ![](../graphics/stm_eqn06537.gif), then ![](../graphics/stm_eqn06487.gif); therefore, the material fully recovers the compressive stiffness (which in this case is the initial undamaged stiffness, ![](../graphics/stm_eqn06538.gif)). If, on the other hand, ![](../graphics/stm_eqn06539.gif), then ![](../graphics/stm_eqn06533.gif) and there is no stiffness recovery. Intermediate values of ![](../graphics/stm_eqn06527.gif) result in partial recovery of the stiffness.

Figure 4.5.2&#8211;2 Illustration of the effect of the compression stiffness recovery parameter ![](../graphics/stm_eqn06527.gif).

![](../graphics/cconcretedamaged-wc-nls.png)

The evolution equations of the equivalent plastic strains are also generalized to the uniaxial cyclic conditions as

![](../graphics/stm_eqn06540.gif)which clearly reduces to [Equation 4.5.2&#8211;4](04s05a120.md) during the tensile and compressive phases of the cycle.Multiaxial conditions

The evolution equations for the hardening variables must be extended for the general multiaxial conditions. Based on Lee and Fenves ([1998](07s01a01-References.md)) we assume that the equivalent plastic strain rates are evaluated according to the expressions

![](../graphics/stm_eqn06541.gif)where ![](../graphics/stm_eqn06542.gif) and ![](../graphics/stm_eqn06543.gif) are, respectively, the maximum and minimum eigenvalues of the plastic strain rate tensor ![](../graphics/stm_eqn05528.gif) and

![](../graphics/stm_eqn06544.gif)is a stress weight factor that is equal to one if all principal stresses ![](../graphics/stm_eqn06545.gif), are positive and equal to zero if they are negative. The Macauley bracket ![](../graphics/stm_eqn06546.gif) is defined by ![](../graphics/stm_eqn06547.gif). In uniaxial loading conditions [Equation 4.5.2&#8211;8](04s05a120.md) reduces to the uniaxial definitions [Equation 4.5.2&#8211;4](04s05a120.md) and [Equation 4.5.2&#8211;7](04s05a120.md), since ![](../graphics/stm_eqn06548.gif) in tension, and ![](../graphics/stm_eqn06549.gif) in compression.

If the eigenvalues of the plastic strain rate tensor (![](../graphics/stm_eqn06550.gif)) are ordered such that ![](../graphics/stm_eqn06551.gif), the evolution equation for general multiaxial stress conditions can be expressed in the following matrix form:

![](../graphics/stm_eqn06552.gif)where

![](../graphics/stm_eqn06553.gif)and

![](../graphics/stm_eqn06554.gif)Elastic stiffness degradation

The plastic-damage concrete model assumes that the elastic stiffness degradation is isotropic and characterized by a single scalar variable, *d*:

![](../graphics/stm_eqn06555.gif)The definition of the scalar degradation variable *d* must be consistent with the uniaxial monotonic responses (![](../graphics/stm_eqn06510.gif) and ![](../graphics/stm_eqn06511.gif)), and it should also should capture the complexity associated with the degradation mechanisms under cyclic loading. For the general multiaxial stress conditions Abaqus assumes that

![](../graphics/stm_eqn06556.gif)similar to the uniaxial cyclic case, only that ![](../graphics/stm_eqn06522.gif) and ![](../graphics/stm_eqn06523.gif) are now given in terms of the function ![](../graphics/stm_eqn06557.gif) as

![](../graphics/stm_eqn06558.gif)

It can be easily verified that [Equation 4.5.2&#8211;10](04s05a120.md) for the scalar degradation variable is consistent with the uniaxial response.

The experimental observation in most quasi-brittle materials, including concrete, is that the compressive stiffness is recovered upon crack closure as the load changes from tension to compression. On the other hand, the tensile stiffness is not recovered as the load changes from compression to tension once crushing micro-cracks have developed. This behavior, which corresponds to ![](../graphics/stm_eqn06559.gif) and ![](../graphics/stm_eqn06537.gif), is the default used by Abaqus. [Figure 4.5.2&#8211;3](04s05a120.md) illustrates a uniaxial load cycle assuming the default behavior.

Figure 4.5.2&#8211;3 Uniaxial load cycle (tension-compression-tension) assuming default values for the stiffness recovery factors: ![](../graphics/stm_eqn06559.gif) and ![](../graphics/stm_eqn06537.gif).

![](../graphics/cconcretedamaged-cycle.png)
### Yield condition

The plastic-damage concrete model uses a yield condition based on the yield function proposed by Lubliner et al. ([1989](07s01a01-References.md)) and incorporates the modifications proposed by Lee and Fenves ([1998](07s01a01-References.md)) to account for different evolution of strength under tension and compression. In terms of effective stresses the yield function takes the form

![](../graphics/stm_eqn06560.gif)where ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01256.gif) are dimensionless material constants;

![](../graphics/stm_eqn06561.gif)is the effective hydrostatic pressure;

![](../graphics/stm_eqn06562.gif)is the Mises equivalent effective stress;

![](../graphics/stm_eqn06563.gif)is the deviatoric part of the effective stress tensor ![](../graphics/stm_eqn06488.gif); and ![](../graphics/stm_eqn06564.gif) is the algebraically maximum eigenvalue of ![](../graphics/stm_eqn06488.gif). The function ![](../graphics/stm_eqn06565.gif) is given as

![](../graphics/stm_eqn06566.gif)where ![](../graphics/stm_eqn06515.gif) and ![](../graphics/stm_eqn06516.gif) are the effective tensile and compressive cohesion stresses, respectively.

In biaxial compression, with ![](../graphics/stm_eqn06567.gif), [Equation 4.5.2&#8211;11](04s05a120.md) reduces to the well-known Drucker-Prager yield condition. The coefficient ![](../graphics/stm_eqn00904.gif) can be determined from the initial equibiaxial and uniaxial compressive yield stress, ![](../graphics/stm_eqn06568.gif) and ![](../graphics/stm_eqn06569.gif), as

![](../graphics/stm_eqn06570.gif)Typical experimental values of the ratio ![](../graphics/stm_eqn06571.gif) for concrete are in the range from 1.10 to 1.16, yielding values of ![](../graphics/stm_eqn00904.gif) between 0.08 and 0.12 ([Lubliner et al., 1989](07s01a01-References.md)).

The coefficient ![](../graphics/stm_eqn01256.gif) enters the yield function only for stress states of triaxial compression, when ![](../graphics/stm_eqn06572.gif) This coefficient can be determined by comparing the yield conditions along the tensile and compressive meridians. By definition, the *tensile meridian* (TM) is the locus of stress states satisfying the condition ![](../graphics/stm_eqn06573.gif) and the *compressive meridian* (CM) is the locus of stress states such that ![](../graphics/stm_eqn06574.gif), where ![](../graphics/stm_eqn06575.gif), ![](../graphics/stm_eqn06576.gif), and ![](../graphics/stm_eqn06577.gif) are the eigenvalues of the effective stress tensor. It can be easily shown that ![](../graphics/stm_eqn06578.gif) and ![](../graphics/stm_eqn06579.gif), along the tensile and compressive meridians, respectively. With ![](../graphics/stm_eqn06580.gif) the corresponding yield conditions are

![](../graphics/stm_eqn06581.gif)

![](../graphics/stm_eqn06582.gif)Let ![](../graphics/stm_eqn06583.gif) for any given value of the hydrostatic pressure ![](../graphics/stm_eqn06584.gif) with ![](../graphics/stm_eqn06580.gif); then

![](../graphics/stm_eqn06585.gif)The fact that ![](../graphics/stm_eqn06586.gif) is constant does not seem to be contradicted by experimental evidence ([Lubliner et al., 1989](07s01a01-References.md)). The coefficient ![](../graphics/stm_eqn01256.gif) is, therefore, evaluated as

![](../graphics/stm_eqn06587.gif)A value of ![](../graphics/stm_eqn06588.gif), which is typical for concrete, gives ![](../graphics/stm_eqn06589.gif)

If ![](../graphics/stm_eqn06590.gif), the yield conditions along the tensile and compressive meridians reduce to

![](../graphics/stm_eqn06591.gif)

![](../graphics/stm_eqn06592.gif)Let ![](../graphics/stm_eqn06593.gif) for any given value of the hydrostatic pressure ![](../graphics/stm_eqn06584.gif) with ![](../graphics/stm_eqn06590.gif); then

![](../graphics/stm_eqn06594.gif)

Typical yield surfaces are shown in [Figure 4.5.2&#8211;4](04s05a120.md) in the deviatoric plane and in [Figure 4.5.2&#8211;5](04s05a120.md) for plane-stress conditions.

Figure 4.5.2&#8211;4 Yield surfaces in the deviatoric plane, corresponding to different values of ![](../graphics/stm_eqn06586.gif).

![](../graphics/cconcretedamaged-deviatoric.png)

Figure 4.5.2&#8211;5 Yield surface in plane stress.

![](../graphics/cconcretedamaged-yield-nls.png)
### Flow rule

The plastic-damage model assumes nonassociated potential flow,

![](../graphics/stm_eqn06595.gif)The flow potential *G* chosen for this model is the Drucker-Prager hyperbolic function:

![](../graphics/stm_eqn06596.gif)where ![](../graphics/stm_eqn02064.gif) is the dilation angle measured in the *p&#8211;q* plane at high confining pressure; ![](../graphics/stm_eqn06597.gif) is the uniaxial tensile stress at failure; and ![](../graphics/stm_eqn02163.gif) is a parameter, referred to as the eccentricity, that defines the rate at which the function approaches the asymptote (the flow potential tends to a straight line as the eccentricity tends to zero). This flow potential, which is continuous and smooth, ensures that the flow direction is defined uniquely. The function asymptotically approaches the linear Drucker-Prager flow potential at high confining pressure stress and intersects the hydrostatic pressure axis at 90. See "Models for granular or polymer behavior,"  Section 4.4.2, for further discussion of this potential.

Because plastic flow is nonassociated, the use of the plastic-damage concrete model requires the solution of nonsymmetric equations.
### Viscoplastic regularization

Material models exhibiting softening behavior and stiffness degradation often lead to severe convergence difficulties in implicit analysis programs. Some of these convergence difficulties can be overcome by using a viscoplastic regularization of the constitutive equations. The concrete damaged plasticity model can be regularized using viscoplasticity, therefore permitting stresses to be outside of the yield surface. We use a generalization of the Duvaut-Lions regularization, according to which the viscoplastic strain rate tensor, ![](../graphics/stm_eqn06598.gif), is defined as

![](../graphics/stm_eqn06599.gif)Here ![](../graphics/stm_eqn01087.gif) is the viscosity parameter representing the relaxation time of the viscoplastic system and ![](../graphics/stm_eqn05870.gif) is the plastic strain evaluated in the inviscid backbone model.

Similarly, a viscous stiffness degradation variable, ![](../graphics/stm_eqn06600.gif), for the viscoplastic system is defined as

![](../graphics/stm_eqn06601.gif)where *d* is the degradation variable evaluated in the inviscid backbone model. The stress-strain relation of the viscoplastic model is given as

![](../graphics/stm_eqn06602.gif)

The solution of the viscoplastic system relaxes to that of the inviscid case as ![](../graphics/stm_eqn06603.gif), where *t* represents time. Using the viscoplastic regularization with a small value for the viscosity parameter (small compared to the characteristic time increment) usually helps improve the rate of convergence of the model in the softening regime, without compromising results.
### Integration of the model

The model is integrated using the backward Euler method generally used with the plasticity models in Abaqus. A material Jacobian consistent with this integration operator is used for the equilibrium iterations.