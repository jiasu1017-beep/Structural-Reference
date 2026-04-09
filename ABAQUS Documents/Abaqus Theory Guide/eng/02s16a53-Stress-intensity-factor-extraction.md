# 2.16.2 Stress intensity factor extraction

### 2.16.2 Stress intensity factor extraction

**Product: **Abaqus/Standard

The stress intensity factors ![](../graphics/stm_eqn02639.gif), ![](../graphics/stm_eqn02640.gif), and ![](../graphics/stm_eqn02641.gif) play an important role in linear elastic fracture mechanics. They characterize the influence of load or deformation on the magnitude of the crack-tip stress and strain fields and measure the propensity for crack propagation or the crack driving forces. Furthermore, the stress intensity can be related to the energy release rate (the *J*-integral) for a linear elastic material through

![](../graphics/stm_eqn02642.gif)where ![](../graphics/stm_eqn02643.gif) and ![](../graphics/stm_eqn02644.gif) is called the pre-logarithmic energy factor matrix ([Shih and Asaro, 1988](07s01a01-References.md); [Barnett and Asaro, 1972](07s01a01-References.md); [Gao, Abbudi, and Barnett, 1991](07s01a01-References.md); [Suo, 1990](07s01a01-References.md)). For homogeneous, isotropic materials ![](../graphics/stm_eqn02644.gif) is diagonal and the above equation simplifies to

![](../graphics/stm_eqn02645.gif)where ![](../graphics/stm_eqn02646.gif) for plane stress and ![](../graphics/stm_eqn02647.gif) for plane strain, axisymmetry, and three dimensions. For an interfacial crack between two dissimilar isotropic materials with Young's moduli ![](../graphics/stm_eqn02648.gif) and ![](../graphics/stm_eqn02649.gif), Poisson's ratios ![](../graphics/stm_eqn02650.gif) and ![](../graphics/stm_eqn02651.gif), and shear moduli ![](../graphics/stm_eqn02652.gif) and ![](../graphics/stm_eqn02653.gif),

![](../graphics/stm_eqn02654.gif)where

![](../graphics/stm_eqn02655.gif)

![](../graphics/stm_eqn02656.gif)and ![](../graphics/stm_eqn02657.gif) for plane strain, axisymmetry, and three dimensions; and ![](../graphics/stm_eqn02658.gif) for plane stress. Unlike their analogues in a homogeneous material, ![](../graphics/stm_eqn02639.gif) and ![](../graphics/stm_eqn02640.gif) are no longer the pure Mode I and Mode II stress intensity factors for an interfacial crack. They are simply the real and imaginary parts of a complex stress intensity factor, whose physical meaning can be understood from the interface traction expressions:

![](../graphics/stm_eqn02659.gif)where *r* and ![](../graphics/stm_eqn01111.gif) are polar coordinates centered at the crack tip. The bimaterial constant ![](../graphics/stm_eqn00377.gif) is defined as

![](../graphics/stm_eqn02660.gif)

In this section we describe an interaction integral method ([Shih and Asaro, 1988](07s01a01-References.md)) to extract the individual stress intensity factors for a crack under mixed-mode loading. The method is applicable to cracks in isotropic and anisotropic linear materials.
### Interaction integral method

In general, the *J*-integral for a given problem can be written as

![](../graphics/stm_eqn02661.gif)where ![](../graphics/stm_eqn02662.gif) correspond to ![](../graphics/stm_eqn02663.gif) when indicating the components of *B*. We define the *J*-integral for an auxiliary, pure Mode I, crack-tip field with stress intensity factor ![](../graphics/stm_eqn02664.gif) as

![](../graphics/stm_eqn02665.gif)Superimposing the auxiliary field onto the actual field yields

![](../graphics/stm_eqn02666.gif)

Since the terms not involving ![](../graphics/stm_eqn02639.gif) or ![](../graphics/stm_eqn02667.gif) in ![](../graphics/stm_eqn02668.gif) and *J* are equal, the interaction integral can be defined as

![](../graphics/stm_eqn02669.gif)

If the calculations are repeated for Mode ![](../graphics/stm_eqn02670.gif) and Mode ![](../graphics/stm_eqn02671.gif), a linear system of equations results:

![](../graphics/stm_eqn02672.gif)If the ![](../graphics/stm_eqn02673.gif) are assigned unit values, the solution of the above equations leads to

![](../graphics/stm_eqn02674.gif) where ![](../graphics/stm_eqn02675.gif) The calculation of this integral is discussed next.

Based on the definition of the *J*-integral, the interaction integrals ![](../graphics/stm_eqn02676.gif) can be expressed as

![](../graphics/stm_eqn02677.gif)with ![](../graphics/stm_eqn02678.gif) given as

![](../graphics/stm_eqn02679.gif)The subscript ![](../graphics/stm_eqn02680.gif) represents three auxiliary pure Mode I, Mode II, and Mode III crack-tip fields for ![](../graphics/stm_eqn02681.gif), respectively. ![](../graphics/stm_eqn02597.gif) is a contour that lies in the normal plane at position *s* along the crack front, beginning on the bottom crack surface and ending on the top surface (see [Figure 2.16.2&#8211;1](02s16a53-Stress-intensity-factor-extraction.md)). The limit ![](../graphics/stm_eqn02598.gif) indicates that ![](../graphics/stm_eqn02597.gif) shrinks onto the crack tip.

Figure 2.16.2&#8211;1 Definition of local orthogonal Cartesian coordinates at the point *s* on the crack front; the crack is in the ![](../graphics/stm_eqn01412.gif)&#8211;![](../graphics/stm_eqn02618.gif) plane.

![](../graphics/stmcinter-crack-front-nls.png)

Following the domain integral procedure used in Abaqus/Standard for calculating the *J*-integral, we define an interaction integral for a virtual crack advance ![](../graphics/stm_eqn02621.gif):

![](../graphics/stm_eqn02682.gif)where *L* denotes the crack front under consideration; ![](../graphics/stm_eqn02623.gif) is a surface element on a vanishingly small tubular surface enclosing the crack tip (i.e., ![](../graphics/stm_eqn02624.gif)); ![](../graphics/stm_eqn00483.gif) is the outward normal to ![](../graphics/stm_eqn02623.gif); and ![](../graphics/stm_eqn00178.gif) is the local direction of virtual crack propagation. The integral ![](../graphics/stm_eqn02683.gif) can be calculated by the same domain integral method as that used for calculating the *J*-integral.

To obtain ![](../graphics/stm_eqn02676.gif) at each node set *P* along the crack front line, ![](../graphics/stm_eqn00280.gif) is discretized with the same interpolation functions as those used in the finite elements along the crack front:

![](../graphics/stm_eqn02635.gif)where ![](../graphics/stm_eqn02636.gif) at the node set *P* and all other ![](../graphics/stm_eqn02637.gif) are zero. The result is substituted into the expression for ![](../graphics/stm_eqn02684.gif). Finally, the interaction integral value at each node set *P* along the crack front can be calculated as

![](../graphics/stm_eqn02685.gif)
### Reference

### Reference

"Contour integral evaluation,"  Section 11.4.2 of the Abaqus Analysis User's Guide