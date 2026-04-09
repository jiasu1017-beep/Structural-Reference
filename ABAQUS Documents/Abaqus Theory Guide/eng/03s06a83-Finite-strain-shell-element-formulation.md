# 3.6.5 Finite-strain shell element formulation

### 3.6.5 Finite-strain shell element formulation

**Products: **Abaqus/Standard  Abaqus/Explicit

This section describes the formulation of the quadrilateral finite-membrane-strain element S4R, the triangular element S3R and S3 obtained through degeneration of S4R, and the fully integrated finite-membrane-strain element S4.
### Geometric description

At a given stage in the deformation history of the shell, the position of a material point in the shell is defined by

![](../graphics/stm_eqn04193.gif)where the subscript *i* and other Roman subscripts range from 1 to 3. Subscripts ![](../graphics/stm_eqn00904.gif) and other lowercase Greek subscripts which describe the quantities in the reference surface of the shell range from 1 to 2. In the above equation ![](../graphics/stm_eqn04194.gif) is the normal to the reference surface of the shell. The gradient of the position is

![](../graphics/stm_eqn04195.gif)where we have neglected derivatives of ![](../graphics/stm_eqn04196.gif) with respect to ![](../graphics/stm_eqn04197.gif). Note that in the above ![](../graphics/stm_eqn04198.gif) are local surface coordinates that are assumed to be orthogonal and distance measuring in the reference state. ![](../graphics/stm_eqn04199.gif) is the coordinate in the thickness direction, distance measuring and orthogonal to ![](../graphics/stm_eqn04198.gif) in the reference state. The thickness increase factor ![](../graphics/stm_eqn04196.gif) is assumed to be independent of ![](../graphics/stm_eqn04199.gif).

In the deformed state we define local, orthonormal shell directions ![](../graphics/stm_eqn04200.gif) such that

![](../graphics/stm_eqn04201.gif)where ![](../graphics/stm_eqn02353.gif) is the Kronecker delta and ![](../graphics/stm_eqn00064.gif) is the identity tensor of rank 2. Summation convention is used for repeated subscripts. The in-plane components of the gradient of the position are obtained as

![](../graphics/stm_eqn04202.gif)where we have introduced the reference surface deformation gradient

![](../graphics/stm_eqn04203.gif)and the reference surface normal gradient

![](../graphics/stm_eqn04204.gif)

In the original (reference) configuration we denote the position by ![](../graphics/stm_eqn00141.gif) (![](../graphics/stm_eqn01007.gif) for the reference surface) and the direction vectors by ![](../graphics/stm_eqn04205.gif), which yields

![](../graphics/stm_eqn04206.gif)The gradient of the position is

![](../graphics/stm_eqn04207.gif)and the in-plane components of the gradient are obtained as

![](../graphics/stm_eqn04208.gif)where we have assumed that the in-plane direction vectors follow from the surface coordinates with

![](../graphics/stm_eqn04209.gif)and defined the original reference surface normal gradient,

![](../graphics/stm_eqn04210.gif)The original reference surface normal gradient is obtained in the finite element formulation from the interpolation of the nodal normals with the shape functions. In the deformed configuration it is not derived from the nodal normals but is updated independently based on the gradient of the incremental rotations.
### Parametric interpolation

The position of the points in the shell reference surface is described in terms of discrete nodal positions with parametric interpolation functions ![](../graphics/stm_eqn04211.gif). The functions are ![](../graphics/stm_eqn04212.gif) continuous, and ![](../graphics/stm_eqn01209.gif) are nonorthogonal, nondistance measuring parametric coordinates. For the reference surface positions one, thus, obtains

![](../graphics/stm_eqn04213.gif)The gradients of the position with respect to ![](../graphics/stm_eqn04214.gif) are

![](../graphics/stm_eqn04215.gif)Note that uppercase Roman superscripts such as *I* denote nodes of an element and that repeated superscripts imply summation over all nodes of an element.

Now consider the original configuration. The unit normal to the shell reference surface is readily obtained as

![](../graphics/stm_eqn04216.gif)Subsequently, we define two orthonormal tangent vectors ![](../graphics/stm_eqn02587.gif) and distance measuring coordinates ![](../graphics/stm_eqn04198.gif) along these vectors. The derivatives of these coordinates with respect to ![](../graphics/stm_eqn04214.gif) follow from

![](../graphics/stm_eqn04217.gif)The gradient of ![](../graphics/stm_eqn01209.gif) with respect to ![](../graphics/stm_eqn04197.gif) is readily obtained by inversion:

![](../graphics/stm_eqn04218.gif)which makes it possible to obtain the gradient operator

![](../graphics/stm_eqn04219.gif)The original reference surface normal gradient is obtained from the nodal normals ![](../graphics/stm_eqn04220.gif) with

![](../graphics/stm_eqn04221.gif)Since the original reference surface normal gradient is obtained by taking derivatives with respect to orthogonal distance measuring coordinates, we will call ![](../graphics/stm_eqn04222.gif) the original *curvature* of the reference surface.
### Membrane deformation and curvature

It is convenient to define the inverse of the reference surface deformation gradient

![](../graphics/stm_eqn04223.gif)With this expression we can define the gradient operator in the current state:

![](../graphics/stm_eqn04224.gif)The gradient operator in the current state can also be defined as the derivative with respect to distance measuring coordinates ![](../graphics/stm_eqn01359.gif) along the base vectors ![](../graphics/stm_eqn01706.gif), since

![](../graphics/stm_eqn04225.gif)and, hence,

![](../graphics/stm_eqn04226.gif)Hence, it is possible to write for the ![](../graphics/stm_eqn04227.gif):

![](../graphics/stm_eqn04228.gif)since

![](../graphics/stm_eqn04229.gif)In an incremental analysis we can also define the incremental deformation tensor

![](../graphics/stm_eqn04230.gif)and its inverse

![](../graphics/stm_eqn04231.gif)With a local coordinate system defined in the current state, the current gradient of the normal can be transformed into the curvature of the surface:

![](../graphics/stm_eqn04232.gif)
### Orientation update

The equations given in the earlier sections are valid for any local coordinate system defined in the current state. The ![](../graphics/stm_eqn01706.gif) vectors at the beginning of the analysis are determined following the standard Abaqus conventions. In this section, we outline the way in which the in-plane coordinates are made corotational.

To obtain the updated version of ![](../graphics/stm_eqn01706.gif), we follow a two-step approach. First, we construct orthogonal vectors ![](../graphics/stm_eqn04233.gif) tangential to the surface (following Abaqus conventions). Subsequently, we calculate

![](../graphics/stm_eqn04234.gif)We then apply an in-plane rotation ![](../graphics/stm_eqn04235.gif) to the vectors: ![](../graphics/stm_eqn04233.gif):

![](../graphics/stm_eqn04236.gif)

![](../graphics/stm_eqn04237.gif)where ![](../graphics/stm_eqn04238.gif) is to be determined such that the resulting deformation tensor is symmetric, as

![](../graphics/stm_eqn04239.gif)From this follows

![](../graphics/stm_eqn04240.gif)Thus, we can calculate the updated local material directions as

![](../graphics/stm_eqn04241.gif)
### Curvature change

We assume that the nodal spin will be interpolated with the interpolation functions ![](../graphics/stm_eqn04211.gif). During an increment the nodal spin is assumed to be constant; consequently, the value of the spin at each material point will be constant. Hence, we can use the same interpolation functions for the incremental finite rotation vector ![](../graphics/stm_eqn03595.gif):

![](../graphics/stm_eqn04242.gif)The finite rotation vector can be split in a rotation amplitude ![](../graphics/stm_eqn03570.gif) and a rotation axis ![](../graphics/stm_eqn00156.gif):

![](../graphics/stm_eqn04243.gif)To rotate the shell normal, we use quaternion algebra. The incremental nodal rotation is represented by the rotation quaternion ![](../graphics/stm_eqn03564.gif), which is defined by

![](../graphics/stm_eqn04244.gif)An updated shell normal is then obtained according to

![](../graphics/stm_eqn04245.gif)This updated shell normal does not actually have to be calculated: it is used only for the derivation of the expression for the curvature change. It is not equal to the shell normal used at the start of the next increment ![](../graphics/stm_eqn04246.gif), which will again be chosen perpendicular to the reference surface. The updated normal used here will be approximately orthogonal to the reference surface, depending upon the amount of transverse shear deformation. The gradient of the updated shell normal can be obtained by differentiation:

![](../graphics/stm_eqn04247.gif)The second term on the right-hand side can be written in the form

![](../graphics/stm_eqn04248.gif)Hence, the scalar parts of the first two terms cancel each other and the vector parts reinforce each other, leading to

![](../graphics/stm_eqn04249.gif)The inverse of a rotation quaternion such as ![](../graphics/stm_eqn03564.gif) is equal to its conjugate  (![](../graphics/stm_eqn03565.gif)). Hence, we can write

![](../graphics/stm_eqn04250.gif)where we have formally defined the incremental gradient update vectors

![](../graphics/stm_eqn04251.gif)which must be expressed in terms of the gradient of the incremental rotation. From the definition of the incremental quaternion ![](../graphics/stm_eqn03564.gif) follows

![](../graphics/stm_eqn04252.gif) thus, for ![](../graphics/stm_eqn04253.gif), again with use of the incremental quaternion definition

![](../graphics/stm_eqn04254.gif)From the definition of ![](../graphics/stm_eqn03570.gif) and  ![](../graphics/stm_eqn00156.gif) follows

![](../graphics/stm_eqn04255.gif) After substitution in the expression for ![](../graphics/stm_eqn04253.gif) and some algebra one obtains

![](../graphics/stm_eqn04256.gif) Note that ![](../graphics/stm_eqn04257.gif) when ![](../graphics/stm_eqn03575.gif).

For the gradient ![](../graphics/stm_eqn04258.gif) of the updated shell normal we obtain

![](../graphics/stm_eqn04259.gif) where we have introduced the two-dimensional alternator ![](../graphics/stm_eqn03511.gif):

![](../graphics/stm_eqn04260.gif)Note that the *change* in ![](../graphics/stm_eqn04258.gif) is independent of ![](../graphics/stm_eqn04261.gif).

Calculation of ![](../graphics/stm_eqn04258.gif) involves taking the gradient with respect to the reference configuration. It is more convenient to use the reference surface curvature tensor

![](../graphics/stm_eqn04262.gif)We then introduce the incremental curvature update vectors

![](../graphics/stm_eqn04263.gif)which makes it possible to write the update equation as

![](../graphics/stm_eqn04264.gif)This expression makes it feasible to calculate the update in the reference surface curvature by taking gradients in the latest updated state only.
### Deformation gradient

We already have obtained an expression for the deformation gradient in the reference surface, and we have assumed that the thickness change is constant:

![](../graphics/stm_eqn04265.gif)At other points in the shell we obtain for the in-plane component

![](../graphics/stm_eqn04266.gif)We neglect terms of order ![](../graphics/stm_eqn04267.gif), which yields the simplified relation

![](../graphics/stm_eqn04268.gif)We can write this as the product of a finite-membrane deformation and a bending perturbation:

![](../graphics/stm_eqn04269.gif)It will be assumed that the deformation (strain and rotation) due to bending is small and, therefore,

![](../graphics/stm_eqn04270.gif)
### Membrane strain increment

The membrane strain increment follows from the incremental stretch tensor ![](../graphics/stm_eqn00572.gif), whose components follow from the incremental deformation gradient ![](../graphics/stm_eqn04271.gif) by the polar decomposition ![](../graphics/stm_eqn04272.gif).

Let ![](../graphics/stm_eqn04273.gif) and ![](../graphics/stm_eqn04274.gif) be the deformation gradient at the beginning and the end of the increment, respectively. By definition ![](../graphics/stm_eqn04275.gif). The incremental deformation gradient follows as

![](../graphics/stm_eqn04276.gif)Since ![](../graphics/stm_eqn04277.gif) are the components of an orthogonal matrix, the square of the incremental stretch tensor can be obtained by

![](../graphics/stm_eqn04278.gif)(see "Deformation,"  Section 1.4.1). The logarithmic strain increment is then

![](../graphics/stm_eqn04279.gif)and the average material rotation increment is defined from the polar decomposition:

![](../graphics/stm_eqn04280.gif)Due to the choice of the element basis directions, it follows that

![](../graphics/stm_eqn04281.gif)
### Curvature increment

Following Koiter-Sanders shell theory, and compensating for the rotation of the base vectors relative to the material, we define the physical curvature increment ![](../graphics/stm_eqn04282.gif) as

![](../graphics/stm_eqn04283.gif)Neglecting terms of the order ![](../graphics/stm_eqn04284.gif) relative to ![](../graphics/stm_eqn04285.gif), this expression can be rewritten as

![](../graphics/stm_eqn04286.gif)where use was made of the curvature update formula. Observe that the curvature at the beginning of the increment, ![](../graphics/stm_eqn04287.gif), does not appear in this equation. Hence, there is no need to calculate the initial curvature ![](../graphics/stm_eqn04288.gif), and we can assume ![](../graphics/stm_eqn04289.gif). The deformation gradient can, hence, also be simplified to

![](../graphics/stm_eqn04290.gif)For the material strain increment at a point through the shell thickness Koiter-Sanders theory thus yields

![](../graphics/stm_eqn04291.gif)
### Virtual work

The virtual work contribution of the stresses is

![](../graphics/stm_eqn04292.gif)We assume that the variations in the strain can be expressed in terms of variation in membrane strain and curvature with the same relations as apply to the increment in strain:

![](../graphics/stm_eqn04293.gif)which transforms the virtual work equation into

![](../graphics/stm_eqn04294.gif)We introduce the membrane forces ![](../graphics/stm_eqn04295.gif) and the bending moments ![](../graphics/stm_eqn04296.gif):

![](../graphics/stm_eqn04297.gif)which allows us to write

![](../graphics/stm_eqn04298.gif)The membrane strain variation follows with the usual expression

![](../graphics/stm_eqn04299.gif)where we have used the identity ![](../graphics/stm_eqn04300.gif).

The variation in the curvature is obtained by taking variations in the incremental curvature, which yields

![](../graphics/stm_eqn04301.gif)We neglect the terms of order ![](../graphics/stm_eqn04282.gif) and also terms of order ![](../graphics/stm_eqn04302.gif),  which yields

![](../graphics/stm_eqn04303.gif)We evaluate ![](../graphics/stm_eqn04304.gif) with respect to the current state (at the end of the increment). Hence for the evaluation we can assume ![](../graphics/stm_eqn04305.gif). Moreover, we neglect terms of the order ![](../graphics/stm_eqn04306.gif) since they are proportional to ![](../graphics/stm_eqn04282.gif). Hence, we obtain

![](../graphics/stm_eqn04307.gif)which substituted in the expression for ![](../graphics/stm_eqn04308.gif) yields

![](../graphics/stm_eqn04309.gif)
### The rate of virtual work

To obtain an expression for the rate of virtual work, we first write the virtual work equation in terms of the reference volume

![](../graphics/stm_eqn04310.gif)where ![](../graphics/stm_eqn04311.gif) is the Kirchhoff stress tensor, related to the Cauchy or true stress tensor via

![](../graphics/stm_eqn04312.gif)The rate of change then becomes

![](../graphics/stm_eqn04313.gif)Here ![](../graphics/stm_eqn04314.gif) indicates that the rates are taken in a material, corotational coordinate system. The terms involving stress rates are related to the material behavior. We assume constitutive equations of the form

![](../graphics/stm_eqn04315.gif)Substituted in the expression  ![](../graphics/stm_eqn04316.gif) and transformed back to the current configuration, this yields

![](../graphics/stm_eqn04317.gif)Consistent with the derivation of the virtual work equation itself, we neglect terms of the order ![](../graphics/stm_eqn04318.gif). Hence, the rate of virtual work can be written as

![](../graphics/stm_eqn04319.gif)
### Second variation of the membrane strain

It remains to determine ![](../graphics/stm_eqn04320.gif) and ![](../graphics/stm_eqn04321.gif). From the first variation ![](../graphics/stm_eqn04322.gif) follows

![](../graphics/stm_eqn04323.gif)Since ![](../graphics/stm_eqn04227.gif) is the inverse of ![](../graphics/stm_eqn04324.gif), it follows that

![](../graphics/stm_eqn04325.gif)Substitution in the expression for the second variation yields

![](../graphics/stm_eqn04326.gif)The corotational rate of the base vectors follows from

![](../graphics/stm_eqn04327.gif)Substituted in the first term of the previous expression yields

![](../graphics/stm_eqn04328.gif) The in-plane components of the corotational rate of the base vectors can also be expressed in terms of the in-plane material spin in the reference surface:

![](../graphics/stm_eqn04329.gif)Substitution in the last obtained expression for ![](../graphics/stm_eqn04330.gif) yields

![](../graphics/stm_eqn04331.gif)This expression is identical to the one obtained with "standard" continuum elements.
### Second variation of the curvature

We need to calculate the second variation of the curvature to calculate the initial stress contribution from the curvature:

![](../graphics/stm_eqn04332.gif)To simplify the computation, we rely on the intrinsic definition of curvature and express the curvature in derivatives with respect to the isoparametric coordinates. Accordingly,

![](../graphics/stm_eqn04333.gif) where the bending resultant components ![](../graphics/stm_eqn04334.gif) are the components expressed in the orthonormal coordinate system (![](../graphics/stm_eqn04335.gif)) transformed by ![](../graphics/stm_eqn04336.gif).

Denoting derivatives with respect to the isoparametric coordinates as ![](../graphics/stm_eqn04337.gif), the second variation of the curvature is

![](../graphics/stm_eqn04338.gif)Using the fact that ![](../graphics/stm_eqn04339.gif) and ![](../graphics/stm_eqn04340.gif), we find that

![](../graphics/stm_eqn04341.gif)Here ![](../graphics/stm_eqn04342.gif) indicates the skew-symmetric tensor with axial vector ![](../graphics/stm_eqn04194.gif).
### Transverse shear treatment

Several interpolation schemes have been proposed to avoid shear-locking, which typically arises as the thickness of a plate or shell goes to zero. Here we employ an assumed strain method based on the Hu-Washizu principle. This scheme derives from that by [MacNeal (1978)](07s01a01-References.md), subsequently extended and reformulated in [Hughes and Tezduyar (1981)](07s01a01-References.md) and [MacNeal (1982)](07s01a01-References.md) and revisited in [Bathe and Dvorkin (1984)](07s01a01-References.md). Computational aspects of the nonlinear theory are investigated in [Simo, Fox, and Rifai (1989)](07s01a01-References.md) for fully integrated quadrilateral shell elements. For reduced integration quadrilateral and triangular shell elements that can be used for both implicit and explicit integration, this assumed strain method needs to be modified. We summarize below the assumed strain method used with fully integrated elements, followed by the modifications required for the one-point integration plus stabilization used in Abaqus.Construction of the assumed strain field

Consider a typical isoparametric finite element, as depicted in [Figure 3.6.5&#8211;1](03s06a83-Finite-strain-shell-element-formulation.md), and denote by ![](../graphics/stm_eqn04343.gif) the set of midpoints of the element boundaries.

Figure 3.6.5&#8211;1 Notation for the assumed strain field on the standard isoparametric element.

![](../graphics/stmstrain-notation.png)

The following assumed transverse shear strain field is used:

![](../graphics/stm_eqn04344.gif)where

![](../graphics/stm_eqn04345.gif)are the covariant transverse shear strains evaluated at the midpoints of the element boundaries. In the above transverse shear strain definitions, the use of uppercase letters indicates quantities in the reference configuration and the use of lowercase letters indicates the deformed configuration. For readability we have omitted the subscript 3 from the director field. Making use of the bilinear element interpolation, it follows that

![](../graphics/stm_eqn04346.gif)where ![](../graphics/stm_eqn04347.gif), for ![](../graphics/stm_eqn04348.gif), are the reference surface position vectors of the element nodes.

By making use of the assumed strain field along with the update formulae for the director field, the assumed covariant transverse shear field can be written concisely in matrix notation. Recall the director field update equation and the corresponding linearized director field:

![](../graphics/stm_eqn04349.gif)It follows from the element interpolation that

![](../graphics/stm_eqn04350.gif) Define the following vectors:

![](../graphics/stm_eqn04351.gif)Then, the linearized transverse shear strain is

![](../graphics/stm_eqn04352.gif)where

![](../graphics/stm_eqn04353.gif)Define the four vectors:

![](../graphics/stm_eqn04354.gif)Then the rotation or bending part of the strain/displacement operator is written

![](../graphics/stm_eqn04355.gif)Constitutive relations

A St. Venant-Kirchhoff constitutive model for the Kirchhoff curvilinear components of the resultant transverse shear force is written in terms of the transverse shear strains as

![](../graphics/stm_eqn04356.gif)where ![](../graphics/stm_eqn04357.gif) is the transverse shear stiffness in curvilinear coordinates. For a single isotropic layer,

![](../graphics/stm_eqn04358.gif)The matrix ![](../graphics/stm_eqn04359.gif) is the inverse of the metric ![](../graphics/stm_eqn04360.gif), where metric components in the reference configuration ![](../graphics/stm_eqn04361.gif) are defined by the inner product

![](../graphics/stm_eqn04362.gif)The Cauchy or true transverse shear force components in the shell orthonormal coordinate system ![](../graphics/stm_eqn04363.gif) are calculated with the coordinate transformation ![](../graphics/stm_eqn04364.gif) as

![](../graphics/stm_eqn04365.gif)where *A* is the element's reference area and *a* is the current area.Initial stress stiffness

The calculation of the initial stress stiffness matrix requires the second variation of the assumed transverse strain field. This calculation can be summarized in matrix notation as follows. Define vectors of variations of the nodal displacement quantities:

![](../graphics/stm_eqn04366.gif)Then the initial stress contribution is written

![](../graphics/stm_eqn04367.gif)where ![](../graphics/stm_eqn04368.gif) is the area measure in the current configuration and ![](../graphics/stm_eqn04369.gif) is the (symmetric) transverse shear contribution to the initial stress, defined as follows. Let ![](../graphics/stm_eqn00064.gif) be the ![](../graphics/stm_eqn04370.gif) identity matrix; then define the symmetric matrices

![](../graphics/stm_eqn04371.gif)Also define the skew-symmetric matrices

![](../graphics/stm_eqn04372.gif)Also, let ![](../graphics/stm_eqn04373.gif) be the ![](../graphics/stm_eqn04370.gif) zero matrix. Then ![](../graphics/stm_eqn04369.gif)  is written

![](../graphics/stm_eqn04374.gif)One point integration plus stabilization

For reduced-integration elements the transverse shear force components need to be evaluated at the center of the elements. Consider ![](../graphics/stm_eqn04375.gif) the transverse shear contribution to the internal energy:

![](../graphics/stm_eqn04376.gif)The reference area measure ![](../graphics/stm_eqn02623.gif) is written in terms of the isoparametric coordinates as ![](../graphics/stm_eqn04377.gif), where ![](../graphics/stm_eqn04378.gif) and ![](../graphics/stm_eqn04361.gif) are the components of the reference surface metric in the undeformed configuration.

This transverse shear energy can be approximated in many ways to produce a one point integration at the center of the element plus hourglass stabilization. It is important that this treatment yield accurate representation of transverse shear deformation in thick shell problems and provide robust performance for skewed elements. The treatment should collapse smoothly to a triangle, which should be insensitive to the node numbering during collapse; that is, the triangle's response should not depend on the nodal connectivity. For an entire mesh of triangular elements, the treatment should give convergent results (that is, the element should not lock). Furthermore, the high frequency response of the transverse shear treatment should be controlled so that transverse shear response does not dominate the stable time increment for explicit dynamic analysis (including for skewed triangular or quadrilateral geometries). All of these requirements are embodied in the following transverse shear treatment.

Define the transverse shear strain at the center of the element (the homogeneous part) and the "hourglass" transverse shear strain vectors as

![](../graphics/stm_eqn04379.gif)The element distortion coefficients ![](../graphics/stm_eqn04380.gif) and ![](../graphics/stm_eqn04381.gif) are constants determined by the element reference geometry. For geometries with constant Jacobian transformation, ![](../graphics/stm_eqn04382.gif). The components of the hourglass strain vector ![](../graphics/stm_eqn04383.gif) are defined in terms of the edge strains as

![](../graphics/stm_eqn04384.gif)The coefficients  ![](../graphics/stm_eqn04385.gif), ![](../graphics/stm_eqn04386.gif), ![](../graphics/stm_eqn04387.gif), and ![](../graphics/stm_eqn04388.gif) are constants determined from the reference geometry of the element. For rectangular elements ![](../graphics/stm_eqn04389.gif), ![](../graphics/stm_eqn04390.gif), ![](../graphics/stm_eqn04391.gif), ![](../graphics/stm_eqn04392.gif) and ![](../graphics/stm_eqn04393.gif) can be identified as the strain associated with the rotational "butterfly" deformation pattern. We call ![](../graphics/stm_eqn04394.gif) the "crop circle" mode strain since it corresponds to a deformation pattern that resembles the sweeping over the element normals in a circular pattern.

The inclusion of the crop circle strain ![](../graphics/stm_eqn04394.gif) in the homogeneous part of the transverse shear strain ![](../graphics/stm_eqn04395.gif) has two important consequences. First, it makes the transverse shear response insensitive to the nodal connectivity for a triangular element. That is, when a side of a quadrilateral element is collapsed to form a triangle, the element's response is independent of the choice of node numbering on the element. Second, for explicit dynamic analyses the coefficients ![](../graphics/stm_eqn04380.gif) and ![](../graphics/stm_eqn04381.gif) are chosen to minimize the highest frequencies associated with the homogeneous part of the transverse shear response.

To illustrate the crop circle and butterfly transverse shear patterns, consider a square, initially flat element. Furthermore, consider plate theory kinematics; that is, two rotations and a vertical deflection at the nodes. The crop circle pattern has zero vertical deflection at the nodes and a nodal rotation vector pattern as illustrated in [Figure 3.6.5&#8211;2](03s06a83-Finite-strain-shell-element-formulation.md).

Figure 3.6.5&#8211;2 Crop circle pattern: zero deflection and circularly symmetric rotations.

![](../graphics/stmcrop-circle.png)The butterfly pattern has vertical deflections that correspond to cross-diagonal bending; that is, two equal deflections at two nodes across a diagonal, with equal and opposite deflections at the remaining two nodes. The nodal rotations develop in a way that opposes the bending motion of the reference surface; that is, the rotations are opposite the rotations that would develop for this displacement pattern to produce pure bending. The butterfly mode's nodal vertical deflection and rotation vector pattern are illustrated in [Figure 3.6.5&#8211;3](03s06a83-Finite-strain-shell-element-formulation.md).

Figure 3.6.5&#8211;3 Butterfly pattern: vertical deflection and rotation vectors.

![](../graphics/stmbutterfly.png)Let the reference element area be ![](../graphics/stm_eqn04396.gif). The transverse shear energy can be approximated as a center point value plus a stabilization term:

![](../graphics/stm_eqn04397.gif)where ![](../graphics/stm_eqn04398.gif) is the transverse shear stiffness evaluated at the center of the element and the hourglass stiffness ![](../graphics/stm_eqn00677.gif) is the diagonal matrix

![](../graphics/stm_eqn04399.gif)The effective stiffness ![](../graphics/stm_eqn04400.gif) is the average direct component of the transverse shear stiffness, ![](../graphics/stm_eqn04401.gif).

The formulation of the homogeneous part of the transverse shear has two contributions: the average edge strain across the element, plus the element distortion term. The average strain treatment is essentially the same as that for the assumed strain formulation of MacNeal and others presented earlier, with expressions evaluated at the center of the element (![](../graphics/stm_eqn04402.gif) and ![](../graphics/stm_eqn04403.gif)). The details of this part are omitted; only the element distortion term is presented in detail. The variation of the homogeneous transverse shear strain can be written

![](../graphics/stm_eqn04404.gif)where ![](../graphics/stm_eqn04405.gif) and ![](../graphics/stm_eqn04406.gif) are ![](../graphics/stm_eqn04407.gif) and ![](../graphics/stm_eqn04408.gif) evaluated at the center of the element,

![](../graphics/stm_eqn04409.gif)and

![](../graphics/stm_eqn04410.gif)

The stabilization term has a similar formulation. The variation of the hourglass strain is

![](../graphics/stm_eqn04411.gif)where

![](../graphics/stm_eqn04412.gif)and

![](../graphics/stm_eqn04413.gif)

The hourglass force components ![](../graphics/stm_eqn04414.gif) and ![](../graphics/stm_eqn04415.gif) are given by the constitutive relations

![](../graphics/stm_eqn04416.gif)Comments on stabilization

(1) The butterfly mode ![](../graphics/stm_eqn04393.gif) is applied with a "large" or physical hourglass stiffness. For a reference geometry with constant Jacobian, the butterfly stabilization term can be derived from an exact integration of the assumed strain formulation of the transverse shear energy. It is important to apply this constraint with a high stiffness to prevent overly flexible response for quadrilateral elements. The crop circle mode is applied with a "small" or weak stiffness. Although this mode can propagate, it is rarely problematic and is often prevented with boundary conditions.

(2) As the quadrilateral element is degenerated to a triangle, the two hourglass constraints converge into a single constraint: the crop circle constraint. However, as is well-known, for a constant strain triangle the element will lock for certain meshes with three transverse shear constraints per element. Therefore, in the case of a triangular element, the (strong) butterfly mode stabilization is not applied. Only the (weak) crop circle mode stabilization is applied. Thus, in addition to the two homogeneous transverse shear strains, the triangle has a weak constraint to prevent spurious zero energy modes, yet avoids locking in most situations.

The initial stress contribution from the stabilization terms takes the following form:

![](../graphics/stm_eqn04417.gif)where ![](../graphics/stm_eqn04418.gif) is the (symmetric) transverse shear stabilization contribution to the initial stress. Define the symmetric matrices

![](../graphics/stm_eqn04419.gif) Also define the skew-symmetric matrices

![](../graphics/stm_eqn04420.gif)Then ![](../graphics/stm_eqn04418.gif) is written

![](../graphics/stm_eqn04421.gif)Note that once the matrix entries in ![](../graphics/stm_eqn04418.gif) are defined, ![](../graphics/stm_eqn04418.gif) is filled just as ![](../graphics/stm_eqn04369.gif).

The initial stress contribution from the homogeneous part consists of two terms, one from the assumed strain formulation (evaluated at ![](../graphics/stm_eqn04422.gif)) as detailed earlier, and the other from the crop circle mode addition. These two terms can be written

![](../graphics/stm_eqn04423.gif)where ![](../graphics/stm_eqn04424.gif) and ![](../graphics/stm_eqn04425.gif) are the shear force and matrix ![](../graphics/stm_eqn04369.gif) evaluated at the element center. The matrix expression for ![](../graphics/stm_eqn04426.gif) is analogous to ![](../graphics/stm_eqn04418.gif) from the stabilization terms.
### In-plane displacement hourglass control

The in-plane displacement hourglass control is applied in the same way as in the Abaqus membrane elements. The hourglass strains are defined by

![](../graphics/stm_eqn04427.gif)where ![](../graphics/stm_eqn04428.gif) is the hourglass mode. This mode is obtained by making the "regular" hourglass mode ![](../graphics/stm_eqn04429.gif) orthogonal to the homogeneous deformation mode in the undeformed shape of the element. This last condition can be written as

![](../graphics/stm_eqn04430.gif)Observe that

![](../graphics/stm_eqn04431.gif)and consequently

![](../graphics/stm_eqn04432.gif)This expression can be worked out further. We define the projected nodal coordinates

![](../graphics/stm_eqn04433.gif)and the projected element area

![](../graphics/stm_eqn04434.gif)The hourglass mode can then be written in the form

![](../graphics/stm_eqn04435.gif)The hourglass stiffness is chosen equal to

![](../graphics/stm_eqn04436.gif)where *G* is the shear modulus and ![](../graphics/stm_eqn04437.gif) is a small number chosen to be 0.005 in Abaqus/Standard and 0.05 in Abaqus/Explicit. When the hourglass control is based on assumed enhanced strain,  the artificial stiffness factor is replaced by coefficients derived from a three-field variational principle. The hourglass force *Z* conjugate to *z* is then equal to

![](../graphics/stm_eqn04438.gif)For virtual work we need the first variation of the hourglass strain. From the expression for the strain follows immediately

![](../graphics/stm_eqn04439.gif)Note that the second term vanishes in the initial configuration since ![](../graphics/stm_eqn04440.gif). The second variation is needed for the Jacobian. From the first variation follows right away

![](../graphics/stm_eqn04441.gif)The second variation does not contribute in the initial configuration since initially ![](../graphics/stm_eqn04442.gif).
### Rotational hourglass control

The expressions for the curvature change, the transverse shear constraints, and the drilling mode constraints still leave three nonhomogeneous rotational modes unconstrained. These modes correspond to zero rotation at the midedges and zero gradient at the centroid. Hence, they correspond to the familiar ![](../graphics/stm_eqn04429.gif) hourglass pattern. To pass curvature patch tests exactly, it is necessary to use orthogonalized hourglass patterns as derived for in-plane hourglass control.

This last aspect implies that the rotational hourglass mode corresponds to the mixed derivative of the rotation at the centroid:

![](../graphics/stm_eqn04443.gif)

We cannot use the above formulation directly in a formulation suitable for multiple finite rotation increments. Hence, we use the same approach as for the calculation of the curvature change. For the purpose of the calculation we define the updated shell direction vectors

![](../graphics/stm_eqn04444.gif)The updated shell direction vectors do not actually have to be stored: they are used only for the derivation of the expression for the hourglass strain. We now formally define the hourglass strain tensor as

![](../graphics/stm_eqn04445.gif)Observe that

![](../graphics/stm_eqn04446.gif)For the purpose of hourglass strain calculation we assume that all products of first-order derivatives with respect to  ![](../graphics/stm_eqn04447.gif) and ![](../graphics/stm_eqn04448.gif) can be neglected. Consequently,

![](../graphics/stm_eqn04449.gif)and, hence,

![](../graphics/stm_eqn04450.gif)is skew-symmetric. Observe that the mixed derivative of ![](../graphics/stm_eqn04200.gif) can be expressed in terms of the hourglass strain tensor with

![](../graphics/stm_eqn04451.gif)In the undeformed configuration, we assume that ![](../graphics/stm_eqn04452.gif). Subsequent values of ![](../graphics/stm_eqn04453.gif) are obtained incrementally. From the expression for ![](../graphics/stm_eqn04454.gif)  we obtain

![](../graphics/stm_eqn04455.gif) In this expression we also ignore all terms with products of derivatives with respect to ![](../graphics/stm_eqn04447.gif) and ![](../graphics/stm_eqn04448.gif). Hence, the above expression simplifies to

![](../graphics/stm_eqn04456.gif)The second term on the right-hand side can be written in the form

![](../graphics/stm_eqn04457.gif)Hence, the scalar parts of the first two terms cancel each other and the vector parts reinforce each other, leading to

![](../graphics/stm_eqn04458.gif)The inverse of a rotation quaternion such as ![](../graphics/stm_eqn03564.gif) is equal to its conjugate (![](../graphics/stm_eqn03565.gif)); hence,  we can write

![](../graphics/stm_eqn04459.gif)where we have formally defined the incremental hourglass update vector

![](../graphics/stm_eqn04460.gif)which must be expressed in terms of the incremental rotation hourglass mode. From the definition of the incremental quaternion ![](../graphics/stm_eqn03564.gif) follows, while neglecting the products of ![](../graphics/stm_eqn04447.gif) and ![](../graphics/stm_eqn04448.gif) derivatives:

![](../graphics/stm_eqn04461.gif)thus, for ![](../graphics/stm_eqn04462.gif) again with use of the incremental quaternion definition

![](../graphics/stm_eqn04463.gif)From the definition of ![](../graphics/stm_eqn03570.gif) and ![](../graphics/stm_eqn00156.gif) follows, again neglecting the products of first derivatives

![](../graphics/stm_eqn04464.gif)After substitution in the expression for ![](../graphics/stm_eqn04462.gif) and some algebra one obtains

![](../graphics/stm_eqn04465.gif)Note that ![](../graphics/stm_eqn04466.gif) when ![](../graphics/stm_eqn03575.gif). For the updated hourglass tensor one readily obtains

![](../graphics/stm_eqn04467.gif)This expression simplifies further with the introduction of the hourglass vector

![](../graphics/stm_eqn04468.gif)which yields the update formula

![](../graphics/stm_eqn04469.gif)The first and second variation are obtained in entirely the same way as the first and second variation of the curvature change. For the first variation we neglect terms of order ![](../graphics/stm_eqn04462.gif) and obtain

![](../graphics/stm_eqn04470.gif)For the second variation we ignore in addition the terms of order ![](../graphics/stm_eqn04471.gif) and ![](../graphics/stm_eqn04472.gif) with as final result

![](../graphics/stm_eqn04473.gif)
### Degenerate elements

In general meshes it will be desirable to collapse at least some of the quadrilateral elements to triangles or to use the triangular element S3 or S3R, which is in fact an internally collapsed S4R element. For this case the calculation of the membrane strains and the curvature changes proceeds along the same lines as before. The transverse shears will now be zero at the degenerate edges. Finally, calculation of all hourglass constraints will be omitted.
### Rotary inertia scaling for explicit dynamics

For numerical efficiency in explicit dynamic analysis, it is desirable to have the stable time increment determined by the membrane response of the structure. For this reason scaling of the rotary inertia based on the element's reference geometry is included in Abaqus/Explicit.

In explicit dynamic analyses the stable time increment is proportional to the inverse of the highest frequency of the element. Therefore, we must ensure that the highest frequency associated with the transverse shear response does not exceed the highest frequency associated with the membrane response. For thick elements (that is, for elements whose thickness is order unity relative to a characteristic length in the element), the membrane frequencies are dominant. The primary consideration in choosing appropriate scalings is that in the limit as the element's thickness goes to zero, the transverse shear frequencies remain below the membrane ones. Recall that for a one-dimensional spring-mass oscillator, the natural frequency ![](../graphics/stm_eqn01091.gif) can be written in terms of the stiffness *K* and the mass *M* as

![](../graphics/stm_eqn04474.gif)For the transverse shear response the rotary inertia, which is proportional to the cube of the thickness, plays the role of the mass of the system. All other quantities---the membrane stiffness, the mass associated with membrane deformation, and the transverse shear stiffness---are proportional to the thickness. Hence as the thickness of the element goes to zero, the frequencies associated with transverse shear go to infinity proportional to the inverse of the thickness, while the membrane frequencies remain constant. Without scaling, the stable time increment would go to zero as the thickness becomes small.Rotary inertia scaling

For thin elements the rotary inertia is small (negligible) relative to the rotational inertia of the mass at the nodes rotating about an axis through the element center. Therefore, we choose a scaling on the rotary inertia such that it never becomes smaller than a fixed (small) percentage of the rotational inertia of the mass at the nodes rotating about an axis through the center of the element.

Let *R* be the nondimensional rotary inertia scaling, where ![](../graphics/stm_eqn04475.gif). When ![](../graphics/stm_eqn04476.gif), the true rotary inertia is used. Consider a lumped mass matrix for a 4-node element, and let the element be flat and square. For rotations about an axis in the plane of the element, parallel to an element edge, passing through the center, the contribution to the rotational inertia of the mass at the nodes is

![](../graphics/stm_eqn04477.gif)where *A* is the area of the element, *L* is the edge length, and ![](../graphics/stm_eqn00593.gif) is the mass density. The sum of the rotary inertia at the four nodes is

![](../graphics/stm_eqn04478.gif)The ratio of the in-plane contribution to the rotary contribution is

![](../graphics/stm_eqn04479.gif)For the rotary inertia to remain a fixed fraction---say ![](../graphics/stm_eqn02163.gif)---of the mass contribution as the thickness goes to zero, asymptotically *R* must be proportional to ![](../graphics/stm_eqn04480.gif); that is,

![](../graphics/stm_eqn04481.gif)

For planar geometries with element directors along the normal direction, closed-form expressions are possible for the highest membrane and transverse shear frequencies. In such cases the length parameter *L* is interpreted as a characteristic element length that depends on the element distortion. To handle arbitrarily shaped curved elements, exact calculation of the element frequencies becomes difficult. However, we can safely bound the frequencies by an appropriate choice of *L* in the following scaling:

![](../graphics/stm_eqn04482.gif)where ![](../graphics/stm_eqn04483.gif). For triangular elements the characteristic length, ![](../graphics/stm_eqn04484.gif) is the minimum element edge length; and for quadrilateral elements,

![](../graphics/stm_eqn04485.gif)The factor 16 in the definition of *R* is used to protect against bending frequencies determining the stable time increment in very fine meshes subjected to loads that cause an increase in thickness of the shell.
### Rotational bulk viscosity for explicit dynamics

For the displacement degrees of freedom, bulk viscosity introduces damping associated with volumetric straining. Linear bulk viscosity or truncation frequency damping is used to damp the high frequency ringing that leads to unwanted noise in the solution or spurious overshoot in the response amplitude. For the same reason, in shells we need to damp the high frequency ringing in the rotational degrees of freedom with linear bulk viscosity acting on the mean curvature strain rate. This damping generates a bulk viscosity "pressure moment," *m*, which is linear in the mean curvature strain rate:

![](../graphics/stm_eqn04486.gif)where *b* is a damping coefficient (default = 0.06), ![](../graphics/stm_eqn01077.gif) is the original thickness, ![](../graphics/stm_eqn00593.gif) is the mass density, ![](../graphics/stm_eqn01078.gif) is the current dilatational wave speed, *L* is the characteristic length used for rotary inertia scaling, and ![](../graphics/stm_eqn01079.gif) is twice the increment in mean curvature. The dilatational wave speed is given in terms of the effective Lam's constants as

![](../graphics/stm_eqn04487.gif)The resultant pressure moment ![](../graphics/stm_eqn01081.gif), where *h* is the current thickness, is added to the direct components of the moment resultant.
### Fully integrated finite-membrane-strain shell formulation

Element S4 is a fully integrated finite-membrane-strain shell element. Since the element's stiffness is fully integrated, no spurious membrane or bending zero energy modes exist and no membrane or bending mode hourglass stabilization is used. Drill rotation control, however, is required. Element S4 uses the same drill stiffness formulation as used for element S4R. Similarly, element S4 assumes that the transverse shear strain (and force, since the transverse shear treatment is elastic based on the initial elastic modulus of the material) is constant over the element. Therefore, all four stiffness integration locations will have the same transverse shear strain, transverse shear section force, and transverse shear stress distribution. The transverse shear treatment for S4 is identical to that for S4R.

It is well known that a standard displacement formulation will exhibit shear locking for applications dominated by in-plane bending deformation. However, a standard displacement formulation for the out-of-plane bending stiffness is not subject to similar locking response. Hence, S4 uses a standard displacement formulation for the element's bending stiffness, and the theory presented above for the rotation kinematics and bending strain measures applies to S4. The primary difference between the element formulations for S4 and S4R is the treatment of the membrane strain field. This formulation is the topic of the following discussion.

The membrane formulation used for S4 does not rely on the fact that S4 is a shell element. Hence, the discussion below details the formulation from the point of view that the membrane response is governed by the equilibrium for a three-dimensional body in a state of plane stress.

Consider an *enhancement* ![](../graphics/stm_eqn04488.gif) to the rate of deformation tensor ![](../graphics/stm_eqn00424.gif). We introduce the enhanced rate of deformation tensor, ![](../graphics/stm_eqn04489.gif), as

![](../graphics/stm_eqn04490.gif)where ![](../graphics/stm_eqn04488.gif) is defined subsequently.

Admissible variations in the rate of deformation are also introduced as

![](../graphics/stm_eqn04491.gif)where

![](../graphics/stm_eqn04492.gif)

We now introduce constraints on the enhancements ![](../graphics/stm_eqn00424.gif) and ![](../graphics/stm_eqn04493.gif):

![](../graphics/stm_eqn04494.gif)so that the modified virtual work statement can be written in the form

![](../graphics/stm_eqn04495.gif)where ![](../graphics/stm_eqn00479.gif) is the specified traction on ![](../graphics/stm_eqn04496.gif) and ![](../graphics/stm_eqn04497.gif) on ![](../graphics/stm_eqn04498.gif). ![](../graphics/stm_eqn04499.gif) is an arbitrary stress field, and the constitutive equation ![](../graphics/stm_eqn04500.gif) (![](../graphics/stm_eqn04489.gif)) is enforced pointwise.

In the modified virtual work statement all kinematic quantities and corresponding variations (![](../graphics/stm_eqn04489.gif), ![](../graphics/stm_eqn00424.gif), ![](../graphics/stm_eqn04501.gif), and ![](../graphics/stm_eqn00503.gif)) are known functions of ![](../graphics/stm_eqn00117.gif), ![](../graphics/stm_eqn04502.gif), and the reference configuration. A fundamental requirement for the validity of the formulation is that the modified virtual work statement leads to the proper equilibrium equations. If ![](../graphics/stm_eqn04499.gif) is arbitrary, the constraint equations can be rewritten as

![](../graphics/stm_eqn04503.gif)Substituting these two relations in the modified virtual work equation yields

![](../graphics/stm_eqn04504.gif)where we have used the constitutive equation ![](../graphics/stm_eqn04500.gif) ![](../graphics/stm_eqn04505.gif). We recognize this variational statement as the usual virtual work equation, and a straightforward application of the divergence theorem leads to the standard equilibrium equations.

In the actual implementation we choose to satisfy the constraints only for piecewise constant stress fields ![](../graphics/stm_eqn04499.gif). Hence, over the element domain ![](../graphics/stm_eqn04506.gif) we require

![](../graphics/stm_eqn04507.gif)The enhancements ![](../graphics/stm_eqn04488.gif) and ![](../graphics/stm_eqn04508.gif) are chosen such that they eliminate the shear locking for in-plane bending. In addition, the direct strain field is enhanced to approximate the strains caused by Poisson's effect in bending.Patch test

To pass the patch test, the choice of enhancements ![](../graphics/stm_eqn04488.gif) cannot be arbitrary. A sufficient condition for the satisfaction of the patch test is that for homogeneous deformations we have ![](../graphics/stm_eqn04509.gif) or ![](../graphics/stm_eqn04510.gif) pointwise. In that case ![](../graphics/stm_eqn04511.gif) and the stress is homogeneous. Since the stress is homogeneous, it can be moved outside the volume integral in the modified virtual work statement. The volume integral condition on ![](../graphics/stm_eqn04512.gif) implies that the expression is independent of the enhancement and leads to the standard displacement formulation, which is known to satisfy the patch test.
### References

### References

"Shell elements: overview,"  Section 29.6.1 of the Abaqus Analysis User's Guide

"Shell section behavior,"  Section 29.6.4 of the Abaqus Analysis User's Guide