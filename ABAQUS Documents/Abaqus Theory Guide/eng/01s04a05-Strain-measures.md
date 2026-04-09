# 1.4.2 Strain measures

### 1.4.2 Strain measures

**Products: **Abaqus/Standard  Abaqus/Explicit

Strain measures used in general motions are most simply understood by first considering the concept of strain in one dimension and then generalizing this to arbitrary motions by using the polar decomposition theorem just derived.
### Strain in one dimension

We already have a measure of deformation---the stretch ratio ![](../graphics/stm_eqn00280.gif). In fact, ![](../graphics/stm_eqn00280.gif) is itself an adequate measure of "strain" for a number of problems. To see where it is useful and where not, first notice that the unstrained value of ![](../graphics/stm_eqn00280.gif) is 1.0. A typical soft rubber component (such as a rubber band) can change length by a large factor when it is loaded, so the stretch ratio ![](../graphics/stm_eqn00280.gif) would often have values of 2 or more. In contrast, a typical structural steel component will be designed to respond elastically to its working loads. Such a material has an elastic modulus of about 200  103 MPa (30  106 lb/in2) at room temperature and a yield stress of about 200 MPa (30  103 lb/in2), so the stretch at yield will be about 1.001 in tension, 0.999 in compression. The stretch ratio is an unsatisfactory way of measuring deformation for this case because the numbers of interest begin in the fourth significant digit. To avoid this inconvenience, the concept of strain is introduced, the basic idea being that the strain is zero at ![](../graphics/stm_eqn00275.gif), when the material is "unstrained." In one dimension, along some "gauge length" ![](../graphics/stm_eqn00272.gif), we define strain as a function of the stretch ratio, ![](../graphics/stm_eqn00280.gif), of that gauge length:

![](../graphics/stm_eqn00376.gif)

The objective of introducing the concept of strain is that the function *f* is chosen for convenience. To see what this implies, suppose ![](../graphics/stm_eqn00377.gif) is expanded in a Taylor series about the unstrained state:

![](../graphics/stm_eqn00378.gif)

We must have ![](../graphics/stm_eqn00379.gif), so ![](../graphics/stm_eqn00380.gif) at ![](../graphics/stm_eqn00381.gif) (this was the main reason for introducing this idea of "strain" instead of just using the stretch ratio). In addition, we choose ![](../graphics/stm_eqn00382.gif) at ![](../graphics/stm_eqn00381.gif) so that for small strains we have the usual definition of strain as the "change in length per unit length." This ensures that, in one dimension, all strain measures defined in this way will give the same numerical value to the order of the approximation when strains are small (because then the higher-order terms in the Taylor series are all negligible)---regardless of the magnitude of any rigid body rotation. Finally, we require that ![](../graphics/stm_eqn00383.gif) for all physically reasonable values of ![](../graphics/stm_eqn00280.gif) (that, is for all ![](../graphics/stm_eqn00384.gif)) so that strain increases monotonically with stretch; hence, to each value of stretch there corresponds a unique value of strain. (The choice of ![](../graphics/stm_eqn00383.gif) is arbitrary: we could equally well choose ![](../graphics/stm_eqn00385.gif), implying that the strain is positive in compression when ![](../graphics/stm_eqn00386.gif). This alternative choice is often made in geomechanics textbooks because geotechnical problems usually involve compressive stress and strain. The choice is a matter of convenience. In Abaqus we always use the convention that positive direct strains represent tension when ![](../graphics/stm_eqn00387.gif). This choice is retained consistently in Abaqus, including in the geotechnical options.)

With these reasonable restrictions (![](../graphics/stm_eqn00388.gif) and ![](../graphics/stm_eqn00382.gif) at ![](../graphics/stm_eqn00381.gif), and ![](../graphics/stm_eqn00383.gif) for all ![](../graphics/stm_eqn00384.gif)), many strain measures are possible, and several are commonly used. Some examples are

![](../graphics/stm_eqn00389.gif)In a uniformly strained uniaxial specimen, where *l* is the current and *L* the original gauge length, this strain is measured as ![](../graphics/stm_eqn00390.gif). This definition is the most familiar one to engineers who perform uniaxial testing of stiff specimens.

![](../graphics/stm_eqn00391.gif)This strain measure is commonly used in metal plasticity. One motivation for this choice in this case is that, when "true" stress (force per current area) is plotted against log strain, tension, compression and torsion test results coincide closely. Later we will see that this strain measure is mathematically appropriate for such materials because, for these materials, the elastic part of the strain can be assumed to be small.

![](../graphics/stm_eqn00392.gif)This strain measure is convenient computationally for problems involving large motions but only small strains, because, as we will show later, its generalization to a strain tensor in any three-dimensional motion can be computed directly from the deformation gradient without requiring solution for the principal stretch ratios and their directions.

All of these strains satisfy the basic restrictions. Obviously many strain functions are possible: the choice is strictly a matter of convenience. Since strain is usually the link between the kinematic and the constitutive theories, the convenience of this choice in the context of finite elements is based on two considerations: the ease with which the strain can be computed from the displacements, since the latter are usually the basic variables in the finite element model, and the appropriateness of the strain measure with respect to the particular constitutive model. For example, as mentioned above, it appears that log strain is particularly appropriate to plasticity, while large-strain elasticity analysis (for rubbers and similar materials) can be done quite satisfactorily without ever using any "strain" measure except the stretch ratio ![](../graphics/stm_eqn00280.gif).
### Strain in general three-dimensional motions

Having defined the basic concept of "strain" in one dimension, we now generalize the idea to three dimensions. In "Deformation,"  Section 1.4.1, we established that the deforming part of the motion in the immediate neighborhood of a material point is completely characterized by six variables: the three principal stretch ratios ![](../graphics/stm_eqn00393.gif), ![](../graphics/stm_eqn00293.gif), and ![](../graphics/stm_eqn00394.gif) and the orientation of the three principal stretch directions in the current (or in the reference) configuration. This immediately gives the generalization of the one-dimensional strain function introduced above. We first choose the function *f* that will be used as the strain measure. ![](../graphics/stm_eqn00395.gif) will be the strain along the first principal direction, ![](../graphics/stm_eqn00298.gif); ![](../graphics/stm_eqn00396.gif) will be the strain along ![](../graphics/stm_eqn00299.gif); and ![](../graphics/stm_eqn00397.gif) will be the strain along ![](../graphics/stm_eqn00300.gif).

The matrix

![](../graphics/stm_eqn00398.gif)completely characterizes the state of strain at the material point. Notice the resemblance to the definition of the stretch matrix, [Equation 1.4.1&#8211;10](01s04a04-Deformation.md): we might consider ![](../graphics/stm_eqn00399.gif) to be defined by the matrix function

![](../graphics/stm_eqn00400.gif)where we understand a matrix function to mean that the two matrices have the same principal directions with their principal values related by the definition of *f*, which is a convenient shorthand way of indicating a relationship between two matrices.

In [Equation 1.4.2&#8211;2](01s04a05-Strain-measures.md) we have written the matrix ![](../graphics/stm_eqn00399.gif) by using the principal strain directions in the current configuration. We could equally have begun with the polar decomposition into a stretch followed by rotation of the principal directions of stretch: ![](../graphics/stm_eqn00399.gif) would be defined in a similar way and would then be associated with its principal directions in the reference configuration. Abaqus generally reports strains referred to directions in the current configuration. There is no obvious reason for this choice: either approach would suffice so long as the user knows which is being used. The strain measures reported by Abaqus are enumerated in "Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide.

In a finite element code the deformation gradient ![](../graphics/stm_eqn00319.gif) is usually computed at each material calculation point from the displacement solution at the nodes of each element and the interpolation function chosen for the element. We now need an algorithm to obtain ![](../graphics/stm_eqn00399.gif), given a choice of strain measure. This algorithm is available immediately from [Equation 1.4.1&#8211;12](01s04a04-Deformation.md): the eigenvalues and eigenvectors of the ![](../graphics/stm_eqn00335.gif) matrix ![](../graphics/stm_eqn00330.gif) are ![](../graphics/stm_eqn00331.gif); ![](../graphics/stm_eqn00332.gif) and ![](../graphics/stm_eqn00333.gif); and ![](../graphics/stm_eqn00298.gif), ![](../graphics/stm_eqn00401.gif) and ![](../graphics/stm_eqn00300.gif). We can then calculate ![](../graphics/stm_eqn00402.gif),  etc. for the function *f* chosen as the strain measure and, thus, construct

![](../graphics/stm_eqn00403.gif)

This algorithm also gives principal strain and stretch values---often a useful output because they give a concise description of the state of deformation at a point. However, the algorithm requires computation of the eigenvalues and eigenvectors of a ![](../graphics/stm_eqn00335.gif) matrix at each of many points in the model at each of many iterations, which involves some computational cost. Thus, it would be useful if ![](../graphics/stm_eqn00404.gif) could be computed less expensively from ![](../graphics/stm_eqn00319.gif), which is possible only for certain choices of the strain measure, ![](../graphics/stm_eqn00405.gif). We now consider one such possibility.

The unit matrix ![](../graphics/stm_eqn00064.gif) can be written as

![](../graphics/stm_eqn00406.gif)Using [Equation 1.4.1&#8211;12](01s04a04-Deformation.md),

![](../graphics/stm_eqn00407.gif)

Green's strain was defined in one dimension as

![](../graphics/stm_eqn00408.gif)

Comparing this one-dimensional definition with [Equation 1.4.2&#8211;2](01s04a05-Strain-measures.md) and [Equation 1.4.2&#8211;3](01s04a05-Strain-measures.md), we see that

![](../graphics/stm_eqn00409.gif)is then a generalization of Green's strain in one dimension. (The more standard definition of Green's strain matrix is obtained by using ![](../graphics/stm_eqn00291.gif) instead of ![](../graphics/stm_eqn00330.gif), so the strain matrix is taken on the reference configuration instead of the current configuration as a basis:

![](../graphics/stm_eqn00410.gif)The definition we have adopted is consistent with taking the strain matrix on the current configuration. The only difference between the two definitions is the configuration in which the matrix is defined---whether we think of the motion as rigid body rotation of the principal axes of stretch, ![](../graphics/stm_eqn00304.gif), followed by stretch along those axes, ![](../graphics/stm_eqn00320.gif), or stretch along the principal axes, ![](../graphics/stm_eqn00411.gif), followed by rigid body rotation of those axes, ![](../graphics/stm_eqn00304.gif). The choice is arbitrary.)

Green's strain matrix is, thus, available directly from the deformation gradient without first having to solve for the principal directions. This advantage makes Green's strain computationally attractive. Recall that strain is the link between the kinematics and the constitutive theory, so the strain choice should be optimal based on the two considerations of convenience and appropriateness. We have already suggested that logarithmic strain is the most appropriate for elastic-plastic or elastic-viscoplastic materials in which the elastic strains are always small (because the yield stress is small compared to the elastic modulus), so it appears that the computational convenience of Green's strain cannot be used to advantage. However, the choice of a strain function, ![](../graphics/stm_eqn00405.gif), was restricted so that, for small strains but arbitrary rotations, all strain measures are the same to the order of the approximation. Thus, for such cases Green's strain is a very convenient choice for computing the strain. The small-strain, large-rotation approximation is often useful---especially in structural problems (shells and beams) because there the thinness or slenderness of the members often allows large rotations to occur with quite small-strains---and Green's strain is commonly used in large-rotation, small-strain formulations for such problems as shell buckling.

Finally, it is worth remarking that the familiar "small-strain" measure used in most elementary elasticity textbooks,

![](../graphics/stm_eqn00412.gif)is useful only for small displacement gradients---that is, both the strains and the rotations must be small for this strain measure to be appropriate. This can be demonstrated by considering pure rotation of a specimen: even though the material is not stretched, the components of this measure of strain become nonzero as the rotation increases.
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide