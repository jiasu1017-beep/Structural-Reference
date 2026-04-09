# 2.4.5 Explicit dynamic analysis

### 2.4.5 Explicit dynamic analysis

**Product: **Abaqus/Explicit

The explicit dynamics analysis procedure in Abaqus/Explicit is based upon the implementation of an explicit integration rule together with the use of diagonal or "lumped" element mass matrices. The equations of motion for the body are integrated using the explicit central difference integration rule

![](../graphics/stm_eqn01023.gif)

![](../graphics/stm_eqn01024.gif)where ![](../graphics/stm_eqn00116.gif) is velocity and ![](../graphics/stm_eqn00890.gif) is acceleration. The superscript ![](../graphics/stm_eqn01025.gif) refers to the increment number and ![](../graphics/stm_eqn01026.gif) and ![](../graphics/stm_eqn01027.gif) refer to midincrement values. The central difference integration operator is explicit in that the kinematic state can be advanced using known values of ![](../graphics/stm_eqn01028.gif) and ![](../graphics/stm_eqn01029.gif) from the previous increment. The explicit integration rule is quite simple but by itself does not provide the computational efficiency associated with the explicit dynamics procedure. The key to the computational efficiency of the explicit procedure is the use of diagonal element mass matrices because the inversion of the mass matrix that is used in the computation for the accelerations at the beginning of the increment is triaxial:

![](../graphics/stm_eqn01030.gif)where ![](../graphics/stm_eqn01031.gif) is the diagonal lumped mass matrix, ![](../graphics/stm_eqn00319.gif) is the applied load vector, and ![](../graphics/stm_eqn00064.gif) is the internal force vector. The explicit procedure requires no iterations and no tangent stiffness matrix.

Special treatment of the mean velocities ![](../graphics/stm_eqn01032.gif), ![](../graphics/stm_eqn01028.gif) etc. is required for initial conditions, certain constraints, and presentation of results. For presentation of results, the state velocities are stored as a linear interpolation of the mean velocities:

![](../graphics/stm_eqn01033.gif)

The central difference operator is not self-starting because the value of the mean velocity ![](../graphics/stm_eqn01034.gif) needs to be defined. The initial values (at time ![](../graphics/stm_eqn01035.gif)) of velocity and acceleration are set to zero unless they are specified by the user. We assert the following condition:

![](../graphics/stm_eqn01036.gif)Substituting this expression into the update expression for ![](../graphics/stm_eqn01032.gif) yields the following definition of ![](../graphics/stm_eqn01034.gif):

![](../graphics/stm_eqn01037.gif)
### Stability

The explicit procedure integrates through time by using many small time increments. The central difference operator is conditionally stable, and the stability limit for the operator (with no damping) is given in terms of the highest eigenvalue in the system as

![](../graphics/stm_eqn01038.gif)In Abaqus/Explicit a small amount of damping is introduced to control high frequency oscillations. With damping the stable time increment is given by

![](../graphics/stm_eqn01039.gif)where ![](../graphics/stm_eqn01040.gif) is the fraction of critical damping in the highest mode. Contrary to our usual engineering intuition, introducing damping to the solution reduces the stable time increment.

The time incrementation scheme in Abaqus/Explicit is fully automatic and requires no user intervention. Abaqus/Explicit uses an adaptive algorithm to determine conservative bounds for the highest element frequency. An estimate of the highest eigenvalue in the system can be obtained by determining the maximum element dilatational mode of the mesh. The stability limit based upon this highest element frequency is conservative in that it will give a smaller stable time increment than the true stability limit that is based upon the maximum frequency of the entire model. In general, constraints such as boundary conditions and contact have the effect of compressing the eigenvalue spectrum, which the element by element estimates do not take into account. Abaqus/Explicit contains a global estimation algorithm, which determines the maximum frequency of the entire model. This algorithm continuously updates the estimate for the maximum frequency. Abaqus/Explicit initially uses the element by element estimates. As the step proceeds, the stability limit will be determined from the global estimator once the algorithm determines that the accuracy of the global estimation is acceptable. The global estimation algorithm is not used when any of the following capabilities are included in the model: fluid elements, JWL equation of state, infinite elements, material damping, dashpots, thick shells (thickness to characteristic length ratio larger than 0.92) or thick beams (thickness to length ratio larger than 1.0), and nonisotropic elastic materials with temperature and field variable dependency.

A trial stable time increment is computed for each element in the mesh using the following expression:

![](../graphics/stm_eqn01041.gif)where ![](../graphics/stm_eqn01042.gif) is the element maximum eigenvalue. A conservative estimate of the stable time increment is given by the minimum taken over all the elements. The above stability limit can be rewritten as

![](../graphics/stm_eqn01043.gif)where ![](../graphics/stm_eqn01044.gif) is the characteristic element dimension and ![](../graphics/stm_eqn01045.gif) is the current effective, dilatational wave speed of the material. The characteristic element dimension is derived from an analytic upper bound expression for the maximum element eigenvalue. Considering the 4-node uniform strain quadrilateral (CPE4R), the characteristic element dimension is

![](../graphics/stm_eqn01046.gif)where ![](../graphics/stm_eqn01047.gif) is the element area and ![](../graphics/stm_eqn01048.gif) is the element gradient operator  (see "Solid isoparametric quadrilaterals and hexahedra,"  Section 3.2.4). Similar characteristic element dimensions are derived for all element types found in Abaqus/Explicit.

The current dilatational wave speed is determined in Abaqus/Explicit by calculating the effective hypoelastic material moduli from the material's constitutive response. Effective Lam's constants, ![](../graphics/stm_eqn01049.gif) and ![](../graphics/stm_eqn01050.gif), are determined in the following manner. We define ![](../graphics/stm_eqn01051.gif) as the increment in the equivalent pressure stress, ![](../graphics/stm_eqn01052.gif), ![](../graphics/stm_eqn01053.gif) as the increment in the deviatoric stress, ![](../graphics/stm_eqn01054.gif) as the increment of volumetric strain, and ![](../graphics/stm_eqn01055.gif) as the deviatoric strain increment. We assume a hypoelastic stress-strain rule of the form

![](../graphics/stm_eqn01056.gif)

![](../graphics/stm_eqn01057.gif)where ![](../graphics/stm_eqn01058.gif) is the effective bulk modulus. The effective moduli can then be computed as

![](../graphics/stm_eqn01059.gif)

![](../graphics/stm_eqn01060.gif)

![](../graphics/stm_eqn01061.gif)If the strain increments are insignificant, these relationships will not yield numerically meaningful results. In this circumstance Abaqus/Explicit sets the effective Lam's constants to the initial values for the material, ![](../graphics/stm_eqn01062.gif) and ![](../graphics/stm_eqn01063.gif). In the case where the volumetric strain increment is significant but the deviatoric stress increment is not, the effective shear modulus is estimated to be

![](../graphics/stm_eqn01064.gif)These effective moduli represent the element stiffness and determine the current dilatational wave speed in the element as

![](../graphics/stm_eqn01065.gif)
### Bulk viscosity

Bulk viscosity introduces damping associated with the volumetric straining. Its purpose is to improve the modeling of high-speed dynamic events.

There are two forms of bulk viscosity in Abaqus/Explicit. The first is found in all elements and is introduced to damp the "ringing" in the highest element frequency. This damping is sometimes referred to as truncation frequency damping. It generates a bulk viscosity pressure, which is linear in the volumetric strain:

![](../graphics/stm_eqn01066.gif)where ![](../graphics/stm_eqn01067.gif) is a damping coefficient (default=.06), ![](../graphics/stm_eqn00593.gif) is the current material density, ![](../graphics/stm_eqn01045.gif) is the current dilatational wave speed, ![](../graphics/stm_eqn01044.gif) is an element characteristic length, and ![](../graphics/stm_eqn01068.gif) is the volumetric strain rate.

The second form of bulk viscosity pressure is found only in solid continuum elements (except CPS4R). This form is quadratic in the volumetric strain rate:

![](../graphics/stm_eqn01069.gif)where ![](../graphics/stm_eqn01070.gif) is a damping coefficient (default=1.2) and all other quantities are as defined for the linear bulk viscosity. The quadratic bulk viscosity is applied only if the volumetric strain rate is compressive.

The quadratic bulk viscosity pressure will smear a shock front across several elements and is introduced to prevent elements from collapsing under extremely high velocity gradients. Consider a simple one element problem in which the nodes on one side of the element are fixed and the nodes on the other side have an initial velocity in the direction of the fixed nodes. If the initial velocity is equal to the dilatational wave speed of the material, the element---without the quadratic bulk viscosity---would collapse to zero volume in one time increment (because the stable time increment size is precisely the transit time of a dilatational wave across the element). The quadratic bulk viscosity pressure will introduce a resisting pressure that will prevent the element from collapsing.

The bulk viscosity pressure is not included in the material point stresses because it is intended as a numerical effect only---it is not considered to be part of the material's constitutive response. The bulk viscosity pressures are based upon the dilatational mode of each element. The fraction of critical damping in the dilatational mode of each element is given by

![](../graphics/stm_eqn01071.gif)

Linear bulk viscosity is always included in Abaqus/Explicit. The parameters ![](../graphics/stm_eqn01072.gif) and ![](../graphics/stm_eqn01073.gif) can be redefined by the user. The default values are ![](../graphics/stm_eqn01074.gif) and ![](../graphics/stm_eqn01075.gif). The bulk viscosity parameters can be changed from step to step. If the default values are changed in a step, the new values will be used in any subsequent steps unless they are redefined.
### Rotational bulk viscosity for shell elements

For the displacement degrees of freedom, bulk viscosity introduces damping associated with volumetric straining. Linear bulk viscosity or truncation frequency damping is used to damp the high frequency ringing that leads to unwanted noise in the solution or spurious overshoot in the response amplitude. For the same reason, in shells the high frequency ringing in the rotational degrees of freedom is damped with linear bulk viscosity acting on the mean curvature strain rate. This damping generates a bulk viscosity "pressure moment," *m*, which is linear in the mean curvature strain rate:

![](../graphics/stm_eqn01076.gif)where ![](../graphics/stm_eqn01072.gif) is a damping coefficient (default = 0.06), ![](../graphics/stm_eqn01077.gif) is the original thickness, ![](../graphics/stm_eqn00593.gif) is the mass density, ![](../graphics/stm_eqn01078.gif) is the current dilatational wave speed, *L* is the characteristic length used for rotary inertia and transverse shear stiffness scaling, and ![](../graphics/stm_eqn01079.gif) is twice the increment in mean curvature. The dilatational wave speed is given in terms of the effective Lam constants as

![](../graphics/stm_eqn01080.gif)The resultant pressure moment ![](../graphics/stm_eqn01081.gif), where *h* is the current thickness, is added to the direct components of the moment resultant.
### Reference

### Reference

"Explicit dynamic analysis,"  Section 6.3.3 of the Abaqus Analysis User's Guide