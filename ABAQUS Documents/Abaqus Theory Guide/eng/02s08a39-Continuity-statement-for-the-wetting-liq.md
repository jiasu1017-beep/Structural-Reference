# 2.8.4 Continuity statement for the wetting liquid phase in a porous medium

### 2.8.4 Continuity statement for the wetting liquid phase in a porous medium

**Product: **Abaqus/Standard

Abaqus/Standard provides capabilities for particular cases of fluid flow through a porous medium. These cases are associated with having a relatively incompressible wetting liquid present in the medium. The medium may be wholly or partially saturated, with this liquid. When the medium is only partially saturated the remainder of the voids is filled with another fluid. An example is a geotechnical problem, with soil containing water and air: continuity is written for the water phase.

The wetting liquid can attach to and, thus, be trapped by certain solid particles in the medium: this volume of trapped liquid attached to solid particles forms a "gel."

A porous medium is modeled approximately in Abaqus by attaching the finite element mesh to the solid phase. Liquid can flow through this mesh. A continuity equation is, therefore, required for the liquid, equating the rate of increase in liquid mass stored at a point to the rate of mass of liquid flowing into the point within the time increment. This continuity statement is defined in this section. It is written in a variational form as a basis for finite element approximation. The liquid flow is described by introducing Darcy's law or, alternatively, Forchheimer's law. The continuity equation is satisfied approximately in the finite element model by using excess wetting liquid pressure as the nodal variable (degree of freedom 8), interpolated over the elements. The equation is integrated in time by using the backward Euler approximation. The total derivative of this integrated variational statement of continuity with respect to the nodal variables is required for the Newton iterations used to solve the nonlinear, coupled, equilibrium and continuity equations. This expression is also derived in this section.

Consider a volume containing a fixed amount of solid matter. In the current configuration this volume occupies space *V* with surface *S*. In the reference configuration it occupied space ![](../graphics/stm_eqn01828.gif). Wetting liquid can flow through this volume: at any time the volume of such "free" liquid (liquid that can flow if driven by pressure) is written ![](../graphics/stm_eqn01829.gif). Wetting liquid can also become trapped in the volume, by absorption into the gel. The volume of such trapped liquid is written ![](../graphics/stm_eqn01830.gif).

The total mass of wetting liquid in the control volume is

![](../graphics/stm_eqn01831.gif)where ![](../graphics/stm_eqn01748.gif) is the mass density of the liquid.

The time rate of change of this mass of wetting liquid is

![](../graphics/stm_eqn01832.gif)

The mass of wetting liquid crossing the surface and entering the volume per unit time is

![](../graphics/stm_eqn01833.gif)where ![](../graphics/stm_eqn01834.gif) is the average velocity of the wetting liquid relative to the solid phase (the seepage velocity) and ![](../graphics/stm_eqn00483.gif) is the outward normal to *S*.

Equating the addition of liquid mass across the surface *S* to the rate of change of liquid mass within the volume *V* gives the wetting liquid mass continuity equation

![](../graphics/stm_eqn01835.gif)Using the divergence theorem and because the volume is arbitrary, this provides the pointwise equation

![](../graphics/stm_eqn01836.gif)

The equivalent weak form is

![](../graphics/stm_eqn01837.gif)where ![](../graphics/stm_eqn01838.gif) is an arbitrary, continuous, variational field. This statement can also be written on the reference volume:

![](../graphics/stm_eqn01839.gif)

In Abaqus/Standard this continuity statement is integrated approximately in time by the backward Euler formula, giving

![](../graphics/stm_eqn01840.gif)which, over the current volume, is

![](../graphics/stm_eqn01841.gif)We now drop the subscript ![](../graphics/stm_eqn01842.gif) by adopting the convention that any quantity not explicitly associated with a point in time is taken at ![](../graphics/stm_eqn01842.gif).

The divergence theorem allows the equation to be rewritten as

![](../graphics/stm_eqn01843.gif)where---for convenience---we have normalized the equation by the density of the liquid in the reference configuration, ![](../graphics/stm_eqn01777.gif).

Since ![](../graphics/stm_eqn01844.gif), this is the same as

![](../graphics/stm_eqn01845.gif)
### Constitutive behavior

The constitutive behavior for pore fluid flow is governed either by Darcy's law or by Forchheimer's law. Darcy's law is generally applicable to low fluid flow velocities, whereas Forchheimer's law is commonly used for situations involving higher flow velocities. Darcy's law can be thought of as a linearized version of Forchheimer's law. Darcy's law states that, under uniform conditions, the volumetric flow rate of the wetting liquid through a unit area of the medium, ![](../graphics/stm_eqn01846.gif), is proportional to the negative of the gradient of the piezometric head ([Bear, 1972](07s01a01-References.md)):

![](../graphics/stm_eqn01847.gif)where ![](../graphics/stm_eqn01848.gif) is the permeability of the medium and ![](../graphics/stm_eqn00155.gif) is the piezometric head, defined as

![](../graphics/stm_eqn01849.gif)where *z* is the elevation above some datum and *g* is the magnitude of the gravitational acceleration, which acts in the direction opposite to *z*. On the other hand, Forchheimer's law states that the negative of the gradient of the piezometric head is related to a quadratic function of the volumetric flow rate of the wetting liquid through a unit area of the medium ([Desai, 1975](07s01a01-References.md)):

![](../graphics/stm_eqn01850.gif)where ![](../graphics/stm_eqn01851.gif) is a "velocity coefficient" ([Tariq, 1987](07s01a01-References.md)). This nonlinear permeability can be defined to be dependent on the void ratio of the material. We see that, as the fluid velocity tends to zero, Forchheimer's law approaches Darcy's law. Also, if ![](../graphics/stm_eqn01852.gif), the two flow laws are identical.

![](../graphics/stm_eqn01848.gif) can be anisotropic and is a function of the saturation and void ratio of the material. ![](../graphics/stm_eqn01848.gif) has units of velocity (length/time). [Some authors refer to ![](../graphics/stm_eqn01848.gif) as the hydraulic conductivity ([Bear, 1972](07s01a01-References.md)) and define the permeability as

![](../graphics/stm_eqn01853.gif)where ![](../graphics/stm_eqn01854.gif) is the kinematic viscosity of the fluid (the ratio of the fluid's dynamic viscosity to its density).]

We assume that *g* is constant in magnitude and direction, so

![](../graphics/stm_eqn01855.gif)where ![](../graphics/stm_eqn01856.gif) is the gravitational acceleration (we assume that ![](../graphics/stm_eqn01748.gif) varies slowly with position).

The permeability of a particular fluid in a multiphase flow system depends on the saturation of the phase being considered and on the porosity of the medium. We assume these dependencies are separable, so

![](../graphics/stm_eqn01857.gif)where ![](../graphics/stm_eqn01858.gif) provides the dependency on saturation, with ![](../graphics/stm_eqn01859.gif) and ![](../graphics/stm_eqn01860.gif) is the permeability of the fully saturated medium.

The function ![](../graphics/stm_eqn01861.gif) can be defined by the user. [Nguyen and Durso (1983)](07s01a01-References.md) observe that, in steady flow through a partially saturated medium, the permeability varies with ![](../graphics/stm_eqn01862.gif). We, therefore, take ![](../graphics/stm_eqn01863.gif) by default.

Introducing the flow constitutive law allows the mass continuity equation ([Equation 2.8.4&#8211;1](02s08a39-Continuity-statement-for-the-wetting-liq.md)) to be written

![](../graphics/stm_eqn01864.gif)
### Volumetric strain in the liquid and grains

The bulk behavior of the grains was discussed in "Constitutive behavior in a porous medium,"  Section 2.8.3. From [Equation 2.8.3&#8211;2](02s08a38-Constitutive-behavior-in-a-porous-medium.md),

![](../graphics/stm_eqn01865.gif)Combining this with [Equation 2.8.1&#8211;4](02s08a36-Effective-stress-principle-for-porous-me.md) and neglecting all but first-order terms in small quantities, we obtain

![](../graphics/stm_eqn01866.gif)Using [Equation 2.8.3&#8211;1](02s08a38-Constitutive-behavior-in-a-porous-medium.md) and again neglecting second-order terms in small quantities, we obtain

![](../graphics/stm_eqn01867.gif)Combining this result with [Equation 2.8.3&#8211;4](02s08a38-Constitutive-behavior-in-a-porous-medium.md), and again approximating to first-order in small quantities,

![](../graphics/stm_eqn01868.gif)
### Saturation

Because ![](../graphics/stm_eqn01719.gif) measures pressure in the wetting liquid and we neglect the pressure in the other fluid phase in the medium (see "Effective stress principle for porous media,"  Section 2.8.1), the medium is fully saturated for ![](../graphics/stm_eqn01869.gif). Negative values of ![](../graphics/stm_eqn01719.gif) represent capillary effects in the medium. For ![](../graphics/stm_eqn01870.gif) it is known (see, for example, [Nguyen and Durso, 1983](07s01a01-References.md)) that, at a given value of capillary pressure, ![](../graphics/stm_eqn01871.gif), the saturation lies within certain limits. Typical forms of these limits are shown in [Figure 2.8.4&#8211;1](02s08a39-Continuity-statement-for-the-wetting-liq.md).

Figure 2.8.4&#8211;1 Typical liquid absorption and exsorption behavior.

![](../graphics/stmliquid-absorp-exsorp-nls.png) We write these limits as ![](../graphics/stm_eqn01872.gif), where ![](../graphics/stm_eqn01873.gif) is the limit at which absorption will occur (so that ![](../graphics/stm_eqn01874.gif)), and ![](../graphics/stm_eqn01875.gif) is the limit at which exsorption will occur, and thus ![](../graphics/stm_eqn01876.gif). We assume that these relationships are uniquely invertible and can, thus, also be written as ![](../graphics/stm_eqn01877.gif) during absorption and ![](../graphics/stm_eqn01878.gif) during exsorption. We also assume that some wetting liquid will always be present in the medium: ![](../graphics/stm_eqn01879.gif).

[Bear (1972)](07s01a01-References.md) suggests that the transition between absorption and exsorption and vice versa takes place along "scanning" curves. We approximate these with a straight line, as shown in [Figure 2.8.4&#8211;1](02s08a39-Continuity-statement-for-the-wetting-liq.md).

Saturation is treated as a state variable that may have to change if the wetting liquid pressure is outside the range for which its value is admissible according to that actual data corresponding to [Figure 2.8.4&#8211;1](02s08a39-Continuity-statement-for-the-wetting-liq.md). The evolution of saturation as a state variable is defined as follows. Assume that the saturation at time *t*, ![](../graphics/stm_eqn01880.gif), is known. It must satisfy the constraints

![](../graphics/stm_eqn01881.gif)We solve the continuity equation for ![](../graphics/stm_eqn01882.gif), initially assuming ![](../graphics/stm_eqn01883.gif). We then obtain ![](../graphics/stm_eqn01884.gif) by the following rules:

![](../graphics/stm_eqn01885.gif) where ![](../graphics/stm_eqn01886.gif) is the slope of the scanning line. These choices are shown in [Figure 2.8.4&#8211;2](02s08a39-Continuity-statement-for-the-wetting-liq.md).

Figure 2.8.4&#8211;2 Evolution of *s* in unsaturated cases.

![](../graphics/stmunsat-s-evol.png)
### Jacobian contribution

The Jacobian contribution from the continuity equation is obtained from the variation of [Equation 2.8.4&#8211;2](02s08a39-Continuity-statement-for-the-wetting-liq.md) with respect to ![](../graphics/stm_eqn01887.gif) and ![](../graphics/stm_eqn01719.gif) at time ![](../graphics/stm_eqn00438.gif).

Consider first the surface integral. The surface divides into that part across which the liquid mass flow rate, ![](../graphics/stm_eqn01888.gif), is prescribed and that part where the wetting liquid pressure, ![](../graphics/stm_eqn01719.gif), is prescribed. Thus, the only contribution of this term to the Jacobian is the variation in the integral caused by change in surface area in that part where the mass flow is prescribed. We neglect this contribution.

The remaining part of the variation of [Equation 2.8.4&#8211;2](02s08a39-Continuity-statement-for-the-wetting-liq.md) is

![](../graphics/stm_eqn01889.gif)

Using [Equation 2.8.4&#8211;3](02s08a39-Continuity-statement-for-the-wetting-liq.md) we have

![](../graphics/stm_eqn01890.gif) and, thus, neglecting small terms compared to unity,

![](../graphics/stm_eqn01891.gif)

[Equation 2.8.3&#8211;5](02s08a38-Constitutive-behavior-in-a-porous-medium.md) shows that ![](../graphics/stm_eqn01892.gif), which is defined by the evolution equation given in "Constitutive behavior in a porous medium,"  Section 2.8.3, and so makes no contribution to the Jacobian.

Finally, the Jacobian contribution from the permeability term is rather complex in the general case of the nonlinear Forchheimer flow law. Although we include it in the software, here we only write the linearized flow version reflecting Darcy's law (![](../graphics/stm_eqn01852.gif)):

![](../graphics/stm_eqn01893.gif)

Using these results provides the Jacobian of the continuity equation as

![](../graphics/stm_eqn01894.gif)
### References

### References

"Coupled pore fluid diffusion and stress analysis,"  Section 6.8.1 of the Abaqus Analysis User's Guide

"Pore fluid flow properties,"  Section 26.6.1 of the Abaqus Analysis User's Guide