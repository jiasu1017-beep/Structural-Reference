# 5.2.4 Thermal interface definition

### 5.2.4 Thermal interface definition

**Products: **Abaqus/Standard  Abaqus/Explicit

Abaqus/Standard allows heat flow across an interface via conduction or radiation. Generally, both modes of heat transfer are present to some degree. Regardless of the mode, heat transfer across the interface is assumed to occur only in the normal direction.
### Conduction

Heat conduction across the interface is assumed to be defined by

![](../graphics/stm_eqn07777.gif)where ![](../graphics/stm_eqn02389.gif) is the heat flux per unit area crossing the interface from point ![](../graphics/stm_eqn01047.gif) on one surface to point ![](../graphics/stm_eqn07778.gif) on the other, ![](../graphics/stm_eqn05050.gif) and ![](../graphics/stm_eqn02435.gif) are the temperatures of the points on the surfaces, and ![](../graphics/stm_eqn02390.gif) is the gap conductance.

The derivatives of ![](../graphics/stm_eqn02389.gif) are

![](../graphics/stm_eqn07779.gif)and

![](../graphics/stm_eqn07780.gif)where

![](../graphics/stm_eqn07781.gif)
### Radiation

The heat flow per unit area between corresponding points is assumed to be given by

![](../graphics/stm_eqn07782.gif)where ![](../graphics/stm_eqn02243.gif) is the value of absolute zero temperature on the temperature scale being used; ![](../graphics/stm_eqn02389.gif) is the heat flux per unit surface area crossing the gap at this point, from surface ![](../graphics/stm_eqn01047.gif) to surface ![](../graphics/stm_eqn07778.gif); ![](../graphics/stm_eqn05050.gif) and ![](../graphics/stm_eqn02435.gif) are the temperatures of the two surfaces; and ![](../graphics/stm_eqn07783.gif) is the gap radiation constant derived from the emissivities of the two surfaces.

The derivatives of ![](../graphics/stm_eqn02389.gif) are

![](../graphics/stm_eqn07784.gif)and

![](../graphics/stm_eqn07785.gif)
### Jacobian matrix

The contribution to the variational statement of thermal equilibrium is

![](../graphics/stm_eqn07786.gif)where ![](../graphics/stm_eqn01047.gif) is the area. The contribution to the Jacobian matrix for the Newton solution is

![](../graphics/stm_eqn07787.gif)where

![](../graphics/stm_eqn07788.gif)

For "tied" thermal contact the temperature at point ![](../graphics/stm_eqn01047.gif) is constrained to have the same temperature as point ![](../graphics/stm_eqn07778.gif). The Lagrange multiplier method is used to impose the constraint by augmenting the thermal equilibrium statement as follows:

![](../graphics/stm_eqn07789.gif)where ![](../graphics/stm_eqn00280.gif) is the Lagrange multiplier. The contribution to the Jacobian matrix for the Newton solution is

![](../graphics/stm_eqn07790.gif)
### Reference

### Reference

"Thermal contact properties,"  Section 37.2.1 of the Abaqus Analysis User's Guide