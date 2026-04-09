# 4.4.5 Mohr-Coulomb model

### 4.4.5 Mohr-Coulomb model

**Products: **Abaqus/Standard  Abaqus/Explicit

The Mohr-Coulomb failure or strength criterion has been widely used for geotechnical applications. Indeed, a large number of the routine design calculations in the geotechnical area are still performed using the Mohr-Coulomb criterion.

The Mohr-Coulomb criterion assumes that failure is controlled by the maximum shear stress and that this failure shear stress depends on the normal stress. This can be represented by plotting Mohr's circle for states of stress at failure in terms of the maximum and minimum principal stresses. The Mohr-Coulomb failure line is the best straight line that touch es these Mohr's circles ([Figure 4.4.5&#8211;1](04s04a117.md)). Thus, the Mohr-Coulomb criterion can be written as

![](../graphics/stm_eqn06275.gif)where ![](../graphics/stm_eqn01399.gif) is the shear stress, ![](../graphics/stm_eqn01110.gif) is the normal stress (negative in compression), *c* is the cohesion of the material, and ![](../graphics/stm_eqn00155.gif) is the material angle of friction.

Figure 4.4.5&#8211;1 Mohr-Coulomb failure criterion.

![](../graphics/cmohrcoulomb-yield-merid.png)From Mohr's circle,

![](../graphics/stm_eqn06276.gif)Substituting for ![](../graphics/stm_eqn01399.gif) and ![](../graphics/stm_eqn01110.gif), the Mohr-Coulomb criterion can be rewritten as

![](../graphics/stm_eqn06277.gif)where

![](../graphics/stm_eqn06278.gif)is half of the difference between the maximum and minimum principal stresses (and is, therefore, the maximum shear stress) and

![](../graphics/stm_eqn06279.gif)is the average of the maximum and minimum principal stresses (the normal stress). Thus, unlike the Drucker-Prager criterion, the Mohr-Coulomb criterion assumes that failure is independent of the value of the intermediate principal stress. The failure of typical geotechnical materials generally includes some small dependence on the intermediate principal stress, but the Mohr-Coulomb model is generally considered to be sufficiently accurate for most applications. This failure model has vertices in the deviatoric stress plane (see [Figure 4.4.5&#8211;2](04s04a117.md)).

Figure 4.4.5&#8211;2 Mohr-Coulomb model in the deviatoric plane.

![](../graphics/cmohrcoulomb-yield-devia-nls.png)

The constitutive model described here is an extension of the classical Mohr-Coulomb failure criterion. It is an elastoplastic model that uses a yield function of the Mohr-Coulomb form; this yield function includes isotropic cohesion hardening/softening. However, the model uses a flow potential that has a hyperbolic shape in the meridional stress plane and has no corners in the deviatoric stress space. This flow potential is then completely smooth and, therefore, provides a unique definition of the direction of plastic flow.
### Strain rate decomposition

An additive strain rate decomposition is assumed:

![](../graphics/stm_eqn06280.gif)where ![](../graphics/stm_eqn06115.gif) is the total strain rate, ![](../graphics/stm_eqn06116.gif) is the elastic strain rate, and ![](../graphics/stm_eqn06117.gif) is the inelastic (plastic) strain rate.
### Elastic behavior

The elastic behavior is modeled as linear and isotropic.
### Yield behavior

The Mohr-Coulomb criterion written above in terms of the maximum and minimum principal stresses can be written for general states of stress in terms of three stress invariants. These invariants are the equivalent pressure stress,

![](../graphics/stm_eqn06281.gif)the Mises equivalent stress,

![](../graphics/stm_eqn06282.gif)where ![](../graphics/stm_eqn05748.gif) is the stress deviator, defined as

![](../graphics/stm_eqn06283.gif)and the third invariant of deviatoric stress,

![](../graphics/stm_eqn06284.gif)The Mohr-Coulomb yield surface is then written as

![](../graphics/stm_eqn06285.gif)where ![](../graphics/stm_eqn06286.gif) is the friction angle of the material in the meridional stress plane, where ![](../graphics/stm_eqn01111.gif) is the temperature and ![](../graphics/stm_eqn02414.gif) are other predefined field variables; ![](../graphics/stm_eqn06287.gif) represents the evolution of the cohesion of the material in the form of isotropic hardening (or softening); ![](../graphics/stm_eqn06101.gif) is the equivalent plastic strain, its rate defined by the plastic work expression

![](../graphics/stm_eqn06288.gif)and ![](../graphics/stm_eqn06289.gif) is the Mohr-Coulomb deviatoric stress measure defined as

![](../graphics/stm_eqn06290.gif)where ![](../graphics/stm_eqn03471.gif) is the deviatoric polar angle ([Chen and Han, 1988](07s01a01-References.md)) defined as

![](../graphics/stm_eqn06291.gif)The friction angle of the material, ![](../graphics/stm_eqn00155.gif), also controls the shape of the yield surface in the deviatoric plane as shown in [Figure 4.4.5&#8211;3](04s04a117.md). The range of values the friction angle can have is 0 ![](../graphics/stm_eqn06292.gif) 90. In the case of ![](../graphics/stm_eqn06293.gif) 0 the Mohr-Coulomb model reduces to the pressure-independent Tresca model with a perfectly hexagonal deviatoric section. In the case of ![](../graphics/stm_eqn06293.gif) 90 the Mohr-Coulomb model would reduce to the "tension cutoff" Rankine model with a triangular deviatoric section and ![](../graphics/stm_eqn06294.gif) (this limiting case is not permitted within the Mohr-Coulomb model described here).

Figure 4.4.5&#8211;3 Mohr-Coulomb yield surface in meridional and deviatoric planes.

![](../graphics/cmohrcoulomb-yield-nls.png)
### Flow rule

Potential flow is assumed, so

![](../graphics/stm_eqn06295.gif)where *g* can be written as

![](../graphics/stm_eqn06296.gif)and *G* is the flow potential, chosen as a hyperbolic function in the meridional stress plane and a smooth elliptic function in the deviatoric stress plane:

![](../graphics/stm_eqn06297.gif)where ![](../graphics/stm_eqn06137.gif) is the dilation angle measured in the *p*&#8211;![](../graphics/stm_eqn06298.gif) plane at high confining pressure; ![](../graphics/stm_eqn06299.gif) is the initial cohesion yield stress; and ![](../graphics/stm_eqn02163.gif) is a parameter, referred to as the eccentricity, that defines the rate at which the function approaches the asymptote (the flow potential tends to a straight line as the eccentricity tends to zero). This flow potential, which is continuous and smooth in the meridional stress plane, ensures that the flow direction is defined uniquely in this plane. The function asymptotically approaches a linear flow potential at high confining pressure stress and intersects the hydrostatic pressure axis at 90. A family of hyperbolic potentials in the meridional stress plane is shown in [Figure 4.4.5&#8211;4](04s04a117.md).

Figure 4.4.5&#8211;4 Family of hyperbolic flow potentials in the meridional plane.

![](../graphics/cmohrcoulomb-flow-merid.png)

The flow potential is also continuous and smooth in the deviatoric stress plane (the ![](../graphics/stm_eqn06097.gif)-plane); we adopt the deviatoric elliptic function used by [Mentrey and Willam (1995)](07s01a01-References.md):

![](../graphics/stm_eqn06300.gif)where ![](../graphics/stm_eqn03471.gif) is the deviatoric polar angle defined previously, ![](../graphics/stm_eqn06301.gif), and *e* is a parameter that describes the "out-of-roundedness" of the deviatoric section in terms of the ratio between the shear stress along the extension meridian (![](../graphics/stm_eqn06302.gif)) and the shear stress along the compression meridian (![](../graphics/stm_eqn06303.gif)). The elliptic function has the value ![](../graphics/stm_eqn06304.gif) along the extension meridian and has the value ![](../graphics/stm_eqn06305.gif) along the compression meridian; this ensures that the flow potential matches the yield surface at the triaxial compression and extension in the deviatoric plane provided that *e* is defined appropriately (see further discussion later). Although the elliptic function is defined only in the sector ![](../graphics/stm_eqn06306.gif), the polar radius ![](../graphics/stm_eqn06307.gif) extends to all polar directions ![](../graphics/stm_eqn06308.gif) using the three-fold symmetry shown in [Figure 4.4.5&#8211;5](04s04a117.md).

Figure 4.4.5&#8211;5 Mentrey-Willam flow potential in the deviatoric plane.

![](../graphics/cmohrcoulomb-flow-devia-nls.png)

By default, the out-of-roundedness parameter, *e*, is dependent on the friction angle ![](../graphics/stm_eqn00155.gif); it is calculated by matching the flow potential to the yield surface in both triaxial tension and compression in the deviatoric plane:

![](../graphics/stm_eqn06309.gif)Alternatively, *e* can also be considered to be an independent material parameter; in this case the user can provide its value directly. Convexity and smoothness of the elliptic function requires that ![](../graphics/stm_eqn06310.gif). The upper limit, ![](../graphics/stm_eqn06311.gif) (or ![](../graphics/stm_eqn06293.gif) 0), leads to ![](../graphics/stm_eqn06312.gif), which describes the Mises circle in the deviatoric plane. The lower limit, ![](../graphics/stm_eqn06313.gif) (or ![](../graphics/stm_eqn06293.gif) 90), leads to ![](../graphics/stm_eqn06314.gif) and would describe the Rankine triangle in the deviatoric plane (this limiting case is not permitted within the Mohr-Coulomb model described here).

Flow in the meridional stress plane can be close to associated when the angle of friction, ![](../graphics/stm_eqn00155.gif), and the angle of dilation, ![](../graphics/stm_eqn02064.gif), are equal and the eccentricity parameter, ![](../graphics/stm_eqn02163.gif), is very small; however, flow in this plane is, in general, nonassociated. Flow in the deviatoric stress plane is always nonassociated. Therefore, the use of this Mohr-Coulomb model generally requires the solution of nonsymmetric equations.
### Reference

### Reference

"Mohr-Coulomb plasticity,"  Section 23.3.3 of the Abaqus Analysis User's Guide