# 2.11.1 Uncoupled heat transfer analysis

### 2.11.1 Uncoupled heat transfer analysis

**Product: **Abaqus/Standard

The Abaqus/Standard capability for uncoupled heat transfer analysis is intended to model solid body heat conduction with general, temperature-dependent conductivity; internal energy (including latent heat effects); and quite general convection and radiation boundary conditions. This section describes the basic energy balance, constitutive models, boundary conditions, finite element discretization, and time integration procedures used.

Heat transfer in flowing materials (convection) is discussed in "Convection/diffusion,"  Section 2.11.3. Radiation heat transfer in cavities is discussed in "Cavity radiation,"  Section 2.11.4. All such heat transfer mechanisms can be present in a model.
### Energy balance

The basic energy balance is (Green and Naghdi)

![](../graphics/stm_eqn02229.gif)where *V* is a volume of solid material, with surface area *S*; ![](../graphics/stm_eqn00593.gif) is the density of the material; ![](../graphics/stm_eqn02230.gif) is the material time rate of the internal energy; *q* is the heat flux per unit area of the body, flowing into the body; and *r* is the heat supplied internally into the body per unit volume.

It is assumed that the thermal and mechanical problems are uncoupled in the sense that ![](../graphics/stm_eqn02231.gif) only, where ![](../graphics/stm_eqn01111.gif) is the temperature of the material, and *q* and *r* do not depend on the strains or displacements of the body. For simplicity a Lagrangian description is assumed, so "volume" and "surface" mean the volume and surface in the reference configuration.
### Constitutive definition

This relationship is usually written in terms of a specific heat, neglecting coupling between mechanical and thermal problems:

![](../graphics/stm_eqn02232.gif)except for latent heat effects at phase changes, which are given separately in terms of solidus and liquidus temperatures (the lower and upper temperature bounds of the phase change range) and the total internal energy associated with the phase change, called the latent heat. When latent heat is given, it is assumed to be in addition to the specific heat effect (see [Figure 2.11.1&#8211;1](02s11a43-Uncoupled-heat-transfer-analysis.md)).

Figure 2.11.1&#8211;1 Specific heat, latent heat definition.

![](../graphics/stmspec-latent-heat-nls.png) For many cases it is reasonable to assume that the phase change occurs within a known temperature range, which can be specified by the user. However, in some cases it may be necessary to include a kinetic theory for the phase change to model the effect accurately (an example would be the prediction of crystallization in a polymer casting process). For such cases the user can model the process in considerable detail, using the solution-dependent state variable feature in Abaqus, with user subroutine HETVAL.

Heat conduction is assumed to be governed by the Fourier law,

![](../graphics/stm_eqn02233.gif)where ![](../graphics/stm_eqn02234.gif) is the conductivity matrix, ![](../graphics/stm_eqn02235.gif); ![](../graphics/stm_eqn00480.gif) is the heat flux; and ![](../graphics/stm_eqn00117.gif) is position. The conductivity ![](../graphics/stm_eqn02234.gif) can be fully anisotropic, orthotropic, or isotropic.
### Boundary conditions

Boundary conditions can be specified as prescribed temperature, ![](../graphics/stm_eqn02236.gif); prescribed surface heat flux, ![](../graphics/stm_eqn02237.gif) per area; prescribed volumetric heat flux, ![](../graphics/stm_eqn02238.gif) per volume; surface convection: ![](../graphics/stm_eqn02239.gif), where ![](../graphics/stm_eqn02240.gif) is the film coefficient and ![](../graphics/stm_eqn02241.gif) is the sink temperature; and radiation: ![](../graphics/stm_eqn02242.gif), where A is the radiation constant (emissivity times the Stefan-Boltzmann constant) and ![](../graphics/stm_eqn02243.gif) is the value of absolute zero on the temperature scale being used. Surfaces can also participate in cavity radiation effects. The cavity radiation formulation in Abaqus is described in "Cavity radiation,"  Section 2.11.4.
### Spatial discretization

A variational statement of the energy balance, [Equation 2.11.1&#8211;1](02s11a43-Uncoupled-heat-transfer-analysis.md), together with the Fourier law, [Equation 2.11.1&#8211;2](02s11a43-Uncoupled-heat-transfer-analysis.md), is obtained directly by the standard Galerkin approach as

![](../graphics/stm_eqn02244.gif)where ![](../graphics/stm_eqn02245.gif) is an arbitrary variational field satisfying the essential boundary conditions. The body is approximated geometrically with finite elements, so the temperature is interpolated as

![](../graphics/stm_eqn02246.gif)where ![](../graphics/stm_eqn02247.gif) are nodal temperatures. The Galerkin approach assumes that ![](../graphics/stm_eqn02245.gif), the variational field, is interpolated by the same functions:

![](../graphics/stm_eqn02248.gif)First- and second-order polynomials in one, two, and three dimensions are used for the ![](../graphics/stm_eqn02249.gif). With these interpolations the variational statement, [Equation 2.11.1&#8211;3](02s11a43-Uncoupled-heat-transfer-analysis.md), becomes

![](../graphics/stm_eqn02250.gif)and since the ![](../graphics/stm_eqn02251.gif) are arbitrarily chosen, this gives the system of equations

![](../graphics/stm_eqn02252.gif)This set of equations is the "continuous time description" of the geometric approximation.
### Time integration

Abaqus/Standard uses the backward difference algorithm:

![](../graphics/stm_eqn02253.gif)This operator is chosen for a number of reasons. First of all, we choose from one-step operators of the form

![](../graphics/stm_eqn02254.gif)because of their simplicity in implementation (for example, no special starting procedures are needed) and well-understood behavior. For ![](../graphics/stm_eqn02255.gif) such operators are only conditionally stable for linear heat transfer problems. We prefer to work with unconditionally stable methods, because Abaqus is most commonly applied to problems where the solution is sought over very long time periods (compared to the stability limit for the explicit form of the operator, ![](../graphics/stm_eqn02256.gif)), and so choose ![](../graphics/stm_eqn02257.gif). Of these operators the central difference method, ![](../graphics/stm_eqn02258.gif), has the highest accuracy. However, that form of the operator tends to produce oscillations in the early time solution that are not present in the backward difference form. Thus, we use ![](../graphics/stm_eqn02259.gif): backward difference. Introducing the operator, [Equation 2.11.1&#8211;5](02s11a43-Uncoupled-heat-transfer-analysis.md), into the energy balance [Equation 2.11.1&#8211;4](02s11a43-Uncoupled-heat-transfer-analysis.md) gives

![](../graphics/stm_eqn02260.gif)This nonlinear system is solved by a modified Newton method. The method is modified Newton because the tangent matrix (the Jacobian matrix)---that is, the rate of change of the left-hand side of [Equation 2.11.1&#8211;6](02s11a43-Uncoupled-heat-transfer-analysis.md) with respect to ![](../graphics/stm_eqn02261.gif)---is not formed exactly. The formation of the terms in this tangent matrix is now described.

The internal energy term gives a Jacobian contribution:

![](../graphics/stm_eqn02262.gif)![](../graphics/stm_eqn02263.gif) is the specific heat, ![](../graphics/stm_eqn02264.gif), outside the latent heat range, and is ![](../graphics/stm_eqn02265.gif) if ![](../graphics/stm_eqn02266.gif) at the integration point, where ![](../graphics/stm_eqn02267.gif) and ![](../graphics/stm_eqn02268.gif) are the liquidus and solidus temperatures and *L* is the latent heat associated with this phase change.

In severe latent heat cases this term can result in numerical instabilities, as the stiffness term ![](../graphics/stm_eqn02269.gif) is small outside the solidus-liquidus temperature range and is very stiff inside that rather narrow range. To avoid such instabilities in those cases this term is modified to a secant term during the early iterations of the solution to a time step. Since the modification occurs only in cases involving latent heat, it affects only those problems.

The conductivity term gives a Jacobian contribution:

![](../graphics/stm_eqn02270.gif)The second of these terms is typically small, since the conductivity usually varies only slowly with temperature. Because of this, and because the term is not symmetric, it is usually more efficient to omit it. This term is omitted unless the unsymmetric solver is chosen. Prescribed surface fluxes and body fluxes can also be temperature dependent and will then give rise to Jacobian contributions.

With film and radiation conditions, the surface flux term gives a Jacobian contribution:

![](../graphics/stm_eqn02271.gif)For film conditions, ![](../graphics/stm_eqn02272.gif)

![](../graphics/stm_eqn02273.gif)while for radiation, ![](../graphics/stm_eqn02274.gif)

![](../graphics/stm_eqn02275.gif)These terms are included in exactly this form in the Jacobian. The modified Newton method is then

![](../graphics/stm_eqn02276.gif)For purely linear systems [Equation 2.11.1&#8211;7](02s11a43-Uncoupled-heat-transfer-analysis.md) is linear in ![](../graphics/stm_eqn02277.gif) and, hence, in ![](../graphics/stm_eqn02278.gif), so a single equation solution provides the ![](../graphics/stm_eqn02278.gif). Since the method usually is only a minor modification of Newton's method, convergence is rapid.

Abaqus/Standard uses an automatic (self-adaptive) time stepping algorithm to choose ![](../graphics/stm_eqn00883.gif). This is based on a user-supplied tolerance on the maximum temperature change allowed in a time increment, and the increment is adjusted according to this parameter, as well as the convergence rate of [Equation 2.11.1&#8211;7](02s11a43-Uncoupled-heat-transfer-analysis.md) in nonlinear cases.

The first-order heat transfer elements (such as 2-node link, 4-node quadrilateral, and 8-node brick) use a numerical integration rule with the integration stations located at the corners of the element for the heat capacitance terms. This means that the Jacobian term associated with the internal energy rate is diagonal. This approach is especially effective when strong latent heat effects are present. The second-order elements use conventional Gaussian integration. Thus, second-order elements are to be preferred for problems when the solution will be smooth (without latent heat effects), whereas the first-order elements should be used in nonsmooth cases (with latent heat).

The HEATCAP element is available for modeling lumped heat capacitance at a point. The associated concentrated film and concentrated radiation loading options are specified by the user. These loading options are also allowed in coupled temperature-displacement, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.
### Reference

### Reference

"Uncoupled heat transfer analysis,"  Section 6.5.2 of the Abaqus Analysis User's Guide