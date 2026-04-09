# 6.5.3 Pressure loadings on elbow elements

### 6.5.3 Pressure loadings on elbow elements

**Product: **Abaqus/Standard

Elbow elements are often used to model pipelines in which the curvature of the pipe can change significantly while the pipe is subjected to uniform or hydrostatic pressure. Therefore, pressure loadings that include large geometry changes are developed for these elements, as described in this section.

The virtual work contribution of pressure on the lateral surface of the elbow is

![](../graphics/stm_eqn08261.gif)where

*p*

is the pressure magnitude,

![](../graphics/stm_eqn04502.gif)

is the variational displacement at a point on the midsurface of the lateral wall of the elbow,

![](../graphics/stm_eqn00483.gif)

is the normal to the lateral wall midsurface, and

*A*

is the area of space occupied by the lateral surface in the current configuration.

The product of the surface normal and the differential area can be rewritten in terms of material coordinates ![](../graphics/stm_eqn08262.gif) along the pipe and ![](../graphics/stm_eqn00155.gif) around the pipe section:

![](../graphics/stm_eqn08263.gif)where ![](../graphics/stm_eqn08264.gif) is the initial pipe radius, so that

![](../graphics/stm_eqn08265.gif)where ![](../graphics/stm_eqn08266.gif) is the area of space occupied by the lateral surface in the reference configuration.

For hydrostatic pressure, the pressure magnitude is a function of position:

![](../graphics/stm_eqn08267.gif)where

![](../graphics/stm_eqn08268.gif)

is the reference pressure magnitude,

![](../graphics/stm_eqn08269.gif)

is the zero pressure height,

![](../graphics/stm_eqn08270.gif)

is the reference height, and

![](../graphics/stm_eqn02234.gif)

is ![](../graphics/stm_eqn08271.gif), a unit vector in the vertical direction.

In the elbow elements position on the lateral surface, ![](../graphics/stm_eqn00117.gif), is interpolated as

![](../graphics/stm_eqn08272.gif)where

![](../graphics/stm_eqn08273.gif)

is the position of a point on the pipe axis,

![](../graphics/stm_eqn08274.gif)

is the radial displacement,

![](../graphics/stm_eqn08275.gif)

is the tangential displacement,

![](../graphics/stm_eqn03949.gif)

is ![](../graphics/stm_eqn08276.gif), and

![](../graphics/stm_eqn00479.gif)

is ![](../graphics/stm_eqn08277.gif) with ![](../graphics/stm_eqn08278.gif) and ![](../graphics/stm_eqn08279.gif) being the cross-sectional basis vectors.

The first variation of the position can now be expressed as

![](../graphics/stm_eqn08280.gif)and the derivatives of the position with respect to the parametrization are

![](../graphics/stm_eqn08281.gif)and

![](../graphics/stm_eqn08282.gif)Assuming that (1) terms in ![](../graphics/stm_eqn08283.gif) and ![](../graphics/stm_eqn08284.gif) can be ignored due to negligible twist in the pipe, (2) terms in ![](../graphics/stm_eqn08285.gif) and its derivatives can be ignored due to negligible warping in the pipe, (3) ![](../graphics/stm_eqn08286.gif), (4) the stretch ![](../graphics/stm_eqn08287.gif) is unity, and (5) ![](../graphics/stm_eqn08288.gif) and ![](../graphics/stm_eqn08289.gif) are small compared to ![](../graphics/stm_eqn08290.gif), we arrive at the following expression for the integrand of ![](../graphics/stm_eqn08291.gif):

![](../graphics/stm_eqn08292.gif)For closed-end loading the virtual work contribution of pressure on the end-caps of the elbow is

![](../graphics/stm_eqn08293.gif)where *r* and ![](../graphics/stm_eqn00155.gif) are the material coordinates in a two-dimensional cylindrical coordinate system of points on the end-caps of the elbow element, ![](../graphics/stm_eqn01642.gif) represents position on the end-caps, and ![](../graphics/stm_eqn08294.gif) is the area of space occupied by the end-caps of the elbow element. We assume the following deformation for the end-caps:

![](../graphics/stm_eqn08295.gif)where ![](../graphics/stm_eqn08296.gif) is the parameter that identifies the end-cap being considered. The assumed deformation arises naturally on considering a deformation of the end-caps in which radial rays of the reference end-cap configuration remain straight lines under deformation. It can be shown easily that the assumed deformation of the end-caps is differentiable as long as the deformations of the circumferential curves of the end-caps are differentiable. For the end-cap boundary shapes that arise in applications (primarily ovalized modes), the assumed deformation will be locally invertible so that integration of functions over the deformed surface is not likely to be a problem.

Ignoring the terms due to warping in the expression for position on the lateral surface, the first variation of position on an end-cap is

![](../graphics/stm_eqn08297.gif)and the derivatives of ![](../graphics/stm_eqn01642.gif) with respect to *r* and ![](../graphics/stm_eqn00155.gif) are

![](../graphics/stm_eqn08298.gif)and

![](../graphics/stm_eqn08299.gif)The integrand of the expression for the virtual work of pressure on the end-caps can now be expressed as

![](../graphics/stm_eqn08300.gif)where ![](../graphics/stm_eqn02561.gif) is ![](../graphics/stm_eqn08301.gif) if the center of the end-cap is node 1 of the element and ![](../graphics/stm_eqn08302.gif) if the center is node 2 or 3 of the element.

The load stiffness for the pressure loading, which by definition is the first variation of the virtual work of the pressure load, is given by ![](../graphics/stm_eqn08303.gif). The following expressions are required for its calculation:

![](../graphics/stm_eqn08304.gif)

![](../graphics/stm_eqn08305.gif)and

![](../graphics/stm_eqn08306.gif)In the above ![](../graphics/stm_eqn08307.gif) is nonzero only in the case of hydrostatic pressure, when it is given in the first case by

![](../graphics/stm_eqn08308.gif)and in the second case by

![](../graphics/stm_eqn08309.gif)
### Reference

### Reference

"Pipes and pipebends with deforming cross-sections: elbow elements,"  Section 29.5.1 of the Abaqus Analysis User's Guide