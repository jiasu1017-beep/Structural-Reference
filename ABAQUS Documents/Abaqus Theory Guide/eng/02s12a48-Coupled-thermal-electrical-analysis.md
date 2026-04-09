# 2.12.1 Coupled thermal-electrical analysis

### 2.12.1 Coupled thermal-electrical analysis

**Product: **Abaqus/Standard

Joule heating arises when the energy dissipated by an electrical current flowing through a conductor is converted into thermal energy. Abaqus/Standard provides a fully coupled thermal-electrical procedure for analyzing this type of problem. Coupling arises from two sources: the conductivity in the electrical problem is temperature dependent, and the internal heat generated in the thermal problem is a function of electrical current. The thermal part of the problem includes all the heat conduction and heat storage (specific and latent heat) features described in "Uncoupled heat transfer analysis,"  Section 2.11.1. (Forced heat convection caused by fluid flowing through the mesh is not considered.)

The thermal-electrical elements have both temperature and electrical potential as nodal variables.

This section describes the governing equilibrium equations, the constitutive model, boundary conditions, the surface interaction model, finite element discretization, and the components of the Jacobian used.
### Governing equations

The electric field in a conducting material is governed by Maxwell's equation of conservation of charge. Assuming steady-state direct current, the equation reduces to

![](../graphics/stm_eqn02403.gif)where *V* is any control volume whose surface is *S*, ![](../graphics/stm_eqn00483.gif) is the outward normal to *S*, ![](../graphics/stm_eqn02404.gif) is the electrical current density (current per unit area), and ![](../graphics/stm_eqn02405.gif) is the internal volumetric current source per unit volume.

The divergence theorem is used to convert the surface integral into a volume integral:

![](../graphics/stm_eqn02406.gif)and since the volume is arbitrary, this provides the pointwise differential equation

![](../graphics/stm_eqn02407.gif)

The equivalent weak form is obtained by introducing an arbitrary, variational, electrical potential field, ![](../graphics/stm_eqn02408.gif), and integrating over the volume:

![](../graphics/stm_eqn02409.gif)Using first the chain rule and then the divergence theorem, this statement can be rewritten as

![](../graphics/stm_eqn02410.gif)where ![](../graphics/stm_eqn02411.gif) is the current density entering the control volume across *S*.
### Constitutive behavior

The flow of electrical current is described by Ohm's law:

![](../graphics/stm_eqn02412.gif)where ![](../graphics/stm_eqn02413.gif) is the electrical conductivity matrix; ![](../graphics/stm_eqn01111.gif) is the temperature; and ![](../graphics/stm_eqn02414.gif) are any predefined field variables. The conductivity can be isotropic, orthotropic, or fully anisotropic. ![](../graphics/stm_eqn02415.gif) is the electrical field intensity defined as

![](../graphics/stm_eqn02416.gif)Since a potential rise occurs when a charged particle moves against the electrical field, the direction of the gradient is opposite to that of the electrical field. Using this definition of the electrical field, Ohm's law is rewritten as

![](../graphics/stm_eqn02417.gif)The constitutive relation is linear; that is, it assumes that the electrical conductivity is independent of the electrical field.

Introducing Ohm's law, the governing conservation of charge equation becomes

![](../graphics/stm_eqn02418.gif)
### Thermal energy balance

The heat conduction behavior is described by the basic energy balance relation

![](../graphics/stm_eqn02419.gif)where *V* is a volume of solid material, with surface area *S*; ![](../graphics/stm_eqn00593.gif) is the density of the material; *U* is the internal energy; ![](../graphics/stm_eqn02234.gif) is the thermal conductivity matrix; *q* is the heat flux per unit area of the body, flowing into the body; and *r* is the heat generated within the body. The thermal problem is discussed in detail in "Uncoupled heat transfer analysis,"  Section 2.11.1.

[Equation 2.12.1&#8211;4](02s12a48-Coupled-thermal-electrical-analysis.md) and [Equation 2.12.1&#8211;5](02s12a48-Coupled-thermal-electrical-analysis.md) describe the electrical and thermal problems, respectively. Coupling arises from two sources: the conductivity in the electrical problem is temperature dependent, ![](../graphics/stm_eqn02420.gif), and the internal heat generation in the thermal problem is a function of electrical current, ![](../graphics/stm_eqn02421.gif), as described below.
### Thermal energy due to electrical current

Joule's law describes the rate of electrical energy, ![](../graphics/stm_eqn02422.gif), dissipated by current flowing through a conductor as

![](../graphics/stm_eqn02423.gif)Using [Equation 2.12.1&#8211;2](02s12a48-Coupled-thermal-electrical-analysis.md) and [Equation 2.12.1&#8211;3](02s12a48-Coupled-thermal-electrical-analysis.md), Joule's law is rewritten as

![](../graphics/stm_eqn02424.gif)In a steady-state analysis ![](../graphics/stm_eqn02422.gif) is evaluated at time ![](../graphics/stm_eqn00438.gif). In a transient analysis an averaged value of ![](../graphics/stm_eqn02422.gif) is obtained over the increment

![](../graphics/stm_eqn02425.gif)where ![](../graphics/stm_eqn02426.gif) and ![](../graphics/stm_eqn02427.gif) are values at time ![](../graphics/stm_eqn00438.gif). The amount of this energy released as internal heat is

![](../graphics/stm_eqn02428.gif)where ![](../graphics/stm_eqn02429.gif) is an energy conversion factor.
### Surface conditions

The surface---*S*---of the body consists of parts on which boundary conditions can be prescribed---![](../graphics/stm_eqn02430.gif)---and parts that can interact with nearby surfaces of other bodies---![](../graphics/stm_eqn00981.gif). Prescribed boundary conditions include the electrical potential, ![](../graphics/stm_eqn02431.gif); temperature, ![](../graphics/stm_eqn02236.gif); electrical current density, ![](../graphics/stm_eqn02432.gif); heat flux, ![](../graphics/stm_eqn02237.gif); and surface convection and radiation conditions. The surface interaction model includes heat conduction and radiation effects between the interface surfaces and electrical current flowing across the interface. Heat conduction and radiation are modeled by

![](../graphics/stm_eqn02433.gif)and

![](../graphics/stm_eqn02434.gif)respectively, where ![](../graphics/stm_eqn01111.gif) is the temperature on the surface of the body under consideration, ![](../graphics/stm_eqn02435.gif) is the temperature on the surface of the other body, ![](../graphics/stm_eqn02436.gif) is the value of absolute zero on the temperature scale being used, ![](../graphics/stm_eqn02437.gif) is the gap thermal conductance, ![](../graphics/stm_eqn02438.gif) is the average interface temperature,![](../graphics/stm_eqn02439.gif) is the average of any predefined field variables at A and B, and *F* and ![](../graphics/stm_eqn02440.gif) are constants.

The electrical current flowing between the interface surfaces is modeled as

![](../graphics/stm_eqn02441.gif)where ![](../graphics/stm_eqn02442.gif) is the electrical potential on the surface of the body under consideration, ![](../graphics/stm_eqn02443.gif) is the electrical potential on the surface of the other body, and ![](../graphics/stm_eqn02444.gif) is the gap electrical conductance. The electrical energy dissipated by the current flowing across the interface,

![](../graphics/stm_eqn02445.gif) is released as heat on the surfaces of the bodies:

![](../graphics/stm_eqn02446.gif)where ![](../graphics/stm_eqn02447.gif) is an energy conversion factor and *f* specifies how the total heat is distributed between the interface surfaces. ![](../graphics/stm_eqn02422.gif) is evaluated at the end of the time increment in a steady-state analysis, and an averaged value over the time increment is used in a transient analysis. This is described in detail in "Heat generation caused by electrical current,"  Section 5.2.6.

Introducing the surface interaction effects and electrical energy released as thermal energy, the governing electric and thermal equations become

![](../graphics/stm_eqn02448.gif)and

![](../graphics/stm_eqn02449.gif)
### Spatial discretization

In a finite element model equilibrium is approximated as a finite set of equations by introducing interpolation functions. Discretized quantities are indicated by uppercase superscripts (for example, ![](../graphics/stm_eqn02450.gif)). The summation convention is adopted for the superscripts. The discretized quantities represent nodal variables, with nodes shared between adjacent elements and appropriate interpolation chosen to provide adequate continuity of the assumed variation.

The virtual electrical potential field is interpolated by

![](../graphics/stm_eqn02451.gif)where ![](../graphics/stm_eqn02452.gif) are the interpolation functions. The discretized electrical equation is then written as

![](../graphics/stm_eqn02453.gif)Since ![](../graphics/stm_eqn02408.gif) is arbitrary,

![](../graphics/stm_eqn02454.gif)

The temperature field in the thermal problem is approximated by the same set of interpolation functions:

![](../graphics/stm_eqn02455.gif)Using these interpolation functions and a backward difference operator to integrate the internal energy rate, ![](../graphics/stm_eqn02456.gif), the thermal energy balance relation is obtained:

![](../graphics/stm_eqn02457.gif)
### Jacobian contributions

The Jacobian contributions are obtained by taking variations of [Equation 2.12.1&#8211;8](02s12a48-Coupled-thermal-electrical-analysis.md) and [Equation 2.12.1&#8211;9](02s12a48-Coupled-thermal-electrical-analysis.md) with respect to the electrical potential, ![](../graphics/stm_eqn02442.gif), and the temperature, ![](../graphics/stm_eqn01111.gif), at time ![](../graphics/stm_eqn00438.gif). This yields

![](../graphics/stm_eqn02458.gif)

![](../graphics/stm_eqn02459.gif)The term ![](../graphics/stm_eqn02460.gif) in the ![](../graphics/stm_eqn02461.gif) component includes prescribed surface convection and radiation conditions. The surface interaction terms ![](../graphics/stm_eqn02462.gif), ![](../graphics/stm_eqn02463.gif), and ![](../graphics/stm_eqn02464.gif) are evaluated in "Heat generation caused by electrical current,"  Section 5.2.6.

The Jacobian contributions give rise to an unsymmetric system of equations, requiring the use of the nonsymmetric matrix storage and solution scheme.
### Reference

### Reference

"Coupled thermal-electrical analysis,"  Section 6.7.3 of the Abaqus Analysis User's Guide