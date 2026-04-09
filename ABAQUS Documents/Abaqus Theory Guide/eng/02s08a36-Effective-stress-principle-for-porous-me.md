# 2.8.1 Effective stress principle for porous media

### 2.8.1 Effective stress principle for porous media

**Product: **Abaqus/Standard

A porous medium is modeled in Abaqus/Standard by the conventional approach that considers the medium as a multiphase material and adopts an effective stress principle to describe its behavior. The porous medium modeling provided considers the presence of two fluids in the medium. One is the "wetting liquid," which is assumed to be relatively (but not entirely) incompressible. Often the other is a gas, which is relatively compressible. An example of such a system is soil containing ground water. When the medium is partially saturated, both fluids exist at a point: when it is fully saturated, the voids are completely filled with the wetting liquid. The elementary volume, ![](../graphics/stm_eqn00798.gif), is made up of a volume of grains of solid material, ![](../graphics/stm_eqn01715.gif); a volume of voids, ![](../graphics/stm_eqn01716.gif); and a volume of wetting liquid, ![](../graphics/stm_eqn01717.gif), that is free to move through the medium if driven. In some systems (for example, systems containing particles that absorb the wetting liquid and swell in the process) there may also be a significant volume of trapped wetting liquid, ![](../graphics/stm_eqn01718.gif).

The total stress acting at a point, ![](../graphics/stm_eqn00033.gif), is assumed to be made up of an average pressure stress in the wetting liquid, ![](../graphics/stm_eqn01719.gif), called the "wetting liquid pressure," an average pressure stress in the other fluid, ![](../graphics/stm_eqn01720.gif), and an "effective stress," ![](../graphics/stm_eqn01721.gif), defined by

![](../graphics/stm_eqn01722.gif)Stress components are stored so that tensile stress is positive, but ![](../graphics/stm_eqn01719.gif) and ![](../graphics/stm_eqn01720.gif) are pressure stress values. This explains the sign in this equation. ![](../graphics/stm_eqn01723.gif) is a factor that depends on saturation and on the surface tension of the liquid/solid system ([Wu, 1976](07s01a01-References.md)). ![](../graphics/stm_eqn01723.gif) is 1.0 when the medium is fully saturated and between 0.0 and 1.0 in unsaturated systems when its value depends on the degree of saturation of the medium. There is very sparse experimental evidence of its dependence on saturation; and because of this lack of data, we simply assume that ![](../graphics/stm_eqn01723.gif) is equal to the saturation of the medium (we define saturation later in this section).

We simplify the model by assuming that the pressure applied to the nonwetting fluid is constant throughout the domain being modeled, does not vary with time, and is small enough that its value can be neglected. This requires that the nonwetting fluid can diffuse through the medium sufficiently freely so that its pressure, ![](../graphics/stm_eqn01720.gif), never exceeds the pressure applied to this fluid at the boundaries of the medium, which remains constant throughout the process being modeled. The most common example where this simplification applies is a porous medium that is quite permeable to gas flow, in which the nonwetting fluid is air, exposed to atmospheric pressure. The dimensions of the region modeled must not be so large that the gravitational gradient of atmospheric pressure causes a significant change in the air pressure, and there can be no external event that provides a transient change in the air pressure. This assumption allows ![](../graphics/stm_eqn01720.gif) to be removed from the equation, provided that the corresponding loading term (for example, atmospheric pressure on the boundary of the medium) is also omitted from the equilibrium equations and that ![](../graphics/stm_eqn01720.gif) is small enough that its effect on the deformation of the medium is not important (or that deformation is measured from the state ![](../graphics/stm_eqn01724.gif)). This simplification reduces the effective stress principle to

![](../graphics/stm_eqn01725.gif)

In the case where trapped fluid is present in the system, we assume that the effective stress is made up of two components weighted according to the relative volume of trapped fluid and porous material:

![](../graphics/stm_eqn01726.gif)where ![](../graphics/stm_eqn01727.gif) is the effective stress in the porous material skeleton, ![](../graphics/stm_eqn01728.gif) is the average pressure stress in the trapped liquid, and ![](../graphics/stm_eqn01729.gif) is the ratio of trapped fluid volume to total volume, as defined later in this section.

We assume that the constitutive response of the porous medium consists of simple bulk elasticity relationships for the liquid and for the soil grains, together with a constitutive theory for the soil skeleton whereby ![](../graphics/stm_eqn01727.gif) is defined as a function of the strain history and temperature of the soil:

![](../graphics/stm_eqn01730.gif)Constitutive models that are appropriate for voided materials, such as soils, are described in Chapter 4, "Mechanical Constitutive Theories."

The remaining parts of "Analysis of porous media,"  Section 2.8, discuss the equilibrium equation for porous media ("Discretized equilibrium statement for a porous medium,"  Section 2.8.2), fundamental constitutive assumptions that incorporate the effective stress principle as outlined above ("Constitutive behavior in a porous medium,"  Section 2.8.3), and the continuity equation that governs the flow of the wetting liquid ("Continuity statement for the wetting liquid phase in a porous medium,"  Section 2.8.4). Newton's method is generally used to solve the governing equations for the implicit time integration procedure. Analysis of small, linearized, perturbations about a deformed state is also sometimes required (for vibration studies, for example). For these reasons the development includes a definition of the form of the Jacobian matrix for the two-phase model.

As preliminaries, porosity, void ratio, and saturation are defined. The porosity of the medium, *n*, is the ratio of the volume of voids to the total volume:

![](../graphics/stm_eqn01731.gif)Using the superscript ![](../graphics/stm_eqn01732.gif) to indicate values in some convenient reference configuration allows the porosity in the current configuration to be expressed as

![](../graphics/stm_eqn01733.gif)so that

![](../graphics/stm_eqn01734.gif)where

![](../graphics/stm_eqn01735.gif)is the ratio of the medium's volume in the current configuration to its volume in the reference configuration,

![](../graphics/stm_eqn01736.gif)is the ratio of the current to reference volume for the grains, and

![](../graphics/stm_eqn01737.gif)is the volume of trapped wetting liquid per unit of current volume.

Abaqus generally uses void ratio, ![](../graphics/stm_eqn01738.gif), instead of porosity. Conversion relationships are readily derived as

![](../graphics/stm_eqn01739.gif)

Saturation, *s*, is the ratio of free (untrapped) wetting liquid volume to void volume:

![](../graphics/stm_eqn01740.gif)

The volume ratio of free wetting liquid at a point is

![](../graphics/stm_eqn01741.gif)

The total volume of wetting liquid (free liquid plus trapped liquid) per unit of current volume is

![](../graphics/stm_eqn01742.gif)
### References

### References

"Coupled pore fluid diffusion and stress analysis,"  Section 6.8.1 of the Abaqus Analysis User's Guide

"Geostatic stress state,"  Section 6.8.2 of the Abaqus Analysis User's Guide