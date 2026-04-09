# 4.8.3 Frequency domain viscoelasticity

### 4.8.3 Frequency domain viscoelasticity

**Product: **Abaqus/Standard

Many applications of elastomers involve dynamic loading in the form of steady-state vibration, and often in such cases the dissipative losses in the material (the "viscous" part of the material's viscoelastic behavior) must be modeled to obtain useful results. In most problems of this class the structure is first preloaded statically, and this preloading generally involves large deformation of the elastomers. The response to that preloading is computed on the basis of purely elastic behavior in the elastomeric parts of the model---that is, we assume that the preloading is applied for a sufficiently long time so that any viscous response in the material has time to decay away.

The dynamic analysis problem in this case is, therefore, to investigate the dynamic, viscoelastic response about a predeformed elastic state. In some such cases we can reasonably assume that the vibration amplitude is sufficiently small that both the kinematic and material response in the dynamic phase of the problem can be treated as linear perturbations about the predeformed state. The small amplitude viscoelastic vibration capability provided in Abaqus/Standard, which is described in [Morman and Nagtegaal (1983)](07s01a01-References.md) and uses the procedure described in "Direct steady-state dynamic analysis,"  Section 2.6.1, is based on such a linearization. Its appropriateness to a particular application will depend on the magnitude of the vibration with respect to possible kinematic nonlinearities (the additional strains and rotations that occur during the dynamic loading must be small enough so that the linearization of the kinematics is reasonable) and with respect to possible nonlinearities in the material response, and on the particular constitutive assumptions incorporated in the viscoelastic model described in this section---in particular, the assumption of separation of prestrain and time effects described below.

In "Hyperelastic material behavior,"  Section 4.6.1, it is shown that the rate of change of the true (Cauchy) stress in an elastomeric material with a strain energy potential is given by

![](../graphics/stm_eqn07308.gif)for the deviatoric part of the stress and

![](../graphics/stm_eqn07309.gif)for the equivalent pressure stress in a compressible material. The various quantities in these equations are defined in "Hyperelastic material behavior,"  Section 4.6.1. For a fully incompressible material all components of ![](../graphics/stm_eqn06756.gif) are zero and the equivalent pressure stress is defined only by the loading of the structure, so that the second equation is not applicable.

For small viscoelastic vibrations about a predeformed state we linearize the additional motions that occur during the vibration so that the differential of a quantity in [Equation 4.8.3&#8211;1](04s08a130.md) and [Equation 4.8.3&#8211;2](04s08a130.md) can be interpreted as the additional incremental value,

![](../graphics/stm_eqn07310.gif)for any quantity *f*, where ![](../graphics/stm_eqn07311.gif) is the current value of *f* at some time during the vibration and ![](../graphics/stm_eqn07312.gif) is the reference value of *f*; that is, ![](../graphics/stm_eqn07312.gif) is the value of *f* at the end of the static (long term) preloading, about which *f* is fluctuating during the vibration.

The incremental elastic constitutive behavior for small added motions defined by this interpretation of [Equation 4.8.3&#8211;1](04s08a130.md) and [Equation 4.8.3&#8211;2](04s08a130.md) is now generalized to include viscous dissipation as well as elastic response in the material, following [Lianis (1965)](07s01a01-References.md), to give

![](../graphics/stm_eqn07313.gif)and, for a compressible material,

![](../graphics/stm_eqn07314.gif)

In these expressions ![](../graphics/stm_eqn07315.gif) is meant to indicate that *f* depends on the elastic predeformation that has occurred prior to the small dynamic vibrations (the state at ![](../graphics/stm_eqn07316.gif)) and is evaluated at time ![](../graphics/stm_eqn07317.gif), between the start of the vibrations and the current time, *t*. ![](../graphics/stm_eqn07318.gif) and ![](../graphics/stm_eqn04549.gif) are the functions that define the viscous part of the material's response: the notation is intended to imply that these are functions of the elastic predeformation and time. ![](../graphics/stm_eqn07319.gif) is the time rate of change of a quantity.

The definitions of the viscous parts of the behavior, ![](../graphics/stm_eqn07318.gif) and ![](../graphics/stm_eqn04549.gif), provided in Abaqus are simplified by assuming that this viscous behavior exhibits separation of time and prestrain effects; that is, that

![](../graphics/stm_eqn07320.gif)and

![](../graphics/stm_eqn07321.gif)where ![](../graphics/stm_eqn07322.gif) and ![](../graphics/stm_eqn07323.gif) are the "effective elasticity" of the material in its predeformed state, prior to the vibration. This assumption simply means that measurements of the viscous behavior during small motions of the material about a predeformed state depend only on the predeformation to the extent that the effective elasticity of the material also depends on that predeformation. There is experimental evidence that this simplification is appropriate for some practical materials (see [Morman's (1979) ](07s01a01-References.md)discussion). With this assumption the definition of the viscous part of the material's behavior is reduced to finding the scalar functions of time, *g* and *k* (only *g* for fully incompressible materials), and the constitutive response to small perturbations is simplified to

![](../graphics/stm_eqn07324.gif)and, for compressible materials,

![](../graphics/stm_eqn07325.gif)

In Abaqus this model is provided only for the direct-solution and subspace-based steady-state dynamic analysis procedures, in which we assume that the dynamic response is steady-state harmonic vibration, so that we can write

![](../graphics/stm_eqn07326.gif)where ![](../graphics/stm_eqn07327.gif) is the complex amplitude of a variable *f*.

Defining the Fourier transforms of the viscous relaxation functions ![](../graphics/stm_eqn00713.gif) and ![](../graphics/stm_eqn07328.gif) as

![](../graphics/stm_eqn07329.gif)and

![](../graphics/stm_eqn07330.gif)allows the constitutive model to be written for such harmonic motions in the linear form

![](../graphics/stm_eqn07331.gif)and

![](../graphics/stm_eqn07332.gif)and, for compressible materials,

![](../graphics/stm_eqn07333.gif)and

![](../graphics/stm_eqn07334.gif)

The viscous behavior of the material is, thus, reduced to defining ![](../graphics/stm_eqn07335.gif), ![](../graphics/stm_eqn07336.gif), ![](../graphics/stm_eqn07337.gif), and ![](../graphics/stm_eqn07338.gif) as functions of frequency.

When the pure displacement formulation is used for a compressible material, the virtual work equation for dynamic response is

![](../graphics/stm_eqn07339.gif)where

![](../graphics/stm_eqn07340.gif)is the internal virtual work,

![](../graphics/stm_eqn07341.gif)is the virtual work of the d'Alembert forces (![](../graphics/stm_eqn07342.gif) is the mass density of the material in the original configuration), and

![](../graphics/stm_eqn07343.gif)is the virtual work of externally prescribed surface tractions ![](../graphics/stm_eqn00156.gif) per current surface area and body forces ![](../graphics/stm_eqn00480.gif) per current volume.

For the linearized perturbations considered here we recast [Equation 4.8.3&#8211;3](04s08a130.md) in incremental form, giving

![](../graphics/stm_eqn07344.gif)where ![](../graphics/stm_eqn07345.gif) is obtained from [Equation 4.6.1&#8211;12](04s06a123.md) with the interpretation ![](../graphics/stm_eqn07346.gif);

![](../graphics/stm_eqn07347.gif)and

![](../graphics/stm_eqn07348.gif)where

![](../graphics/stm_eqn07349.gif)in which

![](../graphics/stm_eqn07350.gif)is the ratio of current to reference surface area;

![](../graphics/stm_eqn07351.gif)

![](../graphics/stm_eqn07352.gif)

![](../graphics/stm_eqn07353.gif)and *p* and *f* are the externally prescribed tractions, so that ![](../graphics/stm_eqn01051.gif) and ![](../graphics/stm_eqn01224.gif) are externally prescribed traction increments. Note that ![](../graphics/stm_eqn07354.gif) includes terms dependent on ![](../graphics/stm_eqn07355.gif): these give rise to the "load stiffness matrix" when the finite element interpolations are introduced.

When the motion is harmonic we can recast these quantities as

![](../graphics/stm_eqn07356.gif)where

![](../graphics/stm_eqn07357.gif)

![](../graphics/stm_eqn07358.gif)and

![](../graphics/stm_eqn07359.gif)

In these expressions ![](../graphics/stm_eqn07360.gif) and ![](../graphics/stm_eqn07361.gif) are understood to be independent variations. Thus, when the finite element displacement interpolations are introduced into [Equation 4.8.3&#8211;4](04s08a130.md), we obtain a linear, frequency-dependent system that can be solved at each frequency for the real and imaginary parts of the nodal degrees of freedom of the model. In like fashion, the augmented variational principles for almost incompressible behavior and for fully incompressible behavior described in "Hyperelastic material behavior,"  Section 4.6.1, can be used to obtain linear, frequency-dependent systems for harmonic viscoelastic vibration problems. The steady-state dynamic analysis procedure based on modal superposition cannot be used because the viscous behavior assumed does not correspond to a small amount of Rayleigh damping, which is a requirement for steady-state harmonic response based on modal superposition.
### Reference

### Reference

"Frequency domain viscoelasticity,"  Section 22.7.2 of the Abaqus Analysis User's Guide