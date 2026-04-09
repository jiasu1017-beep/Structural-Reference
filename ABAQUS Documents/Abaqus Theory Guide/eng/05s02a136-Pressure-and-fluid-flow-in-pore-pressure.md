# 5.2.2 Pressure and fluid flow in pore pressure contact

### 5.2.2 Pressure and fluid flow in pore pressure contact

**Product: **Abaqus/Standard

Abaqus/Standard provides a surface-based capability for modeling fully saturated porous media. The surface-based capability can be used for small or finite sliding. Only flow normal to the surface is considered; tangential flow cannot be modeled.
### The pore fluid constraints on the contact interface for infinite interface permeability

Let ![](../graphics/stm_eqn07652.gif) and ![](../graphics/stm_eqn07653.gif) be the pore pressures at the two sides of the interface. If the interface permeability is considered infinite (i.e., no resistance to fluid flow), it is required at all times that the pore pressures on opposite sides be equal:

![](../graphics/stm_eqn07654.gif)Similarly, let ![](../graphics/stm_eqn05787.gif) and ![](../graphics/stm_eqn05788.gif) be the volume flow rate densities normal to the interface at the two sides, and let ![](../graphics/stm_eqn07655.gif) be the relative velocity of the two sides in the direction of the interface normal.

It is assumed that the interface is filled with fluid up to a separation threshold. Hence, continuity requires that

![](../graphics/stm_eqn07656.gif)whereas the difference corresponds to twice the flow across the interface.

![](../graphics/stm_eqn07657.gif)is undetermined and is to be treated as an independent variable in the case of infinite permeability. Inversion of these equations yields

![](../graphics/stm_eqn07658.gif)
### The pore fluid constraints on the contact interface for finite interface permeability

For finite gap permeability, ![](../graphics/stm_eqn02390.gif), the volume flow rate density directly across the interface is

![](../graphics/stm_eqn07659.gif)

It is assumed that the interface is filled with fluid up to a separation threshold. Hence, continuity requires that

![](../graphics/stm_eqn07660.gif)

Volume flow rate densities normal to the interface at the two sides of the interface are

![](../graphics/stm_eqn07661.gif)where

![](../graphics/stm_eqn07662.gif)![](../graphics/stm_eqn07663.gif) and ![](../graphics/stm_eqn07664.gif) are underlying material permeabilities.
### The transient equations

The contribution of the interfacial virtual work equation and its linearized form are first obtained in the general form including finite sliding. The equations are then specialized to the various formulations implemented in Abaqus.

Since we want to achieve force and volume flow rate equilibrium at each side of the interface, as well as obtain continuity in the pore pressures, we add the following integral to the virtual work equation:

![](../graphics/stm_eqn07665.gif)where ![](../graphics/stm_eqn02890.gif) is an arbitrary Lagrange multiplier and ![](../graphics/stm_eqn01047.gif) is the interface area. Eliminating ![](../graphics/stm_eqn05787.gif) and ![](../graphics/stm_eqn05788.gif) and using a suitable choice for ![](../graphics/stm_eqn02890.gif),

![](../graphics/stm_eqn07666.gif)we obtain

![](../graphics/stm_eqn07667.gif)where

![](../graphics/stm_eqn07668.gif)Since Abaqus uses displacements (not velocities) and fluxes integrated over ![](../graphics/stm_eqn00883.gif), the equation can be multiplied by ![](../graphics/stm_eqn00883.gif) to obtain

![](../graphics/stm_eqn07669.gif)where ![](../graphics/stm_eqn07670.gif) is the incremental change in ![](../graphics/stm_eqn07404.gif) in the direction of the interface normal. Linearization yields

![](../graphics/stm_eqn07671.gif)
### Closed contact

If the two sides are locally in contact, ![](../graphics/stm_eqn07672.gif) and ![](../graphics/stm_eqn06487.gif); therefore, the virtual work simplifies to

![](../graphics/stm_eqn07673.gif)Similarly, the linearized form simplifies to

![](../graphics/stm_eqn07674.gif)
### The steady-state equations

For steady-state analysis the transient terms can be omitted, and the terms involving fluid flow are written in rate form. In this case we can assume that the interface displacements vanish, which leads to the simplified virtual work contribution

![](../graphics/stm_eqn07675.gif)and the linearized form

![](../graphics/stm_eqn07676.gif)
### Small sliding

When the small-sliding contact formulation is used, the terms ![](../graphics/stm_eqn07677.gif), ![](../graphics/stm_eqn07678.gif), ![](../graphics/stm_eqn07679.gif), and ![](../graphics/stm_eqn07680.gif) in the linearized virtual work equation will vanish.
### Reference

### Reference

"Pore fluid contact properties,"  Section 37.4.1 of the Abaqus Analysis User's Guide