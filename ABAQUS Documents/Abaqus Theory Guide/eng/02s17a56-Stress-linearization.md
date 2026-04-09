# 2.17.1 Stress linearization

### 2.17.1 Stress linearization

**Product: **Abaqus/CAE

Stress linearization is the separation of stresses through a section into constant membrane, linear bending, and nonlinearly varying peak stresses. The capability for calculating linearized stresses is available in the `Visualization` module of Abaqus/CAE; it is most commonly used for two-dimensional axisymmetric models. See Chapter 52, "Calculating linearized stresses," of the Abaqus/CAE User's Guide for detailed information on how to obtain linearized stresses; the computational methods used by Abaqus are discussed here.
### Computing the stress components

Linearized stress components are computed using user-defined sections traversing a finite element model structure. Stress values are extracted at regular intervals along the defined section, and integration is performed numerically using the extracted stress values. Membrane, bending, and peak stress values are computed. These stresses are defined as follows:

**Membrane stress**

The constant portion of the normal stress such that a pure moment acts on a plane after the membrane stress is subtracted from the total stress.

**Bending stress**

The variable portion of the normal stress equal to the equivalent linear stress or, where no peak stresses exist, equal to the total stress minus the membrane stress.

**Peak stress**

The portion of the normal stress that exists after the membrane and bending stresses are subtracted from the total stress.For the best results, the endpoints of the section should be chosen so that the section is normal to the interior and exterior surfaces of the model. This orientation minimizes problems with shear stresses since they will be approximately zero at the ends of the line [(Kroenke, 1973)](07s01a01-References.md).Three-dimensional structures

The membrane values of the stress components are computed using the following equation:

![](../graphics/stm_eqn02726.gif)where

![](../graphics/stm_eqn02727.gif) is the membrane value of stress,

*t* is the thickness of the section,

![](../graphics/stm_eqn00794.gif) is the stress along the path, and

*x* is the coordinate along the path.The linear bending values of the stress components are computed using the following equations:

![](../graphics/stm_eqn02728.gif)where ![](../graphics/stm_eqn02729.gif) and ![](../graphics/stm_eqn02730.gif) are the bending values of the stress at point A and point B (the endpoints of the section; see [Figure 2.17.1&#8211;1](02s17a56-Stress-linearization.md)).

Figure 2.17.1&#8211;1 Recommended stress paths.

![](../graphics/stm-anl-stresslin-paths-nls.png)

The integration is performed numerically. Assuming the path between point A and point B is divided uniformly into *n* intervals, the integrals are evaluated as follows:

![](../graphics/stm_eqn02731.gif)and

![](../graphics/stm_eqn02732.gif)where ![](../graphics/stm_eqn02733.gif) is the stress at point *j* along the path.Axisymmetric structures

The derivation of the above equations is similar for the axisymmetric case, except for the fact that the neutral axis is shifted radially outward. Separate expressions are obtained for the stresses in the thickness, meridional, and hoop directions. In Abaqus/CAE these are represented as local directions 1, 2, and 3, respectively (see [Figure 2.17.1&#8211;2](02s17a56-Stress-linearization.md)).

Figure 2.17.1&#8211;2 Stress directions.

![](../graphics/stm-anl-stresslin-axistress-nls.png)Meridional stress

The meridional stresses are computed using the following relations. The meridional force per unit circumferential length is

![](../graphics/stm_eqn02734.gif)where

![](../graphics/stm_eqn02735.gif) is the stress in the meridional direction,

*R* is the radius of the point being integrated, and

![](../graphics/stm_eqn02736.gif) is the mean circumferential radius.The meridional membrane stress ![](../graphics/stm_eqn02737.gif) is obtained by dividing ![](../graphics/stm_eqn02738.gif) through the thickness:

![](../graphics/stm_eqn02739.gif)

The numerical scheme used to compute the meridional membrane stress is

![](../graphics/stm_eqn02740.gif)where

![](../graphics/stm_eqn02741.gif) is the meridional stress component at point *j* along the path and

![](../graphics/stm_eqn02742.gif) is the radius at point *j* along the path.To compute the meridional bending stresses, we first need to compute the distance from the center surface to the neutral surface for meridional bending. That distance, ![](../graphics/stm_eqn02743.gif), is equal to

![](../graphics/stm_eqn02744.gif)where ![](../graphics/stm_eqn00155.gif) is the angle between the thickness direction and the radial direction.

The meridional bending moment per unit circumferential length is defined as

![](../graphics/stm_eqn02745.gif)and the moment of inertia for meridional bending is given by

![](../graphics/stm_eqn02746.gif)

Hence, the meridional bending stresses at the endpoints A and B are obtained with

![](../graphics/stm_eqn02747.gif)The numerical scheme used to compute the meridional bending moment is

![](../graphics/stm_eqn02748.gif)Hoop stress

The hoop membrane stress ![](../graphics/stm_eqn02749.gif) is obtained with

![](../graphics/stm_eqn02750.gif)where

![](../graphics/stm_eqn02751.gif) is the hoop stress and

![](../graphics/stm_eqn00593.gif) is the radius of curvature of the midsurface of the section in the meridional plane.The hoop bending stresses at the endpoints are obtained using the relations

![](../graphics/stm_eqn02752.gif)where

![](../graphics/stm_eqn02753.gif)is the distance from the center surface to the neutral surface for hoop bending,

![](../graphics/stm_eqn02754.gif)is the hoop bending moment per unit meridional length, and

![](../graphics/stm_eqn02755.gif) is the moment of inertia for circumferential bending.

The numerical scheme to compute the circumferential membrane stress is

![](../graphics/stm_eqn02756.gif) and the bending moment is computed with the summation

![](../graphics/stm_eqn02757.gif)Thickness stress

The thickness stress does not transfer any forces or moments. Typically, the stress arises due to applied external pressures and thermal expansion effects, and there is no obvious preferred method for determining "membrane" and "bending" stresses. Hence, we choose the thickness "membrane" stress as the average thickness stress:

![](../graphics/stm_eqn02758.gif)We choose the thickness "bending" stress such that the sum of the thickness membrane and bending stresses at the endpoints A and B is equal to the total stress at these points:

![](../graphics/stm_eqn02759.gif)and interpolate the bending stress linearly between these values. This is a reasonable assumption, since the thickness surface stresses are determined by the applied pressure and should not have a strong "peak" stress contribution.Shear stress

The membrane shear stress in the meridional plane is computed in the same way as the meridional membrane stress:

![](../graphics/stm_eqn02760.gif)where ![](../graphics/stm_eqn02761.gif) is the shear stress along the path.

The shear stress distribution is assumed to be parabolic and equal to zero at the ends. Hence, the bending shear stresses are set to 0.0. The numerical scheme used to compute the membrane shear stress is:

![](../graphics/stm_eqn02762.gif)
### Curvature correction

The equations used when performing stress linearization in axisymmetric structures include the in-plane and out-of-plane radius of curvature of the stress line section. By default, "curvature correction" is turned on for axisymmetric structures and turned off for nonaxisymmetric structures. Abaqus/CAE allows the inclusion of these curvature correction terms in the equations for nonaxisymmetric structures when computing the S22, S33, and S12 components. The numerical scheme is identical to that used when performing stress linearization in axisymmetric structures. The user must select a coordinate system in which to specify the curvature correction terms. An error message is generated when the *x*-axis of the coordinate system is normal to the stress line.

The user can turn off the curvature correction for axisymmetric structures, in which case the linear stress components are computed using the equations for three-dimensional structures.
### Computing the local coordinate system

Stress linearization requires the results to be transformed from the global coordinate system to a local coordinate system defined by the stress line.Axisymmetric case

The computation of the local coordinate system is a trivial procedure when performed for axisymmetric stress linearization. The transformation matrix in this case will be

![](../graphics/stm_eqn02763.gif)Three-dimensional case

When performing three-dimensional stress linearization, the local *x*-axis will be defined by the stress line. The local *y*- and *z*-axes are computed by a series of cross products. This procedure is shown below.

The vector between points (![](../graphics/stm_eqn02764.gif), ![](../graphics/stm_eqn02765.gif), ![](../graphics/stm_eqn02766.gif)) and (![](../graphics/stm_eqn02767.gif), ![](../graphics/stm_eqn02768.gif), ![](../graphics/stm_eqn02769.gif)) is

![](../graphics/stm_eqn02770.gif)Assuming the local *y*-axis lies in the plane of the local *x*-axis and the global *Y*-axis, the local *z*-axis is defined by

![](../graphics/stm_eqn02771.gif)Therefore, the local *y*-axis will be

![](../graphics/stm_eqn02772.gif)After normalization, the above three vectors can be combined to create the transformation matrix.
### Reference

### Reference

Chapter 52, "Calculating linearized stresses," of the Abaqus/CAE User's Guide