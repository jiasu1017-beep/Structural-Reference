# 3.6.7 Axisymmetric shell element allowing asymmetric loading

### 3.6.7 Axisymmetric shell element allowing asymmetric loading

**Product: **Abaqus/Standard

The Abaqus/Standard element library includes a family of nonlinear thin shell elements with axisymmetric reference geometry that allow asymmetric loading and deformation (SAXA1N and SAXA2N). This section provides their theoretical formulation. These elements encompass a broad range of practical applications from the bending/ovalization of variable diameter pipes to the bending of circular plates. The theoretical formulation of these elements is similar to the general finite-strain shell element described in "Finite-strain shell element formulation,"  Section 3.6.5. Furthermore, this formulation is the shell counterpart to the continuum axisymmetric bending elements described in "Axisymmetric elements allowing nonlinear bending,"  Section 3.2.9.

As with the continuum axisymmetric bending formulation, the restriction is made that a plane of symmetry exists in the *r*&#8211;*z* plane at ![](../graphics/stm_eqn03054.gif). Hence in-plane bending of the model is permitted, while deformations such as torsion about the axis of symmetry are precluded. The symmetries of the undeformed configuration and of the deformation are exploited through the assumption of particular displacement and rotation interpolations around the circumference of the shell. Specifically, Fourier series expansions are used in the ![](../graphics/stm_eqn01111.gif) or circumferential direction that preserve the plane of symmetry.
### Geometric description

Let ![](../graphics/stm_eqn04611.gif) be coordinate functions parametrizing the reference surface of the shell and let ![](../graphics/stm_eqn04612.gif) be the coordinate function in the thickness direction, where *h* is the shell's initial thickness. (For a detailed account of the geometric description of the finite-strain shell formulation, see "Finite-strain shell element formulation,"  Section 3.6.5.) Then points in the reference or undeformed configuration are identified by the normal coordinates mapping

![](../graphics/stm_eqn04613.gif)where ![](../graphics/stm_eqn00141.gif) is the three-dimensional position of a material point, ![](../graphics/stm_eqn01007.gif) is the shell reference surface mapping, and ![](../graphics/stm_eqn04614.gif) is the unit normal to the shell reference surface. The fact that ![](../graphics/stm_eqn04614.gif) is a unit vector assumes that the reference configuration is (locally) of constant thickness. Owing to the axisymmetric reference configuration, ![](../graphics/stm_eqn01007.gif) can be given relative to a global Cartesian coordinate system as

![](../graphics/stm_eqn04615.gif)where ![](../graphics/stm_eqn04616.gif) is the radius, ![](../graphics/stm_eqn04617.gif) is the axial position, and ![](../graphics/stm_eqn04618.gif) are the cylindrical coordinates. (Note that the usual convention for cylindrical coordinates ![](../graphics/stm_eqn04619.gif) has been changed, which is consistent with the axisymmetric shell elements and the axisymmetric elements allowing nonlinear bending.) By definition the normal field to the shell reference surface is ![](../graphics/stm_eqn04620.gif), which by direct computation yields

![](../graphics/stm_eqn04621.gif)where ![](../graphics/stm_eqn04622.gif) and ![](../graphics/stm_eqn04623.gif). Relative to the cylindrical coordinate system, ![](../graphics/stm_eqn04624.gif).

The basic kinematic assumption is that for any deformed configuration, the position of a point in the body can be identified by

![](../graphics/stm_eqn04625.gif)where ![](../graphics/stm_eqn00117.gif) is the deformed position of the material point, ![](../graphics/stm_eqn01008.gif) is the deformed shell reference surface mapping, ![](../graphics/stm_eqn04194.gif) is the deformed unit director field, and ![](../graphics/stm_eqn04196.gif) is the thickness change parameter. Of critical importance for any shell formulation is the treatment of the rotation field; that is, the treatment of the director field ![](../graphics/stm_eqn04194.gif). The geometric description and the incremental update procedure for the director field are given in detail below.

Under the kinematic assumption above, the deformed configuration of the shell is completely determined by the reference surface mapping ![](../graphics/stm_eqn01008.gif), the deformed director field ![](../graphics/stm_eqn04194.gif) and the thickness parameter ![](../graphics/stm_eqn04196.gif).

We define the following displacement quantities. Since ![](../graphics/stm_eqn01008.gif) is an element of a (linear) vector space, we can define the reference surface displacement vector ![](../graphics/stm_eqn00428.gif) by the difference between the deformed reference surface and the undeformed reference surface; i.e.,

![](../graphics/stm_eqn04626.gif)The director field, however, is a unit vector field that is not a member of a linear vector space. The orientation of the director field is defined in terms of a rotation vector ![](../graphics/stm_eqn00152.gif) as

![](../graphics/stm_eqn04627.gif)Here ![](../graphics/stm_eqn00157.gif) is the skew-symmetric matrix with axial vector ![](../graphics/stm_eqn00152.gif), defined by the properties

![](../graphics/stm_eqn04628.gif)and ![](../graphics/stm_eqn00179.gif) is an orthogonal transformation given by the closed-form expression

![](../graphics/stm_eqn04629.gif)Alternatively, quaternion algebra can be used to specify the orientation of the deformed director field ![](../graphics/stm_eqn04194.gif). In this case the orthogonal matrix ![](../graphics/stm_eqn04630.gif) is replaced by the quaternion parameter ![](../graphics/stm_eqn00194.gif), where

![](../graphics/stm_eqn04631.gif)The orientation of the unit director field then follows as

![](../graphics/stm_eqn04632.gif)Similarly, the orthogonal transformation ![](../graphics/stm_eqn04630.gif) can be extracted from the quaternion parameter as

![](../graphics/stm_eqn04633.gif)
### Interpolations

Displacement and rotation components are given relative to the cylindrical coordinate system ![](../graphics/stm_eqn04634.gif) with orthonormal basis vectors ![](../graphics/stm_eqn04635.gif) that are fixed in the reference or undeformed configuration. A general interpolation scheme for ![](../graphics/stm_eqn04636.gif) and ![](../graphics/stm_eqn04637.gif) using a Fourier expansion in the ![](../graphics/stm_eqn01111.gif) variable is

![](../graphics/stm_eqn04638.gif)Here ![](../graphics/stm_eqn04639.gif) are the polynomial interpolation functions along the generator lines of the axisymmetric reference configuration; ![](../graphics/stm_eqn04640.gif), ![](../graphics/stm_eqn04641.gif), ![](../graphics/stm_eqn04642.gif), ![](../graphics/stm_eqn04643.gif), ![](../graphics/stm_eqn04644.gif), ![](../graphics/stm_eqn04645.gif) are the solution amplitude values (Fourier coefficients); *M* is the number of terms used in the interpolation along the generator lines; and *P* is the number of Fourier interpolation terms used around the circumference of the reference shell. Note that an axisymmetric deformation is obtained for the choice ![](../graphics/stm_eqn03129.gif).

The symmetry requirement in the *r*&#8211;*z* plane at ![](../graphics/stm_eqn04646.gif), ![](../graphics/stm_eqn04647.gif), eliminates many of the above Fourier coefficients. For the displacement vector the only admissible terms are

![](../graphics/stm_eqn04648.gif)For the rotation components, symmetry requirements switch the role of the *r* and *z* components with the ![](../graphics/stm_eqn01111.gif) components:

![](../graphics/stm_eqn04649.gif)For practical reasons the values of ![](../graphics/stm_eqn03055.gif), ![](../graphics/stm_eqn03056.gif), and ![](../graphics/stm_eqn04650.gif) are often required at specific locations around the circumference of the shell. Therefore, displacement and rotation components ![](../graphics/stm_eqn04651.gif), ![](../graphics/stm_eqn04652.gif), and ![](../graphics/stm_eqn04653.gif) are used instead of the Fourier coefficients ![](../graphics/stm_eqn03135.gif), ![](../graphics/stm_eqn04654.gif), and ![](../graphics/stm_eqn04655.gif). Furthermore, a negative sign is introduced in the interpolation for ![](../graphics/stm_eqn04650.gif) for the following reason: The Abaqus convention for axisymmetric shell elements is that the axial tangent direction is drawn between nodes in ascending node number (the shell local 1-direction). The normal to the shell is then obtained by a 90 counter-clockwise rotation of the tangent (the shell local 3-direction). However, a positive rotation of the normal field (about the shell local 2-direction) is counterclockwise. This convention implies a left-handed shell local coordinate system. For the axisymmetric shell bending elements, a right-handed shell local coordinate system is required at the integration points; thus, the direction of positive rotation is reversed there.

Rearranging the Fourier series expansions and making the substitution ![](../graphics/stm_eqn04656.gif), the interpolations for the displacement components are

![](../graphics/stm_eqn04657.gif)Similarly, replacing ![](../graphics/stm_eqn04658.gif) and ![](../graphics/stm_eqn04659.gif) with ![](../graphics/stm_eqn04660.gif) and ![](../graphics/stm_eqn04661.gif) respectively, the interpolation for the rotation components becomes

![](../graphics/stm_eqn04662.gif)In the above interpolations, ![](../graphics/stm_eqn04651.gif), ![](../graphics/stm_eqn04652.gif), and ![](../graphics/stm_eqn04653.gif) are physical displacement and rotation components at ![](../graphics/stm_eqn04663.gif) and ![](../graphics/stm_eqn04664.gif) are trigonometric interpolation functions with the property that ![](../graphics/stm_eqn04665.gif) defined by:

![](../graphics/stm_eqn04666.gif): ![](../graphics/stm_eqn04667.gif), ![](../graphics/stm_eqn04668.gif),

![](../graphics/stm_eqn04669.gif)

![](../graphics/stm_eqn04670.gif): ![](../graphics/stm_eqn04671.gif), ![](../graphics/stm_eqn04672.gif), ![](../graphics/stm_eqn04673.gif),

![](../graphics/stm_eqn04674.gif)

![](../graphics/stm_eqn04675.gif): ![](../graphics/stm_eqn04671.gif), ![](../graphics/stm_eqn04676.gif), ![](../graphics/stm_eqn04677.gif), ![](../graphics/stm_eqn04678.gif),

![](../graphics/stm_eqn04679.gif)

![](../graphics/stm_eqn03157.gif): ![](../graphics/stm_eqn04671.gif), ![](../graphics/stm_eqn04680.gif), ![](../graphics/stm_eqn04681.gif), ![](../graphics/stm_eqn04682.gif), ![](../graphics/stm_eqn04683.gif),

![](../graphics/stm_eqn04684.gif)As with the continuum axisymmetric bending element, ![](../graphics/stm_eqn03157.gif) is the highest-order interpolation offered with respect to ![](../graphics/stm_eqn01111.gif). The element becomes significantly more expensive as higher-order interpolations are used, and it is assumed that the general-purpose finite-strain shell is less expensive than using this element with ![](../graphics/stm_eqn03158.gif).
### Virtual work

The virtual work expression from the three-dimensional theory is

![](../graphics/stm_eqn04685.gif)where *V* is the current volume of the deformed body, ![](../graphics/stm_eqn04686.gif) are the curvilinear components of the Cauchy stress tensor, ![](../graphics/stm_eqn04687.gif) are the components of the Lagrange strain tensor, and ![](../graphics/stm_eqn04688.gif) are the variational or linearized strain measure components. By definition the Lagrange strain tensor components are given by

![](../graphics/stm_eqn04689.gif)Note that in the statement of virtual work, no choice has thus far been made regarding the curvilinear coordinate functions ![](../graphics/stm_eqn04690.gif) ![](../graphics/stm_eqn04691.gif). Furthermore, the current volume measure ![](../graphics/stm_eqn00798.gif) is given by the parametric relationship

![](../graphics/stm_eqn04692.gif)

We now introduce the kinematic assumption [Equation 3.6.7&#8211;1](03s06a85.md) into the definition of ![](../graphics/stm_eqn04687.gif) to find

![](../graphics/stm_eqn04693.gif)where differentiation is now with respect to the parametric coordinates, so that ![](../graphics/stm_eqn04694.gif) and ![](../graphics/stm_eqn04695.gif). Define the following shell strain measure components and kinematic relationships:

![](../graphics/stm_eqn04696.gif)In the above, ![](../graphics/stm_eqn04697.gif) are the components of the second fundamental form of the undeformed reference surface.

Substituting the above definitions into the virtual work expression, we find (after some manipulation) that the volume integral reduces to the following integral over the deformed reference surface

![](../graphics/stm_eqn04698.gif)where ![](../graphics/stm_eqn04699.gif) and the current reference surface Jacobian determinant is ![](../graphics/stm_eqn04700.gif). In the above virtual work expression, the ![](../graphics/stm_eqn04267.gif) term in ![](../graphics/stm_eqn04701.gif) has been neglected. This term is ![](../graphics/stm_eqn04702.gif)---where *h* is the thickness and *R* is some characteristic radius of curvature---and is negligible in light of the kinematic assumption [Equation 3.6.7&#8211;1](03s06a85.md). The shell stress resultant components are defined by the following integrals through the thickness of the shell:

![](../graphics/stm_eqn04703.gif)

For thin shells the Kirchhoff-Love approximation, which states that the deformed director field ![](../graphics/stm_eqn04194.gif) is (approximately) the normal field to the deformed reference surface, is introduced along with the plane stress assumption ![](../graphics/stm_eqn04704.gif). Consistent with these approximations, we neglect all ![](../graphics/stm_eqn04705.gif) terms and terms proportional to the gradient of the thickness parameter. Accordingly, we set

![](../graphics/stm_eqn04706.gif)

We can now summarize the virtual work expression for thin (Kirchhoff-Love) shells:

![](../graphics/stm_eqn04707.gif)where the shell resultant components are defined in terms of the Cauchy stress tensor components by the integrals

![](../graphics/stm_eqn04708.gif)In the expression for ![](../graphics/stm_eqn04709.gif), ![](../graphics/stm_eqn04710.gif) is interpreted as a constraint stress that enforces that the director field remain normal to the reference surface. Two other contributions to the virtual work expression ![](../graphics/stm_eqn04711.gif) and ![](../graphics/stm_eqn04712.gif), where ![](../graphics/stm_eqn04713.gif) are ![](../graphics/stm_eqn04705.gif) and, thus, neglected.
### Orthonormal surface coordinate system and coordinate transformation

It is desirable to define stress resultant quantities relative to an orthonormal basis in the deformed configuration. To do this, we define a normal coordinate system ![](../graphics/stm_eqn04714.gif), where ![](../graphics/stm_eqn03500.gif) and ![](../graphics/stm_eqn03501.gif) are tangent to the deformed reference surface and ![](../graphics/stm_eqn04715.gif) is the unit normal field.

Define the following notation. Let ![](../graphics/stm_eqn04716.gif) ![](../graphics/stm_eqn04717.gif) be the components of ![](../graphics/stm_eqn04718.gif) relative to the basis ![](../graphics/stm_eqn04719.gif); that is

![](../graphics/stm_eqn04720.gif)Furthermore, let the inverse of the matrix of components ![](../graphics/stm_eqn04721.gif) be given by ![](../graphics/stm_eqn04722.gif), such that

![](../graphics/stm_eqn04723.gif)Note that the basis vectors ![](../graphics/stm_eqn03500.gif) and ![](../graphics/stm_eqn03501.gif) induce distance measuring coordinates ![](../graphics/stm_eqn04724.gif) and ![](../graphics/stm_eqn04725.gif) such that

![](../graphics/stm_eqn04726.gif)It follows from [Equation 3.6.7&#8211;5](03s06a85.md) that the orthonormal tangent vectors are given by

![](../graphics/stm_eqn04727.gif)

For the material calculations, it is important to express both the strain and stress quantities relative to the local orthonormal frame ![](../graphics/stm_eqn04728.gif). Accordingly, let ![](../graphics/stm_eqn04729.gif) and ![](../graphics/stm_eqn04730.gif) be the membrane and bending stress resultant components relative to this local orthonormal basis. Thus, we can write

![](../graphics/stm_eqn04731.gif)where we recall that ![](../graphics/stm_eqn04732.gif). Then the stress resultant contributions to the virtual work expression can be transformed as follows. First, the membrane contribution:

![](../graphics/stm_eqn04733.gif)Recall, however, that by the definition of the coordinates ![](../graphics/stm_eqn04734.gif), ![](../graphics/stm_eqn04735.gif). Thus,

![](../graphics/stm_eqn04736.gif)Similarly, the bending contribution is:

![](../graphics/stm_eqn04737.gif)Let ![](../graphics/stm_eqn04738.gif) be the two-dimensional alternator, such that ![](../graphics/stm_eqn04739.gif) and ![](../graphics/stm_eqn04740.gif). Then ![](../graphics/stm_eqn04741.gif) and

![](../graphics/stm_eqn04742.gif)Since the second term in the brackets is proportional to the bending curvature, we neglect this term relative to the first, yielding

![](../graphics/stm_eqn04743.gif)
### Strain displacement operators

We now write the virtual work expression [Equation 3.6.7&#8211;4](03s06a85.md) in matrix operator notation. Define the following stress resultant component vectors:

![](../graphics/stm_eqn04744.gif)Define the matrix strain displacement operators as follows:

![](../graphics/stm_eqn04745.gif)where ![](../graphics/stm_eqn04746.gif) is the column of zeros ![](../graphics/stm_eqn04747.gif). Then the virtual work expression [Equation 3.6.7&#8211;4](03s06a85.md) is equivalently stated

![](../graphics/stm_eqn04748.gif)
### Corotational coordinate system

Thus far ![](../graphics/stm_eqn03500.gif) and ![](../graphics/stm_eqn03501.gif) are any two orthonormal vectors in the tangent plane to the reference surface. We can uniquely choose these two vectors by requiring the matrix components of the incremental reference surface deformation gradient ![](../graphics/stm_eqn04749.gif), where

![](../graphics/stm_eqn04750.gif)to be symmetric; i.e., ![](../graphics/stm_eqn04751.gif). Note that by definition ![](../graphics/stm_eqn04752.gif). This symmetry condition defines a corotational orthonormal basis in the deformed configuration. This orthonormal basis is calculated as follows.

Obtain the Abaqus convention pair of orthonormal surface vectors ![](../graphics/stm_eqn04753.gif). We then rotate these vectors in the tangent plane to the reference surface about the normal vector ![](../graphics/stm_eqn04754.gif) by the angle ![](../graphics/stm_eqn03423.gif), where ![](../graphics/stm_eqn03423.gif) is determined by the symmetry condition ![](../graphics/stm_eqn04751.gif). Thus, we define

![](../graphics/stm_eqn04755.gif)It follows by definition that

![](../graphics/stm_eqn04756.gif)Therefore, define the quantity

![](../graphics/stm_eqn04757.gif)The symmetry condition requires that

![](../graphics/stm_eqn04758.gif)From this it can be determined that

![](../graphics/stm_eqn04759.gif)and ![](../graphics/stm_eqn04760.gif) are then determined by [Equation 3.6.7&#8211;6](03s06a85.md).

Having determined the updated vectors ![](../graphics/stm_eqn04761.gif), we can calculate the quantities required for coordinate transformation. First the incremental deformation gradient components and the Jacobian matrix components:

![](../graphics/stm_eqn04762.gif)Note that due to the symmetry of the incremental deformation gradient components, there is no ambiguity in writing ![](../graphics/stm_eqn04763.gif). We can now calculate the inverse components

![](../graphics/stm_eqn04764.gif)
### Consistent linearization

The iterative solution procedure requires the calculation of the consistent tangent stiffness. This stiffness has two parts, one resulting from the material model and the other resulting from the changing geometry. We denote the second variational quantities with ![](../graphics/stm_eqn04765.gif). Returning to [Equation 3.6.7&#8211;4](03s06a85.md), the virtual work expression can be written as

![](../graphics/stm_eqn04766.gif)where ![](../graphics/stm_eqn04767.gif), ![](../graphics/stm_eqn04768.gif) is the Jacobian determinant of the reference configuration parametrization given by ![](../graphics/stm_eqn04769.gif), and components are relative to the corotated frame with ![](../graphics/stm_eqn04770.gif). We assume constitutive behavior such that

![](../graphics/stm_eqn04771.gif)Thus, the variation of the virtual work expression yields

![](../graphics/stm_eqn04772.gif)The first term in the integrand forms the material stiffness, while the second two terms form the geometric stiffness. The second variation of the strain measure components are calculated in "Finite-strain shell element formulation,"  Section 3.6.5. The second variation of the membrane strain is

![](../graphics/stm_eqn04773.gif)The second variation of the bending strain is zero; i.e.,

![](../graphics/stm_eqn04774.gif)
### Incremental degrees of freedom: interpolations and configuration updates

At the beginning of an increment we have the configuration at iteration *k*, denoted ![](../graphics/stm_eqn04775.gif). In the incremental solution procedure we solve for the incremental displacement field and the incremental rotation field in components relative to the reference cylindrical coordinate system:

![](../graphics/stm_eqn04776.gif)We use these incremental fields to update the configuration to iteration ![](../graphics/stm_eqn04777.gif).

1. *Reference surface update*: The displacement increments are interpolated using the same interpolation scheme as the total displacement vector in [Equation 3.6.7&#8211;2](03s06a85.md):

![](../graphics/stm_eqn04778.gif)The reference surface position map is updated from the displacement increment by

![](../graphics/stm_eqn04779.gif)

2. *Rotation field update*: The incremental rotation field is updated with the same interpolation scheme as the total rotation field in [Equation 3.6.7&#8211;3](03s06a85.md):

![](../graphics/stm_eqn04780.gif)This incremental rotation vector corresponds to a finite rotation, characterized by quaternion parameters as

![](../graphics/stm_eqn04781.gif)The total rotation quaternion parameter can be updated by the update formula

![](../graphics/stm_eqn04782.gif)Similarly, the deformed unit director field can be updated from the incremental rotation field as

![](../graphics/stm_eqn04783.gif)Here we have used the notation ![](../graphics/stm_eqn04784.gif) to denote the rotation of the vector ![](../graphics/stm_eqn00427.gif) by the quaternion ![](../graphics/stm_eqn04785.gif). The curvatures are calculated from the gradient of the director field, which is updated by

![](../graphics/stm_eqn04786.gif)where

![](../graphics/stm_eqn04787.gif)For completeness, we record the values of ![](../graphics/stm_eqn04788.gif). First, along the generator lines we have

![](../graphics/stm_eqn04789.gif)For the circumferential derivative we must account for the derivative of the basis vectors in the ![](../graphics/stm_eqn01111.gif)-direction: ![](../graphics/stm_eqn04790.gif) and ![](../graphics/stm_eqn04791.gif). Hence, ![](../graphics/stm_eqn04792.gif). Introducing the interpolation function, we have

![](../graphics/stm_eqn04793.gif)where ![](../graphics/stm_eqn04794.gif) are computed from the definitions of the interpolation functions ![](../graphics/stm_eqn04664.gif) as given above and ![](../graphics/stm_eqn04795.gif) and ![](../graphics/stm_eqn04796.gif) are given by the interpolation for the incremental rotation field as given in the Rotation Field Update.
### Strain increment and stress resultant update

Following the formulation of the finite-strain shell element formulation in "Finite-strain shell element formulation,"  Section 3.6.5, the three-dimensional (finite) strain increment is calculated as

![](../graphics/stm_eqn04797.gif)Here the increment in the membrane strain components ![](../graphics/stm_eqn04798.gif) is given by the Hughes-Winget second-order approximation to the logarithmic membrane strain increment

![](../graphics/stm_eqn04799.gif)and the increment in the bending strain components ![](../graphics/stm_eqn04800.gif) is given by the expression

![](../graphics/stm_eqn04801.gif)where

![](../graphics/stm_eqn04802.gif)

As an example of the stress update procedure, consider the simple case of a Saint Venant-Kirchhoff material model. In this case,

![](../graphics/stm_eqn04803.gif)where ![](../graphics/stm_eqn04804.gif) are the plane stress elastic coefficients given by

![](../graphics/stm_eqn04805.gif)Note that ![](../graphics/stm_eqn04806.gif), and the components ![](../graphics/stm_eqn04807.gif) are relative to the current orthonormal basis ![](../graphics/stm_eqn04808.gif).
### Pressure loads and load stiffness

For geometrically linear problems, equivalent nodal loads due to applied surface pressure are readily calculated since the geometry is axisymmetric. For geometrically nonlinear problems, however, asymmetric deformations must be taken into consideration.

The equivalent nodal loads associated with surface pressure *p* can be obtained by considering the virtual work contribution to the external loading

![](../graphics/stm_eqn04809.gif)where *S* is the parametric surface coordinate in the *R*&#8211;*Z* plane and the reference surface position is

![](../graphics/stm_eqn04810.gif)with ![](../graphics/stm_eqn03233.gif) and ![](../graphics/stm_eqn03234.gif). Recall that the current position of a point can be expressed in terms of the axial interpolator ![](../graphics/stm_eqn04811.gif) and the circumferential interpolators ![](../graphics/stm_eqn04664.gif) by

![](../graphics/stm_eqn04812.gif)The terms in [Equation 3.6.7&#8211;7](03s06a85.md) can be worked out as follows:

![](../graphics/stm_eqn04813.gif)and, hence,

![](../graphics/stm_eqn04814.gif)The variations ![](../graphics/stm_eqn04815.gif) are written ![](../graphics/stm_eqn04816.gif), where the components have interpolations similar to those in [Equation 3.6.7&#8211;7](03s06a85.md). Therefore, the virtual work contribution becomes

![](../graphics/stm_eqn04817.gif)With the introduction of the interpolation functions, we obtain the equivalent nodal forces:

![](../graphics/stm_eqn04818.gif)For geometrically linear analysis, the equivalent nodal forces reduce to the standard axisymmetric expressions

![](../graphics/stm_eqn04819.gif)The linearization of the pressure loading term leads to the following pressure load stiffness matrix:

![](../graphics/stm_eqn04820.gif)with

![](../graphics/stm_eqn04821.gif)

![](../graphics/stm_eqn04822.gif)

![](../graphics/stm_eqn04823.gif)

In the case of hydrostatic pressure (*p* dependent on *z*), additional terms must be included in the pressure load stiffness. These terms appear due to the variation of the pressure magnitude and are readily obtained from the expression

![](../graphics/stm_eqn04824.gif)With use of the interpolation functions and denoting the additional contributions with an over-bar, we obtain the additional load stiffness contributions:

![](../graphics/stm_eqn04825.gif)
### Penalty constraints: transverse shear and drill rotation

It is necessary to enforce rotation constraints at selected points on the element surface to prevent singular modes of deformation. One axial transverse shear constraint is enforced on the ![](../graphics/stm_eqn04650.gif) rotation field between each pair of nodes within each nodal plane. One circumferential transverse shear constraint and one drill rotation constraint on the rotation fields ![](../graphics/stm_eqn02779.gif) and ![](../graphics/stm_eqn04826.gif) are enforced between each pair of nodes on a circumferential line of nodes. In each instance the rotation field is constrained to follow the nodal displacements. To summarize, for element SAXAMN:

Axial transverse shear: ![](../graphics/stm_eqn04827.gif)

Circumferential transverse shear: ![](../graphics/stm_eqn04828.gif)

Drill rotation: ![](../graphics/stm_eqn04828.gif)constraints are enforced, where ![](../graphics/stm_eqn04829.gif) is the order of integration in the axial direction and ![](../graphics/stm_eqn04830.gif) is the number of Fourier modes.Transverse shear

The transverse shear strain is the measure of the amount the director field ![](../graphics/stm_eqn04194.gif) has rotated relative to the normal to the shell surface. We define the transverse shear strain as

![](../graphics/stm_eqn04831.gif)with no sum on *c* and force this quantity to be zero with a penalty constraint. Note that ![](../graphics/stm_eqn04832.gif) is a unit vector tangent to the shell surface defined by the displacement field along a parametric coordinate line. Recall that ![](../graphics/stm_eqn04833.gif) and ![](../graphics/stm_eqn04834.gif). Hence, ![](../graphics/stm_eqn04835.gif) is the axial transverse shear strain and ![](../graphics/stm_eqn04836.gif) is the circumferential transverse shear strain.

For convenience, record the variation of the unit vector ![](../graphics/stm_eqn04832.gif):

![](../graphics/stm_eqn04837.gif)with no sum on *c*. Equivalently, the definition of ![](../graphics/stm_eqn04832.gif) can be used to write

![](../graphics/stm_eqn04838.gif)

The linearized transverse shear strain is calculated as

![](../graphics/stm_eqn04839.gif)Since by definition ![](../graphics/stm_eqn04840.gif), it follows that

![](../graphics/stm_eqn04841.gif)with no sum on *c*.

For completeness, the second variation of the transverse shear strain is

![](../graphics/stm_eqn04842.gif)where terms proportional to ![](../graphics/stm_eqn04843.gif) have been neglected and the coupling between ![](../graphics/stm_eqn00230.gif) and ![](../graphics/stm_eqn00197.gif) has been symmetrized.Drill rotation

Mathematically, the equations governing the deformation of the shell are invariant with respect to drill rotations; that is, a rotation of the director field with axis of rotation parallel to the director. It is necessary then to assign a kinematic definition to this rotation. We define the drill strain as the difference between the rotation of the circumferential tangent vector as measured by the displacement field and that measured by the rotation field. Accordingly, we define the drill strain by

![](../graphics/stm_eqn04844.gif)Here, ![](../graphics/stm_eqn00001.gif) is the rotated reference axial tangent vector and ![](../graphics/stm_eqn00026.gif) is the deformed (unit) circumferential tangent vector, defined by

![](../graphics/stm_eqn04845.gif)In the above ![](../graphics/stm_eqn00007.gif) is a linear approximation to the axial tangent vector in the reference configuration given by ![](../graphics/stm_eqn04846.gif), where ![](../graphics/stm_eqn04847.gif) and ![](../graphics/stm_eqn03522.gif) are the position vectors to two adjacent nodes in an axial plane. The drill rotation constraint then requires that the component of rotation about the normal to the surface match the in-plane rotation of the surface as measured by the displacement field.

The linearized drill strain calculation is similar to the transverse shear linearized strain calculation. Without repeating the calculation,

![](../graphics/stm_eqn04848.gif)Similarly, the second variation of the drill strain

![](../graphics/stm_eqn04849.gif)where terms proportional to ![](../graphics/stm_eqn04850.gif) have been neglected and the coupling between ![](../graphics/stm_eqn00230.gif) and ![](../graphics/stm_eqn00197.gif) has been symmetrized.
### Zero radius: collapsed edge

For the case when the reference radius of any point on the shell surface goes to zero, all of the offset nodes collapse to the same point and the edge constraints along that circumferential edge become redundant. It is, therefore, necessary to treat the zero radius case separately.

For the zero radius case all redundant degrees of freedom are constrained to follow the average motion of the nodes at ![](../graphics/stm_eqn04851.gif)0 and ![](../graphics/stm_eqn04852.gif) 180. The edge constraints are broken into two parts: First, a circumferential transverse shear strain is defined that requires that the rotation in the radial direction follow the circumferential rotations at the first and last nodal plane:

![](../graphics/stm_eqn04853.gif)Introducing the interpolations, the linearized strain is

![](../graphics/stm_eqn04854.gif)Note that ![](../graphics/stm_eqn04855.gif). Second, a drill rotation strain is defined that requires that the rotation about the *Z*-axis be zero:

![](../graphics/stm_eqn04856.gif)This leads to a linearized strain given by

![](../graphics/stm_eqn04857.gif)Note that ![](../graphics/stm_eqn04858.gif).
### Mass matrix

At each material point the displacement components in the three directions (radial, axial, circumferential) are dependent only on the corresponding nodal displacement components. Hence, the mass matrix does not involve any coupling between the radial, axial, and circumferential degrees of freedom, and we can write the mass matrix in the form of three separate expressions:

![](../graphics/stm_eqn04859.gif)Similarly, we can write the terms associated with the rotational degrees of freedom as:

![](../graphics/stm_eqn04860.gif)Here the superscripts *m* and *n* refer to a particular node in the *r*&#8211;*z* plane, and the superscripts *p* and *q* refer to a particular position along the circumference. The interpolation functions ![](../graphics/stm_eqn04861.gif), ![](../graphics/stm_eqn03255.gif), and ![](../graphics/stm_eqn03256.gif) are the product of interpolation functions ![](../graphics/stm_eqn04862.gif) in the *r*&#8211;*z* plane and interpolation functions in the ![](../graphics/stm_eqn01111.gif)-direction:

![](../graphics/stm_eqn04863.gif)The area integral used to form the mass matrix can be split then into an integral along the length of the element in the *r*&#8211;*z* plane and an integral around the circumference. For the *r*&#8211;*r* component of the mass matrix this yields

![](../graphics/stm_eqn04864.gif)and for the ![](../graphics/stm_eqn02779.gif) component of the mass matrix this yields:

![](../graphics/stm_eqn04865.gif)

The matrix can be written in a convenient form by defining the primitive mass matrix as

![](../graphics/stm_eqn04866.gif)or for the rotational components as

![](../graphics/stm_eqn04867.gif)These primitive mass matrices are the same mass matrices that are used for the regular axisymmetric shell elements. We can also define the circumferential distribution matrices

![](../graphics/stm_eqn04868.gif)The various components of the mass matrix then take the form

![](../graphics/stm_eqn04869.gif)

The circumferential distribution matrices can be evaluated for various values of the number of terms *P* in the Fourier series. After some calculations the following results are obtained:

![](../graphics/stm_eqn04666.gif):

![](../graphics/stm_eqn03263.gif)

![](../graphics/stm_eqn04670.gif):

![](../graphics/stm_eqn03264.gif)

![](../graphics/stm_eqn04675.gif):

![](../graphics/stm_eqn04870.gif)

![](../graphics/stm_eqn03157.gif):

![](../graphics/stm_eqn03268.gif)
### Reference

### Reference

"Axisymmetric shell elements with nonlinear, asymmetric deformation,"  Section 29.6.10 of the Abaqus Analysis User's Guide