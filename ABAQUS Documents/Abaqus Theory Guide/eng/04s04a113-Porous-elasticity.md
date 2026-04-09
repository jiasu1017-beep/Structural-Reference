# 4.4.1 Porous elasticity

### 4.4.1 Porous elasticity

**Product: **Abaqus/Standard

The porous elasticity model in Abaqus/Standard is designed to be used in conjunction with plasticity models that allow plastic volume changes as described in "Models for granular or polymer behavior,"  Section 4.4.2, to "Models for crushable foams,"  Section 4.4.6. Use of the porous elasticity model without one of these plasticity options is not recommended. The model is based on the experimental observation that in porous materials during elastic (recoverable) straining, the change in the void ratio---*e*---and the change in the logarithm of the equivalent pressure stress---*p*---defined as

![](../graphics/stm_eqn06080.gif)are linearly related, so that in rate form,

![](../graphics/stm_eqn06081.gif)where ![](../graphics/stm_eqn04549.gif) is a material parameter. In this form the material has zero tensile strength. If the tensile strength ![](../graphics/stm_eqn06082.gif) is nonzero, the equivalent relation is

![](../graphics/stm_eqn06083.gif)which includes the special case of zero tensile strength (![](../graphics/stm_eqn06084.gif)). It can be shown that, if the compressibility of the solid material is neglected, the volume change of a material sample is

![](../graphics/stm_eqn06085.gif)where ![](../graphics/stm_eqn06086.gif) is the initial void ratio. If we define the elastic void ratio from the elastic volume change according to the relationship

![](../graphics/stm_eqn06087.gif)and then integrate the linear relation, the volumetric elasticity relationship is

![](../graphics/stm_eqn06088.gif)where ![](../graphics/stm_eqn01918.gif) is the initial pressure stress, prescribed by initial conditions. Note that for a zero tensile strength material it is required that ![](../graphics/stm_eqn06089.gif). This equation can be inverted to yield

![](../graphics/stm_eqn06090.gif)as illustrated in [Figure 4.4.1&#8211;1](04s04a113.md).

Figure 4.4.1&#8211;1 Porous elastic volumetric behavior.

![](../graphics/stmporouselast-vol-behav-nls.png)

The deviatoric elastic behavior is defined either by choosing a constant shear modulus, *G*, so that the deviatoric elastic stiffness is independent of the equivalent pressure stress or choosing a constant Poisson's ratio, ![](../graphics/stm_eqn01854.gif), so that the deviatoric elastic stiffness increases as the equivalent pressure stress increases. If a constant shear modulus is given, the deviatoric relationship is

![](../graphics/stm_eqn06091.gif)whereas when Poisson's ratio is given, the relationship has the rate form

![](../graphics/stm_eqn06092.gif)where

![](../graphics/stm_eqn06093.gif)for a material with nonzero tensile strength. In these equations ![](../graphics/stm_eqn00522.gif) is the deviatoric stress:

![](../graphics/stm_eqn06036.gif)and ![](../graphics/stm_eqn06094.gif) is the deviatoric part of the elastic strain:

![](../graphics/stm_eqn06095.gif)where ![](../graphics/stm_eqn06096.gif) is the volumetric part of the elastic strain.
### Reference

### Reference

"Elastic behavior of porous materials,"  Section 22.3.1 of the Abaqus Analysis User's Guide