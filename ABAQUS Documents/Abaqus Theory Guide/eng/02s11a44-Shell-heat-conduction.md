# 2.11.2 Shell heat conduction

### 2.11.2 Shell heat conduction

**Product: **Abaqus/Standard

This section describes the formulation used in the shell heat conduction elements in Abaqus/Standard. The basis of the elements is a combination of piecewise quadratic interpolation of temperature through the thickness of the shell and either linear interpolation (in elements DS3 and DS4) or quadratic interpolation (in elements DS6 and DS8) on the reference surface of the shell. The isoparametric interpolation functions for the shell reference surface are identical in form to those used for the solid quadrilateral and triangular elements and can be found in "Solid isoparametric quadrilaterals and hexahedra,"  Section 3.2.4, and "Triangular, tetrahedral, and wedge elements,"  Section 3.2.6, respectively. Nodal temperature values are stored at a set of points through the thickness (points *P* below) at each node of the element (nodes *N* below). For the purpose of numerical integration of the finite element equations, a 2  2 Gauss integration scheme with a 2  2 nodal integration scheme for the internal energy and specific heat term is used for the quadrilateral element DS4 and a 3  3 Gauss integration scheme is used for the quadrilateral element DS8. Three- and six-point integration schemes are used for the triangular elements DS3 and DS6, respectively, the details of which can be found in "Triangular, tetrahedral, and wedge elements,"  Section 3.2.6.

Let ![](../graphics/stm_eqn02279.gif) be material coordinates of a point in the reference surface of the shell, and let ![](../graphics/stm_eqn02280.gif) measure position through the thickness of the shell so that ![](../graphics/stm_eqn02281.gif), where *h* is the thickness of the shell, ![](../graphics/stm_eqn02282.gif) is the offset of the reference surface from the midsurface as discussed in "Transverse shear stiffness in composite shells and offsets from the midsurface,"  Section 3.6.8. The position of any point in the shell is given by

![](../graphics/stm_eqn02283.gif)where

![](../graphics/stm_eqn02284.gif)

is the position of a point in the reference surface, and

![](../graphics/stm_eqn00483.gif)

is the unit normal to the reference surface of the shell.The temperature interpolation can be written as

![](../graphics/stm_eqn02285.gif)where

![](../graphics/stm_eqn02286.gif)

is a piecewise parabolic interpolation,

![](../graphics/stm_eqn02287.gif)

is an interpolator in the reference surface, and

![](../graphics/stm_eqn02288.gif)

are nodal temperature values (at node *N*, point *P* through the thickness).

The basic heat energy balance is [Equation 2.11.1&#8211;3](02s11a43-Uncoupled-heat-transfer-analysis.md), with the approximate Jacobian matrix for the Newton method based on

![](../graphics/stm_eqn02289.gif)where ![](../graphics/stm_eqn02290.gif) is the correction to the temperature solution at time ![](../graphics/stm_eqn00438.gif). The derivation of this form is discussed in "Uncoupled heat transfer analysis,"  Section 2.11.1. The form of these terms for shell heat conduction elements is obtained by introducing the interpolator, [Equation 2.11.2&#8211;1](02s11a44-Shell-heat-conduction.md), and neglecting the change in area, with respect to ![](../graphics/stm_eqn02280.gif), of surfaces parallel to the reference surface.

The internal energy rate term (the first term in [Equation 2.11.1&#8211;3](02s11a43-Uncoupled-heat-transfer-analysis.md)) contributes, to the residual,

![](../graphics/stm_eqn02291.gif)and to the Jacobian,

![](../graphics/stm_eqn02292.gif)

For the second term the temperature derivatives are taken with respect to a local orthogonal system ![](../graphics/stm_eqn02293.gif), where ![](../graphics/stm_eqn02294.gif) and ![](../graphics/stm_eqn02295.gif) measure distance along local base vectors ![](../graphics/stm_eqn00014.gif) and ![](../graphics/stm_eqn00015.gif), in the reference surface of the shell, set up according to the standard convention in Abaqus for such local systems in shells. The term is formed by first introducing an intermediate set of temperature values,

![](../graphics/stm_eqn02296.gif)corresponding to each temperature value point through the thickness, at each section where integration through the thickness is performed. Since the number of temperature values on the section is the same as the number of integration points, ![](../graphics/stm_eqn02297.gif) is unity in the appropriate locations and zero everywhere else. Then we can interpolate to the section by

![](../graphics/stm_eqn02298.gif)where

![](../graphics/stm_eqn02299.gif)The piecewise quadratic interpolation through the thickness then gives

![](../graphics/stm_eqn02300.gif)where

![](../graphics/stm_eqn02301.gif)The conductivity term in the Jacobian then is

![](../graphics/stm_eqn02302.gif)where ![](../graphics/stm_eqn02303.gif) is the local conductivity matrix and the same term multiplied by ![](../graphics/stm_eqn02304.gif) appears in the residual.

Finally, the external flux terms contribute

![](../graphics/stm_eqn02305.gif)to the residual and

![](../graphics/stm_eqn02306.gif)to the Jacobian, where

![](../graphics/stm_eqn02307.gif)

at point *A* through the thickness

![](../graphics/stm_eqn02308.gif)

at all other points through the thickness,and points *A* and *B* are on the top and bottom surfaces of the shell.
### Reference

### Reference

"Three-dimensional conventional shell element library,"  Section 29.6.7 of the Abaqus Analysis User's Guide