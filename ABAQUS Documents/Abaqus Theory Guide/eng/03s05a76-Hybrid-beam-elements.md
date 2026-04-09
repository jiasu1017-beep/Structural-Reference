# 3.5.4 Hybrid beam elements

### 3.5.4 Hybrid beam elements

**Product: **Abaqus/Standard

The hybrid beam elements in Abaqus/Standard are designed to handle very slender situations, where the axial stiffness of the beam is very large compared to the bending stiffness; and so a mixed method, where axial force is treated as an independent unknown, is required. For the shear beams mixed elements are provided where the transverse shear forces are also treated as independent unknowns. This section discusses the basis of these mixed methods.
### Axial and bending behavior

The internal virtual work of the beam can be written

![](../graphics/stm_eqn03898.gif)Alternatively, we can introduce an independent axial force variable, ![](../graphics/stm_eqn03899.gif), and write

![](../graphics/stm_eqn03900.gif)where ![](../graphics/stm_eqn03901.gif) is a Lagrange multiplier introduced to impose the constraint ![](../graphics/stm_eqn03902.gif) A linear combination of these expressions is

![](../graphics/stm_eqn03903.gif)Then

![](../graphics/stm_eqn03904.gif)The contribution of this term to the Newton scheme is then

![](../graphics/stm_eqn03905.gif)where

![](../graphics/stm_eqn03906.gif)The tangent stiffness of the section behavior gives

![](../graphics/stm_eqn03907.gif)If ![](../graphics/stm_eqn03908.gif) (where *L* is the element length), then the beam is flexible axially and the mixed formulation is unnecessary. Otherwise, we assume that an inverse of the first equation above defines ![](../graphics/stm_eqn03909.gif) from ![](../graphics/stm_eqn03910.gif):

![](../graphics/stm_eqn03911.gif)and so

![](../graphics/stm_eqn03912.gif)

![](../graphics/stm_eqn03913.gif)Now using the first tangent section stiffness multiplied by ![](../graphics/stm_eqn00593.gif) and the second multiplied by ![](../graphics/stm_eqn03914.gif), the Newton contribution of the element becomes

![](../graphics/stm_eqn03915.gif) where ![](../graphics/stm_eqn03916.gif) is

![](../graphics/stm_eqn03917.gif)The variable ![](../graphics/stm_eqn03899.gif) is taken as an independent value at each integration point in the element. We choose ![](../graphics/stm_eqn00593.gif) as ![](../graphics/stm_eqn03918.gif), where ![](../graphics/stm_eqn03919.gif) is a small value. With this choice, by ensuring that the variables ![](../graphics/stm_eqn03899.gif) are eliminated after the displacement variables of each element, the Gaussian elimination scheme has no difficulty with solving the equations.
### Transverse shear

In the mixed elements that allow transverse shear (B21H, B22H, B31H, B32H), the transverse shear constraints are imposed by treating the shear forces as independent variables, using the following formulation. The internal virtual work associated with transverse shear is

![](../graphics/stm_eqn03920.gif)where ![](../graphics/stm_eqn03921.gif) and ![](../graphics/stm_eqn03922.gif) are shear forces on the section, and ![](../graphics/stm_eqn03923.gif) and ![](../graphics/stm_eqn03924.gif) are variations of transverse shear strain. The virtual work can also be written by introducing independent shear force variables ![](../graphics/stm_eqn03925.gif) and ![](../graphics/stm_eqn03926.gif), as

![](../graphics/stm_eqn03927.gif)where the ![](../graphics/stm_eqn03928.gif) are Lagrange multipliers. As in the axial case, we take a linear combination of these two forms,

![](../graphics/stm_eqn03929.gif)where ![](../graphics/stm_eqn00593.gif) will be defined later. This gives

![](../graphics/stm_eqn03930.gif)where

![](../graphics/stm_eqn03931.gif)The contribution of this term to the Newton scheme is

![](../graphics/stm_eqn03932.gif)

![](../graphics/stm_eqn03933.gif)

Abaqus treats transverse shear elastically, so ![](../graphics/stm_eqn03934.gif), where ![](../graphics/stm_eqn03935.gif) is constant. Then the Newton contribution is

![](../graphics/stm_eqn03936.gif)

![](../graphics/stm_eqn03937.gif)

We now define ![](../graphics/stm_eqn03938.gif) and choose ![](../graphics/stm_eqn03939.gif), where ![](../graphics/stm_eqn01999.gif) is a small value compared to ![](../graphics/stm_eqn03935.gif), to give

![](../graphics/stm_eqn03940.gif)

![](../graphics/stm_eqn03941.gif)
### Reference

### Reference

"Choosing a beam element,"  Section 29.3.3 of the Abaqus Analysis User's Guide