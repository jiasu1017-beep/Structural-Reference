# 3.5.2 Beam element formulation

### 3.5.2 Beam element formulation

**Products: **Abaqus/Standard  Abaqus/Explicit

At a given stage in the deformation history of the beam, the position of a material point in the cross-section is given by the expression

![](../graphics/stm_eqn03496.gif)In this expression ![](../graphics/stm_eqn03497.gif) is the position of a point on the centerline, ![](../graphics/stm_eqn03498.gif) are unit orthogonal direction vectors in the plane of the beam section, ![](../graphics/stm_eqn03499.gif) is the unit vector orthogonal to ![](../graphics/stm_eqn03500.gif) and ![](../graphics/stm_eqn03501.gif), ![](../graphics/stm_eqn03502.gif) is the warping function of the section, ![](../graphics/stm_eqn03503.gif) is the warping amplitude, and ![](../graphics/stm_eqn03504.gif) is a cross-sectional scaling factor depending on the stretch of the beam.

These quantities are functions of the beam axis coordinate *S* and the cross-sectional coordinates ![](../graphics/stm_eqn03505.gif), which are assumed to be distances measured in the original (reference) configuration of the beam. The warping function is chosen such that the value at the origin of the section vanishes: ![](../graphics/stm_eqn03506.gif).

It is assumed that at the integration points along the beam, the beam section directions are approximately orthogonal to the beam axis tangent ![](../graphics/stm_eqn03507.gif) given by

![](../graphics/stm_eqn03508.gif)where ![](../graphics/stm_eqn00280.gif) is the axial stretch given by

![](../graphics/stm_eqn03509.gif)The normality condition is enforced numerically by penalizing the transverse shear strains

![](../graphics/stm_eqn03510.gif)This condition is assumed to be satisfied exactly in the original configuration.

In what follows, ![](../graphics/stm_eqn03511.gif) is the alternator

![](../graphics/stm_eqn03512.gif)The curvature of the beam is defined by

![](../graphics/stm_eqn03513.gif)and the twist of the beam follows from

![](../graphics/stm_eqn03514.gif)The "bicurvature" of the beam is defined by

![](../graphics/stm_eqn03515.gif)

The bicurvature defines the axial strain variation in the section due to the twist of the beam. The expression for the curvature and the twist can be combined to yield

![](../graphics/stm_eqn03516.gif)Before we derive strain measures from these expressions, we will consider in detail how the above quantities and their first and second variations are obtained for a typical beam finite element.
### Beam element in undeformed configuration

In the undeformed configuration, we use capital letters for all quantities. We assume that the undeformed state has no warping, so the position of a material point is given by

![](../graphics/stm_eqn03517.gif)and the curvatures and twist are defined by

![](../graphics/stm_eqn03518.gif)where ![](../graphics/stm_eqn00553.gif) is the unit vector orthogonal to ![](../graphics/stm_eqn03519.gif) and ![](../graphics/stm_eqn03520.gif); i.e.,

![](../graphics/stm_eqn03521.gif)We assume that the section normal ![](../graphics/stm_eqn00553.gif) coincides with the beam tangent ![](../graphics/stm_eqn00522.gif).

In the element the position of a point on the axis is interpolated from nodal positions ![](../graphics/stm_eqn03522.gif) with standard interpolation functions as

![](../graphics/stm_eqn03523.gif)where ![](../graphics/stm_eqn01040.gif) is a parametric coordinate, typically varying between ![](../graphics/stm_eqn02916.gif) and *1* along the element. The beam axis tangent is readily computed as

![](../graphics/stm_eqn03524.gif)The section normals are interpolated from user-defined nodal normals ![](../graphics/stm_eqn00893.gif). However, we cannot use a simple interpolation since this would not create integration point normals orthogonal to the beam tangent ![](../graphics/stm_eqn00522.gif). Hence, we use a two-step approach. First, we create approximate normals by the interpolation

![](../graphics/stm_eqn03525.gif)Then, we orthonormalize these vectors with respect to ![](../graphics/stm_eqn00522.gif) by

![](../graphics/stm_eqn03526.gif)and subsequently, with respect to each other by

![](../graphics/stm_eqn03527.gif)where it has been assumed that ![](../graphics/stm_eqn03528.gif) and ![](../graphics/stm_eqn00522.gif) form a right-handed system. This provides ![](../graphics/stm_eqn03529.gif).

The curvature and the twist in the initial configuration are calculated directly from ![](../graphics/stm_eqn03528.gif) as

![](../graphics/stm_eqn03530.gif)The "average" twist is taken, since, in general,

![](../graphics/stm_eqn03531.gif)The gradient of the normal vectors is then obtained as

![](../graphics/stm_eqn03532.gif)and, therefore, the curvature and twist are also equal to

![](../graphics/stm_eqn03533.gif)The procedure followed above to derive ![](../graphics/stm_eqn03534.gif) and ![](../graphics/stm_eqn03535.gif) is not unique but provides values that satisfy the proper orthonormality conditions. This procedure is followed only for the undeformed configuration. For subsequent configurations ![](../graphics/stm_eqn03536.gif) and ![](../graphics/stm_eqn03537.gif) are obtained individually by forward integration of the kinematic equations.
### Change of position, warping, and normal direction

We assume that the position of the beam axis and the orientation of the normals can undergo (independent) changes. The change in position of the axis is described by the velocity vector ![](../graphics/stm_eqn03538.gif), which can be obtained from nodal velocities ![](../graphics/stm_eqn03539.gif) with the standard interpolation functions as

![](../graphics/stm_eqn03540.gif)The change in orientation of the normals is described by the spin vector ![](../graphics/stm_eqn03541.gif), which is obtained from nodal spin vectors ![](../graphics/stm_eqn03542.gif) with the same interpolation functions ![](../graphics/stm_eqn03543.gif), as

![](../graphics/stm_eqn03544.gif)Rigid body motion is included since the original position ![](../graphics/stm_eqn03545.gif) is obtained by the same interpolation as ![](../graphics/stm_eqn03546.gif). The rate of change of warping is also defined in terms of the rate of change of nodal warping ![](../graphics/stm_eqn03547.gif) with the standard interpolation functions as

![](../graphics/stm_eqn03548.gif)The velocity and spin describe the *rate* of change of the position and orientation. *Finite* changes in position are obtained by integration of the velocities over a finite time increment as

![](../graphics/stm_eqn03549.gif)Similarly, for the warping,

![](../graphics/stm_eqn03550.gif)The spin is related to the rate of change of the rotation quaternion ![](../graphics/stm_eqn03551.gif) by

![](../graphics/stm_eqn03552.gif)where ![](../graphics/stm_eqn03553.gif) is the total or Euler rotation.

The relation between spin and quaternion can be integrated exactly if it is assumed that the spin is constant over the time increment ![](../graphics/stm_eqn00883.gif). We then define

![](../graphics/stm_eqn03554.gif)and the incremental rotation quaternion follows from

![](../graphics/stm_eqn03555.gif)This allows us to update the normal directions at the nodes and at stress points with

![](../graphics/stm_eqn03556.gif)In this equation we use the notation that ![](../graphics/stm_eqn03534.gif) is ![](../graphics/stm_eqn03536.gif) at the beginning of the current increment; i.e.,

![](../graphics/stm_eqn03557.gif)For the entire motion the new normal directions can be formally expressed as

![](../graphics/stm_eqn03558.gif)where ![](../graphics/stm_eqn03551.gif) is defined by the product rule

![](../graphics/stm_eqn03559.gif)Here *i* is an increment and ![](../graphics/stm_eqn03560.gif) is the rotation quaternion for that increment. The section normal ![](../graphics/stm_eqn00479.gif) is updated the same way.
### Change of curvature and twist

The curvature and the twist involve the derivative of the normal vector with respect to *S*. From the update rule for ![](../graphics/stm_eqn03536.gif),

![](../graphics/stm_eqn03561.gif)The second term can be written as

![](../graphics/stm_eqn03562.gif)Hence, the scalar parts of the first two terms cancel each other, and the vector parts are the same. Therefore,

![](../graphics/stm_eqn03563.gif)Because ![](../graphics/stm_eqn03564.gif) is a rotation quaternion, its inverse is equal to its conjugate (![](../graphics/stm_eqn03565.gif)), and, hence, we can write

![](../graphics/stm_eqn03566.gif)where ![](../graphics/stm_eqn03567.gif) denotes the vector part of a quaternion. For the first term we use the relation

![](../graphics/stm_eqn03568.gif)This leads to

![](../graphics/stm_eqn03569.gif)which is a vector. From the definitions of  ![](../graphics/stm_eqn03570.gif) and ![](../graphics/stm_eqn03571.gif) it follows that

![](../graphics/stm_eqn03572.gif)These results provide

![](../graphics/stm_eqn03573.gif)We see that ![](../graphics/stm_eqn03574.gif) if ![](../graphics/stm_eqn03575.gif).

For the second term we express ![](../graphics/stm_eqn03535.gif) in terms of the curvature and twist at the beginning of the increment, which yields

![](../graphics/stm_eqn03576.gif)Combining these terms,

![](../graphics/stm_eqn03577.gif)The current curvature and twist are, therefore,

![](../graphics/stm_eqn03578.gif)and

![](../graphics/stm_eqn03579.gif)Hence, the current curvature and twist are updated by a summation over all increments as given by

![](../graphics/stm_eqn03580.gif)
### First variations

The first variations of the geometric quantities are readily obtained. Recall that

![](../graphics/stm_eqn03581.gif)It follows that

![](../graphics/stm_eqn03582.gif)where in the expression for ![](../graphics/stm_eqn03583.gif) we have assumed that ![](../graphics/stm_eqn03584.gif) and ![](../graphics/stm_eqn03585.gif). For the variations in the curvature and twist, we note that ![](../graphics/stm_eqn03586.gif). Hence, it follows that

![](../graphics/stm_eqn03587.gif)These terms will be used in the virtual work equation that will be discussed later. In using the above expressions the rotational quantities are obtained by interpolation from nodal variational quantities that are assumed to be valid for the velocity fields as

![](../graphics/stm_eqn03588.gif)
### Solution with Newton's algorithm

Newton's algorithm involves linearization of the incremental equations. The equations must be linearized around the current (latest) state. At the integration points these equations simply take the form

![](../graphics/stm_eqn03589.gif)The corrections  ![](../graphics/stm_eqn03590.gif) and ![](../graphics/stm_eqn03591.gif) are readily obtained from the nodal corrections with the interpolation functions ![](../graphics/stm_eqn03592.gif) as

![](../graphics/stm_eqn03593.gif)The corrections ![](../graphics/stm_eqn03594.gif) are defined with respect to the end of the increment: we call such corrections "compound" corrections. However, it has been assumed that the total incremental rotation ![](../graphics/stm_eqn03595.gif) would be interpolated with ![](../graphics/stm_eqn03592.gif) as

![](../graphics/stm_eqn03596.gif)Linearization of this equation yields

![](../graphics/stm_eqn03597.gif)where ![](../graphics/stm_eqn03598.gif) are corrections in ![](../graphics/stm_eqn03595.gif) in an additive sense such that

![](../graphics/stm_eqn03599.gif)To relate the additive correction ![](../graphics/stm_eqn03598.gif) to the compound correction ![](../graphics/stm_eqn03600.gif), we use the formula obtained for ![](../graphics/stm_eqn03595.gif) to find

![](../graphics/stm_eqn03601.gif)Similarly, at the nodes we find

![](../graphics/stm_eqn03602.gif) Now we assume that the difference in incremental rotation along a beam element is small; i.e.,

![](../graphics/stm_eqn03603.gif)which implies that either

![](../graphics/stm_eqn03604.gif)or

![](../graphics/stm_eqn03605.gif)In the first case we can use the approximations ![](../graphics/stm_eqn03606.gif) and ![](../graphics/stm_eqn03607.gif) which, with the use of the interpolation functions for ![](../graphics/stm_eqn03598.gif), gives

![](../graphics/stm_eqn03608.gif)In the second case it follows directly that

![](../graphics/stm_eqn03609.gif)In either case

![](../graphics/stm_eqn03610.gif)This approximate relationship is used only in the creation of the Jacobian, so the approximation will at worst result in reduced speed of convergence.

Once a nodal update vector ![](../graphics/stm_eqn03611.gif) is obtained, an exact update procedure is followed. This is achieved by a transformation into quaternions, use of exact quaternion update formula, and transformation of the results back into an incremental Euler rotation vector:

![](../graphics/stm_eqn03612.gif)

![](../graphics/stm_eqn03613.gif)

![](../graphics/stm_eqn03614.gif)

![](../graphics/stm_eqn03615.gif)The incremental rotation vector at the integration point is obtained by interpolation. Subsequently, we can calculate the updated integration point normals and the incremental curvature and twist.
### Second variations

For the calculation of the Jacobian, we also need the second variation in the generalized quantities. These follow from the first variations:

![](../graphics/stm_eqn03616.gif)where we have again used ![](../graphics/stm_eqn03617.gif).

For the second variation of the curvature we find

![](../graphics/stm_eqn03618.gif) Rewriting the second and third terms and combining the others yields

![](../graphics/stm_eqn03619.gif)

The second variation of twist is

![](../graphics/stm_eqn03620.gif)Then, following the same procedure as for ![](../graphics/stm_eqn03621.gif),

![](../graphics/stm_eqn03622.gif) Finally, we note

![](../graphics/stm_eqn03623.gif)The resulting second variations are summarized as

![](../graphics/stm_eqn03624.gif)
### Strains

The gradient of the current position of a point in the section with respect to the coordinate *S* is

![](../graphics/stm_eqn03625.gif)We will keep only terms up to order ![](../graphics/stm_eqn03626.gif). We assume that ![](../graphics/stm_eqn03627.gif), and---hence---the second term can be neglected. We also assume that ![](../graphics/stm_eqn03628.gif) and---since ![](../graphics/stm_eqn03629.gif)---we can neglect the last term as well. However, the warping function may vary rapidly near the ends where warping is constrained. Hence, ![](../graphics/stm_eqn03630.gif)  and should be preserved. With those approximations,

![](../graphics/stm_eqn03631.gif)The gradients with respect to ![](../graphics/stm_eqn03505.gif) are

![](../graphics/stm_eqn03632.gif)Correspondingly, in the original configuration

![](../graphics/stm_eqn03633.gif)The above relations are readily inverted to yield

![](../graphics/stm_eqn03634.gif)The deformation gradient then becomes

![](../graphics/stm_eqn03635.gif) We define the initial length ratio R as

![](../graphics/stm_eqn03636.gif)In the expression enclosed within square  brackets above, terms of order ![](../graphics/stm_eqn03637.gif) can again be neglected. However, it is assumed that the section may have low resistance to torsion and that, hence, the warping and twist may be large. This is particularly true for thin walled open sections. Hence, we obtain:

![](../graphics/stm_eqn03638.gif)We calculate the components of ![](../graphics/stm_eqn00319.gif) in a corotational system with the approximation  ![](../graphics/stm_eqn03639.gif). This provides

![](../graphics/stm_eqn03640.gif)We again neglect all terms of order ![](../graphics/stm_eqn03641.gif) for ![](../graphics/stm_eqn03642.gif), except the term involving ![](../graphics/stm_eqn03643.gif). The equations then simplify to

![](../graphics/stm_eqn03644.gif) Consistent with traditional shell and beam theories, we slightly adapt the term involving the initial curvature ![](../graphics/stm_eqn03645.gif)---instead of multiplying it with ![](../graphics/stm_eqn00280.gif), we multiply it with *f*.  Such a change does not significantly increase the error in the curvature calculation, since we do not properly account for the initial curvature in the volume integration anyway. Hence, we find for ![](../graphics/stm_eqn03646.gif):

![](../graphics/stm_eqn03647.gif)We now make a multiplicative decomposition of ![](../graphics/stm_eqn00319.gif) into a "stretch" part ![](../graphics/stm_eqn03648.gif) and a "distortion" part ![](../graphics/stm_eqn03649.gif) such that ![](../graphics/stm_eqn03650.gif).

For ![](../graphics/stm_eqn03648.gif) we choose

![](../graphics/stm_eqn03651.gif)and, hence, ![](../graphics/stm_eqn03649.gif) is

![](../graphics/stm_eqn03652.gif)Since ![](../graphics/stm_eqn03648.gif) is a diagonal tensor, the logarithmic "stretch" strains are immediately available as

![](../graphics/stm_eqn03653.gif)Since the "distortional" strains are small, we obtain them from  ![](../graphics/stm_eqn03649.gif) with the Green-Lagrange formula:

![](../graphics/stm_eqn03654.gif) For the components this yields

![](../graphics/stm_eqn03655.gif)

![](../graphics/stm_eqn03656.gif)Note that these strains are small. Since the various terms have different dependence on the cross-sectional coordinates, this leads to the conditions

![](../graphics/stm_eqn03657.gif)The last condition will generally require that both *w* and ![](../graphics/stm_eqn03658.gif) are small, since ![](../graphics/stm_eqn03659.gif) will not be proportional to ![](../graphics/stm_eqn03660.gif). However, for thin walled open section beams the proportionality is approximately satisfied and, therefore, we obtain in that case

![](../graphics/stm_eqn03661.gif)Note that within the desired accuracy this equation even holds for other sections: in that case both the right-hand and left-hand side are very small. Substitution in the expression for the Green-Lagrange strain yields the (small)  distortional strains:

![](../graphics/stm_eqn03662.gif)The total strains are obtained simply by addition as

![](../graphics/stm_eqn03663.gif)We assume that there are no stresses in the ![](../graphics/stm_eqn03664.gif) directions. Hence, the strains in these directions do not contribute to virtual work and do not need to be considered any further.

It is useful to split the total warping *w* in two parts: a part due to "free" warping ![](../graphics/stm_eqn03665.gif) minus a part due to warping prevention ![](../graphics/stm_eqn03666.gif): ![](../graphics/stm_eqn03667.gif). We assume that the warping function ![](../graphics/stm_eqn02064.gif) is chosen such that the free warping is related to the twist with the relation

![](../graphics/stm_eqn03668.gif)This makes it possible to write the expression for ![](../graphics/stm_eqn03669.gif) as

![](../graphics/stm_eqn03670.gif)It is desirable to choose the cross-sectional resultants such that they are completely uncoupled. In addition, we assume that the axial strain variation across the section due to the second-order term in the twist is not significant. Therefore, we consider only the *average* axial strain due to the second-order twist term. Hence, we introduce the average axial strain

![](../graphics/stm_eqn03671.gif)where ![](../graphics/stm_eqn03672.gif) are the coordinates of the centroid, ![](../graphics/stm_eqn03673.gif) is the polar moment of inertia, and ![](../graphics/stm_eqn03674.gif) is the average value of the warping function:

![](../graphics/stm_eqn03675.gif)

Similarly, we introduce the average shear strain

![](../graphics/stm_eqn03676.gif)

This last expression can be simplified by the introduction of the shear center coordinates ![](../graphics/stm_eqn03677.gif), which are related to the warping function by

![](../graphics/stm_eqn03678.gif)This yields

![](../graphics/stm_eqn03679.gif)Note that the average value is in fact the value at the shear center if warping prevention is absent (![](../graphics/stm_eqn03680.gif)). However, for full warping prevention (![](../graphics/stm_eqn03681.gif)) the average value corresponds to the value obtained at the centroid.

Instead of the original warping function ![](../graphics/stm_eqn03502.gif) we now introduce a modified warping function ![](../graphics/stm_eqn03682.gif) related to ![](../graphics/stm_eqn02064.gif) by

![](../graphics/stm_eqn03683.gif)This function in fact represents the classical definition of a warping function with an area weighted average of zero. The average value ![](../graphics/stm_eqn03674.gif) can be obtained from the classical warping function with the condition that ![](../graphics/stm_eqn03506.gif):

![](../graphics/stm_eqn03684.gif)The expression for the average axial strain then becomes

![](../graphics/stm_eqn03685.gif)and  the location of the shear center is

![](../graphics/stm_eqn03686.gif)The strains can, thus, be written in the form

![](../graphics/stm_eqn03687.gif)The second term in the expression for ![](../graphics/stm_eqn03669.gif) is proportional to the shear strain field for pure elastic torsion:

![](../graphics/stm_eqn03688.gif)We use this definition to eliminate the gradient of ![](../graphics/stm_eqn01258.gif) from the expression for the shear strain, which yields as final expression for the strains

![](../graphics/stm_eqn03689.gif)
### Virtual work

Since it was assumed that there are no stresses in the ![](../graphics/stm_eqn03664.gif) directions, the virtual work contribution is

![](../graphics/stm_eqn03690.gif)The strain variations are obtained by linearization of the expressions for the strains

![](../graphics/stm_eqn03691.gif)where all terms of the order of the "distortional" strains have been neglected. From the expressions for the average axial strain and average shear strain, we obtain the average axial and shear strain variations as

![](../graphics/stm_eqn03692.gif)where ![](../graphics/stm_eqn03693.gif) and again all terms of the order of the "distortional" strains have been neglected.

We now introduce the generalized section forces as defined below:| Axial force |  |
| --- | --- |
| Shear forces |  |
| Bending moments |  |
| Twisting moment |  |
| Warping moment |  |
| Bimoment |  | which transforms the virtual work contribution into

![](../graphics/stm_eqn03700.gif)Observe that the total torque *T* relative to the centroid of the section is the sum of the twisting moment and the warping moment:

![](../graphics/stm_eqn03701.gif)
### The rate of change of virtual work

To obtain the rate of change of virtual work, we first transform the integrations in the virtual work equation to the original volume such that

![](../graphics/stm_eqn03702.gif)The strain variations relative to the original state are then

![](../graphics/stm_eqn03703.gif) The strain variations relative to the original state are

![](../graphics/stm_eqn03704.gif) The rate of change of virtual work is then

![](../graphics/stm_eqn03705.gif) where we have neglected terms of order *b*. The changes in stress follow from the constitutive law

![](../graphics/stm_eqn03706.gif)We approximate ![](../graphics/stm_eqn03707.gif) and  ![](../graphics/stm_eqn03708.gif) with the same relations as used for virtual work:

![](../graphics/stm_eqn03709.gif)and for the average strain rates

![](../graphics/stm_eqn03710.gif)We now neglect all terms that involve the product of a  stress tensor; a variation in curvature, twist, or warping; and a change in axial strain of the cross-section. Using the previously obtained expressions for the second variations in ![](../graphics/stm_eqn03711.gif), and ![](../graphics/stm_eqn01723.gif) and transforming the results into the current state, this provides

![](../graphics/stm_eqn03712.gif) The incremental moments, forces, etc. are defined as

![](../graphics/stm_eqn03713.gif)For the determination of the initial stress stiffness, we assume that the second variations of the warping function and its derivative vanish: ![](../graphics/stm_eqn03714.gif). Consequently,

![](../graphics/stm_eqn03715.gif)and, therefore, only the torque relative to the centroid plays a role in the initial stress contribution to the rate of change of virtual work:

![](../graphics/stm_eqn03716.gif)The second variations of  ![](../graphics/stm_eqn03717.gif) and ![](../graphics/stm_eqn03718.gif) contain contributions of the second variation in  curvature and twist. These can be separated out by defining the bending moments and the torque relative to the origin of the cross-sectional coordinate system:

![](../graphics/stm_eqn03719.gif)The expression for the rate of change of virtual work then takes the form

![](../graphics/stm_eqn03720.gif)We propose to make the "cross-section size" a function of the stretch ![](../graphics/stm_eqn00280.gif). For the thermal stretch of the section we use isotropic expansion ![](../graphics/stm_eqn03721.gif) and for the "mechanical" stretch of the section we assume an effective Poisson's ratio ![](../graphics/stm_eqn03722.gif). The total cross-sectional stretch is

![](../graphics/stm_eqn03723.gif)so that

![](../graphics/stm_eqn03724.gif)Using this in the above expression for the rate of change of virtual work, we find

![](../graphics/stm_eqn03725.gif)This expression is symmetric if the material tensor ![](../graphics/stm_eqn03726.gif) is symmetric.
### Section integration

The formulation presented in the previous pages is valid for all possible beam types. However, different classes of beams will result in different final formulations. We consider three different classes of beams:

Beams in which warping may be constrained. These beams generally have an open, thin walled section reinforced with some relatively solid parts or some relatively small closed cells and have a torsional constant that is considerably smaller than the polar moment of inertia. Hence, in the elastic range, the warping can be large, and warping prevention at the ends can contribute significantly to the torsional rigidity of the beam. In this case both the torsional shear stresses and the axial warping stresses can be of the same order of magnitude as the stresses due to axial forces and bending moments, and the complete theory must be used.

Beams in which warping is unconstrained. These beams generally have a solid section or a closed, thin walled section and have a torsional constant that is of the same order of magnitude as the polar moment of inertia of the section. Hence, in the elastic range the warping is rather small, and it is assumed that warping prevention at the ends can be neglected. The axial warping stresses are assumed to be negligible, but the torsional shear stresses are assumed to be of the same order of magnitude as the stresses due to axial forces and bending moments. In this case the warping is dependent on the twist and can be eliminated as an independent variable, which leads to a considerably simplified formulation.

Beams in which warping constraints dominate the torsional stiffness. These beams generally have an open, thin walled section and have a torsional constant that is much smaller than the polar moment of inertia. In the elastic range the warping is likely to be large, and warping constraints are essential to provide torsional stiffness for the beam. In this case the axial stresses may be of the same order of magnitude as the stresses due to axial forces and bending moments, but the torsional shear stresses are relatively small. Hence, the warping can be coupled to the twist with a relatively stiff elastic constraint but cannot be eliminated because it must be possible to prevent warping at the nodes.Examples of cross-sections for the last two classes will be derived after the general discussion of sections with and without warping prevention.

In Abaqus we neglect the effect of shear stresses due to transverse shear forces at individual material points. We will consequently always assume elastic behavior of the section in transverse shear, leading to the relations

![](../graphics/stm_eqn03727.gif)where ![](../graphics/stm_eqn03728.gif) are the transverse shear forces, working at the shear center, and ![](../graphics/stm_eqn03729.gif) is the "slenderness compensation factor" used to prevent the shear stiffness from becoming too big in slender beams. The slenderness compensation factor is defined as

![](../graphics/stm_eqn03730.gif)

![](../graphics/stm_eqn03731.gif)where ![](../graphics/stm_eqn03732.gif) is the length of the element and *I* is the larger of the moments of inertia ![](../graphics/stm_eqn03733.gif) and ![](../graphics/stm_eqn03734.gif). Hence, the transverse shear terms do not need to be considered in any further detail.

The fact that the transverse shear forces are considered separately allows us to write

![](../graphics/stm_eqn03735.gif)where ![](../graphics/stm_eqn03736.gif) and ![](../graphics/stm_eqn03737.gif) are the strains and stresses due to transverse shear forces and ![](../graphics/stm_eqn03738.gif) and ![](../graphics/stm_eqn03739.gif) are the strains and stresses due to a twisting around the shear center. Substitution in the expressions for the twisting and warping moments yields

![](../graphics/stm_eqn03740.gif)where we used the fact that ![](../graphics/stm_eqn03741.gif) was calculated based on application of a twisting moment around the shear center and, hence, does not do any work on the shear stresses due to transverse shear forces.

The warping function ![](../graphics/stm_eqn01258.gif) is assumed to be determined based on isotropic, homogeneous elastic behavior of the section in shear. For this case the elastic energy due to twist is

![](../graphics/stm_eqn03742.gif)For twist without warping constraints ![](../graphics/stm_eqn03666.gif) vanishes and the energy per unit length of the beam is

![](../graphics/stm_eqn03743.gif)where we have introduced the torsion integral *J* given by

![](../graphics/stm_eqn03744.gif)With complete warping prevention the ![](../graphics/stm_eqn03681.gif) and the energy per unit length of the beam is

![](../graphics/stm_eqn03745.gif)where we have introduced the polar moment of inertia

![](../graphics/stm_eqn03746.gif)

For unconstrained warping ![](../graphics/stm_eqn03747.gif). Since the twisting moment must be equal to

![](../graphics/stm_eqn03748.gif)and since

![](../graphics/stm_eqn03749.gif)it follows that

![](../graphics/stm_eqn03750.gif)
### Beams with unconstrained warping

For this beam type, warping prevention is not taken into consideration. Hence we assume ![](../graphics/stm_eqn03680.gif). In addition we assume that axial strains due to warping can be neglected: ![](../graphics/stm_eqn03751.gif).

For the strains at a material point this yields

![](../graphics/stm_eqn03752.gif)and for the variations in the strains

![](../graphics/stm_eqn03753.gif)Substitution in the virtual work statement yields

![](../graphics/stm_eqn03754.gif)where the expressions derived earlier for *F*, ![](../graphics/stm_eqn03728.gif), ![](../graphics/stm_eqn03755.gif), and ![](../graphics/stm_eqn03756.gif) apply.

Although there is no warping prevention in the section, the warping moment ![](../graphics/stm_eqn03757.gif) does not vanish. From the expression obtained earlier follows

![](../graphics/stm_eqn03758.gif)This yields for the torque around the centroid

![](../graphics/stm_eqn03759.gif)and for the torque around the origin

![](../graphics/stm_eqn03760.gif)For the rate of change of virtual work we obtain

![](../graphics/stm_eqn03761.gif)
### Beams with elastic torsion and constrained warping

Consider the case that the shear stresses are defined from the shear strains by linear elastic response, with a constant shear modulus *G*:

![](../graphics/stm_eqn03762.gif)This allows us to write for the twisting and warping moments:

![](../graphics/stm_eqn03763.gif)Substitution of these expressions in the part of the virtual work equation related to torsion yields

![](../graphics/stm_eqn03764.gif)Note that the torque *T* around the centroid is

![](../graphics/stm_eqn03765.gif)Hence, we can write virtual work in terms of the primary variables *b* and *w*:

![](../graphics/stm_eqn03766.gif)The complete virtual work equation has the form

![](../graphics/stm_eqn03767.gif)where *F*, ![](../graphics/stm_eqn03728.gif), ![](../graphics/stm_eqn03755.gif) and *W* are defined as before.

For the rate of change of virtual work we obtain similarly

![](../graphics/stm_eqn03768.gif)with

![](../graphics/stm_eqn03769.gif)

We now discuss some specific section types incorporated in Abaqus.
### Circular section

For this type of section, warping is absent. Hence,

![](../graphics/stm_eqn03770.gif)
### Solid noncircular sections

Solid sections such as rectangles or trapezoids are included in this category. The warping function ![](../graphics/stm_eqn02064.gif) is a harmonic function and is subject to the condition that no shear stress component can act normal to the boundary of the cross-section. Although it is possible to determine the warping function ![](../graphics/stm_eqn02064.gif) in this manner, we choose to work in terms of the Saint-Venant's stress function because of its simplicity. Following standard procedures we normalize this function so that the (elastic) shear strains can be derived directly from it. We introduce the function ![](../graphics/stm_eqn03771.gif), which is differentiable in the cross-section and has the property that

![](../graphics/stm_eqn03772.gif)The stress function is determined by solving the differential equation of the form

![](../graphics/stm_eqn03773.gif)where *S* represents the boundary of the section. This boundary condition ensures that no shear stress component can act normal to the boundary.

For the solid noncircular sections this differential equation is solved numerically using a second-order isoparametric finite element. The torsional constant of the bar is then equal to twice the volume under the normalized stress function surface.
### Closed, thin walled cross-sections

In this case we assume that the shear strain perpendicular to the section must vanish so that

![](../graphics/stm_eqn03774.gif)Since ![](../graphics/stm_eqn03775.gif), this yields

![](../graphics/stm_eqn03776.gif)which can be identically satisfied anywhere. The normalized shear strain along the section is

![](../graphics/stm_eqn03777.gif)where *s* is the distance along the section. Integrating this around the circumference yields

![](../graphics/stm_eqn03778.gif)where ![](../graphics/stm_eqn03779.gif) is the area enclosed by the section. With the assumption that the shear modulus is constant along the section, the total torsional elastic strain energy is

![](../graphics/stm_eqn03780.gif)where *t* is the wall thickness. Minimization of the energy with the constraint enforced with a Lagrange multiplier ![](../graphics/stm_eqn01087.gif) yields

![](../graphics/stm_eqn03781.gif)Hence, ![](../graphics/stm_eqn03782.gif) which combine to define

![](../graphics/stm_eqn03783.gif)This allows calculation of ![](../graphics/stm_eqn03784.gif) at any point in the section based on the section geometry.
### Thin walled open sections

The most important sections that exhibit substantial warping are the thin walled open sections. For a single branch section we can conveniently express ![](../graphics/stm_eqn01258.gif) as a function of the coordinate *s* along the section and the coordinate *z* perpendicular to the section. A suitable approximation for ![](../graphics/stm_eqn01258.gif) is

![](../graphics/stm_eqn03785.gif)where ![](../graphics/stm_eqn03786.gif) is the value at the centerline of the wall. Minimization of the torsional elastic energy yields

![](../graphics/stm_eqn03787.gif)We now introduce  ![](../graphics/stm_eqn03788.gif), which is the position of the middle of the wall. With ![](../graphics/stm_eqn03789.gif) and ![](../graphics/stm_eqn03790.gif), and after carrying out the integration over *z*, the minimization condition simplifies to

![](../graphics/stm_eqn03791.gif)Clearly, the dominant terms are of order *h*. This yields the equations

![](../graphics/stm_eqn03792.gif)so that ![](../graphics/stm_eqn03793.gif) is

![](../graphics/stm_eqn03794.gif)where ![](../graphics/stm_eqn03795.gif) is the value of ![](../graphics/stm_eqn01258.gif) at the start of the integration over the section. Observe that

![](../graphics/stm_eqn03796.gif)represents the *sectorial area* between two points on the midsection relative to the shear center. Therefore, it readily follows that

![](../graphics/stm_eqn03797.gif)so there is no coupling between twist and bending in the section for linear elastic material behavior. As was discussed before, ![](../graphics/stm_eqn03795.gif) must be chosen such that

![](../graphics/stm_eqn03798.gif)which eliminates the coupling between twist and axial extension in the section for linear elasticity.

Note that coupling terms still exist but that they are incorporated in the generalized strain displacement relations. The coupling between twist and extension is governed by ![](../graphics/stm_eqn03799.gif), the value of the warping function at the origin of the cross-sectional coordinate system. If the origin is on the section, this value can be evaluated properly. If the origin is not on the section (which means that the node is not connected to the section), we assume that ![](../graphics/stm_eqn03800.gif).

The torsion integral *J* is readily obtained as

![](../graphics/stm_eqn03801.gif)and the polar moment of inertia is given by the expression

![](../graphics/stm_eqn03802.gif)The above derivations cover single branch open sections. Multibranch open sections can be transformed into single branch open sections by connecting the end of one branch with the beginning of the next branch with a section that has thickness ![](../graphics/stm_eqn03803.gif). Such dummy sections do not yield any contribution to the area, the moments of inertia, or the torsion integral and, hence, have no influence on the results.
### Reference

### Reference

"Beam modeling: overview,"  Section 29.3.1 of the Abaqus Analysis User's Guide