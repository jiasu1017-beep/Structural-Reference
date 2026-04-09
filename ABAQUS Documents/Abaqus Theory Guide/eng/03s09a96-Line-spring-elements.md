# 3.9.5 Line spring elements

### 3.9.5 Line spring elements

**Product: **Abaqus/Standard

The line spring elements in Abaqus/Standard provide a computationally inexpensive tool for the analysis of part-through cracks in plates and shells. The basic concept was first proposed by [Rice (1972)](07s01a01-References.md) and has been further discussed by [Parks and White (1982)](07s01a01-References.md). The "line spring" is a series of one-dimensional finite elements placed along the part-through flaw, which allows local flexibility of one side of the flaw with respect to the other (points *A* and *B* in [Figure 3.9.5&#8211;1](03s09a96-Line-spring-elements.md)). This local flexibility is calculated from existing solutions for single edge notch specimens in plane strain ([Figure 3.9.5&#8211;2](03s09a96-Line-spring-elements.md)). The approach is computationally inexpensive compared to fully three-dimensional models of the vicinity of the flaw; it is also approximate because of the use of two-dimensional solutions embedded in the shell model. Practical experience with the method on typical geometries has shown that, for several important geometries, the method provides acceptable accuracy.

Figure 3.9.5&#8211;1 Surface geometry; line spring modeling. Side *B* of the element contains nodes *1*, *2*, and *3*; and for LS6 elements side *A* contains nodes *4*, *5*, and *6*.

![](../graphics/elinespring-strain-not.png)

Figure 3.9.5&#8211;2 Line spring compliance calibration model.

![](../graphics/stmlinespring-compliance-nls.png)

This section discusses the geometric and kinematic basis of the elements as well as the equilibrium statement and the development of the local solutions that define the constitutive relationships. The constitutive relations are expressed in terms of the forces and moments carried across the crack and the relative displacements and rotations of points on opposite sides of the crack (*A* and *B* in [Figure 3.9.5&#8211;1](03s09a96-Line-spring-elements.md)), and are derived from local solutions to single edge cracked plane strain specimens. Elastic and fully plastic (limit analysis) solutions are used to construct an approximate elastic-plastic model.

At each point along the flaw a local orthonormal basis system is defined ![](../graphics/stm_eqn05402.gif), with ![](../graphics/stm_eqn00479.gif) the tangent to the shell along the flaw, ![](../graphics/stm_eqn00483.gif) the normal to the shell, and ![](../graphics/stm_eqn00178.gif) defined as

![](../graphics/stm_eqn05403.gif)

We use the shell normal, ![](../graphics/stm_eqn00483.gif), to determine the side of the shell on which the flaw occurs; flaws that open on the positive ![](../graphics/stm_eqn00483.gif) side are given positive flaw depths to indicate this, and those on the negative ![](../graphics/stm_eqn00483.gif) side are given negative flaw depths. The relative motion between two points---*A* and *B* in [Figure 3.9.5&#8211;1](03s09a96-Line-spring-elements.md)---on opposite sides of the flaw but otherwise at the same place, then defines a set of six generalized strains as follows. Side *B* of the element contains nodes *1*, *2*, *3*; and for LS6 elements side *A* contains nodes *4*, *5*, and *6*.

Mode I:| opening displacement |  |
| --- | --- |
| opening rotation |  |

Mode II: through-thickness shear is defined by the relative displacement,

![](../graphics/stm_eqn05406.gif)

Mode III: antiplane shear is defined by the relative displacement,

![](../graphics/stm_eqn05407.gif)and by the relative rotation,

![](../graphics/stm_eqn05408.gif)The relative rotation ![](../graphics/stm_eqn05409.gif) plays no role in the deformation.

These relative motions form the kinematic basis of the element.

Since the line spring elements are written for geometrically linear analysis only, the first variations of these relative motions are identical to the above definitions, with the total values replaced by their variations.
### Virtual work contribution

The virtual work contribution of the element is defined as

![](../graphics/stm_eqn05410.gif)where ![](../graphics/stm_eqn05411.gif), etc., are forces and moments per unit length of flaw that are conjugate to the corresponding relative displacement and rotation values. In the above expression the integration is taken along the entire flaw.
### Interpolation

The elements use quadratic interpolation of displacement and rotation components along the crack, so they are compatible with the second-order shell elements (S8R, S8R5, S9R5, STRI65).

Two line spring elements are provided---LS6 is a general element for use with arbitrary flaws in a shell, while LS3S is provided for Mode I use in cases when the crack lies on a plane of symmetry and the deformation will be symmetric about the same plane, so that only one-half of the geometry must be modeled.
### Elasticity

The Mode I line spring compliance is based on a single edge notched specimen subject to far-field tension and bending, as shown in [Figure 3.9.5&#8211;2](03s09a96-Line-spring-elements.md). This compliance is

![](../graphics/stm_eqn05412.gif)where the matrix ![](../graphics/stm_eqn05413.gif) can be obtained from the energy compliance calibrations of [Rice (1972)](07s01a01-References.md). The inverse of ![](../graphics/stm_eqn05413.gif) provides the Mode I stiffness per unit length of flaw, relating ![](../graphics/stm_eqn05414.gif) and ![](../graphics/stm_eqn05415.gif) to ![](../graphics/stm_eqn05416.gif) and ![](../graphics/stm_eqn05417.gif). Similar results in Mode II and Mode III complete the elastic stiffness.

Stress intensity factors are calculated as

![](../graphics/stm_eqn05418.gif)where approximate expressions for ![](../graphics/stm_eqn01402.gif) and ![](../graphics/stm_eqn01401.gif) are given by [Tada et al. (1973)](07s01a01-References.md), and similar expressions apply for Mode III and (without ![](../graphics/stm_eqn01401.gif)) for Mode II. The *J*-integral is then calculated by combining these stress intensities as

![](../graphics/stm_eqn05419.gif)where

![](../graphics/stm_eqn05420.gif)*E* is Young's modulus and ![](../graphics/stm_eqn01854.gif) is Poisson's ratio.
### Plasticity

The elastic-plastic line spring model in Abaqus is based on Mode I response only, since no theory is available for an elastic-plastic line spring model in mixed mode loading. For convenience we define a generalized "strain" vector as

![](../graphics/stm_eqn05421.gif)and conjugate generalized "forces" as

![](../graphics/stm_eqn05422.gif)

The formalism of a simple associated flow, isotropic hardening plasticity model is used as follows. The generalized strain rate is decomposed into elastic and plastic response as

![](../graphics/stm_eqn05423.gif)and the Mode I elasticity relationship described above is used to define the generalized stresses:

![](../graphics/stm_eqn05424.gif)

The plastic strain rate is defined to be normal to a yield surface, ![](../graphics/stm_eqn05209.gif):

![](../graphics/stm_eqn05425.gif)where ![](../graphics/stm_eqn05426.gif) is the yield function, whose definition is discussed in detail below, and ![](../graphics/stm_eqn05427.gif) is a scalar hardening parameter used to provide isotropic hardening. The hardening is calculated from the basic stress-strain data for the material by a work equivalency argument. The plastic work per unit length of flaw is

![](../graphics/stm_eqn05428.gif)and is also given by

![](../graphics/stm_eqn05429.gif)where ![](../graphics/stm_eqn05430.gif) is the uniaxial stress-strain behavior of the material and *z* and *y* measure position through the thickness and along the length of the single edge notch specimen. We approximate this second expression by

![](../graphics/stm_eqn05431.gif)where ![](../graphics/stm_eqn05432.gif) is a representative value of the yield stress (at an equivalent plastic strain of ![](../graphics/stm_eqn05433.gif)); *t* is the shell thickness; *a* is the flaw depth; and *f* is a constant, introduced to provide a matching to numerical results for the specimen. [Parks and White (1982)](07s01a01-References.md) suggest choosing ![](../graphics/stm_eqn05434.gif), and this value is used in Abaqus.

The yield surface is defined with respect to the generalized stress variables ![](../graphics/stm_eqn05414.gif) and ![](../graphics/stm_eqn05415.gif) as follows. Following [Rice (1972)](07s01a01-References.md), we define

![](../graphics/stm_eqn05435.gif)and

![](../graphics/stm_eqn05436.gif)

Then for ![](../graphics/stm_eqn05437.gif) the yield function, ![](../graphics/stm_eqn05209.gif), is taken as an envelope to limit analysis results, as proposed by Rice:

![](../graphics/stm_eqn05438.gif)Otherwise, we use

![](../graphics/stm_eqn05439.gif)with

![](../graphics/stm_eqn05440.gif)

This surface is chosen to blend continuously with ![](../graphics/stm_eqn05441.gif) at ![](../graphics/stm_eqn05442.gif) and as a reasonable estimate of the behavior for ![](../graphics/stm_eqn05443.gif). It is, otherwise, arbitrary. [Rice (1972)](07s01a01-References.md) points out that at ![](../graphics/stm_eqn05444.gif), the yield surface will have a vertex. The smooth surface used in Abaqus has been adopted for numerical reasons. This smoothness restricts the possible flow behavior at ![](../graphics/stm_eqn05445.gif), but we assume that this is not a critical issue.

These surfaces are shown in [Figure 3.9.5&#8211;3](03s09a96-Line-spring-elements.md). The figure also indicates a region where the model is not appropriate (because the crack will close). Warning messages are provided if the generalized stress point enters this region at any integration point.

Figure 3.9.5&#8211;3 Generalized stress yield surface assumed for line springs.

![](../graphics/stmlinespring-yieldsurf-nls.png)

The plasticity model is integrated by the usual backward Euler method (see "Integration of plasticity models,"  Section 4.2.2, for details). Once the plastic strain increments are known, from the kinematics of the slip line field proposed by [Rice (1972)](07s01a01-References.md) for an edge cracked strip, the increment of plastic crack-tip opening is given by

![](../graphics/stm_eqn05446.gif)The increment in the plastic part of the *J*-integral is related to the increment of plastic crack-tip opening by

![](../graphics/stm_eqn05447.gif)where *m* is given by ([Parks and White, 1982](07s01a01-References.md)),

![](../graphics/stm_eqn05448.gif)where ![](../graphics/stm_eqn05449.gif) indicates differentiation with respect to crack depth and ![](../graphics/stm_eqn05450.gif) indicate differentiation by ![](../graphics/stm_eqn05363.gif) and ![](../graphics/stm_eqn05365.gif), respectively. ![](../graphics/stm_eqn05451.gif) is either ![](../graphics/stm_eqn05441.gif) or ![](../graphics/stm_eqn05452.gif) depending on the state of deformation.

The elastic part of the *J*-integral is obtained from the generalized stresses by calculating the stress intensity factors as described in the previous section (ignoring plasticity effects). The total *J*-integral is the sum of the plastic and elastic *J*-integral contributions. Although the method used for computing the elastic contribution is obviously approximate, it is reasonably accurate if ![](../graphics/stm_eqn05453.gif) dominates ![](../graphics/stm_eqn05454.gif), which is the case once a significant amount of plasticity develops ([Parks and White, 1982](07s01a01-References.md)).
### Reference

### Reference

"Line spring elements for modeling part-through cracks in shells,"  Section 32.9.1 of the Abaqus Analysis User's Guide