# 3.7.3 Rebar modeling in shell, membrane, and surface elements

### 3.7.3 Rebar modeling in shell, membrane, and surface elements

**Products: **Abaqus/Standard  Abaqus/Explicit

The definition of rebar in shell, membrane, or surface elements is based on three geometric properties: the cross-sectional area of each individual rebar, the spacing between the rebars, and the orientation of the rebar with respect to the local coordinate system of the element. For shell elements the rebar definition also requires the distance from the midsurface to the rebar. In Abaqus an equivalent "smeared" orthotropic layer is created based on these geometric properties and the elastic modulus of the rebar material. The equivalent rebar layer lies parallel to the midsurface of the element. For membrane and surface elements this layer coincides with the plane of the element, and for shell elements this layer can be offset by an amount up to half of the shell's thickness. In geometrically linear analyses the geometric properties of the equivalent rebar layer remain constant. However, in geometrically nonlinear analyses each of these properties can change as a result of finite-strain effects.

The user has many options for defining which direction the rebar acts in the element. In each case an angle ![](../graphics/stm_eqn03471.gif) is determined between the reinforcement and one of the element's isoparametric coordinate directions (selected by the user), measured positive with the axis of rotation along the normal to the element. Let the unit vector ![](../graphics/stm_eqn00553.gif) define the rebar direction at a point in the element. The isoparametric directions are given by the tangent vectors ![](../graphics/stm_eqn04990.gif) defined

![](../graphics/stm_eqn04991.gif)where ![](../graphics/stm_eqn00141.gif) is the reference midsurface position, ![](../graphics/stm_eqn04992.gif) are the isoparametric coordinate functions (![](../graphics/stm_eqn04993.gif) 1 or 2), ![](../graphics/stm_eqn04994.gif) are the element's shape functions, and ![](../graphics/stm_eqn04995.gif) are the element's reference nodal positions.

The reference or initial rebar angle, ![](../graphics/stm_eqn03471.gif), is calculated from the inner product between the rebar unit vector, ![](../graphics/stm_eqn00553.gif), and the isoparametric direction, ![](../graphics/stm_eqn04990.gif), where ![](../graphics/stm_eqn00904.gif) is specified by the user.

![](../graphics/stm_eqn04996.gif)

Both the rebar direction, ![](../graphics/stm_eqn00553.gif), and the user-selected isoparametric direction, ![](../graphics/stm_eqn04990.gif), lie in a tangent plane parallel to the midsurface. The in-plane unit vector perpendicular to the rebar direction, ![](../graphics/stm_eqn00779.gif), is defined by rotating ![](../graphics/stm_eqn00553.gif) through 90 around the normal to the midsurface, ![](../graphics/stm_eqn00278.gif). The normal direction, ![](../graphics/stm_eqn00278.gif), is found as

![](../graphics/stm_eqn04997.gif)

As the rebar-reinforced element deforms, the rebars change in length and spacing. The smeared rebar layer assumption implies that the deformation of the rebar layer is determined from the deformation gradient ![](../graphics/stm_eqn00319.gif) of the underlying element. Following from this assumption, the rebar stretch ![](../graphics/stm_eqn04998.gif) is

![](../graphics/stm_eqn04999.gif)where ![](../graphics/stm_eqn05000.gif) is the deformed rebar material fiber. Since the deformation gradient maps material lines that are etched into the reference body into the deformed configuration, the length change of these material lines defines the stretch. The rebar logarithmic strain, ![](../graphics/stm_eqn05001.gif), is

![](../graphics/stm_eqn05002.gif)

The rebar spacing stretch ![](../graphics/stm_eqn05003.gif) is the stretch in the plane of the rebar in the direction perpendicular to the rebar. To determine the spacing stretch ![](../graphics/stm_eqn05003.gif), use the fact that the unit normal, ![](../graphics/stm_eqn00156.gif), perpendicular to the deformed rebar direction, ![](../graphics/stm_eqn00479.gif), in the plane of the rebar is

![](../graphics/stm_eqn05004.gif)It is easily verified that ![](../graphics/stm_eqn00156.gif) is a unit vector. To see that it is perpendicular to ![](../graphics/stm_eqn00479.gif), take the inner product:

![](../graphics/stm_eqn05005.gif)The spacing stretch, ![](../graphics/stm_eqn05003.gif), can be defined as the component along ![](../graphics/stm_eqn00156.gif) of the deformation of the direction ![](../graphics/stm_eqn00779.gif) perpendicular to the reference rebar direction. Since the deformation of ![](../graphics/stm_eqn00779.gif) is ![](../graphics/stm_eqn05006.gif), the spacing stretch follows from

![](../graphics/stm_eqn05007.gif)Since ![](../graphics/stm_eqn00779.gif) is a unit vector,

![](../graphics/stm_eqn05008.gif)

The final angle ![](../graphics/stm_eqn01111.gif) that the rebar direction makes with respect to the user-selected isoparametric direction is

![](../graphics/stm_eqn05009.gif)The rebar rotation or change in rebar angle, ![](../graphics/stm_eqn05010.gif), is the difference between the final angle and the original angle:

![](../graphics/stm_eqn05011.gif)Abaqus reports the current angle, ![](../graphics/stm_eqn01111.gif), and the change in the rebar angle, ![](../graphics/stm_eqn05012.gif), for each rebar definition at each integration location of the element.

The equivalent thickness of the smeared layer is equal to the area of the rebar divided by the rebar's spacing; Abaqus assumes that the volume of the rebar remains constant throughout the analysis. This assumption implies that the area and spacing of the rebar may change as a result of finite-strain effects. The rebar's area and spacing in the deformed configuration are defined as follows:

![](../graphics/stm_eqn05013.gif)where

![](../graphics/stm_eqn05014.gif)

In shell elements the rebar layer can be defined initially at a distance above or below the midsurface. In shell elements that permit finite strain, the shell's thickness can change as a function of the in-plane deformation. In Abaqus/Standard the thickness change is defined by the section Poisson's ratio, which can be specified by the user. In Abaqus/Explicit this behavior is based on the actual material properties through the shell's thickness. To account for the change in the shell's thickness, the rebar layer's distance from the midsurface is scaled by the thickness stretch.
### Reference

### Reference

"Defining reinforcement,"  Section 2.2.3 of the Abaqus Analysis User's Guide