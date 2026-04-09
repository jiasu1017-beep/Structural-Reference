# 1.5.5 Energy balance

### 1.5.5 Energy balance

**Products: **Abaqus/Standard  Abaqus/Explicit

The conservation of energy implied by the first law of thermodynamics states that the time rate of change of kinetic energy and internal energy for a fixed body of material is equal to the sum of the rate of work done by the surface and body forces. This can be expressed as

![](../graphics/stm_eqn00592.gif)where

![](../graphics/stm_eqn00593.gif)

is the current mass density,

![](../graphics/stm_eqn00427.gif)

is the velocity field vector,

*U*

is the internal energy per unit mass,

![](../graphics/stm_eqn00479.gif)

is the surface traction vector,

![](../graphics/stm_eqn00480.gif)

is the body force vector, and

![](../graphics/stm_eqn00483.gif)

is the normal direction vector on boundary *S*.

Using Gauss' theorem and the identity that ![](../graphics/stm_eqn00594.gif) on the boundary *S*, the first term of the right-hand side of [Equation 1.5.5&#8211;1](01s05a12-Energy-balance.md) can be rewritten as

![](../graphics/stm_eqn00595.gif) where we have used the fact that ![](../graphics/stm_eqn00596.gif) is symmetric, and we also know (see "Equilibrium and virtual work,"  Section 1.5.1) that

![](../graphics/stm_eqn00597.gif)where ![](../graphics/stm_eqn00598.gif)  is the strain rate tensor (see "Rate of deformation and strain increment,"  Section 1.4.3).  Substituting [Equation 1.5.5&#8211;2](01s05a12-Energy-balance.md) into [Equation 1.5.5&#8211;1](01s05a12-Energy-balance.md) yields

![](../graphics/stm_eqn00599.gif)

From Cauchy's equation of motion we have

![](../graphics/stm_eqn00600.gif) Substituting this into [Equation 1.5.5&#8211;3](01s05a12-Energy-balance.md) gives

![](../graphics/stm_eqn00601.gif)From this we get the energy equation

![](../graphics/stm_eqn00602.gif)Integrating this equation we find

![](../graphics/stm_eqn00603.gif)where ![](../graphics/stm_eqn00604.gif) is the energy at time ![](../graphics/stm_eqn00605.gif). To make the energy balance ([Equation 1.5.5&#8211;1](01s05a12-Energy-balance.md)) more convenient to use, we integrate it in time:

![](../graphics/stm_eqn00606.gif)or

![](../graphics/stm_eqn00607.gif)where

![](../graphics/stm_eqn00608.gif) defined as the rate of work done to the body by external forces and contact friction forces between the contact surfaces. ![](../graphics/stm_eqn00609.gif), the kinetic energy, is given by

![](../graphics/stm_eqn00610.gif)and ![](../graphics/stm_eqn00611.gif) is defined as

![](../graphics/stm_eqn00612.gif)To track physically distinguishable engineering phenomena more narrowly, we introduce decompositions of the stress, strain, and tractions.

We can split the traction, ![](../graphics/stm_eqn00479.gif), into the surface distributed load, ![](../graphics/stm_eqn00613.gif), the solid infinite element radiation traction, ![](../graphics/stm_eqn00614.gif), and the frictional traction, ![](../graphics/stm_eqn00615.gif). Then ![](../graphics/stm_eqn00616.gif) can be written as

![](../graphics/stm_eqn00617.gif)where ![](../graphics/stm_eqn00618.gif) is the rate of work done to the body by external forces, ![](../graphics/stm_eqn00619.gif) is the rate of energy dissipated by the damping effect of solid medium infinite elements, and ![](../graphics/stm_eqn00620.gif) is the rate of energy dissipated by contact friction forces between the contact surfaces. An energy balance for the entire model can then be written as

![](../graphics/stm_eqn00621.gif)For convenience, the dissipated portions of the internal energy are split off:

![](../graphics/stm_eqn00622.gif) where ![](../graphics/stm_eqn00623.gif)  is the stress derived from the user-specified constitutive equation, without viscous dissipation effects included;  ![](../graphics/stm_eqn00624.gif) is the elastic stress;  ![](../graphics/stm_eqn00625.gif) is the viscous stress (defined for bulk viscosity, material damping,  and dashpots); ![](../graphics/stm_eqn00626.gif) is the energy dissipated by viscous effects;  and  ![](../graphics/stm_eqn00627.gif) is the remaining energy, which we continue to call the internal energy.  If we introduce the strain decomposition, ![](../graphics/stm_eqn00628.gif)  (where ![](../graphics/stm_eqn00629.gif),  ![](../graphics/stm_eqn00630.gif), and  ![](../graphics/stm_eqn00631.gif) are elastic, plastic, and creep strain rates, respectively),  the internal energy, ![](../graphics/stm_eqn00627.gif), can be expressed as

![](../graphics/stm_eqn00632.gif)where ![](../graphics/stm_eqn00633.gif)  is the applied elastic strain energy, ![](../graphics/stm_eqn00634.gif) is the energy dissipated by plasticity, and  ![](../graphics/stm_eqn00635.gif) is the energy dissipated by time-dependent deformation  (creep, swelling, and viscoelasticity).

If damage occurs in the material, not all of the applied elastic strain energy is recoverable. At any given time, the stress, ![](../graphics/stm_eqn00623.gif), can be expressed in terms of the "undamaged" stress, ![](../graphics/stm_eqn00636.gif), and the continuum damage parameter, *d*:

![](../graphics/stm_eqn00637.gif)The damage parameter, *d*, starts at zero (undamaged material) and increases to a maximum value of no more than one (fully damaged material). Hence, we can write

![](../graphics/stm_eqn00638.gif)We assume that, upon unloading, the damage parameter remains fixed at the value attained at time *t*. Therefore, the recoverable strain energy is equal to

![](../graphics/stm_eqn00639.gif)and the energy dissipated through damage is equal to

![](../graphics/stm_eqn00640.gif)If we define

![](../graphics/stm_eqn00641.gif)as the undamaged elastic energy function, we can write

![](../graphics/stm_eqn00642.gif)and

![](../graphics/stm_eqn00643.gif)Interchanging the integrals yields

![](../graphics/stm_eqn00644.gif)and

![](../graphics/stm_eqn00645.gif)The first term in the last expression vanishes, since at time *t*, ![](../graphics/stm_eqn00646.gif) and at time zero, ![](../graphics/stm_eqn00647.gif). If we now define the damage strain energy function

![](../graphics/stm_eqn00648.gif)then

![](../graphics/stm_eqn00649.gif)For a linear elastic energy function

![](../graphics/stm_eqn00650.gif)and, hence,

![](../graphics/stm_eqn00651.gif)
### References

### References

"Abaqus/Standard output variable identifiers,"  Section 4.2.1 of the Abaqus Analysis User's Guide

"Abaqus/Explicit output variable identifiers,"  Section 4.2.2 of the Abaqus Analysis User's Guide