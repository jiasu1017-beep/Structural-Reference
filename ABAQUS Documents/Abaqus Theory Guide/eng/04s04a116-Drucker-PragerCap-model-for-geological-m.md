# 4.4.4 Drucker-Prager/Cap model for geological materials

### 4.4.4 Drucker-Prager/Cap model for geological materials

**Products: **Abaqus/Standard  Abaqus/Explicit

The modified Drucker-Prager/Cap plasticity model in Abaqus is intended for geological materials that exhibit pressure-dependent yield. The yield surface includes two main segments: a shear failure surface, providing dominantly shearing flow, and a "cap," which intersects the equivalent pressure stress axis ([Figure 4.4.4&#8211;1](04s04a116.md)).

Figure 4.4.4&#8211;1 Modified Drucker-Prager/Cap model: yield surfaces in the *p*&#8211;*t* plane.

![](../graphics/ccapplas-yield-p-t-nls.png)There is a transition region between these segments, introduced to provide a smooth surface. The cap serves two main purposes: it bounds the yield surface in hydrostatic compression, thus providing an inelastic hardening mechanism to represent plastic compaction, and it helps to control volume dilatancy when the material yields in shear by providing softening as a function of the inelastic volume increase created as the material yields on the Drucker-Prager shear failure and transition yield surfaces.

The model uses associated flow in the cap region and nonassociated flow in the shear failure and transition regions. The model has been extended to include creep, with certain limitations that are outlined in this section. The creep behavior is envisaged as arising out of two possible mechanisms: one dominated by shear behavior and the other dominated by hydrostatic compression.
### Strain rate decomposition

A linear strain rate decomposition is assumed, so

![](../graphics/stm_eqn06218.gif)where ![](../graphics/stm_eqn06115.gif) is the total strain rate, ![](../graphics/stm_eqn06116.gif) is the elastic strain rate, ![](../graphics/stm_eqn06117.gif) is the inelastic (plastic) time-independent strain rate, and ![](../graphics/stm_eqn06118.gif) is the inelastic (creep) time-dependent strain rate.
### Elastic behavior

The elastic behavior can be modeled as linear elastic or by using the porous elasticity model including tensile strength, described in "Porous elasticity,"  Section 4.4.1. If creep has been defined, the elastic behavior must be modeled as linear.
### Plastic behavior

The yield/failure surfaces used with this model are written in terms of the three stress invariants: the equivalent pressure stress,

![](../graphics/stm_eqn06219.gif)the Mises equivalent stress,

![](../graphics/stm_eqn06220.gif)and the third invariant of deviatoric stress,

![](../graphics/stm_eqn05837.gif)where ![](../graphics/stm_eqn00522.gif) is the stress deviator, defined as

![](../graphics/stm_eqn06221.gif)

We also define the deviatoric stress measure

![](../graphics/stm_eqn06222.gif)where ![](../graphics/stm_eqn06223.gif) is a material parameter that may depend on temperature, ![](../graphics/stm_eqn01111.gif), and other predefined fields ![](../graphics/stm_eqn06224.gif). This measure of deviatoric stress is used because it allows matching of different stress values in tension and compression in the deviatoric plane, thereby providing flexibility in fitting experimental results and a smooth approximation to the Mohr-Coulomb surface. Since ![](../graphics/stm_eqn06225.gif) in uniaxial tension, ![](../graphics/stm_eqn06123.gif) in this case; since ![](../graphics/stm_eqn06226.gif) in uniaxial compression, ![](../graphics/stm_eqn06125.gif) in that case. When ![](../graphics/stm_eqn06208.gif), the dependence on the third deviatoric stress invariant is removed; and the Mises circle is recovered in the deviatoric plane: ![](../graphics/stm_eqn06125.gif). [Figure 4.4.4&#8211;2](04s04a116.md) shows the dependence of *t* on *K*. To ensure convexity of the yield surface, ![](../graphics/stm_eqn06121.gif).

Figure 4.4.4&#8211;2 Typical yield/flow surfaces in the deviatoric plane.

![](../graphics/cdruckprag-yield-dev-nls.png)

With this expression for the deviatoric stress measure, the Drucker-Prager failure surface is written as

![](../graphics/stm_eqn06227.gif)where ![](../graphics/stm_eqn06165.gif) is the material's angle of friction and ![](../graphics/stm_eqn06228.gif) is its cohesion (see [Figure 4.4.4&#8211;1](04s04a116.md)).

The cap yield surface has an elliptical shape with constant eccentricity in the meridional (*p*&#8211;*t*) plane ([Figure 4.4.4&#8211;1](04s04a116.md)) and also includes dependence on the third stress invariant in the deviatoric plane ([Figure 4.4.4&#8211;2](04s04a116.md)). The cap surface hardens or softens as a function of the volumetric plastic strain: volumetric plastic compaction (when yielding on the cap) causes hardening, while volumetric plastic dilation (when yielding on the shear failure surface) causes softening. The cap yield surface is written as

![](../graphics/stm_eqn06229.gif)where ![](../graphics/stm_eqn06230.gif) is a material parameter that controls the shape of the cap, ![](../graphics/stm_eqn06231.gif) is a small number that is defined below, and ![](../graphics/stm_eqn06232.gif) is an evolution parameter that represents the volumetric plastic strain driven hardening/softening. The hardening/softening law is a user-defined piecewise linear function relating the hydrostatic compression yield stress, ![](../graphics/stm_eqn06233.gif), and the corresponding volumetric inelastic (plastic and/or creep) strain, ![](../graphics/stm_eqn06234.gif) ([Figure 4.4.4&#8211;3](04s04a116.md)), where ![](../graphics/stm_eqn06235.gif).

Figure 4.4.4&#8211;3 Typical Cap hardening.

![](../graphics/ccapplas-hard.png)

The evolution parameter, ![](../graphics/stm_eqn06232.gif), is defined as

![](../graphics/stm_eqn06236.gif)

The parameter ![](../graphics/stm_eqn00904.gif) is a small number (typically 0.01 to 0.05) used to define a smooth transition surface between the shear failure surface and the cap:

![](../graphics/stm_eqn06237.gif)
### Flow rule

Plastic flow is defined by a flow potential that is associated on the cap and nonassociated on the failure yield surface and transition yield surfaces. The nonassociated nature of these surfaces stems from the shape of the flow potential in the meridional plane. The flow potential surface in the meridional plane is shown in [Figure 4.4.4&#8211;4](04s04a116.md).

Figure 4.4.4&#8211;4 Modified Drucker-Prager/Cap model: flow potential in the *p*&#8211;*t* plane.

![](../graphics/ccapplas-flow-p-t-nls.png)It is made up of an elliptical portion in the cap region that is identical to the cap yield surface:

![](../graphics/stm_eqn06238.gif)and another elliptical portion in the failure and transition regions that provides the nonassociated flow component in the model:

![](../graphics/stm_eqn06239.gif)The two elliptical portions, ![](../graphics/stm_eqn05852.gif) and ![](../graphics/stm_eqn06240.gif), form a continuous and smooth potential surface.

Nonassociated flow implies that the material stiffness matrix is not symmetric, so the unsymmetric solver should be invoked by the user. However, if the region of the model in which nonassociated inelastic deformation is occurring is confined, it is possible that a symmetric approximation to the material stiffness matrix will give an acceptable convergence rate: in such cases the unsymmetric solver may not be needed.
### Creep model

Classical "creep" behavior of materials that also exhibit plastic behavior according to the modified Drucker-Prager/Cap model can be defined.

The creep behavior in such materials is intimately tied to the plasticity behavior (through the definition of creep flow potentials and test data), so it is necessary to define the modified Drucker-Prager/Cap plasticity and hardening behavior as well. The elastic part of the behavior must be linear.

The rate-independent part of the plastic behavior is limited by the following restrictions:

![](../graphics/stm_eqn00905.gif)---that is, no transition zone is allowed;

K=1---that is, no third stress invariant effects are taken into account.In such a case, the deviatoric stress measure *t* is equal to the Mises equivalent stress, *q*, and the yield surface has a von Mises (circular) section in the deviatoric stress plane.Creep behavior

The built-in Abaqus creep laws or uniaxial laws defined through user subroutine CREEP can be used. The integration of the creep strain rate is first attempted explicitly, as described in "Rate-dependent metal plasticity (creep),"  Section 4.3.4. The integration is done by the backward Euler method (as described in "Rate-dependent metal plasticity (creep),"  Section 4.3.4) if the stability limit is exceeded, a geometrically nonlinear analysis is being performed, or plasticity becomes active.

In this model we assume the existence of two separate and independent creep mechanisms. One is a cohesion mechanism, which operates similarly to the Drucker-Prager creep model described in "Models for granular or polymer behavior,"  Section 4.4.2. The other is a consolidation mechanism, which operates similarly to the cap zone plasticity. We then have

![](../graphics/stm_eqn06241.gif)where ![](../graphics/stm_eqn06242.gif) is the creep strain rate due to the cohesion mechanism and ![](../graphics/stm_eqn06243.gif) is the creep strain rate due to the consolidation mechanism.

As described above, the cap surface hardens or softens as a function of the volumetric plastic strain and volumetric creep strain: volumetric inelastic compaction (when yielding on the cap or creeping through the consolidation mechanism) causes hardening, while volumetric plastic dilation (when yielding on the shear failure surface or creeping through the cohesion mechanism) causes softening. The separation between the two yield surfaces and the dominant regions for the two creep mechanisms are defined by the evolution parameter, ![](../graphics/stm_eqn06232.gif), which relates to the user-defined hydrostatic compression yield stress, ![](../graphics/stm_eqn06244.gif) ([Figure 4.4.4&#8211;3](04s04a116.md)).

The cohesion mechanism is active for all stress states that have a positive equivalent creep stress as explained below. The consolidation mechanism is active for all stress states in which the pressure is larger than ![](../graphics/stm_eqn06232.gif). [Figure 4.4.4&#8211;5](04s04a116.md) illustrates the active regions in this formulation.

Figure 4.4.4&#8211;5 Regions of activity of cohesion and consolidation creep mechanisms.

![](../graphics/ccapplas-active-creep-nls.png)

We adopt the notion of the existence of creep isosurfaces (or equivalent creep surfaces) of stress points that share the same creep "intensity," as measured by an equivalent creep stress. Consider the cohesion creep mechanism first. When the material plastifies, the equivalent creep surface should coincide with the yield surface; therefore, we define the equivalent creep surfaces by homogeneously scaling down the yield surface. In the *p*&#8211;*q* plane that translates into parallels to the yield surface, as depicted in [Figure 4.4.4&#8211;6](04s04a116.md). Abaqus requires that cohesion creep properties be measured in a uniaxial compression test.

Figure 4.4.4&#8211;6 Equivalent creep stress for cohesion creep.

![](../graphics/ccapplas-cohesion-creep-nls.png)The equivalent creep stress, ![](../graphics/stm_eqn06163.gif), is determined as the intersection of the equivalent creep surface with the uniaxial compression curve. As a result,

![](../graphics/stm_eqn06245.gif)where ![](../graphics/stm_eqn06165.gif) is the material angle of friction. [Figure 4.4.4&#8211;6](04s04a116.md) shows how the equivalent creep stress was determined. In uniaxial compression ![](../graphics/stm_eqn06246.gif); therefore, the uniaxial compression test line has a slope of 1/3. This approach has several consequences. One is that the cohesion creep strain rate is a function of both *q* and *p*. This allows the determination of realistic material properties in cases in which, due to high hydrostatic pressures, *q* is very high. If one looks at the yield strength of the material in this region to be a composite of cohesion strength and friction strength, this model corresponds to cohesion-determined creep. As a result, there is a cone in *p*&#8211;*q* space inside which there is no cohesion creep.

Next consider the consolidation creep mechanism. In this case we wish to make creep dependent on the hydrostatic pressure above a threshold value of ![](../graphics/stm_eqn06232.gif), with a smooth transition to the areas in which the mechanism is not active (![](../graphics/stm_eqn06247.gif)). Therefore, we define equivalent creep surfaces as constant pressure surfaces. In the *p*&#8211;*q* plane that translates into vertical lines. Abaqus requires that consolidation creep properties be measured in a hydrostatic compression test. The effective creep pressure, ![](../graphics/stm_eqn06248.gif), is then the point on the *p*-axis with a relative pressure

![](../graphics/stm_eqn06249.gif)This value is used in the uniaxial creep law. The equivalent volumetric creep strain rate produced by this type of law is defined as positive for a positive equivalent pressure. The internal tensor calculations in Abaqus will account for the fact that a positive pressure will produce negative (that is, compressive) volumetric creep components.Creep flow rule

The creep flow rules are derived from creep potentials, ![](../graphics/stm_eqn06167.gif), in such a way that

![](../graphics/stm_eqn06250.gif)where ![](../graphics/stm_eqn06169.gif) is the equivalent creep strain rate, which must be work conjugate to the equivalent creep stress:

![](../graphics/stm_eqn06251.gif)Since ![](../graphics/stm_eqn06118.gif) is obviously work conjugate to ![](../graphics/stm_eqn00596.gif), ![](../graphics/stm_eqn06172.gif) is a proportionality factor defined by

![](../graphics/stm_eqn06252.gif)with

![](../graphics/stm_eqn06253.gif)Cohesion creep

For the cohesion mechanism the creep potential is assumed to follow the same potential as the creep strain rate in the Drucker-Prager creep model ("Models for granular or polymer behavior,"  Section 4.4.2); that is, a hyperbolic function. This creep flow potential, which is continuous and smooth, ensures that the flow direction is always uniquely defined. The function approaches a parallel to the shear-failure yield surface asymptotically at high confining pressure stress and intersects the hydrostatic pressure axis at a right angle. A family of hyperbolic potentials in the meridional stress plane is shown in [Figure 4.4.4&#8211;7](04s04a116.md):

![](../graphics/stm_eqn06254.gif)where *d* is the material cohesion.

Figure 4.4.4&#8211;7 Creep potentials: cohesion mechanism.

![](../graphics/ccapplas-cohesion-p-q-nls.png)

The equivalent cohesion creep strain rate is then determined from the uniaxial law:

![](../graphics/stm_eqn06255.gif)[Equation 4.4.4&#8211;1](04s04a116.md), [Equation 4.4.4&#8211;3](04s04a116.md), and [Equation 4.4.4&#8211;5](04s04a116.md) produce the flow rule for this mechanism

![](../graphics/stm_eqn06256.gif)where

![](../graphics/stm_eqn06178.gif)and

![](../graphics/stm_eqn06257.gif)The proportionality factor, ![](../graphics/stm_eqn06172.gif), is not a constant in this model. Its expression indicates that it will become negative if

![](../graphics/stm_eqn06258.gif)It turns out that below this stress level, which for typical materials will be very low, the stress vector and the normal to the creep potential are pointing in opposite directions:

![](../graphics/stm_eqn06259.gif)which is equivalent to

![](../graphics/stm_eqn06260.gif)Thus, there is a small zone just outside the "no creep" cone for which this is the case. Consequently, creep data obtained within this zone should show a creep strain rate in the opposite direction from the applied stress at very low stress levels, which will usually not be the case. To overcome this difficulty, Abaqus will modify the creep data entered such that ![](../graphics/stm_eqn06184.gif). Therefore, you would not expect correspondence between calculated creep strains and measured creep properties in a region defined by

![](../graphics/stm_eqn06261.gif)This modification is usually not significant, since typical creep analyses have loads that are applied quickly, followed by long-term creep. Hence, the stress level for most of the analysis will usually be well beyond the modified zone.

An example of "slow" loading in which the approximation is visible is included in "Verification of creep integration,"  Section 3.2.6 of the Abaqus Benchmarks Guide. As is clear in the example, the effect of the approximation is small in spite of the fact that the load is ramped up over the step.

The equivalent cohesion creep strain rate is a function of both *q* and *p* through ![](../graphics/stm_eqn06163.gif). The creep potential is the von Mises circle in the deviatoric stress plane (the ![](../graphics/stm_eqn06097.gif)-plane). Although creep flow is associated in the deviatoric stress plane, the use of a creep potential different from the equivalent creep surface implies that creep flow is nonassociated.Consolidation creep

For the consolidation mechanism the creep potential is derived from the plastic potential of the cap zone ([Figure 4.4.4&#8211;8](04s04a116.md)):

![](../graphics/stm_eqn06262.gif)Recall that this mechanism is active only if ![](../graphics/stm_eqn06263.gif).

Figure 4.4.4&#8211;8 Creep potentials: consolidation mechanism.

![](../graphics/ccapplas-consolid-creep-nls.png)

The equivalent consolidation creep strain rate is then determined from the uniaxial law

![](../graphics/stm_eqn06264.gif)

[Equation 4.4.4&#8211;3](04s04a116.md) and [Equation 4.4.4&#8211;4](04s04a116.md) produce ![](../graphics/stm_eqn06265.gif); and [Equation 4.4.4&#8211;2](04s04a116.md), [Equation 4.4.4&#8211;3](04s04a116.md), and [Equation 4.4.4&#8211;6](04s04a116.md) produce the flow rule for this mechanism:

![](../graphics/stm_eqn06266.gif)Note that there is an equivalent pressure stress, ![](../graphics/stm_eqn06267.gif), work conjugate of the equivalent consolidation creep strain, which is different from the effective creep pressure, ![](../graphics/stm_eqn06268.gif). Such equivalent pressure stress is given by

![](../graphics/stm_eqn06269.gif)and has the characteristic that it reduces to the pressure in a hydrostatic compression test.

The creep potential is the von Mises circle in the deviatoric stress plane (the ![](../graphics/stm_eqn06097.gif)-plane). Creep flow is nonassociated in this mechanism.

This formulation is quite simplistic and ignores the effects of *q* on the creep function, ![](../graphics/stm_eqn06270.gif). The two creep mechanisms operate independently from each other. This implies that ![](../graphics/stm_eqn06271.gif) does not depend on ![](../graphics/stm_eqn06272.gif) and that ![](../graphics/stm_eqn06273.gif) does not depend on ![](../graphics/stm_eqn06274.gif). The only cross effects between both mechanisms are obtained through the dependency of ![](../graphics/stm_eqn06232.gif) on the volumetric creep from any of them.
### Reference

### Reference

"Modified Drucker-Prager/Cap model,"  Section 23.3.2 of the Abaqus Analysis User's Guide