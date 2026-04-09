# 2.6.1 Direct steady-state dynamic analysis

### 2.6.1 Direct steady-state dynamic analysis

**Product: **Abaqus/Standard

For structures subjected to continuous harmonic excitation, Abaqus/Standard offers a "direct" steady-state dynamic analysis procedure in addition to the "modal" procedure described in "Steady-state linear dynamic analysis,"  Section 2.5.7, and the "subspace" procedure described in "Subspace-based steady-state dynamic analysis,"  Section 2.6.2. This procedure is a perturbation procedure, where the perturbed solution is obtained by linearization about the current base state. For the calculation of the base state the structure may exhibit material and geometrical nonlinear behavior as well as contact nonlinearities. Structural and viscous damping can be included in the procedure using the Rayleigh and structural damping coefficients specified under the material definition.  Discrete damping such as mass, dashpot, spring, and connector elements can be included. In addition, global damping coefficients ![](../graphics/stm_eqn01591.gif), ![](../graphics/stm_eqn01592.gif), and ![](../graphics/stm_eqn01593.gif) can be specified at the procedure level to define additional viscous and structural damping contributions. The procedure can also be used for coupled acoustic-structural medium analysis ("Coupled acoustic-structural medium analysis,"  Section 2.9.1), piezoelectric medium analysis ("Piezoelectric analysis,"  Section 2.10.1), and viscoelastic material modeling ("Frequency domain viscoelasticity,"  Section 4.8.3). All properties can be frequency dependent.

The formulation is based on the dynamic virtual work equation,

![](../graphics/stm_eqn01594.gif)where ![](../graphics/stm_eqn00116.gif) and ![](../graphics/stm_eqn00890.gif) are the velocity and the acceleration, ![](../graphics/stm_eqn00593.gif) is the density of the material, ![](../graphics/stm_eqn01595.gif) is the mass proportional damping factor (part of the Rayleigh damping assumption), ![](../graphics/stm_eqn00033.gif) is the stress, ![](../graphics/stm_eqn00479.gif) is the surface traction, and ![](../graphics/stm_eqn01596.gif) is the strain variation that is compatible with the displacement variation ![](../graphics/stm_eqn01597.gif). The discretized form of this equation is

![](../graphics/stm_eqn01598.gif)where the following definitions apply:

![](../graphics/stm_eqn01599.gif)

For the steady-state harmonic response we assume that the structure undergoes small harmonic vibrations about a deformed, stressed state, defined by the subscript *0*. Since steady-state dynamics is a perturbation procedure, the load and response in the step define the change from the base state. The change in internal force vector follows by linearization:

![](../graphics/stm_eqn01600.gif)The change in stress can be written in the form

![](../graphics/stm_eqn01601.gif)where ![](../graphics/stm_eqn01602.gif) is the elasticity matrix for the material, ![](../graphics/stm_eqn01603.gif) is the stiffness proportional damping factor (the other part of the Rayleigh damping assumption), and ![](../graphics/stm_eqn01604.gif) is the structural damping factor that forms the imaginary part of the stiffness matrix (known as the structural damping matrix). The strain and strain rate changes follow from the displacement and velocity changes:

![](../graphics/stm_eqn01605.gif)This allows us to write [Equation 2.6.1&#8211;2](02s06a33.md) as

![](../graphics/stm_eqn01606.gif)where we have defined the stiffness matrix

![](../graphics/stm_eqn01607.gif)the stiffness proportional viscous damping matrix

![](../graphics/stm_eqn01608.gif)and the stiffness proportional structural damping matrix

![](../graphics/stm_eqn01609.gif)

For harmonic excitation and response we can write

![](../graphics/stm_eqn01610.gif)and

![](../graphics/stm_eqn01611.gif)where ![](../graphics/stm_eqn01612.gif) and ![](../graphics/stm_eqn01613.gif) are the real and imaginary parts of the amplitudes of the displacement, ![](../graphics/stm_eqn01614.gif) and ![](../graphics/stm_eqn01615.gif) are the real and imaginary parts of the amplitude of the force applied to the structure, and ![](../graphics/stm_eqn01258.gif) is the circular frequency. Substituting the expressions for harmonic excitation and response in [Equation 2.6.1&#8211;4](02s06a33.md) and writing the result in matrix form yields

![](../graphics/stm_eqn01616.gif)where

![](../graphics/stm_eqn01617.gif)Both the real and imaginary parts of ![](../graphics/stm_eqn01618.gif) are symmetric.

The procedure is activated by defining a direct-solution steady-state dynamic analysis step. Both real and imaginary loads can be defined.

As output Abaqus/Standard provides amplitudes and phases for all element and nodal variables at the requested frequencies. For this procedure all amplitude references must be given in the frequency domain.
### Reference

### Reference

"Direct-solution steady-state dynamic analysis,"  Section 6.3.4 of the Abaqus Analysis User's Guide