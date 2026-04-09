# 2.13.1 Mass diffusion analysis

### 2.13.1 Mass diffusion analysis

**Product: **Abaqus/Standard

Abaqus/Standard provides for the modeling of the transient or steady-state diffusion of one material through another, such as the diffusion of hydrogen through a metal ([Crank (1956)](07s01a01-References.md), [deGroot and Mazur (1962)](07s01a01-References.md)). The governing equations are an extension of Fick's equations, to allow for nonuniform solubility of the diffusing substance in the base material.

The basic solution variable (used as the degree of freedom at the nodes of the mesh) is the "normalized concentration" (often referred to as the "activity" of the diffusing material), ![](../graphics/stm_eqn02465.gif), where *c* is the mass concentration of the diffusing material and *s* is its solubility in the base material. This means that when the mesh includes dissimilar materials that share nodes, the normalized concentration is continuous across the interface between the different materials. Since ![](../graphics/stm_eqn00155.gif) is the square root of the partial pressure of the diffusing phase, the partial pressure is the same on both sides of the interface; Sievert's law is assumed to hold at the interface.
### Governing equations

The diffusion problem is defined from the requirement of mass conservation for the diffusing phase:

![](../graphics/stm_eqn02466.gif)where *V* is any volume whose surface is *S*, ![](../graphics/stm_eqn00483.gif) is the outward normal to *S*, ![](../graphics/stm_eqn02404.gif) is the flux of concentration of the diffusing phase, and ![](../graphics/stm_eqn02467.gif) is the flux of concentration leaving *S*.

Using the divergence theorem,

![](../graphics/stm_eqn02468.gif)Because the volume is arbitrary, this provides the pointwise equation

![](../graphics/stm_eqn02469.gif)

The equivalent weak form is

![](../graphics/stm_eqn02470.gif)where ![](../graphics/stm_eqn02471.gif) is an arbitrary, suitably continuous, scalar field.

This statement can be rewritten as

![](../graphics/stm_eqn02472.gif)Using the divergence theorem again yields

![](../graphics/stm_eqn02473.gif)
### Constitutive behavior

The diffusion is assumed to be driven by the gradient of a chemical potential, which gives the general behavior

![](../graphics/stm_eqn02474.gif)where ![](../graphics/stm_eqn02475.gif) is the diffusivity; ![](../graphics/stm_eqn02476.gif) is the solubility; ![](../graphics/stm_eqn02477.gif) is the "Soret effect" factor, providing diffusion because of the temperature gradient; ![](../graphics/stm_eqn01111.gif) is the temperature; ![](../graphics/stm_eqn02243.gif) is the absolute zero on the temperature scale used; ![](../graphics/stm_eqn02478.gif) is the pressure stress factor, providing diffusion driven by the gradient of the equivalent pressure stress, ![](../graphics/stm_eqn02479.gif); and ![](../graphics/stm_eqn00480.gif) are any predefined field variables.

An example of a particular form of this constitutive model is the assumption made for hydrogen diffusion in a metal:

![](../graphics/stm_eqn02480.gif)with the chemical potential, ![](../graphics/stm_eqn01087.gif), defined as

![](../graphics/stm_eqn02481.gif)where ![](../graphics/stm_eqn02482.gif) is a fixed datum, *R* is the universal gas constant, and ![](../graphics/stm_eqn02483.gif) is the partial molar volume of hydrogen in the solid solution. This form is similar to that used by [Sofronis and McMeeking (1989)](07s01a01-References.md) and results in a constitutive expression of the form

![](../graphics/stm_eqn02484.gif)To implement this particular form, data for ![](../graphics/stm_eqn01709.gif) and ![](../graphics/stm_eqn02485.gif) must be calculated from the equations

![](../graphics/stm_eqn02486.gif)

Changing variables (![](../graphics/stm_eqn02487.gif)) and introducing the constitutive assumption of [Equation 2.13.1&#8211;3](02s13a49.md) into [Equation 2.13.1&#8211;2](02s13a49.md) yields

![](../graphics/stm_eqn02488.gif)where

![](../graphics/stm_eqn02489.gif)is the concentration flux entering the body across *S*.
### Discretization and time integration

Equilibrium in a finite element model is approximated by a finite set of equations through the introduction of appropriate interpolation functions. Discretized quantities are indicated by uppercase superscripts (for example, ![](../graphics/stm_eqn02490.gif)). The summation convention is adopted for the superscripts. These represent nodal variables, with nodes shared between adjacent elements and appropriate interpolation chosen to provide adequate continuity of the assumed variation. The interpolation is based on material coordinates ![](../graphics/stm_eqn00981.gif), ![](../graphics/stm_eqn02491.gif), 2, 3.

The virtual normalized concentration field is interpolated by

![](../graphics/stm_eqn02492.gif)where ![](../graphics/stm_eqn02493.gif) are interpolation functions. Then, the discretized equations are written as

![](../graphics/stm_eqn02494.gif)

Time integration in transient problems utilizes the backward Euler method (the modified Crank-Nicholson operator). Adopting the convention that any quantity not explicitly associated with a point in time is taken at ![](../graphics/stm_eqn01842.gif), we can drop the subscript ![](../graphics/stm_eqn01842.gif) and write the integrated equations as

![](../graphics/stm_eqn02495.gif)
### Jacobian contribution

The Jacobian contribution from the conservation equation is obtained from the variation of [Equation 2.13.1&#8211;6](02s13a49.md) with respect to ![](../graphics/stm_eqn00155.gif) at time ![](../graphics/stm_eqn00438.gif). This yields

![](../graphics/stm_eqn02496.gif)

![](../graphics/stm_eqn02497.gif)Rearranging and using the interpolation ![](../graphics/stm_eqn02498.gif), we obtain

![](../graphics/stm_eqn02499.gif)

![](../graphics/stm_eqn02500.gif)

Inspecting the above equation, we observe that the Jacobian becomes unsymmetric whenever the diffusivity, ![](../graphics/stm_eqn00424.gif); the temperature-driven diffusion coefficient, ![](../graphics/stm_eqn01709.gif); or the pressure-driven diffusion coefficient, ![](../graphics/stm_eqn02485.gif), is defined as a function of concentration.
### Reference

### Reference

"Mass diffusion analysis,"  Section 6.9.1 of the Abaqus Analysis User's Guide