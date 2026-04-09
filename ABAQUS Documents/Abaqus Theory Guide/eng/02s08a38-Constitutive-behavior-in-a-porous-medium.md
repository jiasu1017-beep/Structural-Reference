# 2.8.3 Constitutive behavior in a porous medium

### 2.8.3 Constitutive behavior in a porous medium

**Product: **Abaqus/Standard

A porous medium in Abaqus/Standard is considered to consist of a mixture of solid matter, voids that contain liquid and gas, and entrapped liquid attached to the solid matter. The mechanical behavior of the porous medium consists of the responses of the liquid and solid matter to local pressure and of the response of the overall material to effective stress. The assumptions made about these responses are discussed in this section.
### Liquid response

For the liquid in the system (the free liquid in the voids and the entrapped liquid) we assume that

![](../graphics/stm_eqn01776.gif)where ![](../graphics/stm_eqn01748.gif) is the density of the liquid, ![](../graphics/stm_eqn01777.gif) is its density in the reference configuration, ![](../graphics/stm_eqn01778.gif) is the liquid's bulk modulus, and

![](../graphics/stm_eqn01779.gif)is the volumetric expansion of the liquid caused by temperature change. Here ![](../graphics/stm_eqn01780.gif) is the liquid's thermal expansion coefficient, ![](../graphics/stm_eqn01111.gif) is the current temperature, ![](../graphics/stm_eqn01781.gif) is the initial temperature at this point in the medium, and ![](../graphics/stm_eqn01782.gif) is the reference temperature for thermal expansion. Both ![](../graphics/stm_eqn01783.gif) and ![](../graphics/stm_eqn01784.gif) are assumed to be small.
### Grains response

The solid matter in the porous medium is assumed to have the local mechanical response under pressure

![](../graphics/stm_eqn01785.gif)where ![](../graphics/stm_eqn01786.gif) is the bulk modulus of this solid matter, *s* is the saturation in the wetting fluid, and

![](../graphics/stm_eqn01787.gif)is its volumetric thermal strain. Here ![](../graphics/stm_eqn01788.gif) is the thermal expansion coefficient for the solid matter and ![](../graphics/stm_eqn01789.gif) is the reference temperature for this expansion. ![](../graphics/stm_eqn01790.gif) is assumed to be small.

It is important to distinguish ![](../graphics/stm_eqn01791.gif) and ![](../graphics/stm_eqn01591.gif) as properties of the solid grains material. The porous medium as a whole will exhibit a much softer (and generally nonrecoverable) bulk behavior than is indicated by ![](../graphics/stm_eqn01791.gif) and will also show a different thermal expansion. These effects are partially structural, caused by the medium being made up of irregular grains in partial contact. They may also be caused by the system being only partially saturated, with the voids containing a mixture of relatively compressible gas and relatively incompressible liquid.
### Liquid entrapment

Entrapment of liquid is associated with specific materials that absorb liquid and swell into a "gel." A simple model of this behavior is based on the idealization of this gel as a volume of individual spherical particles of equal radius ![](../graphics/stm_eqn01792.gif). [Tanaka and Fillmore (1979)](07s01a01-References.md) show that, when a single sphere of such material is fully exposed to liquid, its radius change can be modeled as

![](../graphics/stm_eqn01793.gif)where ![](../graphics/stm_eqn01794.gif) is the fully swollen radius approached as ![](../graphics/stm_eqn01795.gif) and *N*, ![](../graphics/stm_eqn01796.gif) and ![](../graphics/stm_eqn01797.gif) are material parameters. Tanaka and Fillmore also show the first term in the series dominates, so the model can be simplified to

![](../graphics/stm_eqn01798.gif)This provides the rate form

![](../graphics/stm_eqn01799.gif)

When the gel particles are only partially exposed to liquid (in an unsaturated system), it seems reasonable to assume that the swelling rate will be lessened according to the level of saturation. Further, we assume that the gel will swell only when the saturation of the surrounding medium exceeds the effective saturation of the gel, ![](../graphics/stm_eqn01800.gif), where ![](../graphics/stm_eqn01801.gif) is the radius of a gel particle that is completely dry. We combine these into a simple, linear effect:

![](../graphics/stm_eqn01802.gif)where ![](../graphics/stm_eqn01803.gif) if ![](../graphics/stm_eqn01804.gif), ![](../graphics/stm_eqn01805.gif) otherwise.

The packing density and swelling may cause the gel particles to touch. In that case the surface available to absorb and entrap liquid is reduced until, if the gel particles occupy the entire volume except for solid material, liquid entrapment must cease altogether. With ![](../graphics/stm_eqn01806.gif) gel particles per unit reference volume, the maximum radius that the gel particles can achieve before they must touch (in a face center cubic arrangement) is

![](../graphics/stm_eqn01807.gif)and the volume is entirely occupied with gel and solid matter when the effective gel radius is

![](../graphics/stm_eqn01808.gif)The gel swelling behavior is, therefore, further modified to be

![](../graphics/stm_eqn01809.gif)Thus, in an unstressed medium the entrapped liquid volume is assumed to be

![](../graphics/stm_eqn01810.gif)where

![](../graphics/stm_eqn01811.gif)where ![](../graphics/stm_eqn01812.gif) is defined by the integration of [Equation 2.8.3&#8211;3](02s08a38.md). This entrapped liquid can be compressed by pressure so that, when the porous medium is under stress, we assume

![](../graphics/stm_eqn01813.gif)and thus

![](../graphics/stm_eqn01814.gif)Combining this with [Equation 2.8.3&#8211;1](02s08a38.md) and neglecting small terms compared to unity then provides

![](../graphics/stm_eqn01815.gif)

We assume that, in the initial state, the effective saturation of the gel is the same as the saturation of the surrounding medium:

![](../graphics/stm_eqn01816.gif)

The constitutive behavior of the gel containing entrapped fluid is given by the elastic bulk relationship

![](../graphics/stm_eqn01817.gif)where ![](../graphics/stm_eqn01728.gif) is the average pressure stress in the gel fluid and ![](../graphics/stm_eqn01818.gif) is its volumetric effective strain.
### Effective strain

From [Equation 2.8.3&#8211;2](02s08a38.md) we see that the volumetric strain ![](../graphics/stm_eqn01819.gif) represents that part of the total volumetric strain caused by pore pressure acting on the solid matter in the porous medium and by thermal expansion of that solid matter. In addition, entrapment of liquid in the medium may cause an additional volume change ratio:

![](../graphics/stm_eqn01820.gif)Finally, ![](../graphics/stm_eqn01821.gif) is a saturation driven moisture swelling strain that represents the volumetric swelling of the solid skeleton in partially saturated flow conditions. This moisture swelling can be isotropic or anisotropic. The remaining part of the strain in the medium,

![](../graphics/stm_eqn01822.gif) is the strain that is assumed to modify the effective stress in the medium. That is, we assume

![](../graphics/stm_eqn01823.gif)Specific constitutive models of this type are discussed in Chapter 4, "Mechanical Constitutive Theories." From this assumption, and using [Equation 2.8.3&#8211;5](02s08a38.md), we can write the Jaumann rate of change of the effective stress in terms of the rate of change of the kinematic and pore liquid pressure variables as

![](../graphics/stm_eqn01824.gif) where ![](../graphics/stm_eqn01825.gif) is defined for each particular model in Chapter 4, "Mechanical Constitutive Theories."

Also, for the effective pressure stress of the fluid entrapped in the gel,

![](../graphics/stm_eqn01826.gif)

Then, from [Equation 2.8.2&#8211;3](02s08a37.md),

![](../graphics/stm_eqn01827.gif)
### Reference

### Reference

"Pore fluid flow properties,"  Section 26.6 of the Abaqus Analysis User's Guide