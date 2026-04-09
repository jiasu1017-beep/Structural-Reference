# 1.4.1 Deformation

### 1.4.1 Deformation

**Products: **Abaqus/Standard  Abaqus/Explicit

In any structural problem the analyst describes the initial configuration of the structure and is interested in its deformation throughout the history of loading. The material particle initially located at some position ![](../graphics/stm_eqn00141.gif) in space will move to a new position ![](../graphics/stm_eqn00117.gif): since we assume material cannot appear or disappear, there will be a one-to-one correspondence between ![](../graphics/stm_eqn00117.gif) and ![](../graphics/stm_eqn00141.gif), so we can always write the history of the location of a particle as

![](../graphics/stm_eqn00267.gif)and this relationship can be inverted---we know ![](../graphics/stm_eqn00141.gif) when we know ![](../graphics/stm_eqn00117.gif) and *t*. Now consider two neighboring particles, located at ![](../graphics/stm_eqn00141.gif) and at ![](../graphics/stm_eqn00268.gif) in the initial configuration. In the current configuration we must have

![](../graphics/stm_eqn00269.gif)using the "mapping" [Equation 1.4.1&#8211;1](01s04a04-Deformation.md).

The matrix

![](../graphics/stm_eqn00270.gif)is called the deformation gradient matrix, and [Equation 1.4.1&#8211;2](01s04a04-Deformation.md) is written

![](../graphics/stm_eqn00271.gif)

As the material behavior depends on the straining of the material and not on its rigid body motion, those parts of the motion in the vicinity of a material point must be distinguished. Looking at an infinitesimal gauge length ![](../graphics/stm_eqn00272.gif) emanating from the particle initially at ![](../graphics/stm_eqn00141.gif), we can measure its initial and current lengths as

![](../graphics/stm_eqn00273.gif)so the "stretch ratio" of this gauge length is

![](../graphics/stm_eqn00274.gif)

If ![](../graphics/stm_eqn00275.gif), there is no strain of this infinitesimal gauge length---it has undergone rigid body motion only. Now using [Equation 1.4.1&#8211;4](01s04a04-Deformation.md),

![](../graphics/stm_eqn00276.gif)so that, from [Equation 1.4.1&#8211;5](01s04a04-Deformation.md),

![](../graphics/stm_eqn00277.gif)where ![](../graphics/stm_eqn00278.gif) is a unit vector in the direction of the gauge length ![](../graphics/stm_eqn00272.gif).

[Equation 1.4.1&#8211;6](01s04a04-Deformation.md) shows how to measure the stretch ratio associated with any direction, ![](../graphics/stm_eqn00278.gif), at any material point defined by ![](../graphics/stm_eqn00141.gif) (or by ![](../graphics/stm_eqn00117.gif)). Useful results are obtained when we vary the direction defined by ![](../graphics/stm_eqn00279.gif) at a particular material point and look for stationary values of the stretch ratio, ![](../graphics/stm_eqn00280.gif). Since ![](../graphics/stm_eqn00278.gif) must always be a unit vector, stationary values of ![](../graphics/stm_eqn00281.gif) are obtained by solving the constrained variational equation

![](../graphics/stm_eqn00282.gif)where ![](../graphics/stm_eqn00283.gif) is a Lagrange multiplier, introduced to retain the constraint

![](../graphics/stm_eqn00284.gif)

Taking the variation gives back the constraint (conjugate to ![](../graphics/stm_eqn00285.gif)) and, conjugate to ![](../graphics/stm_eqn00286.gif), gives

![](../graphics/stm_eqn00287.gif)

Taking the dot product of the left-hand side of this equation with ![](../graphics/stm_eqn00278.gif) and comparing with [Equation 1.4.1&#8211;6](01s04a04-Deformation.md) identifies ![](../graphics/stm_eqn00288.gif), so [Equation 1.4.1&#8211;7](01s04a04-Deformation.md) is

![](../graphics/stm_eqn00289.gif)This problem is an eigenvalue one that can be solved for the three extreme values of ![](../graphics/stm_eqn00281.gif). Since ![](../graphics/stm_eqn00280.gif) is always real and positive (and nonzero), ![](../graphics/stm_eqn00290.gif), and hence ![](../graphics/stm_eqn00291.gif) must be positive definite. [Equation 1.4.1&#8211;8](01s04a04-Deformation.md) thus gives three real, positive eigenvalues, ![](../graphics/stm_eqn00292.gif), ![](../graphics/stm_eqn00293.gif), ![](../graphics/stm_eqn00294.gif), the "principal stretches," with three corresponding eigenvectors, ![](../graphics/stm_eqn00295.gif), ![](../graphics/stm_eqn00296.gif), ![](../graphics/stm_eqn00297.gif), which will be orthogonal, by [Equation 1.4.1&#8211;8](01s04a04-Deformation.md), if the corresponding eigenvalues are different, and can be orthogonalized otherwise. The ![](../graphics/stm_eqn00295.gif) are the principal directions of strain.

Now let ![](../graphics/stm_eqn00298.gif), ![](../graphics/stm_eqn00299.gif), ![](../graphics/stm_eqn00300.gif) be unit vectors corresponding to ![](../graphics/stm_eqn00295.gif), ![](../graphics/stm_eqn00296.gif), ![](../graphics/stm_eqn00297.gif), but in the current configuration, so that, using [Equation 1.4.1&#8211;4](01s04a04-Deformation.md),

![](../graphics/stm_eqn00301.gif)Then

![](../graphics/stm_eqn00302.gif)by the orthogonality results just mentioned. Thus, ![](../graphics/stm_eqn00298.gif), ![](../graphics/stm_eqn00299.gif), and ![](../graphics/stm_eqn00300.gif) will also be an orthogonal set. Since each is a unit vector,

![](../graphics/stm_eqn00303.gif)where ![](../graphics/stm_eqn00304.gif) is the same pure rigid body rotation matrix in each of these equations. A pure rigid body motion matrix has the property that its inverse is its transpose: ![](../graphics/stm_eqn00305.gif). Comparing the principal stretch directions in the current and original configurations, therefore, isolates the rigid body rotation and the stretch. Finding the principal stretch ratios and their directions thus provides one solution to the problem of isolating straining motion and rigid body motion in the vicinity of a material point.

Now consider a gauge length in the reference configuration, d![](../graphics/stm_eqn00306.gif), directed along ![](../graphics/stm_eqn00295.gif). The same infinitesimal material line in the current configuration will be along ![](../graphics/stm_eqn00298.gif) and will be stretched by ![](../graphics/stm_eqn00292.gif), so that

![](../graphics/stm_eqn00307.gif)Similarly, along the other principal directions,

![](../graphics/stm_eqn00308.gif)and

![](../graphics/stm_eqn00309.gif)Since (![](../graphics/stm_eqn00295.gif), ![](../graphics/stm_eqn00296.gif), ![](../graphics/stm_eqn00297.gif)) is an orthonormal set of base vectors in the reference configuration, any infinitesimal material line (gauge length) ![](../graphics/stm_eqn00272.gif) at ![](../graphics/stm_eqn00141.gif) can be written in terms of its components in this basis:

![](../graphics/stm_eqn00310.gif)where

![](../graphics/stm_eqn00311.gif)Each of the vectors ![](../graphics/stm_eqn00312.gif) moves and stretches to the corresponding ![](../graphics/stm_eqn00313.gif), as defined above. Thus, the current gauge length, ![](../graphics/stm_eqn00314.gif), is

![](../graphics/stm_eqn00315.gif)which we write as

![](../graphics/stm_eqn00316.gif)where

![](../graphics/stm_eqn00317.gif)is the "left stretch" matrix, which is the sum of three dyadic products.

Comparison with the definition of the deformation gradient, [Equation 1.4.1&#8211;4](01s04a04-Deformation.md), shows that

![](../graphics/stm_eqn00318.gif)which is the polar decomposition theorem---that any motion can be represented as a pure rigid body rotation, followed by a pure stretch of three orthogonal directions. The polar decomposition theorem is important because it allows us to distinguish the straining part of the motion from the rigid body rotation. Specifically, ![](../graphics/stm_eqn00319.gif) completely defines the relative motions of material particles in the infinitesimal neighborhood of the material particle that was at ![](../graphics/stm_eqn00141.gif) in the reference configuration; and the left stretch matrix, ![](../graphics/stm_eqn00320.gif), completely defines the deformation of the material particles at ![](../graphics/stm_eqn00141.gif). The rotation matrix ![](../graphics/stm_eqn00304.gif) defines the rigid body rotation of the principal directions of strain (![](../graphics/stm_eqn00295.gif) in the reference configuration; ![](../graphics/stm_eqn00298.gif) in the current configuration). ![](../graphics/stm_eqn00304.gif) represents only the rigid body rotation of the material at the point under consideration in some average sense: in a general motion, each infinitesimal gauge length emanating from a material particle has a different amount of rotation. This distinction between the rotation of the principal directions of strain, ![](../graphics/stm_eqn00304.gif), and the rotations of individual directions in the material becomes significant when we must discuss large deformations of nonisotropic materials. Nevertheless, we have established an important result: if ![](../graphics/stm_eqn00321.gif) only, we know there is no deformation of the material in the immediate neighborhood of the point originally at ![](../graphics/stm_eqn00141.gif) and currently at ![](../graphics/stm_eqn00322.gif), since in this case ![](../graphics/stm_eqn00323.gif) and so ![](../graphics/stm_eqn00324.gif). ![](../graphics/stm_eqn00325.gif) must be nonzero for there to be any deformation of the material at the point in question: in this sense ![](../graphics/stm_eqn00325.gif) (and, hence, ![](../graphics/stm_eqn00320.gif) itself) is sufficient to define the deforming part of the motion (it contains complete information about all except pure rigid body rotation of the point). For this reason---so that, later in the development, we will be able to link the kinematics to the stressing of the material---we will need to be able to isolate ![](../graphics/stm_eqn00320.gif) from ![](../graphics/stm_eqn00319.gif). It is easy to obtain ![](../graphics/stm_eqn00326.gif), for

![](../graphics/stm_eqn00327.gif)since ![](../graphics/stm_eqn00305.gif) and ![](../graphics/stm_eqn00320.gif) is symmetric.

Since we originally defined ![](../graphics/stm_eqn00320.gif) from the principal stretches and their principal directions in the current configuration as

![](../graphics/stm_eqn00328.gif)then

![](../graphics/stm_eqn00329.gif)We see that the eigenvalues of ![](../graphics/stm_eqn00330.gif), are ![](../graphics/stm_eqn00331.gif), ![](../graphics/stm_eqn00332.gif), and ![](../graphics/stm_eqn00333.gif), and the corresponding eigenvectors are ![](../graphics/stm_eqn00298.gif), ![](../graphics/stm_eqn00299.gif), and ![](../graphics/stm_eqn00300.gif). We can then construct ![](../graphics/stm_eqn00334.gif). The deformation at the point is, thus, readily obtained by multiplying a ![](../graphics/stm_eqn00335.gif) matrix with its transpose (![](../graphics/stm_eqn00330.gif)) and solving the real eigenproblem for the resulting (symmetric) matrix. We can then obtain the rotation ![](../graphics/stm_eqn00304.gif) as

![](../graphics/stm_eqn00336.gif)Since ![](../graphics/stm_eqn00320.gif) has been constructed from its eigenvalues and eigenvectors, its inverse is immediately available:

![](../graphics/stm_eqn00337.gif)

So far we have written the results quite generally, without reference to any particular coordinate system. To perform computations we must choose a basis system to express these results as arrays of individual numbers. We now do so with some generality with respect to the choice of basis system. The justification for retaining generality at this stage is twofold: as an exercise, to provide a little more familiarity in the notation system we have chosen to use in this guide, and because we do need some---but, as it turns out, not all---of the generality when we have to deal with shell elements, where it is undesirable to use the rectangular Cartesian base vectors of the global, spatial system because the natural orientation of the shell reference surface causes us to prefer to choose two of the base vectors to be tangent to the shell's reference surface and the other to be normal to this surface. This preference causes us to need two basis systems: one associated with the body in its current configuration, when the point in question is at ![](../graphics/stm_eqn00117.gif), and one associated with the body in its reference configuration, when the same point was at ![](../graphics/stm_eqn00141.gif), because the orientation of the shell's reference surface---which determines our choice of basis vectors---will be quite different in these two configurations. We will write ![](../graphics/stm_eqn00008.gif), ![](../graphics/stm_eqn00338.gif), as the basis vectors chosen to write components associated with the current configuration (so that any vector ![](../graphics/stm_eqn00001.gif) associated with the current configuration is written as ![](../graphics/stm_eqn00092.gif)) and ![](../graphics/stm_eqn00103.gif), ![](../graphics/stm_eqn00338.gif), as the basis at the same material point but in the reference configuration. (Since we assume that both of these basis systems are adequate to express any vector-valued function by its components in the basis system---that is, the basis vectors are not linearly dependent---either would, in principal, serve for both configurations. We introduce two distinct systems by preference, because each is chosen as particularly suitable for a particular configuration.) Since we do not yet impose any particular restrictions on the ![](../graphics/stm_eqn00008.gif) or the ![](../graphics/stm_eqn00103.gif) (except for the requirement that the vectors must not be linearly dependent), we cannot assume that they will be orthogonal or of unit length: we will, therefore, need to use the corresponding contravariant vectors defined by

![](../graphics/stm_eqn00339.gif)and the contravariant metric tensors

![](../graphics/stm_eqn00340.gif)

We can express the deformation gradient, ![](../graphics/stm_eqn00319.gif), numerically by projecting it onto the bases:

![](../graphics/stm_eqn00341.gif)Recall the definition of ![](../graphics/stm_eqn00319.gif):

![](../graphics/stm_eqn00342.gif)Since the components of ![](../graphics/stm_eqn00314.gif) along ![](../graphics/stm_eqn00008.gif) are ![](../graphics/stm_eqn00343.gif) and we can write ![](../graphics/stm_eqn00344.gif),

![](../graphics/stm_eqn00345.gif)Thus, writing ![](../graphics/stm_eqn00346.gif) defines

![](../graphics/stm_eqn00347.gif) We must continue to bear in mind that the first index of ![](../graphics/stm_eqn00348.gif) is associated with a component of ![](../graphics/stm_eqn00319.gif) along a base vector in the current configuration (![](../graphics/stm_eqn00008.gif) in this case), while its second index is associated with a component of ![](../graphics/stm_eqn00319.gif) along a base vector in the reference configuration (![](../graphics/stm_eqn00349.gif)).

From [Equation 1.4.1&#8211;13](01s04a04-Deformation.md) we can write

![](../graphics/stm_eqn00350.gif)where ![](../graphics/stm_eqn00351.gif) is the contravariant metric of the basis system that we have chosen in the reference configuration.

The eigenproblem for the squared principal stretch ratios and their directions is solved by finding the eigenvalues of the matrix of numbers ![](../graphics/stm_eqn00352.gif). The eigenvectors will appear as the components ![](../graphics/stm_eqn00353.gif) along the ![](../graphics/stm_eqn00048.gif) base vectors in the current configuration. Since we have defined the left stretch on the current configuration as

![](../graphics/stm_eqn00354.gif)we will write its components on the basis in the current configuration as

![](../graphics/stm_eqn00355.gif)and, since

![](../graphics/stm_eqn00356.gif)

![](../graphics/stm_eqn00357.gif)

The polar decomposition gives

![](../graphics/stm_eqn00358.gif)so

![](../graphics/stm_eqn00359.gif)where ![](../graphics/stm_eqn00360.gif) is the contravariant metric tensor of the basis system we have chosen to use in the current configuration and---as with ![](../graphics/stm_eqn00348.gif)---we see that the first index of ![](../graphics/stm_eqn00361.gif) is associated with the contravariant base vector ![](../graphics/stm_eqn00048.gif) in the current configuration, while the second index is associated with the contravariant base vector ![](../graphics/stm_eqn00362.gif) in the reference configuration.

We should take care to understand the distinction between the direct matrix expression of the rigid body rotation of the principal directions of strain of the material, ![](../graphics/stm_eqn00304.gif), and the components of ![](../graphics/stm_eqn00304.gif) expressed on a particular basis. Suppose, for example, that the rigid body rotation at a point is zero (that is, ![](../graphics/stm_eqn00363.gif)) but we, nevertheless, have chosen different basis systems ![](../graphics/stm_eqn00364.gif) and ![](../graphics/stm_eqn00103.gif). In this case ![](../graphics/stm_eqn00365.gif). This implies that, even though ![](../graphics/stm_eqn00304.gif) is a unit matrix (in the sense that operating on any vector with this matrix makes no change in that vector), the numerical values we have chosen to store the matrix---the ![](../graphics/stm_eqn00361.gif)---do not form a unit matrix of numbers unless the ![](../graphics/stm_eqn00008.gif) and the ![](../graphics/stm_eqn00103.gif) are coincident and orthonormal. Thus, our choice of quite general basis systems that are not the same in the current and reference configurations (introduced as being "natural" for writing results for shells) somewhat complicates the interpretation of the numbers we store.

In the previous few paragraphs we have chosen to explore the expression of the basic results we have derived so far for the kinematics of the total motion in terms of quite general basis systems, ![](../graphics/stm_eqn00008.gif) and ![](../graphics/stm_eqn00103.gif). In Abaqus we wish to express results as simply and directly as possible, and we can do so by choosing particular sets of basis vectors that offer the most convenience for our purposes. First, we take the ![](../graphics/stm_eqn00008.gif) (and, by extension, the ![](../graphics/stm_eqn00103.gif), since these are just the ![](../graphics/stm_eqn00008.gif) at the beginning of the motion) to be a local, orthonormal system at each point. Although it is not possible to construct a Cartesian system with orthonormal base vectors over a general shell surface, we can always project the general results onto such a system when that system is chosen specifically at each point where we need to make the projection---typically at the integration points of the elements. The choice of which system is used as this local orthonormal basis is made in Abaqus at two levels: we distinguish continuum ("solid") elements from structural (shell and beam) elements, and we distinguish the default choice of directions from the particular choice of directions (orientation) specified by the user. For continuum elements the default ![](../graphics/stm_eqn00103.gif) are unit vectors along the axes of the global Cartesian system chosen for the problem. At points where the orientation is defined by the user, the specified ![](../graphics/stm_eqn00103.gif) are used. For shells (and membranes) we take ![](../graphics/stm_eqn00366.gif) and ![](../graphics/stm_eqn00367.gif) tangent to the shell's reference surface and ![](../graphics/stm_eqn00368.gif) normal to that surface at the point under consideration. By default, ![](../graphics/stm_eqn00366.gif) is the projection of the global *x*-axis onto the reference surface or, if the global *x*-axis is almost normal to that surface at the point, ![](../graphics/stm_eqn00366.gif) is the projection of the global *z*-axis onto the surface. If the orientation is defined by the user, ![](../graphics/stm_eqn00366.gif) and ![](../graphics/stm_eqn00367.gif) are the projections of the two specified axes onto the reference surface at the point. In all cases ![](../graphics/stm_eqn00368.gif) is normal to the shell's reference surface. For beams ![](../graphics/stm_eqn00366.gif) is along the beam axis, with ![](../graphics/stm_eqn00367.gif) and ![](../graphics/stm_eqn00368.gif) defined from the beam section definition option and beam normals given as part of the nodal coordinate definition. For continuum elements the same schemes are applied by default to define the basis system in the current configuration. For continuum elements with the orientation specified by the user and in all cases for shells, beams, and membranes, the ![](../graphics/stm_eqn00008.gif) are defined by

![](../graphics/stm_eqn00369.gif)

These schemes all have the same property: at any point in time the ![](../graphics/stm_eqn00008.gif) are orthonormal vectors: ![](../graphics/stm_eqn00370.gif), so ![](../graphics/stm_eqn00094.gif) and, thus, ![](../graphics/stm_eqn00371.gif), and---in particular---![](../graphics/stm_eqn00372.gif) and, thus, ![](../graphics/stm_eqn00373.gif). This simplifies the understanding of all the quantities we write, since the components of any tensor ![](../graphics/stm_eqn00374.gif) are always the physical projections of that tensor-valued quantity on the local orthogonal basis system ![](../graphics/stm_eqn00008.gif) and we need not distinguish covariant and contravariant components as we did in the general development above. In practical terms the only price we must pay for this simplicity is in shells when we have to use a separate basis system at each point under study, since we cannot construct a single system with the orthonormal property on a general curved surface. (In an axisymmetric system we also have to use ![](../graphics/stm_eqn00375.gif) to ensure that the ![](../graphics/stm_eqn00016.gif) base vector is a unit vector, but this is a minor point.) The simplifications are valuable and, from our perspective of studying finite element formulations, they are bought at modest cost, since we generally only consider a single integration point at a time. Throughout the rest of this guide, whenever we need to write down particular components of a tensor, we shall assume that the basis on which they are written has the orthonormal property ![](../graphics/stm_eqn00370.gif).

The material also undergoes rigid body translation, but this is not important in the development since we need consider only relative motion of neighboring points because we are interested in the deformation of the material to link the kinematics of the motion to the material's constitutive behavior. Numerically, rigid body translation is significant only for two reasons. One is that the spatial discretization must allow rigid body translation without giving strain, which is important in choosing interpolation functions for the finite elements. The other is that care must be exercised to ensure that the strain and rotation are calculated accurately when the rigid body motion is large, since then the strain and rotation depend on the difference between two very large motions.
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide