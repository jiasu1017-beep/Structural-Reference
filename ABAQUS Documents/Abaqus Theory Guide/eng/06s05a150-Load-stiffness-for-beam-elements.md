# 6.5.2 Load stiffness for beam elements

### 6.5.2 Load stiffness for beam elements

**Product: **Abaqus/Standard

Abaqus provides for loads per unit length in the beam cross-sectional directions as distributed load options for the beam elements (load types P1, P2). Since these are follower forces, they have a load stiffness; and this stiffness can sometimes be important especially in the case of buckling prediction by eigenvalue extraction. The symmetric form of this load stiffness is included in Abaqus/Standard (see [Hibbitt, 1979](07s01a01-References.md), and [Mang, 1980](07s01a01-References.md)). This form is developed below. The external virtual work on the beam is

![](../graphics/stm_eqn08244.gif)where the pressure load, ![](../graphics/stm_eqn01009.gif), is given by the externally prescribed pressure magnitude, *p*, as ![](../graphics/stm_eqn08245.gif) where ![](../graphics/stm_eqn08246.gif) defines the particular cross-sectional direction of the load. Therefore, ![](../graphics/stm_eqn08247.gif), where ![](../graphics/stm_eqn08248.gif) when ![](../graphics/stm_eqn08249.gif), and ![](../graphics/stm_eqn08250.gif) when ![](../graphics/stm_eqn08251.gif) so that

![](../graphics/stm_eqn08252.gif)where *S* is the material coordinate along the beam. Now assuming that the load magnitude, *p*, is externally prescribed so that it does not change with position, the rate of change of ![](../graphics/stm_eqn08253.gif) with change in position, ![](../graphics/stm_eqn08254.gif), is

![](../graphics/stm_eqn08255.gif)

Now

![](../graphics/stm_eqn08256.gif)and so

![](../graphics/stm_eqn08257.gif)

Thus,

![](../graphics/stm_eqn08258.gif)

This load stiffness is not symmetric, except in the case of a beam in a plane with fixed ends (or no ends, such as a ring), in which case the first term is exactly zero and the second gives the symmetric form

![](../graphics/stm_eqn08259.gif)

In Abaqus, even for the general beams in three dimensions, the load stiffness is introduced as the symmetric part of ![](../graphics/stm_eqn08260.gif) above.
### Reference

### Reference

"Distributed loads,"  Section 34.4.3 of the Abaqus Analysis User's Guide