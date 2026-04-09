# 6.2.3 Stokes wave theory

### 6.2.3 Stokes wave theory

**Product: **Abaqus/Aqua

Assume that an infinite series of plane, uniform waves travels through the fluid in the positive *S*-direction. The *z*-coordinate is chosen to be positive in the vertical direction, so the gravity potential is ![](../graphics/stm_eqn08025.gif), where ![](../graphics/stm_eqn01197.gif) is an arbitrary datum.

Assume that the fluid is inviscid and incompressible. The fluid particle velocities are derivable from a flow potential

![](../graphics/stm_eqn08026.gif)

![](../graphics/stm_eqn08027.gif)Equilibrium is

![](../graphics/stm_eqn08028.gif)where ![](../graphics/stm_eqn00593.gif) is the fluid density and *p* is the pressure. Writing ![](../graphics/stm_eqn08029.gif) in terms of the flow potential then gives

![](../graphics/stm_eqn08030.gif)Integrating with respect to ![](../graphics/stm_eqn00117.gif) (note that ![](../graphics/stm_eqn00593.gif) is constant since the fluid is incompressible) gives the Bernoulli equation

![](../graphics/stm_eqn08031.gif)where ![](../graphics/stm_eqn00739.gif) is an arbitrary function (which for convenience is set to zero) and ![](../graphics/stm_eqn01918.gif) is the atmospheric pressure. Substituting in the gravity potential, this is

![](../graphics/stm_eqn08032.gif)where ![](../graphics/stm_eqn07970.gif) is the undisturbed surface level. From this equation the total pressure at a point below the instantaneous fluid surface is

![](../graphics/stm_eqn07972.gif)Hence, the total pressure is the air pressure plus the hydrostatic pressure plus the dynamic pressure, ![](../graphics/stm_eqn07973.gif), where ![](../graphics/stm_eqn07973.gif) is given by

![](../graphics/stm_eqn08033.gif)

Let ![](../graphics/stm_eqn02098.gif) be the elevation of the free surface above this level. At the free surface the Bernoulli equation is

![](../graphics/stm_eqn08034.gif)assuming the pressure at the surface is negligible.

Assuming the waves are uniform, of wavelength ![](../graphics/stm_eqn00280.gif) and period ![](../graphics/stm_eqn01399.gif), and that they travel in the positive *S*-direction means that the solution as a function of *S* and *t* must appear in terms of a phase angle

![](../graphics/stm_eqn08035.gif)where ![](../graphics/stm_eqn08036.gif) is the wave celerity. This means that, for any function in the solution,

![](../graphics/stm_eqn08037.gif)Thus, at the free surface boundary

![](../graphics/stm_eqn08038.gif)and the Bernoulli equation at the free surface is

![](../graphics/stm_eqn08039.gif)or

![](../graphics/stm_eqn08040.gif)A further boundary condition at the free surface is that the fluid particle velocity relative to the wave celerity must be tangential to the slope of the wave:

![](../graphics/stm_eqn08041.gif)At the seabed ![](../graphics/stm_eqn08042.gif), there is no fluid motion in the vertical direction:

![](../graphics/stm_eqn08043.gif)The problem now consists of finding a potential function, ![](../graphics/stm_eqn00155.gif), that satisfies [Equation 6.2.3&#8211;1](06s02a146.md)---the boundary condition at the seabed---as well as the boundary conditions at the surface---[Equation 6.2.3&#8211;2](06s02a146.md) and [Equation 6.2.3&#8211;3](06s02a146.md).

Stokes proposed a power series solution to this problem, and [Skjelbreia and Hendrickson (1960)](07s01a01-References.md) have obtained that solution to fifth-order. The potential function is assumed to be

![](../graphics/stm_eqn08044.gif)where ![](../graphics/stm_eqn08045.gif), the ![](../graphics/stm_eqn08046.gif) are constants that depend on the ratio of water depth to wavelength ![](../graphics/stm_eqn08047.gif), and ![](../graphics/stm_eqn01087.gif) is a parameter. The wave profile, ![](../graphics/stm_eqn08048.gif), is assumed to be

![](../graphics/stm_eqn08049.gif)where the ![](../graphics/stm_eqn08050.gif) are constants for a given water depth and wavelength. Finally, it is assumed that

![](../graphics/stm_eqn08051.gif)and that

![](../graphics/stm_eqn08052.gif)

Skjelbreia and Hendrickson obtain the 18 constants ![](../graphics/stm_eqn08053.gif), ![](../graphics/stm_eqn05224.gif), and ![](../graphics/stm_eqn06387.gif) from matching terms in equal powers of ![](../graphics/stm_eqn01087.gif) and ![](../graphics/stm_eqn08054.gif) in the free surface boundary conditions, [Equation 6.2.3&#8211;2](06s02a146.md) and [Equation 6.2.3&#8211;3](06s02a146.md). They give the constants as functions of ![](../graphics/stm_eqn08055.gif) as

![](../graphics/stm_eqn08056.gif)

![](../graphics/stm_eqn08057.gif)

[Skjelbreia and Hendrickson (1960)](07s01a01-References.md) have a factor +2592 multiplying ![](../graphics/stm_eqn08058.gif) in the equation for ![](../graphics/stm_eqn07154.gif). This was corrected to 2592 by [Nishimura et al. (1970)](07s01a01-References.md).

They then obtain equations for ![](../graphics/stm_eqn08059.gif) and ![](../graphics/stm_eqn01087.gif). The wave height is

![](../graphics/stm_eqn08060.gif)so [Equation 6.2.3&#8211;5](06s02a146.md) gives

![](../graphics/stm_eqn08061.gif)Also, the form assumed for the wave celerity gives

![](../graphics/stm_eqn08062.gif)Given the wave period, wave height, and water depth, [Equation 6.2.3&#8211;7](06s02a146.md) and [Equation 6.2.3&#8211;8](06s02a146.md) must be solved simultaneously for the wavelength, ![](../graphics/stm_eqn00280.gif), and the parameter ![](../graphics/stm_eqn01087.gif). This is done with a Newton method, using the Airy (linear) wave solution as an initial guess.
### Fluid particle velocities and accelerations for Stokes 5th order wave

The flow potential has been approximated as

![](../graphics/stm_eqn08063.gif)where

![](../graphics/stm_eqn08064.gif)The fluid particle velocities are

![](../graphics/stm_eqn08065.gif)and the fluid particle accelerations are

![](../graphics/stm_eqn08066.gif)Since the solution appears in terms of the phase angle ![](../graphics/stm_eqn01111.gif), it follows that

![](../graphics/stm_eqn08067.gif)This allows the acceleration components to be written as

![](../graphics/stm_eqn08068.gif)Recall the expression for the dynamic pressure:

![](../graphics/stm_eqn08069.gif)Substitution of the expression for ![](../graphics/stm_eqn00155.gif) yields:

![](../graphics/stm_eqn08070.gif)where

![](../graphics/stm_eqn08071.gif)

![](../graphics/stm_eqn08072.gif) Finally, the surface position is given as

![](../graphics/stm_eqn08073.gif)where

![](../graphics/stm_eqn08074.gif)

The Stokes wave field is a spatial description of the wave field. All wave field quantities are calculated up to the instantaneous fluid level. The wave field defines velocity, acceleration, and dynamic pressure at spatial locations for all values of time. Hence, the velocity, acceleration, and dynamic pressure are determined by using the current (for geometrically nonlinear analysis) or reference (for geometrically linear analysis) location of the structure at the current time in the appropriate equations. The time used in the wave field equations is the total time for the analysis, which accumulates over all steps in the analysis (static, dynamic, etc.).
### Reference

### Reference

"Abaqus/Aqua analysis,"  Section 6.11.1 of the Abaqus Analysis User's Guide