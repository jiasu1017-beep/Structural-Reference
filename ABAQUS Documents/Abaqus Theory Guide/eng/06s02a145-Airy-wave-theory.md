# 6.2.2 Airy wave theory

### 6.2.2 Airy wave theory

**Product: **Abaqus/Aqua

This is a linearized wave theory based on irrotational flow of an inviscid incompressible fluid. The linearization is achieved by assuming the wave height *a* is small compared to the wavelength ![](../graphics/stm_eqn00280.gif) and the still water depth. It is also assumed that the fluid is of uniform depth (that is, the bottom is flat).

Since we have irrotational flow, there exists a flow potential, ![](../graphics/stm_eqn00155.gif), obeying

![](../graphics/stm_eqn07962.gif)and giving the fluid particle velocities as

![](../graphics/stm_eqn07963.gif)

Now assume there is a potential energy per unit mass, *G*, (in this case associated with the gravity field). Then, equilibrium is given by

![](../graphics/stm_eqn07964.gif)where ![](../graphics/stm_eqn00593.gif) is the fluid density and *p* is the pressure. Substituting [Equation 6.2.2&#8211;2](06s02a145.md) in [Equation 6.2.2&#8211;3](06s02a145.md), we obtain

![](../graphics/stm_eqn07965.gif)This equation can be integrated with respect to position to give

![](../graphics/stm_eqn07966.gif)since the fluid is assumed to be incompressible; thus, ![](../graphics/stm_eqn00593.gif) is constant. Here *F* is an arbitrary function of *t* and ![](../graphics/stm_eqn01918.gif) is the pressure in the air just above the free surface. For convenience we choose ![](../graphics/stm_eqn07967.gif)

The term ![](../graphics/stm_eqn07968.gif) can be neglected compared to the other terms (this can be shown, from the resulting solution, to be consistent with the order of approximation that the wave height is small compared to the wavelength). By choosing the *z*-coordinate to point vertically upward, the gravity potential is conveniently chosen as

![](../graphics/stm_eqn07969.gif)where ![](../graphics/stm_eqn07970.gif) is the undisturbed surface level. [Equation 6.2.2&#8211;4](06s02a145.md) then becomes

![](../graphics/stm_eqn07971.gif)From this equation the total pressure at a point below the instantaneous fluid surface is

![](../graphics/stm_eqn07972.gif)Hence, the total pressure is the air pressure plus the hydrostatic pressure plus the dynamic pressure, ![](../graphics/stm_eqn07973.gif), where ![](../graphics/stm_eqn07973.gif) is given by

![](../graphics/stm_eqn07974.gif)

Let ![](../graphics/stm_eqn02098.gif) be the elevation of the fluid surface at time *t* above the mean (undisturbed) fluid surface level, ![](../graphics/stm_eqn07970.gif). Since the position of the free surface is a part of the solution, there are two boundary conditions that must be applied on ![](../graphics/stm_eqn07975.gif). The first is a dynamic equilibrium condition at the interface between the fluid and the air. Since the interface is assumed to have no mass, the forces normal to the interface in the fluid and the air must be equal. If the surface tension of the interface is neglected, the pressure in the water and the air must be equal at the interface. Assuming that the pressure due to the motion of the air is negligible (which can be shown to be reasonable), the air pressure can be approximated by its undisturbed value ([Whitham, 1974](07s01a01-References.md)). The dynamic boundary condition then implies ![](../graphics/stm_eqn07976.gif), where *p* is the pressure in the water at the free surface and ![](../graphics/stm_eqn01918.gif) is the pressure in the undisturbed air. Since ![](../graphics/stm_eqn07107.gif) is assumed to be small with respect to the depth of fluid, the boundary condition can be made linear by applying it at ![](../graphics/stm_eqn07977.gif) instead of at ![](../graphics/stm_eqn07978.gif).

With these assumptions [Equation 6.2.2&#8211;5](06s02a145.md) provides the boundary term

![](../graphics/stm_eqn07979.gif)

The second boundary condition on the free surface comes from the kinematics of the free surface. Let the free surface be given by

![](../graphics/stm_eqn07980.gif)The velocity of the fluid normal to the surface must be equal to the velocity of the surface normal to itself.

Differentiating this expression with respect to time yields

![](../graphics/stm_eqn07981.gif)If we assume that the wave height is small compared to the wavelength ![](../graphics/stm_eqn07982.gif) then we can approximate ![](../graphics/stm_eqn07983.gif) by the velocity ![](../graphics/stm_eqn07984.gif), so that

![](../graphics/stm_eqn07985.gif)Eliminating ![](../graphics/stm_eqn02098.gif) between [Equation 6.2.2&#8211;6](06s02a145.md) and [Equation 6.2.2&#8211;7](06s02a145.md) gives

![](../graphics/stm_eqn07986.gif)The boundary condition on the bottom, ![](../graphics/stm_eqn07987.gif), is

![](../graphics/stm_eqn07988.gif)

The problem is now defined by [Equation 6.2.2&#8211;1](06s02a145.md), [Equation 6.2.2&#8211;8](06s02a145.md), [Equation 6.2.2&#8211;9](06s02a145.md), and the requirement that the solution be a plane wave periodic in the horizontal plane, such that

![](../graphics/stm_eqn07989.gif)where ![](../graphics/stm_eqn02568.gif) is the direction of wave propagation and *c* is the wave speed.

We solve the problem by assuming that ![](../graphics/stm_eqn07990.gif). Since *P* and ![](../graphics/stm_eqn05209.gif) are independent functions, [Equation 6.2.2&#8211;1](06s02a145.md) provides the two equations

![](../graphics/stm_eqn07991.gif)where *k* is a constant.

Let ![](../graphics/stm_eqn07992.gif) (so that *s* measures distance in the direction of travel of the wave). The solution to these equations is ![](../graphics/stm_eqn07993.gif) and ![](../graphics/stm_eqn07994.gif) hence,

![](../graphics/stm_eqn07995.gif)where ![](../graphics/stm_eqn07919.gif) and ![](../graphics/stm_eqn07920.gif) are constants and ![](../graphics/stm_eqn00904.gif) is the phase angle of the wave in degrees (![](../graphics/stm_eqn00904.gif) provides an arbitrary choice of origin in time and is chosen so that the vertical displacement of a fluid particle is a minimum when ![](../graphics/stm_eqn03287.gif), ![](../graphics/stm_eqn07316.gif), and ![](../graphics/stm_eqn07996.gif)).

There is no motion at the bottom of the fluid in the vertical direction, so by [Equation 6.2.2&#8211;9](06s02a145.md) we find

![](../graphics/stm_eqn07997.gif)

Substituting this into [Equation 6.2.2&#8211;10](06s02a145.md) gives

![](../graphics/stm_eqn07998.gif)where *C* is a constant.

The dispersion relation can be obtained by substituting [Equation 6.2.2&#8211;11](06s02a145.md) into [Equation 6.2.2&#8211;8](06s02a145.md) and setting ![](../graphics/stm_eqn07977.gif), giving

![](../graphics/stm_eqn07999.gif)The wave frequency ![](../graphics/stm_eqn01091.gif) is related to the wave period ![](../graphics/stm_eqn01399.gif) by ![](../graphics/stm_eqn08000.gif). The constant *k* is called the wave number and is related to the wavelength ![](../graphics/stm_eqn00280.gif) by ![](../graphics/stm_eqn08001.gif), so that ![](../graphics/stm_eqn08002.gif).

The free surface elevation above the undisturbed fluid surface, ![](../graphics/stm_eqn02098.gif), is given by [Equation 6.2.2&#8211;6](06s02a145.md):

![](../graphics/stm_eqn08003.gif)Writing the wave amplitude (half the wave height) as *a*, this defines

![](../graphics/stm_eqn08004.gif)so that [Equation 6.2.2&#8211;11](06s02a145.md) can be rewritten

![](../graphics/stm_eqn08005.gif)

This solution provides fluid particle velocities ![](../graphics/stm_eqn08006.gif) and accelerations throughout the fluid for this one wave component. The term ![](../graphics/stm_eqn08007.gif) in [Equation 6.2.2&#8211;4](06s02a145.md) was neglected because the wave amplitude *a* is small compared to the wavelength ![](../graphics/stm_eqn00280.gif). This implies, from [Equation 6.2.2&#8211;3](06s02a145.md), that the fluid particle acceleration is approximated as ![](../graphics/stm_eqn08008.gif); that is, the convective part of the acceleration, ![](../graphics/stm_eqn08009.gif), is neglected.

Since the theory is linear, any set of waves can be superposed by linear superposition of its components:

![](../graphics/stm_eqn08010.gif)where ![](../graphics/stm_eqn02820.gif) is the potential [Equation 6.2.2&#8211;10](06s02a145.md) of the ![](../graphics/stm_eqn00695.gif) wave component. Hence, the theory can be summarized as follows.

For ![](../graphics/stm_eqn08011.gif):

Velocity potential:

![](../graphics/stm_eqn08012.gif)Fluid particle displacements:

horizontally,

![](../graphics/stm_eqn08013.gif)

and vertically,

![](../graphics/stm_eqn08014.gif)Fluid particle velocities:

horizontally,

![](../graphics/stm_eqn08015.gif)

and vertically,

![](../graphics/stm_eqn08016.gif)

Fluid particle accelerations:

horizontally,

![](../graphics/stm_eqn08017.gif)

and vertically,

![](../graphics/stm_eqn08018.gif)

Free surface profile:

![](../graphics/stm_eqn08019.gif)Dispersion relation for each mode:

![](../graphics/stm_eqn08020.gif)Dynamic pressure:

![](../graphics/stm_eqn08021.gif)

Airy wave theory is a linearized theory; however, the wave amplitude can be large compared with the size of a structure. We, therefore, must make an assumption about the wave kinematics below a crest and above the mean water level. The assumption used here follows modified Airy wave theory as described in [Hansen (1988)](07s01a01-References.md) and [Faltinsen (1990)](07s01a01-References.md). The free surface boundary condition has been made linear in [Equation 6.2.2&#8211;6](06s02a145.md). Above the mean or undisturbed surface level ![](../graphics/stm_eqn07970.gif) the velocity, acceleration, and dynamic pressure are extrapolated from their values at the mean surface level. Hence, for ![](../graphics/stm_eqn08022.gif)

![](../graphics/stm_eqn08023.gif)Accordingly,

![](../graphics/stm_eqn08024.gif)

When a gravity wave is defined, the penetration of the structure into the fluid must be calculated. Although the Airy wave theory assumes that the fluid displacements are small with respect to the wavelength and the fluid depth, they cannot be small with respect to the dimensions of the structure immersed in the fluid. Hence, the instantaneous fluid surface is used to determine if a point on the structure sees loads due to the presence of the fluid.

The Airy wave field is a spatial description of the wave field. The wave field defines velocity, acceleration, and dynamic pressure at spatial locations for all values of time. Hence, the velocity, acceleration, and dynamic pressure are determined by using the current (for geometrically nonlinear analysis) or reference (for geometrically linear analysis) location of the structure at the current time in the appropriate equations. The time used in the wave field equations is the total time for the analysis, which accumulates over all steps in the analysis (static, dynamic, etc.).
### Reference

### Reference

"Abaqus/Aqua analysis,"  Section 6.11.1 of the Abaqus Analysis User's Guide