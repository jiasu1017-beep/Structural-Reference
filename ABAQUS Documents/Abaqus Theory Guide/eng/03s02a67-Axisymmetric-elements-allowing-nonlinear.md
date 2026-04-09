# 3.2.9 Axisymmetric elements allowing nonlinear bending

### 3.2.9 Axisymmetric elements allowing nonlinear bending

**Product: **Abaqus/Standard

Abaqus/Standard includes a library of solid elements whose geometry is initially axisymmetric and that allow for nonlinear analysis in which bending can occur about the plane ![](../graphics/stm_eqn03117.gif) in the (*r*, *z*, ![](../graphics/stm_eqn01111.gif)) cylindrical coordinate system of the model. The geometric model is defined in the *r*&#8211;*z* plane only. The displacements are the usual isoparametric interpolations with respect to *r* and *z*, augmented by Fourier expansions with respect to ![](../graphics/stm_eqn01111.gif). Since the elements are written for bending about the plane ![](../graphics/stm_eqn03117.gif) only, they cannot be used to model torsion of the structure about the original axis of symmetry. Because the elements are intended for nonlinear applications, the orthogonality properties associated with Fourier modes cannot be used to reduce the problem to a series of smaller, uncoupled, cases, since the stiffness before projection onto the Fourier modes is not necessarily constant. For this reason these elements are significantly more expensive to use than the corresponding axisymmetric elements intended for axisymmetric deformations.
### Interpolation

The coordinate system used with these elements is the cylindrical system (*r*, *z*, ![](../graphics/stm_eqn01111.gif)), where *r* measures the distance of a point from the axis of the cylindrical system, *z* measures its position along this axis, and ![](../graphics/stm_eqn01111.gif) measures the angle between the plane containing the point and the axis of the coordinate system and some fixed reference plane that contains the coordinate system axis. The order in which the coordinates and displacements are taken in these elements is based on the convention used in Abaqus for axisymmetric elements, so that *z* is the second coordinate. This allows these elements to be used in conjunction with other elements in the library that allow only axisymmetric deformation. This order is not the same as that used in three-dimensional elements in Abaqus in which *z* is the third coordinate, nor is it the order (*r*, ![](../graphics/stm_eqn01111.gif), *z*), usually taken in cylindrical systems.

The original geometry of the elements is assumed to be axisymmetric with respect to the axis of the coordinate system and, thus, independent of ![](../graphics/stm_eqn01111.gif). Let ![](../graphics/stm_eqn03101.gif), ![](../graphics/stm_eqn03066.gif), and ![](../graphics/stm_eqn03118.gif) be unit vectors in the radial, axial, and circumferential directions at a point in the undeformed state. The reference position ![](../graphics/stm_eqn00141.gif) of the point can be represented in terms of the original radius *R* and the axial position *Z*:

![](../graphics/stm_eqn03119.gif)Similarly the displacement ![](../graphics/stm_eqn00428.gif) of the point can be represented in terms of the components ![](../graphics/stm_eqn03055.gif), ![](../graphics/stm_eqn03056.gif), and ![](../graphics/stm_eqn03120.gif) with respect to these same vectors at the original position of the point:

![](../graphics/stm_eqn03121.gif)For small radial and circumferential displacements the circumferential displacement is proportional to the change in circumferential angle (![](../graphics/stm_eqn03122.gif)), but for large displacements this relation becomes nonlinear (![](../graphics/stm_eqn03123.gif)), as shown in [Figure 3.2.9&#8211;1](03s02a67.md).

Figure 3.2.9&#8211;1 Displacement and rotation in the *r*&#8211;![](../graphics/stm_eqn01111.gif) plane.

![](../graphics/stmrtheta-disp-rot.png) The distinction is of importance only in geometrically nonlinear analysis with radially applied concentrated loads and/or sliding radial boundary conditions.This definition of the degrees of freedom is equivalent to applying transformations to the global (*x*, *y*, *z*) degrees of freedom associated with a standard continuum element. Hence, the nonlinear equations associated with these elements have the same structure as the equations for standard continuum elements.

A general interpolation scheme for ![](../graphics/stm_eqn00428.gif) using Fourier terms with respect to ![](../graphics/stm_eqn01111.gif) is used:

![](../graphics/stm_eqn03124.gif)where *g*, *h* are isoparametric coordinates in the original *R*&#8211;*Z* plane; ![](../graphics/stm_eqn03125.gif) are polynomial interpolation functions; and ![](../graphics/stm_eqn03126.gif), ![](../graphics/stm_eqn03127.gif), and ![](../graphics/stm_eqn03128.gif) are solution amplitude values. *M* is the number of terms used for interpolation with respect to *g*, *h*; and *P* is the number of terms used in the Fourier interpolation with respect to ![](../graphics/stm_eqn01111.gif). Purely axisymmetric deformation results when ![](../graphics/stm_eqn03129.gif).

We reduce the number of variables in such an element by assuming that bending is allowed only about one plane, ![](../graphics/stm_eqn03117.gif), so that the plane ![](../graphics/stm_eqn03130.gif), *n* integer, is a plane of symmetry. The only terms that satisfy this condition are

![](../graphics/stm_eqn03131.gif) For convenience we use the values of the ![](../graphics/stm_eqn03072.gif) and ![](../graphics/stm_eqn03056.gif) displacement components at specific locations around the model between ![](../graphics/stm_eqn03132.gif) and ![](../graphics/stm_eqn03133.gif) instead of the Fourier amplitudes ![](../graphics/stm_eqn03134.gif) and ![](../graphics/stm_eqn03135.gif). The main reason for this is to allow the elements to be used with interface elements, such as slide lines, for which physical displacement values are required. This is accurate only if it is assumed that the relative displacements in the ![](../graphics/stm_eqn01111.gif)-direction are small so that the interface conditions are considered with respect to ![](../graphics/stm_eqn03055.gif) and ![](../graphics/stm_eqn03056.gif) only; that is, in planes of constant ![](../graphics/stm_eqn01111.gif). In addition, we omit the subscript *s* in the expression for the circumferential displacement: ![](../graphics/stm_eqn03136.gif). [Equation 3.2.9&#8211;1](03s02a67.md) is, therefore, rewritten

![](../graphics/stm_eqn03137.gif)where ![](../graphics/stm_eqn03138.gif) are trigonometric interpolation functions and ![](../graphics/stm_eqn03139.gif), ![](../graphics/stm_eqn03140.gif) are physical radial and axial displacement components at ![](../graphics/stm_eqn03141.gif).

The ![](../graphics/stm_eqn03142.gif) interpolators at the associated positions ![](../graphics/stm_eqn03143.gif) are taken as

![](../graphics/stm_eqn03144.gif):

![](../graphics/stm_eqn03145.gif)and

![](../graphics/stm_eqn03146.gif)

![](../graphics/stm_eqn03147.gif):

![](../graphics/stm_eqn03148.gif)and

![](../graphics/stm_eqn03149.gif)

![](../graphics/stm_eqn03150.gif):

![](../graphics/stm_eqn03151.gif)

![](../graphics/stm_eqn03152.gif)and

![](../graphics/stm_eqn03153.gif)

![](../graphics/stm_eqn03154.gif):

![](../graphics/stm_eqn03155.gif)and

![](../graphics/stm_eqn03156.gif)

![](../graphics/stm_eqn03157.gif) is the highest-order interpolation offered with respect to ![](../graphics/stm_eqn01111.gif) in these elements: the elements become significantly more expensive as higher-order interpolation is used; and it is assumed that, because of this, full three-dimensional modeling is less expensive than using these elements with ![](../graphics/stm_eqn03158.gif).
### Integration

The integration scheme used in these elements is a product of integration with respect to element coordinates in surfaces that were originally in the ![](../graphics/stm_eqn03159.gif)&#8211;*Z* plane and integration with respect to ![](../graphics/stm_eqn01111.gif). For the former the same scheme is used as in the corresponding purely axisymmetric elements (for example, either full or reduced Gauss integration in the isoparametric quadrilaterals). For integration with respect to ![](../graphics/stm_eqn01111.gif) the trapezoidal rule is used, with the number of integration points set to ![](../graphics/stm_eqn03160.gif).
### Deformation gradient

For a material point in space the deformation gradient ![](../graphics/stm_eqn03161.gif) is defined as the gradient of the current position ![](../graphics/stm_eqn01887.gif) with respect to the original position ![](../graphics/stm_eqn00141.gif):

![](../graphics/stm_eqn03162.gif)The current position ![](../graphics/stm_eqn00117.gif) can be described in terms of the original position ![](../graphics/stm_eqn03163.gif) and the displacement ![](../graphics/stm_eqn03164.gif)

![](../graphics/stm_eqn03165.gif)and the gradient operator can be described in terms of partial derivatives with respect to the cylindrical coordinates:

![](../graphics/stm_eqn03166.gif)

Since the radial and circumferential base vectors depend on the original circumferential coordinate ![](../graphics/stm_eqn01111.gif): ![](../graphics/stm_eqn03167.gif), ![](../graphics/stm_eqn03168.gif), the partial derivatives of these base vectors with respect to ![](../graphics/stm_eqn01111.gif) are nonvanishing:

![](../graphics/stm_eqn03169.gif)With this result the deformation gradient is obtained as

![](../graphics/stm_eqn03170.gif)Alternatively, this can be written in matrix form with components relative to the local reference basis ![](../graphics/stm_eqn03101.gif), ![](../graphics/stm_eqn03066.gif), ![](../graphics/stm_eqn03118.gif):

![](../graphics/stm_eqn03171.gif)

To be able to analyze approximately incompressible material behavior, the volume change in the fully integrated 4-node quadrilaterals is assumed to be independent of *g* and ![](../graphics/stm_eqn03079.gif) in an *R*&#8211;*Z* plane. Hence, ![](../graphics/stm_eqn03172.gif) is modified according to

![](../graphics/stm_eqn03173.gif)where ![](../graphics/stm_eqn03174.gif) is the volume change at the integration point and ![](../graphics/stm_eqn03175.gif) is the average volume change over the *R*&#8211;*Z* plane of the element. In addition, the part of the axisymmetric hoop strain that does not depend on ![](../graphics/stm_eqn01111.gif) is made independent of *g* and *h*. Experience has shown this considerably improves the solution accuracy for axisymmetric problems. Thus, we use

![](../graphics/stm_eqn03176.gif)where

![](../graphics/stm_eqn03177.gif)with ![](../graphics/stm_eqn03178.gif) the leading (constant) term in ![](../graphics/stm_eqn03179.gif).
### Strain and rotation increments

Strain and rotation increments are calculated from the integrated velocity gradient matrix, ![](../graphics/stm_eqn03180.gif), defined as

![](../graphics/stm_eqn03181.gif)where ![](../graphics/stm_eqn03182.gif). This expression is not easily evaluated directly, since points that were in an *R*&#8211;*Z* plane in the undeformed shape will no longer be located in the same plane after deformation. Instead, we calculate the gradient of ![](../graphics/stm_eqn03183.gif) with respect to the reference state and obtain ![](../graphics/stm_eqn03180.gif) with the transformation

![](../graphics/stm_eqn03184.gif)In matrix form this can be written as

![](../graphics/stm_eqn03185.gif)with

![](../graphics/stm_eqn03186.gif)

The strain increments are approximated as the symmetric part of ![](../graphics/stm_eqn03180.gif):

![](../graphics/stm_eqn03187.gif)As was the case for the deformation gradient, we modify the volume strain increment in the fully integrated 4-node quadrilaterals to be independent of *g* and *h* in an *R*&#8211;*Z* plane, which yields

![](../graphics/stm_eqn03188.gif)where ![](../graphics/stm_eqn03189.gif) is the unit matrix, ![](../graphics/stm_eqn03190.gif) is the volume strain increment at the integration point, and ![](../graphics/stm_eqn03191.gif) is the average volume strain increment over the *R*&#8211;*Z* plane of the element. In addition we use the approximation

![](../graphics/stm_eqn03192.gif)

The spin increments, ![](../graphics/stm_eqn03193.gif), are approximated as the antisymmetric part of ![](../graphics/stm_eqn03194.gif), which in matrix form becomes

![](../graphics/stm_eqn03195.gif)
### Virtual work

The formulation of equilibrium (virtual work) requires linearization of the strain-displacement relation in the current state. For fully integrated 4-node elements the volume strain modification provides

![](../graphics/stm_eqn03196.gif)where

![](../graphics/stm_eqn03197.gif)and

![](../graphics/stm_eqn03198.gif)As was the case for the strain increments, the linearized strain-displacement relation involves taking derivatives in the deformed shape (![](../graphics/stm_eqn03199.gif)), which is troublesome since points that were in an *R*&#8211;*Z* plane in the undeformed shape will no longer be located in the same plane. Hence, ![](../graphics/stm_eqn03092.gif) is computed in a similar manner to ![](../graphics/stm_eqn03180.gif):

![](../graphics/stm_eqn03200.gif)In matrix form this can be written as

![](../graphics/stm_eqn03201.gif)where

![](../graphics/stm_eqn03202.gif)

For fully integrated, 4-node quadrilaterals we again use the approximation

![](../graphics/stm_eqn03203.gif)

The displacements and, hence, the displacement variations, are interpolated in terms of nodal displacement variations with [Equation 3.2.9&#8211;2](03s02a67.md). The derivatives of the displacements with respect to ![](../graphics/stm_eqn03159.gif), *Z*, and ![](../graphics/stm_eqn03077.gif) are readily obtained from these expressions:

![](../graphics/stm_eqn03204.gif)
### Stiffness in the current state

Since the elements are formulated in terms of Cartesian components of displacements, the equations presented in "Solid element formulation,"  Section 3.2.2, apply. For the 4-node quadrilaterals, we can adapt [Equation 3.2.2&#8211;1](03s02a60.md) to the averaged volume change formulation, which yields

![](../graphics/stm_eqn03205.gif)The second variation in ![](../graphics/stm_eqn03206.gif) is obtained with the standard procedure

![](../graphics/stm_eqn03207.gif)where ![](../graphics/stm_eqn03208.gif) has the same form as ![](../graphics/stm_eqn03209.gif) After introduction of the corotational stress rate, ![](../graphics/stm_eqn03210.gif) this yields

![](../graphics/stm_eqn03211.gif)This can be worked out in terms of nodal degrees of freedom with the expressions for ![](../graphics/stm_eqn03092.gif) and ![](../graphics/stm_eqn03212.gif) obtained in the previous paragraph on virtual work.
### Hourglass control

In the 4-node reduced integration element the hourglass modes must be controlled. These modes are similar to the ones in regular axisymmetric elements but have some additional features.

The hourglass pattern can vary along the circumference, which requires application of an hourglass stiffness at multiple points around the circumference.

Hourglassing can also occur in the circumferential direction.Hence, at each integration point around the circumference, we calculate the hourglass strains

![](../graphics/stm_eqn03213.gif)Here ![](../graphics/stm_eqn00319.gif) is the deformation gradient as given by [Equation 3.2.9&#8211;3](03s02a67.md) and ![](../graphics/stm_eqn03214.gif) and ![](../graphics/stm_eqn03215.gif) are the hourglass modes in the deformed and undeformed geometry respectively:

![](../graphics/stm_eqn03216.gif)where ![](../graphics/stm_eqn03217.gif) is the same hourglass operator as used for the 4-node axisymmetric continuum elements and ![](../graphics/stm_eqn03218.gif) and ![](../graphics/stm_eqn03219.gif) are the nodal positions at angle ![](../graphics/stm_eqn01111.gif) in the deformed and undeformed states. Observe that since the initial geometry is axisymmetric, ![](../graphics/stm_eqn03219.gif) is independent of ![](../graphics/stm_eqn01111.gif):

![](../graphics/stm_eqn03220.gif)In the deformed state we write

![](../graphics/stm_eqn03221.gif)With [Equation 3.2.9&#8211;2](03s02a67.md) this becomes

![](../graphics/stm_eqn03222.gif)The hourglass "strain" transforms into an hourglass "force" with the hourglass stiffness *c*:

![](../graphics/stm_eqn03223.gif)This hourglass stiffness can be obtained with the same procedure as used for the regular axisymmetric elements, where the only difference is the scaling factor required to reflect the fact that each point reflects only part of the circumference. The first variation of ![](../graphics/stm_eqn00178.gif) is readily obtained as

![](../graphics/stm_eqn03224.gif)

Here ![](../graphics/stm_eqn03225.gif) follows from [Equation 3.2.9&#8211;7](03s02a67.md), and for ![](../graphics/stm_eqn03226.gif) we obtain

![](../graphics/stm_eqn03227.gif)

Similarly, we obtain for the second variation

![](../graphics/stm_eqn03228.gif)where ![](../graphics/stm_eqn03229.gif) and ![](../graphics/stm_eqn03230.gif) follow with the same expressions as used in the first variation.
### Pressure loads and load stiffness

For geometrically linear problems equivalent nodal loads due to applied surface pressures and body forces are readily calculated since the geometry is axisymmetric. For geometrically nonlinear problems the treatment of body forces does not change because of the fixed direction of the forces and because the forces are proportional to the volume, which is assumed to change by a negligible amount. However, for surface pressures nonaxisymmetric deformations must be taken into consideration.

The equivalent nodal loads associated with surface pressure *p* can be obtained by considering the virtual work contribution

![](../graphics/stm_eqn03231.gif) where ![](../graphics/stm_eqn01040.gif) is the parametric surface coordinate in the *R*&#8211;*Z* plane and

![](../graphics/stm_eqn03232.gif)with ![](../graphics/stm_eqn03233.gif) and ![](../graphics/stm_eqn03234.gif). Hence, the current position of a point can be expressed in terms of the surface interpolator ![](../graphics/stm_eqn03235.gif) and the standard circumferential interpolators:

![](../graphics/stm_eqn03236.gif)

The terms in [Equation 3.2.9&#8211;8](03s02a67.md) can be worked out as follows:

![](../graphics/stm_eqn03237.gif)and, hence,

![](../graphics/stm_eqn03238.gif)

Hence, we obtain the virtual work contribution

![](../graphics/stm_eqn03239.gif)

With use of the interpolation functions we, thus, obtain the equivalent nodal forces:

![](../graphics/stm_eqn03240.gif)

![](../graphics/stm_eqn03241.gif) For geometrically linear analysis this reduces to the standard axisymmetric equivalent nodal loads

![](../graphics/stm_eqn03242.gif)The load stiffness matrix follows by linearization:

![](../graphics/stm_eqn03243.gif) with

![](../graphics/stm_eqn03244.gif)

![](../graphics/stm_eqn03245.gif)

![](../graphics/stm_eqn03246.gif)

![](../graphics/stm_eqn03247.gif)

![](../graphics/stm_eqn03248.gif)

![](../graphics/stm_eqn03249.gif)

![](../graphics/stm_eqn03250.gif)

In the case of hydrostatic pressure (*p* dependent on *z*) some additional terms appear. These terms are readily obtained from the expression

![](../graphics/stm_eqn03251.gif)

With use of the interpolation functions we, thus, obtain the additional load stiffness contributions:

![](../graphics/stm_eqn03252.gif)
### Mass matrix

At each material point the displacement components in the three directions (radial, axial, circumferential) are dependent only on the corresponding nodal displacement components. Hence, the mass matrix does not involve any coupling between the radial, axial, and circumferential degrees of freedom, and we can write the mass matrix in the form of three separate expressions:

![](../graphics/stm_eqn03253.gif)Here the superscripts *m* and *n* refer to a particular node in the *r*&#8211;*z* plane, and the superscripts *p* and *q* refer to a particular position along the circumference. The interpolation functions ![](../graphics/stm_eqn03254.gif), ![](../graphics/stm_eqn03255.gif), and ![](../graphics/stm_eqn03256.gif) are the product of interpolation functions ![](../graphics/stm_eqn03257.gif) in the *r*&#8211;*z* plane and interpolation functions in the ![](../graphics/stm_eqn01111.gif)-direction:

![](../graphics/stm_eqn03258.gif)The volume integral used to form the mass matrix can be split into an integral over the *r*&#8211;*z* cross-section and an integral around the circumference. For the *r*&#8211;*r* component of the mass matrix this yields

![](../graphics/stm_eqn03259.gif)This matrix can be written in a convenient form by defining the primitive mass matrix,

![](../graphics/stm_eqn03260.gif)This primitive mass matrix is the same mass matrix that is used for the regular axisymmetric elements. We can also define the circumferential distribution matrices

![](../graphics/stm_eqn03261.gif)The radial, axial, and circumferential components of the mass matrix then take the form

![](../graphics/stm_eqn03262.gif)

The circumferential distribution matrices can be evaluated for various values of the number of terms *P* in the Fourier series. After some calculations the following results are obtained:

![](../graphics/stm_eqn03144.gif):

![](../graphics/stm_eqn03263.gif)

![](../graphics/stm_eqn03147.gif):

![](../graphics/stm_eqn03264.gif)

![](../graphics/stm_eqn03265.gif):

![](../graphics/stm_eqn03266.gif)

![](../graphics/stm_eqn03267.gif):

![](../graphics/stm_eqn03268.gif)
### Hybrid and pore pressure elements

For hybrid and pore pressure elements additional degrees of freedom *p* are added. In the hybrid elements these degrees of freedom are internal to the element and represent the hydrostatic pressure in the material. In the pore pressure elements the degrees of freedom represent the hydrostatic pressure in the fluid as interpolated from the pressure variables at the external, user-defined nodes. Let the interpolation function for the (hydrostatic or pore) pressure in the *r*&#8211;*z* plane be denoted by ![](../graphics/stm_eqn03269.gif). The interpolation functions are the same as for the regular axisymmetric hybrid and pore pressure elements, respectively. Along the circumference, we observe that in the geometrically linear formulation the volumetric strain ![](../graphics/stm_eqn00155.gif) only shows cosine dependence:

![](../graphics/stm_eqn03270.gif)Hence, we choose the hydrostatic/pore pressure to have cosine dependence only:

![](../graphics/stm_eqn03271.gif)In the nonlinear case ![](../graphics/stm_eqn00155.gif) will exhibit higher-order variations in ![](../graphics/stm_eqn01111.gif). For approximately incompressible materials, these higher-order terms are likely to lead to "locking" of the finite element mesh for nonaxisymmetric deformations. In the hybrid formulation, however, the higher-order terms in ![](../graphics/stm_eqn00155.gif) are not used for calculation of hydrostatic pressure: only the cosine terms as used in the interpolation for *p* are used. Hence, the hybrid elements prevent locking in the nonaxisymmetric modes as well as in the axisymmetric modes.
### Pore pressure gradient

For a material point in space in the pore pressure element, the pore pressure gradient calculation involves taking derivatives of the pore pressure with respect to the current position ![](../graphics/stm_eqn00117.gif). Again, we do not evaluate the gradient directly but calculate it with respect to the original position ![](../graphics/stm_eqn00141.gif), with the following transformation:

![](../graphics/stm_eqn03272.gif)where ![](../graphics/stm_eqn00319.gif) is the deformation gradient, and the cylindrical components of the scalar gradient of the pore pressure with respect to ![](../graphics/stm_eqn00141.gif) are readily obtained from the following expressions:

![](../graphics/stm_eqn03273.gif)
### Reference

### Reference

"Axisymmetric solid elements with nonlinear, asymmetric deformation,"  Section 28.1.7 of the Abaqus Analysis User's Guide