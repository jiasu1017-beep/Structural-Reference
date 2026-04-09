# 5.1.2 Finite-sliding interaction between deformable bodies

### 5.1.2 Finite-sliding interaction between deformable bodies

**Product: **Abaqus/Standard

Abaqus/Standard provides two formulations for modeling the interaction between two deformable bodies. The first is a small-sliding formulation in which the contacting surfaces can undergo only relatively small sliding relative to each other but arbitrary rotation of the surfaces is permitted. This formulation is discussed in "Small-sliding interaction between bodies,"  Section 5.1.1. The second is a finite-sliding formulation where separation and sliding of finite amplitude and arbitrary rotation of the surfaces may arise. The formulation for two-dimensional and axisymmetric analysis, as well as for tube-in-tube analysis, is discussed in this section.

Depending on the type of contact problem, two approaches are available to the user for specifying the finite-sliding capability: (1) defining possible contact conditions by identifying and pairing potential contact surfaces and (2) using contact elements. With the first approach Abaqus automatically generates the appropriate contact elements.

In axisymmetric problems with asymmetric deformations, ISL21A and ISL22A elements can be used to model contact with CAXA or SAXA elements. Sliding of tubes inside each other can be modeled with ITT21 and ITT31 elements.

To define a sliding interface between two surfaces, one of the surfaces (the "slave" surface) is covered with ISL or ITT elements. The other surface (the "master" surface) is defined as a slide line surface composed of a series of nodes ordered in sequence. The slide line itself can consist of linear or quadratic segments. If smoothing is used, these segments are connected with quadratic or cubic segments such that full slope continuity is achieved. The smoothing procedure is described later in this section.
### Two-dimensional and axisymmetric slide line elements

Consider contact of a node on the slave surface ![](../graphics/stm_eqn07472.gif) with a segment of the master surface described by nodes ![](../graphics/stm_eqn07473.gif), ![](../graphics/stm_eqn07474.gif), ![](../graphics/stm_eqn04900.gif), where the number of nodes depends on the order of the segment. For a linear segment the number of nodes is 2, whereas for a quadratic segment the number of nodes is 3. For a smoothed section of a linear slide line, the number of nodes is also 3; and for a smoothed section of a quadratic slide line, the number of nodes is 5. If the contact occurs at the (convex) vertex of two segments, only a single node will enter the equations. A typical linear segment is shown in [Figure 5.1.2&#8211;1](05s01a133.md), and a quadratic segment is displayed in [Figure 5.1.2&#8211;2](05s01a133.md). Smoothed segments are shown later in this section.

To derive the equations governing these elements, we consider the coordinates in the plane of the slide line. For the axisymmetric elements, this plane coincides with the two-dimensional space. First, we determine the point ![](../graphics/stm_eqn00117.gif) on the segment closest to the point ![](../graphics/stm_eqn07393.gif) on the slave surface. We also determine the normal ![](../graphics/stm_eqn00483.gif) and tangent ![](../graphics/stm_eqn00479.gif) to the segment at that point. The point ![](../graphics/stm_eqn00117.gif) and the normal ![](../graphics/stm_eqn00483.gif) can be related to the overclosure ![](../graphics/stm_eqn07404.gif) with the relation

![](../graphics/stm_eqn07475.gif)

Figure 5.1.2&#8211;1 Linear slide line segment.

![](../graphics/stmlinear-slideline-nls.png)

Figure 5.1.2&#8211;2 Quadratic slide line segment.

![](../graphics/stmquad-slideline-nls.png)Since ![](../graphics/stm_eqn00117.gif) is on the segment, its position is defined completely by the interpolation function ![](../graphics/stm_eqn07476.gif) for the segment, the position ![](../graphics/stm_eqn07477.gif), and the position ![](../graphics/stm_eqn07478.gif) of the nodes ![](../graphics/stm_eqn07479.gif) that are part of the segment. That allows us to write for [Equation 5.1.2&#8211;1](05s01a133.md)

![](../graphics/stm_eqn07480.gif)where ![](../graphics/stm_eqn07481.gif) and ![](../graphics/stm_eqn07482.gif), ![](../graphics/stm_eqn07483.gif), ![](../graphics/stm_eqn04900.gif) are functions of ![](../graphics/stm_eqn07477.gif). For instance, for a linear segment you obtain ![](../graphics/stm_eqn07484.gif), ![](../graphics/stm_eqn07485.gif). For a quadratic segment you use ![](../graphics/stm_eqn07486.gif), ![](../graphics/stm_eqn07487.gif), ![](../graphics/stm_eqn07488.gif). Similar expressions are obtained for smoothed segments of the slide line. The tangent ![](../graphics/stm_eqn00479.gif) to the slide line at point ![](../graphics/stm_eqn00117.gif) follows with

![](../graphics/stm_eqn07489.gif)where

![](../graphics/stm_eqn07490.gif)The position of point ![](../graphics/stm_eqn00117.gif) is determined from the condition that the normal and tangent must be orthogonal, which leads to the following equation for ![](../graphics/stm_eqn07477.gif):

![](../graphics/stm_eqn07491.gif)For linear segments this yields a linear equation, which can be solved directly. For quadratic and cubic segments it leads to third- or fifth-order equations, which must be solved iteratively. The equation is solved using Newton's method preceded by a number of bisections to find the true minimum distance solution.

To obtain the contact/slip equation, the position equation ([Equation 5.1.2&#8211;2](05s01a133.md)) is linearized. This linearization yields

![](../graphics/stm_eqn07492.gif)where ![](../graphics/stm_eqn07459.gif) is the slip. In the direction of contact, ![](../graphics/stm_eqn07493.gif) this yields

![](../graphics/stm_eqn07494.gif)and in the direction of slip, ![](../graphics/stm_eqn07495.gif) one finds

![](../graphics/stm_eqn07496.gif)It is assumed that slip is relevant only if the node ![](../graphics/stm_eqn07393.gif) is on the slide line; hence, it will be assumed that ![](../graphics/stm_eqn03803.gif). From this follows

![](../graphics/stm_eqn07497.gif)To obtain the initial stress stiffness terms, the second variations of ![](../graphics/stm_eqn07404.gif) and ![](../graphics/stm_eqn01604.gif) must be calculated. From [Equation 5.1.2&#8211;4](05s01a133.md) follows

![](../graphics/stm_eqn07498.gif)The first term is expressed readily in terms of ![](../graphics/stm_eqn07499.gif) with the help of [Equation 5.1.2&#8211;5](05s01a133.md):

![](../graphics/stm_eqn07500.gif)The rate of change of the normal can be re-expressed as

![](../graphics/stm_eqn07501.gif)In this equation ![](../graphics/stm_eqn07502.gif) can be obtained from [Equation 5.1.2&#8211;3](05s01a133.md):

![](../graphics/stm_eqn07503.gif) where use was made of [Equation 5.1.2&#8211;5](05s01a133.md) and ![](../graphics/stm_eqn07504.gif) (the segment curvature) is defined as

![](../graphics/stm_eqn07505.gif)For straight segments ![](../graphics/stm_eqn07504.gif) obviously vanishes. Substitution of [Equation 5.1.2&#8211;7](05s01a133.md) to [Equation 5.1.2&#8211;9](05s01a133.md) in [Equation 5.1.2&#8211;6](05s01a133.md) yields the final result:

![](../graphics/stm_eqn07506.gif)This expression is symmetric, as should be expected. The second variation in ![](../graphics/stm_eqn01604.gif) can be derived along similar lines:

![](../graphics/stm_eqn07507.gif)

![](../graphics/stm_eqn07508.gif)Substitution of [Equation 5.1.2&#8211;7](05s01a133.md), [Equation 5.1.2&#8211;9](05s01a133.md), and [Equation 5.1.2&#8211;13](05s01a133.md) in [Equation 5.1.2&#8211;12](05s01a133.md) yields

![](../graphics/stm_eqn07509.gif)This expression is nonsymmetric. The second variations of ![](../graphics/stm_eqn07404.gif) and ![](../graphics/stm_eqn01604.gif) vanish if no slip in the slide plane occurs ![](../graphics/stm_eqn07510.gif)
### Tube-tube interface elements

In the case of tube-tube interface elements it is assumed that the inner tube can be considered the slave surface and the outer tube the master surface. The tube-tube interface elements differ from the axisymmetric slide line elements in two ways. In the first place there is assumed to be a finite clearance between the tubes, which has the effect that the separation distance ![](../graphics/stm_eqn07404.gif) is finite even when contact occurs. In the second place for the three-dimensional element ITT31 there is a second possible local tangent direction in the plane of the cross-section of the tubes. The derivations for the ITT elements follow much along the same line as the derivations for the ISL elements. The contact equation can be written in the form

![](../graphics/stm_eqn07511.gif)Here ![](../graphics/stm_eqn00117.gif) is a point on the outer tube that potentially contacts point ![](../graphics/stm_eqn07393.gif) on the inner tube, as shown in [Figure 5.1.2&#8211;3](05s01a133.md).

Figure 5.1.2&#8211;3 Tube-tube contact.

![](../graphics/stmtube-tube-contact-nls.png)

In this equation ![](../graphics/stm_eqn07512.gif) is the (positive) radial clearance between the tubes. In a similar way as was done for the ISL elements, the contact equation can be written in the form

![](../graphics/stm_eqn07513.gif)The sign reversal as compared to [Equation 5.1.2&#8211;2](05s01a133.md) is related to the internal nature of the contact as compared to the external nature for the regular slide line elements. The linearized form of [Equation 5.1.2&#8211;16](05s01a133.md) is

![](../graphics/stm_eqn07514.gif)As before, we assume that during contact ![](../graphics/stm_eqn03803.gif). In the contact direction this yields

![](../graphics/stm_eqn07515.gif)and in the direction along the pipe,

![](../graphics/stm_eqn07516.gif)With use of ![](../graphics/stm_eqn07517.gif), it readily follows

![](../graphics/stm_eqn07518.gif)which transforms [Equation 5.1.2&#8211;18](05s01a133.md) into

![](../graphics/stm_eqn07519.gif)where ![](../graphics/stm_eqn07504.gif) is the segment curvature as defined by [Equation 5.1.2&#8211;10](05s01a133.md). For the three-dimensional tube-tube interface element, one can define the transverse local tangent direction ![](../graphics/stm_eqn07520.gif), which yields

![](../graphics/stm_eqn07521.gif)

The initial stress stiffness terms are again obtained by taking the second variations in ![](../graphics/stm_eqn07512.gif), ![](../graphics/stm_eqn01604.gif), and ![](../graphics/stm_eqn02295.gif). From [Equation 5.1.2&#8211;17](05s01a133.md) follows

![](../graphics/stm_eqn07522.gif)and with [Equation 5.1.2&#8211;19](05s01a133.md) and [Equation 5.1.2&#8211;21](05s01a133.md) follows

![](../graphics/stm_eqn07523.gif)

Substitution of [Equation 5.1.2&#8211;20](05s01a133.md) and [Equation 5.1.2&#8211;23](05s01a133.md) in [Equation 5.1.2&#8211;22](05s01a133.md) yields

![](../graphics/stm_eqn07524.gif)This expression is symmetric. In the ![](../graphics/stm_eqn00479.gif)-direction the virtual work term has the form

![](../graphics/stm_eqn07525.gif)which yields with [Equation 5.1.2&#8211;18](05s01a133.md)

![](../graphics/stm_eqn07526.gif)For the second variation follows

![](../graphics/stm_eqn07527.gif)

![](../graphics/stm_eqn07528.gif)where the transverse segment curvature ![](../graphics/stm_eqn07529.gif) is defined by

![](../graphics/stm_eqn07530.gif)In this expression the terms involving ![](../graphics/stm_eqn03507.gif) vanish for element type ITT21. Substitution of [Equation 5.1.2&#8211;20](05s01a133.md) and [Equation 5.1.2&#8211;27](05s01a133.md) in [Equation 5.1.2&#8211;26](05s01a133.md) yields

![](../graphics/stm_eqn07531.gif)In the ![](../graphics/stm_eqn03507.gif)-direction one simply looks at the first variation in ![](../graphics/stm_eqn07468.gif):

![](../graphics/stm_eqn07532.gif)

![](../graphics/stm_eqn07533.gif)With [Equation 5.1.2&#8211;20](05s01a133.md), [Equation 5.1.2&#8211;23](05s01a133.md), and [Equation 5.1.2&#8211;27](05s01a133.md) follows

![](../graphics/stm_eqn07534.gif)Substituted in [Equation 5.1.2&#8211;30](05s01a133.md) this yields

![](../graphics/stm_eqn07535.gif)
### Slide line smoothing

At the junction of two segments along a slide line, a discontinuity in slope may occur. This discontinuity can cause convergence problems because during iteration a contact point might move back and forth between two segments. Hence, it is useful to smooth the transition between segments. Consider first the transition between two linear segments ([Figure 5.1.2&#8211;4](05s01a133.md)).

Figure 5.1.2&#8211;4 Transition between linear segments.

![](../graphics/stmlinear-transition.png)

The junction of the two segments is connected by a Hermitian polynomial between the points ![](../graphics/stm_eqn07536.gif) and ![](../graphics/stm_eqn07537.gif), which are located on the segments:

![](../graphics/stm_eqn07538.gif)

The positions of ![](../graphics/stm_eqn07536.gif) and ![](../graphics/stm_eqn07537.gif) are, hence, determined by the smoothing factor ![](../graphics/stm_eqn00904.gif), which is specified directly by the user in the range ![](../graphics/stm_eqn07539.gif).

We choose ![](../graphics/stm_eqn07477.gif) as the parameter coordinate on the smoothed segment, with ![](../graphics/stm_eqn07540.gif). At the extreme values for ![](../graphics/stm_eqn07477.gif) the coordinates are ![](../graphics/stm_eqn07536.gif) and ![](../graphics/stm_eqn07537.gif), and for the coordinate derivatives we choose

![](../graphics/stm_eqn07541.gif)With the Hermitian interpolation functions we can calculate the position ![](../graphics/stm_eqn00117.gif) of a point on the segment as a function of ![](../graphics/stm_eqn07477.gif):

![](../graphics/stm_eqn07542.gif)Combining the above equations yields

![](../graphics/stm_eqn07543.gif)

The smoothing has in fact been done with a second-order polynomial. In the formulation of the interface contact and friction equations, the treatment of a smoothing segment is identical to the treatment of a regular segment. A transition between quadratic segments is shown in [Figure 5.1.2&#8211;5](05s01a133.md).

Figure 5.1.2&#8211;5 Transition between quadratic segments.

![](../graphics/stmquad-transition.png)It is readily established that in this case

![](../graphics/stm_eqn07544.gif)For the coordinate derivatives we choose

![](../graphics/stm_eqn07545.gif)As before, ![](../graphics/stm_eqn00904.gif) is specified directly by the user. Substitution of these equations in the Hermite shape functions yields

![](../graphics/stm_eqn07546.gif)If ![](../graphics/stm_eqn07547.gif) and ![](../graphics/stm_eqn07548.gif), the equations reduce to the same equations as were used for smoothing between linear segments.

For the transition between a linear segment with nodes ![](../graphics/stm_eqn07394.gif) and ![](../graphics/stm_eqn07549.gif) and a quadratic segment with nodes ![](../graphics/stm_eqn07549.gif), ![](../graphics/stm_eqn07550.gif), and ![](../graphics/stm_eqn07551.gif) the formulas become

![](../graphics/stm_eqn07552.gif)The coordinate derivatives are

![](../graphics/stm_eqn07553.gif)As a result,

![](../graphics/stm_eqn07554.gif)

For the transition between a quadratic segment with nodes ![](../graphics/stm_eqn07394.gif), ![](../graphics/stm_eqn07555.gif), and ![](../graphics/stm_eqn07549.gif) and a linear segment with nodes ![](../graphics/stm_eqn07549.gif) and ![](../graphics/stm_eqn07551.gif), the formulas become

![](../graphics/stm_eqn07556.gif)The coordinate derivatives are

![](../graphics/stm_eqn07557.gif)As a result,

![](../graphics/stm_eqn07558.gif)

Compared to "pure" linear-to-linear and quadratic-to-quadratic segment transitions, in both "mixed" linear-to-quadratic and quadratic-to-linear cases, only the junction node ![](../graphics/stm_eqn07549.gif) terms change.
### Self contact

Self contact is available in the context of a surface folding and touching itself. Appropriate contact elements are generated internally for each node on the surface. A node is allowed to contact all of the surface segments, with the exception of the segments that are adjacent to the node. Since a node is simultaneously a master and a slave (producing symmetric master-slave relationships), overconstraints would occur, for example, if the meshes on both sides of the interface matched exactly. If only a pair of nodes matches in two dimensions, no problem occurs due to the smoothing carried out on the master side of the interface. To avoid solver problems due to overconstraining, three-dimensional self-contact is activated only if penalty-type contact is used.

The mathematical treatment of contact elements is the same as described above, with a few modifications in two dimensions. When two adjacent segments of the surface fold forming a sharp crack, the contact algorithm becomes pure master-slave instead of symmetric to prevent redundant contact constraints. It has been arbitrarily chosen that of these two segments the shortest is the slave and the longest is the master.
### References

### References

"Contact formulations in Abaqus/Standard,"  Section 38.1.1 of the Abaqus Analysis User's Guide

"Tube-to-tube contact elements,"  Section 40.3.1 of the Abaqus Analysis User's Guide

"Slide line contact elements,"  Section 40.4.1 of the Abaqus Analysis User's Guide