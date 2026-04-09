# 3.7.2 Rebar modeling in three dimensions

### 3.7.2 Rebar modeling in three dimensions

**Products: **Abaqus/Standard  Abaqus/Explicit

Let ![](../graphics/stm_eqn04979.gif) be the isoparametric coordinates of the basic finite element in which the rebar are placed. Let ![](../graphics/stm_eqn04980.gif), be isoparametric coordinates on the surface of reinforcement, with ![](../graphics/stm_eqn04981.gif). Let *t* be a material coordinate along the rebar direction. See [Figure 3.7.2&#8211;1](03s07a89-Rebar-modeling-in-three-dimensions.md).

Figure 3.7.2&#8211;1 Rebar in a solid, three-dimensional element.

![](../graphics/stm3drebar.png)

The rebar is integrated using ![](../graphics/stm_eqn03441.gif) or ![](../graphics/stm_eqn04982.gif) Gauss points, depending on the order of the underlying element. The volume of integration at a Gauss point is

![](../graphics/stm_eqn04983.gif)where ![](../graphics/stm_eqn04957.gif) is the cross-sectional area of each rebar, ![](../graphics/stm_eqn04958.gif) is the rebar spacing, ![](../graphics/stm_eqn04962.gif) is the Gauss weighting associated with the integration point, ![](../graphics/stm_eqn00141.gif) is the position of the Gauss point, and

![](../graphics/stm_eqn04984.gif)In these expressions all quantities are taken in the reference configuration, and so Abaqus ignores changes in rebar cross-sectional area due to straining of the rebar and changes in the rebar spacing due to straining of the finite element in which the rebar is placed.

The strain in the rebar is

![](../graphics/stm_eqn04985.gif)where

![](../graphics/stm_eqn04986.gif)and *G* is the value of *g* in the original configuration.

For convenience we define *s*, a material coordinate that is distance measuring along the rebar in the current configuration:

![](../graphics/stm_eqn04987.gif)The first variation of strain is

![](../graphics/stm_eqn04988.gif)and the second variation of strain is

![](../graphics/stm_eqn04989.gif)
### Reference

### Reference

"Defining rebar as an element property,"  Section 2.2.4 of the Abaqus Analysis User's Guide