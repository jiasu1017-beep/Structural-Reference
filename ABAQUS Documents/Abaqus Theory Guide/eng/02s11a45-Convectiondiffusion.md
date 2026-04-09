# 2.11.3 Convection/diffusion

### 2.11.3 Convection/diffusion

**Product: **Abaqus/Standard

The formulation in this section describes a capability for modeling heat transfer with convection in Abaqus/Standard. The resulting elements can be used in any general heat transfer mesh. These elements have a nonsymmetric Jacobian matrix: the nonsymmetric capability is invoked automatically if elements of this type are included in the model. Both steady-state and transient capabilities are provided. The transient capability introduces a limit on the time increment (the limit is defined below): the time increment is adjusted to satisfy this limit if necessary. The steady-state versions of the elements can be used in a transient analysis, which means that transient effects in the fluid are not included in the model. The formulation is based on the work of Yu and Heinrich ([1986](07s01a01-References.md), [1987](07s01a01-References.md)).
### Thermal equilibrium equation

The thermal equilibrium equation for a continuum in which a fluid is flowing with velocity ![](../graphics/stm_eqn00427.gif), is

![](../graphics/stm_eqn02309.gif)where ![](../graphics/stm_eqn02310.gif) is the temperature at a point, ![](../graphics/stm_eqn02311.gif) is an arbitrary variational field, ![](../graphics/stm_eqn02312.gif) is the fluid density, ![](../graphics/stm_eqn02264.gif) is the specific heat of the fluid, ![](../graphics/stm_eqn02313.gif) is the conductivity of the fluid, *q* is the heat added per unit volume from external sources, ![](../graphics/stm_eqn02314.gif) is the heat flowing into the volume across the surface on which temperature is not prescribed (![](../graphics/stm_eqn02315.gif)), ![](../graphics/stm_eqn00483.gif) is the outward normal to the surface, ![](../graphics/stm_eqn00117.gif) is spatial position, and *t* is time. Although most fluids will have isotropic conductivity, so that ![](../graphics/stm_eqn02316.gif) (where ![](../graphics/stm_eqn02317.gif) is a scalar and ![](../graphics/stm_eqn00064.gif) is a unit matrix), we provide for anisotropic conductivity to cover such cases as that of fluid flowing through a set of baffle plates whose conductivity is smeared into that of the fluid.

The boundary conditions are that ![](../graphics/stm_eqn02318.gif) is prescribed over some part of the surface, ![](../graphics/stm_eqn02319.gif), and that the heat flux per unit area entering the domain across the rest of the surface, ![](../graphics/stm_eqn02320.gif), is prescribed or is defined by convection and/or radiation conditions. For example, the boundary layer between fluid convection elements and solid elements might be modeled by DINTER*x*-type elements. The boundary term in the thermal equilibrium equation defines

![](../graphics/stm_eqn02321.gif)This implies that ![](../graphics/stm_eqn02314.gif) is the flux associated with conduction across the surface only---any convection of energy across the surface is not included in ![](../graphics/stm_eqn02314.gif). This makes no difference if the surface is part of a solid body (where ![](../graphics/stm_eqn02314.gif) would be defined by heat transfer into the adjacent body), since then the normal velocity into that body, ![](../graphics/stm_eqn02322.gif), is zero. But it does make a difference when there is fluid crossing the surface, as---for example---on the upstream and downstream boundaries of the mesh. In this case the choice of ![](../graphics/stm_eqn02314.gif) for the natural boundary condition (instead of using the total flux crossing the surface) is desirable because it avoids spurious reflections of energy back into the mesh as the fluid flows through the surface.

These equations are discretized with respect to position by using first-order isoparametric elements. The fluid velocity, ![](../graphics/stm_eqn00427.gif), is assumed to be known. (Abaqus actually requires that the mass flow rate of the fluid per unit area be defined, because this is generally more convenient for the user. The velocity is computed from the mass flow rate and the density of the fluid.)

The time discretization generates the solution at time ![](../graphics/stm_eqn00438.gif) from the known solution at time *t*.

The interpolation for the temperature, ![](../graphics/stm_eqn01111.gif), is defined over an element and over a time increment as

![](../graphics/stm_eqn02323.gif)where the ![](../graphics/stm_eqn02249.gif) are standard isoparametric functions and the time interpolation, ![](../graphics/stm_eqn02324.gif), is linear:

![](../graphics/stm_eqn02325.gif)where ![](../graphics/stm_eqn00883.gif) is the time increment and ![](../graphics/stm_eqn00454.gif).

The Petrov-Galerkin discretization proposed by Yu and Heinrich couples this linear interpolation with the weighting functions

![](../graphics/stm_eqn02326.gif)where

![](../graphics/stm_eqn02327.gif)![](../graphics/stm_eqn02328.gif) is the average fluid velocity over the element; ![](../graphics/stm_eqn02329.gif) is its magnitude; and *h* is a characteristic element length measure, defined below. ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01219.gif) are control parameters. The ![](../graphics/stm_eqn00904.gif) term in the weighting is introduced to eliminate artificial diffusion of the solution, while the ![](../graphics/stm_eqn01219.gif) term is introduced to avoid numerical dispersion. Yu and Heinrich show that the optimal choices are

![](../graphics/stm_eqn02330.gif)where ![](../graphics/stm_eqn01256.gif) is the local Pclet number in an element and *C* is the local Courant number, defined as

![](../graphics/stm_eqn02331.gif)The above expression for ![](../graphics/stm_eqn01219.gif) yields negative values for very small fluid velocities, which may destabilize the solution; hence, for low velocities dispersion control is switched off.

The characteristic element length measure, *h*, is defined by Yu and Heinrich as follows.

Let ![](../graphics/stm_eqn02332.gif) be the ![](../graphics/stm_eqn00904.gif) isoparametric line across the element passing through its centroid. The projection of ![](../graphics/stm_eqn02332.gif) in the direction of the fluid velocity vector at the element's centroid is

![](../graphics/stm_eqn02333.gif)Then we define *h* as

![](../graphics/stm_eqn02334.gif)When ![](../graphics/stm_eqn01219.gif) is nonzero, these elements require that ![](../graphics/stm_eqn02335.gif) for numerical stability.

Since the weighting functions are biased ("upwinding"), they are discontinuous from one element to the next. Some care is, therefore, required in manipulating the weak form of the thermal equilibrium equation (see [Hughes and Brooks, 1982](07s01a01-References.md)). In particular, the usual integration by parts of the conduction term

![](../graphics/stm_eqn02336.gif)can be performed only for the continuous part of the weighting functions used to discretize ![](../graphics/stm_eqn02337.gif): otherwise, continuity of heat flux between elements is not assured. For convenience we write the discontinuous part of the weighting as

![](../graphics/stm_eqn02338.gif)

The weak form of thermal equilibrium is

![](../graphics/stm_eqn02339.gif)This can be rewritten as

![](../graphics/stm_eqn02340.gif)

![](../graphics/stm_eqn02341.gif)

We now integrate this equation from time *t* to ![](../graphics/stm_eqn00438.gif) to provide an average equilibrium statement for the increment. We use the results

![](../graphics/stm_eqn02342.gif)

![](../graphics/stm_eqn02343.gif)and

![](../graphics/stm_eqn02344.gif)to give

![](../graphics/stm_eqn02345.gif)

For the steady-state case the third term in this equation is omitted. In both transient and steady-state forms the contribution of such a convective element to the system of equations for the heat transfer model is not symmetric, requiring the use of the nonsymmetric matrix storage and solution scheme.
### Reference

### Reference

"Uncoupled heat transfer analysis,"  Section 6.5.2 of the Abaqus Analysis User's Guide