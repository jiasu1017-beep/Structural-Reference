# 4.8.2 Finite-strain viscoelasticity

### 4.8.2 Finite-strain viscoelasticity

**Products: **Abaqus/Standard  Abaqus/Explicit
### Integral formulation

The finite-strain viscoelasticity theory implemented in Abaqus is a time domain generalization of either the hyperelastic or hyperfoam constitutive models. It is assumed that the instantaneous response of the material follows from the hyperelastic constitutive equations:

![](../graphics/stm_eqn07225.gif)for a compressible material and

![](../graphics/stm_eqn07226.gif)for an incompressible material. In the above, ![](../graphics/stm_eqn07227.gif) and ![](../graphics/stm_eqn07228.gif) are, respectively, the deviatoric and the hydrostatic parts of the instantaneous Kirchhoff stress ![](../graphics/stm_eqn07229.gif). ![](../graphics/stm_eqn07230.gif) is the "distortion gradient" related to the deformation gradient ![](../graphics/stm_eqn00319.gif) by

![](../graphics/stm_eqn07231.gif)where

![](../graphics/stm_eqn07232.gif)is the volume change.

Using integration by parts and a variable transformation, the basic hereditary integral formulation for linear isotropic viscoelasticity can be written in the form

![](../graphics/stm_eqn07233.gif)or entirely in terms of stress quantities,

![](../graphics/stm_eqn07234.gif)where ![](../graphics/stm_eqn01399.gif) is the reduced time, ![](../graphics/stm_eqn07235.gif), and ![](../graphics/stm_eqn07236.gif). ![](../graphics/stm_eqn07237.gif) and ![](../graphics/stm_eqn07020.gif) are the instantaneous small-strain shear and bulk moduli, and ![](../graphics/stm_eqn07159.gif) and ![](../graphics/stm_eqn07158.gif) are the time-dependent small-strain shear and bulk relaxation moduli. Recall that the reduced time represents a shift in time with temperature and is related to the actual time through the differential equation

![](../graphics/stm_eqn07238.gif)where ![](../graphics/stm_eqn01111.gif) is the temperature and ![](../graphics/stm_eqn07144.gif) is the shift function.

Using the volumetric/deviatoric-split hereditary integral in the reference configuration for large strain (hyperelastic) materials, and then using a standard push-forward operator (see [Simo, 1987](07s01a01-References.md)), one obtains the following set of equations in the current configuration:

![](../graphics/stm_eqn07239.gif)where ![](../graphics/stm_eqn07240.gif) and ![](../graphics/stm_eqn07241.gif) is the distortional deformation gradient of the state at ![](../graphics/stm_eqn07242.gif) relative to the state at *t* . A transformation is performed on the stress relating the state at time ![](../graphics/stm_eqn07243.gif) to the state at time *t*.
### Implementation

As in small-strain viscoelasticity, we represent the relaxation moduli in terms of the Prony series

![](../graphics/stm_eqn07244.gif)

![](../graphics/stm_eqn07245.gif)where ![](../graphics/stm_eqn05555.gif) and ![](../graphics/stm_eqn07246.gif) are the relative moduli of terms *i*. Note that ![](../graphics/stm_eqn07247.gif). Abaqus assumes that the relaxation times ![](../graphics/stm_eqn07248.gif) are the same so that from here on, we will sum on *N* terms for both bulk and shear behavior. In reality, the number of nonzero terms in bulk and shear, ![](../graphics/stm_eqn07249.gif) and ![](../graphics/stm_eqn07250.gif), need not be equal, unless the instantaneous behavior is based on the hyperfoam model. In the latter case, the two deformation modes are closely related and are then assumed to relax equally and simultaneously.

Substituting [Equation 4.8.2&#8211;2](04s08a129.md) and [Equation 4.8.2&#8211;3](04s08a129.md) in [Equation 4.8.2&#8211;1](04s08a129.md), we obtain

![](../graphics/stm_eqn07251.gif)

Next, we introduce the internal stresses, associated with each term of the series

![](../graphics/stm_eqn07252.gif)

![](../graphics/stm_eqn07253.gif)These stresses are stored at each material point and are integrated forward in time. We will assume that the solution is known at time *t*, and we need to construct the solution at time ![](../graphics/stm_eqn00438.gif).
### Integration of the hydrostatic stress

The internal hydrostatic stresses ![](../graphics/stm_eqn07254.gif) at time ![](../graphics/stm_eqn00438.gif) follow from

![](../graphics/stm_eqn07255.gif)With ![](../graphics/stm_eqn07256.gif) and ![](../graphics/stm_eqn07257.gif), it follows that

![](../graphics/stm_eqn07258.gif)which yields with [Equation 4.8.2&#8211;6](04s08a129.md)

![](../graphics/stm_eqn07259.gif)

To integrate the first integral in [Equation 4.8.2&#8211;7](04s08a129.md), we assume that ![](../graphics/stm_eqn07260.gif) varies linearly with the reduced time ![](../graphics/stm_eqn07261.gif) over the increment

![](../graphics/stm_eqn07262.gif)Substituting into [Equation 4.8.2&#8211;7](04s08a129.md) yields

![](../graphics/stm_eqn07263.gif)

The integrals are readily evaluated, providing the solution at the end of the increment

![](../graphics/stm_eqn07264.gif)or, in a slightly different form

![](../graphics/stm_eqn07265.gif)with

![](../graphics/stm_eqn07266.gif)Observe that for ![](../graphics/stm_eqn07267.gif), ![](../graphics/stm_eqn07268.gif) and ![](../graphics/stm_eqn07269.gif). For ![](../graphics/stm_eqn07270.gif), ![](../graphics/stm_eqn07271.gif) and ![](../graphics/stm_eqn07272.gif).
### Integration of the deviatoric stress

The internal deviatoric stresses ![](../graphics/stm_eqn07273.gif) at time ![](../graphics/stm_eqn07274.gif) follow from

![](../graphics/stm_eqn07275.gif)

Observe that

![](../graphics/stm_eqn07276.gif)and the inverse of this is

![](../graphics/stm_eqn07277.gif)which---when substituted into [Equation 4.8.2&#8211;10](04s08a129.md), with ![](../graphics/stm_eqn07278.gif) and ![](../graphics/stm_eqn07279.gif)---gives

![](../graphics/stm_eqn07280.gif)With ![](../graphics/stm_eqn07281.gif) and ![](../graphics/stm_eqn07282.gif), it follows:

![](../graphics/stm_eqn07283.gif)

Now introduce the variable

![](../graphics/stm_eqn07284.gif)Note that

![](../graphics/stm_eqn07285.gif)and

![](../graphics/stm_eqn07286.gif)

Then we can also introduce

![](../graphics/stm_eqn07287.gif)

Substitution of [Equation 4.8.2&#8211;5](04s08a129.md), [Equation 4.8.2&#8211;12](04s08a129.md), and [Equation 4.8.2&#8211;15](04s08a129.md) into [Equation 4.8.2&#8211;11](04s08a129.md) yields

![](../graphics/stm_eqn07288.gif)

To integrate the first integral in [Equation 4.8.2&#8211;16](04s08a129.md), we assume that ![](../graphics/stm_eqn07289.gif) varies linearly with the reduced time ![](../graphics/stm_eqn07261.gif) over the increment:

![](../graphics/stm_eqn07290.gif)which with [Equation 4.8.2&#8211;14](04s08a129.md) becomes

![](../graphics/stm_eqn07291.gif)

[Equation 4.8.2&#8211;16](04s08a129.md) and [Equation 4.8.2&#8211;17](04s08a129.md) for the deviatoric stress have exactly the same form as [Equation 4.8.2&#8211;7](04s08a129.md) and [Equation 4.8.2&#8211;8](04s08a129.md) for the hydrostatic stress. Hence, after integration we obtain

![](../graphics/stm_eqn07292.gif)with

![](../graphics/stm_eqn07293.gif)[Equation 4.8.2&#8211;13](04s08a129.md), [Equation 4.8.2&#8211;15](04s08a129.md), and [Equation 4.8.2&#8211;18](04s08a129.md), thus, provide a straightforward integration scheme.

The total stress at the end of the increment becomes

![](../graphics/stm_eqn07294.gif)which with [Equation 4.8.2&#8211;9](04s08a129.md) and [Equation 4.8.2&#8211;18](04s08a129.md) can also be written as

![](../graphics/stm_eqn07295.gif)
### Rate equation

To solve the system of nonlinear equations generated by the constitutive equations, we need to generate the corotational constitutive rate equations. From [Equation 4.8.2&#8211;20](04s08a129.md) it follows

![](../graphics/stm_eqn07296.gif)where ![](../graphics/stm_eqn07297.gif) is the corotational (Jaumann) stress rate. The rate form of the above equation is used to compute the Jacobian.
### Cauchy versus Kirchhoff stress

All equations have been worked out in terms of the Kirchhoff stress. However, the implementation in Abaqus uses the Cauchy stress. To transform to Cauchy stress, we use the relations

![](../graphics/stm_eqn07298.gif)

With ![](../graphics/stm_eqn07299.gif), this allows us to write [Equation 4.8.2&#8211;9](04s08a129.md), [Equation 4.8.2&#8211;13](04s08a129.md), [Equation 4.8.2&#8211;15](04s08a129.md), [Equation 4.8.2&#8211;18](04s08a129.md), and [Equation 4.8.2&#8211;19](04s08a129.md) in the following form:

![](../graphics/stm_eqn07300.gif)

![](../graphics/stm_eqn07301.gif)

The virtual work and rate of virtual work equations are written with respect to the current volume. Therefore, the corotational stress rates are rates of Kirchhoff stress mapped into the current configuration and transformed in the same way as the stresses themselves.

This set of equations---combined with the expressions for ![](../graphics/stm_eqn01123.gif), ![](../graphics/stm_eqn01120.gif), and ![](../graphics/stm_eqn05225.gif)---describe the full implementation of the hyper-viscoelasticity model in a displacement formulation.

The rate equations can be written in a form similar to "Hyperelastic material behavior,"  Section 4.6.1. Introduce

![](../graphics/stm_eqn07302.gif)and

![](../graphics/stm_eqn07303.gif)where ![](../graphics/stm_eqn07304.gif) and ![](../graphics/stm_eqn07020.gif) are the instantaneous moduli, corresponding to ![](../graphics/stm_eqn06754.gif) and ![](../graphics/stm_eqn07305.gif) of "Hyperelastic material behavior,"  Section 4.6.1. Thus, all rate equations can be obtained by substitution of ![](../graphics/stm_eqn07304.gif) by ![](../graphics/stm_eqn07306.gif) and ![](../graphics/stm_eqn07020.gif) by ![](../graphics/stm_eqn07307.gif).
### Reference

### Reference

"Time domain viscoelasticity,"  Section 22.7.1 of the Abaqus Analysis User's Guide