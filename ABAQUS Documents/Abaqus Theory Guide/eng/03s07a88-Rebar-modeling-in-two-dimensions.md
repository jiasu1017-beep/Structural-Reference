# 3.7.1 Rebar modeling in two dimensions

### 3.7.1 Rebar modeling in two dimensions

**Products: **Abaqus/Standard  Abaqus/Explicit

Let ![](../graphics/stm_eqn04949.gif) be the element's usual isoparametric coordinates. Let *r* be an isoparametric coordinate along the line where the face of the element intersects the plane of reinforcement, with ![](../graphics/stm_eqn04950.gif) in an element (see [Figure 3.7.1&#8211;1](03s07a88-Rebar-modeling-in-two-dimensions.md)).

Figure 3.7.1&#8211;1 Rebar in a solid, two-dimensional element.

![](../graphics/stm2drebar.png)The plane of reinforcement is always perpendicular to the element face.

The rebar will be integrated at one or two points, depending on the order of interpolation in underlying elements. The volume of integration ![](../graphics/stm_eqn04951.gif), position, rebar strain ![](../graphics/stm_eqn04952.gif), and first and second variations of rebar strain ![](../graphics/stm_eqn04953.gif) and ![](../graphics/stm_eqn04954.gif) at each point are calculated as

![](../graphics/stm_eqn04955.gif)where

![](../graphics/stm_eqn00945.gif)

is the original thickness for plane elements and ![](../graphics/stm_eqn04956.gif) for axisymmetric elements;

![](../graphics/stm_eqn04957.gif)

is the rebar cross-sectional area;

![](../graphics/stm_eqn04958.gif)

is the spacing of rebar (for axisymmetric elements ![](../graphics/stm_eqn04959.gif), where ![](../graphics/stm_eqn04960.gif) is the radius where the spacing ![](../graphics/stm_eqn04961.gif) is given);

![](../graphics/stm_eqn04962.gif)

is the Gauss weight associated with the integration point along the ![](../graphics/stm_eqn04963.gif) line;

![](../graphics/stm_eqn04964.gif)

is position; and

![](../graphics/stm_eqn04965.gif)

Strain is

![](../graphics/stm_eqn04966.gif)where ![](../graphics/stm_eqn04967.gif) and ![](../graphics/stm_eqn04968.gif) measure length along the rebar in the current and initial configurations, respectively.

For the deformations allowed in these elements,

![](../graphics/stm_eqn04969.gif)where ![](../graphics/stm_eqn00904.gif) is the orientation of the rebar from the plane of the model,

![](../graphics/stm_eqn04970.gif)is the squared stretch ratio in the *r*-direction, and ![](../graphics/stm_eqn04027.gif) is the stretch ratio in the thickness direction:

![](../graphics/stm_eqn04971.gif)

for plane stress or plane strain;

![](../graphics/stm_eqn04972.gif)

for generalized plane strain, where *t* is given in "Generalized plane strain elements,"  Section 3.2.7; and

![](../graphics/stm_eqn04973.gif)

for axisymmetric elements.

From these results the first variation of strain is

![](../graphics/stm_eqn04974.gif)where

![](../graphics/stm_eqn04975.gif)

for plane stress and plane strain,

![](../graphics/stm_eqn04976.gif)

for generalized plane strain, and

![](../graphics/stm_eqn04977.gif)

for axisymmetric cases.The second variation of strain is then

![](../graphics/stm_eqn04978.gif)
### Reference

### Reference

"Defining rebar as an element property,"  Section 2.2.4 of the Abaqus Analysis User's Guide