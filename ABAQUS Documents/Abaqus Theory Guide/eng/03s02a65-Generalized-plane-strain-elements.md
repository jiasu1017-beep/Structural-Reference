# 3.2.7 Generalized plane strain elements

### 3.2.7 Generalized plane strain elements

**Product: **Abaqus/Standard

The generalized plane strain theory used in Abaqus assumes that the model lies between two bounding planes, which may move as rigid bodies with respect to each other, thus causing strain of the "thickness direction" fibers of the model. It is assumed that the deformation of the model is independent of position with respect to this thickness direction, so the relative motion of the two planes causes a direct strain of the thickness direction fibers only. This strain and its first and second variations are defined as follows.

Let ![](../graphics/stm_eqn03039.gif) be a fixed point in one of the bounding planes, as shown in [Figure 3.2.7&#8211;1](03s02a65-Generalized-plane-strain-elements.md). The length of the fiber between ![](../graphics/stm_eqn03040.gif) and its image in the other bounding plane is ![](../graphics/stm_eqn03041.gif), where ![](../graphics/stm_eqn00945.gif) is the length of this fiber in the initial configuration and ![](../graphics/stm_eqn03042.gif) is the change in length of this fiber. ![](../graphics/stm_eqn03042.gif) is the value of degree of freedom 3 at the reference node of the element.

Figure 3.2.7&#8211;1 Generalized plane strain element.

![](../graphics/edimension-gen-plane-strain-nls.png)The reference node should be the same for all elements in any given connected region so that the bounding planes are the same for that region. Different regions may have different reference nodes. Since the bounding planes are rigid, the length of a fiber at any other point ![](../graphics/stm_eqn03043.gif) in the element is

![](../graphics/stm_eqn03044.gif)where

![](../graphics/stm_eqn03045.gif)where ![](../graphics/stm_eqn03046.gif) are the initial values of ![](../graphics/stm_eqn03047.gif), specified by the user; and ![](../graphics/stm_eqn03048.gif) are the degrees of freedom 4 and 5 at the reference node of the element.

The thickness direction logarithmic strain is

![](../graphics/stm_eqn03049.gif)

The first variation of thickness direction strain is, therefore,

![](../graphics/stm_eqn03050.gif)where

![](../graphics/stm_eqn03051.gif)and the second variation is

![](../graphics/stm_eqn03052.gif)where

![](../graphics/stm_eqn03053.gif)
### References

### References

"Choosing the element's dimensionality,"  Section 27.1.2 of the Abaqus Analysis User's Guide

"Two-dimensional solid element library,"  Section 28.1.3 of the Abaqus Analysis User's Guide