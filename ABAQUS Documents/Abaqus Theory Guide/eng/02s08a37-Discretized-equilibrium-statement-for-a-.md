# 2.8.2 Discretized equilibrium statement for a porous medium

### 2.8.2 Discretized equilibrium statement for a porous medium

**Product: **Abaqus/Standard

Equilibrium is expressed by writing the principle of virtual work for the volume under consideration in its current configuration at time *t*:

![](../graphics/stm_eqn01743.gif)where ![](../graphics/stm_eqn00140.gif) is a virtual velocity field, ![](../graphics/stm_eqn01744.gif) is the virtual rate of deformation, ![](../graphics/stm_eqn00033.gif) is the true (Cauchy) stress, ![](../graphics/stm_eqn00479.gif) are surface tractions per unit area, and ![](../graphics/stm_eqn01745.gif) are body forces per unit volume.

For our system ![](../graphics/stm_eqn01746.gif) will often include the weight of the wetting liquid,

![](../graphics/stm_eqn01747.gif)where ![](../graphics/stm_eqn01748.gif) is the density of the wetting liquid and ![](../graphics/stm_eqn00678.gif) is the gravitational acceleration, which we assume to be constant and in a constant direction (so that, for example, the formulation cannot be applied directly to a centrifuge experiment unless the model in the machine is small enough that ![](../graphics/stm_eqn00678.gif) can be treated as constant). For simplicity we consider this loading explicitly so that any other gravitational term in ![](../graphics/stm_eqn01746.gif) is associated only with the weight of the dry porous medium. Thus, we write the virtual work equation as

![](../graphics/stm_eqn01749.gif)where ![](../graphics/stm_eqn00480.gif) are all body forces except the weight of the wetting liquid.

In a finite element model equilibrium is approximated as a finite set of equations by introducing interpolation functions. The notation used to indicate such discretization are those quantities with uppercase superscripts (for example, ![](../graphics/stm_eqn01750.gif)), which represent nodal variables, with the summation convention adopted for the superscripts. The interpolation is assumed to be based on material coordinates in the material skeleton (a "Lagrangian" formulation).

For simplicity, in this section we consider only the case where the problem has no internal constraints---such as incompressibility---and the discretization is made entirely by approximating equilibrium: this results in the displacement (or stiffness) method. Mixed formulation ("hybrid") elements are available for porous medium analysis with Abaqus/Standard, but consideration of such formulations does not require any important extension of the development at this stage.

The virtual velocity field is interpolated by

![](../graphics/stm_eqn01751.gif)where ![](../graphics/stm_eqn01752.gif) are interpolation functions defined with respect to material coordinates, ![](../graphics/stm_eqn00981.gif).

The virtual rate of deformation is interpolated as

![](../graphics/stm_eqn01753.gif)where, in the simplest case,

![](../graphics/stm_eqn01754.gif)although more general forms are used in some of the elements in Abaqus.

The virtual work equation is thus discretized as

![](../graphics/stm_eqn01755.gif)where the ![](../graphics/stm_eqn00660.gif) are assumed to be independent.

The term conjugate to ![](../graphics/stm_eqn00660.gif) on the left-hand side of this equation is referred to subsequently as the internal force array, ![](../graphics/stm_eqn01215.gif):

![](../graphics/stm_eqn01756.gif)

Likewise, the external force array, ![](../graphics/stm_eqn00868.gif), is taken from the right-hand side:

![](../graphics/stm_eqn01757.gif)(![](../graphics/stm_eqn00868.gif) includes any d'Alembert forces).

Choosing each ![](../graphics/stm_eqn00660.gif) to be nonzero in turn expresses equilibrium as a balance of internal and external forces:

![](../graphics/stm_eqn01758.gif)

These discretized equilibrium equations, together with the continuity equation discussed in "Continuity statement for the wetting liquid phase in a porous medium,"  Section 2.8.4, define the state of the porous medium. The equilibrium equations are written at the end of a time increment when implicit integration is used and, for all but the simplest cases, they are nonlinear. Newton's method is often used for their solution. Also, small, linear perturbations of the system are sometimes of interest (an example is the small vibration problem). These considerations imply a need for the Jacobian matrix of the system, which defines the variation of each term in the equations with respect to the basic variables of the discretized problem, which---for this case---are the nodal positions, ![](../graphics/stm_eqn01759.gif) (or, equivalently, the displacements ![](../graphics/stm_eqn01760.gif)), and the nodal wetting liquid pressure values, ![](../graphics/stm_eqn01761.gif). Symbolically we write such a variation of a term, *f* say, as ![](../graphics/stm_eqn01762.gif), meaning

![](../graphics/stm_eqn01763.gif)

From the variation of discretized equilibrium, [Equation 2.8.2&#8211;2](02s08a37.md), the term ![](../graphics/stm_eqn01764.gif) gives rise to the mass matrix (for the d'Alembert forces) and the "load stiffness matrix" in the Jacobian. The load stiffness matrix is discussed in Chapter 3, "Elements," and Chapter 6, "Loading and Constraints," for particular load types. The load stiffness term associated with the weight of the wetting liquid is

![](../graphics/stm_eqn01765.gif)where

![](../graphics/stm_eqn01766.gif)is the ratio of volume in the current configuration to volume in the reference configuration.

The term ![](../graphics/stm_eqn01767.gif) is

![](../graphics/stm_eqn01768.gif)

The first term includes ![](../graphics/stm_eqn01769.gif), which is the variation of stress caused by variations in nodal positions and pore liquid pressure values. In a continuum sense (that is, before the spatial discretization of the solution variables) this term is defined by the effective stress principle and by the constitutive assumptions used for the material and is discussed in more detail below. Introducing the spatial discretization into the second term provides a contribution to the initial stress matrix.

Since the effective stress, ![](../graphics/stm_eqn01727.gif), is generally stored as components associated with spatial directions, the rotation of the material during an increment must be included in the formulation. This issue is discussed in detail in "Rate of deformation and strain increment,"  Section 1.4.3; "Stress rates,"  Section 1.5.3; "State storage,"  Section 1.5.4; and "Solid element formulation,"  Section 3.2.2. For the purpose of the present development we assume that the variation of stress is

![](../graphics/stm_eqn01770.gif)where ![](../graphics/stm_eqn01771.gif) is the variation in effective stress associated with constitutive response in the material (that is, caused by variations in the strain or other state variables) and ![](../graphics/stm_eqn01772.gif) is the spin of the material. Using this assumption, the Jacobian contribution from stress in the porous medium is

![](../graphics/stm_eqn01773.gif)where ![](../graphics/stm_eqn01774.gif) is the strain rate (the "rate of deformation") so that

![](../graphics/stm_eqn01775.gif)
### References

### References

"Coupled pore fluid diffusion and stress analysis,"  Section 6.8.1 of the Abaqus Analysis User's Guide

"Geostatic stress state,"  Section 6.8.2 of the Abaqus Analysis User's Guide