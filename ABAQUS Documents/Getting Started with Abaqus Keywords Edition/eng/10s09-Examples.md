# 10.9 Techniques for reducing volumetric locking

A small amount of compressibility is introduced into the rubber material model in order to alleviate volumetric locking. Provided the amount of compressibility is small, the results obtained with a nearly incompressible material will be very similar to those obtained with an incompressible material.

Compressibility is introduced by setting the material constant ![](../graphics/gsa_eqn00261.gif) to a nonzero value. The value is chosen so that the initial Poisson's ratio, ![](../graphics/gsa_eqn00262.gif), is close to 0.5. The equations given in "[Hyperelastic behavior of rubberlike materials," Section 22.5.1 of the Abaqus Analysis User's Guide](https://abaqus-docs.mit.edu/2017/English/SIMACAEANLRefMap/simaanl-c-SimAbout.htm#usb-mat-chyperelastic), can be used to relate ![](../graphics/gsa_eqn00261.gif) and ![](../graphics/gsa_eqn00262.gif) in terms of ![](../graphics/gsa_eqn00263.gif) and ![](../graphics/gsa_eqn00264.gif) (the initial shear and bulk moduli, respectively) for the polynomial form of the strain energy potential. For example, the hyperelastic material coefficients obtained earlier from the test data (see "Preprocessing—creating the model with Abaqus/CAE," Section 10.7.2) were given as ![](../graphics/gsa_eqn00265.gif) 176051 and ![](../graphics/gsa_eqn00266.gif) 4332.63; thus, setting ![](../graphics/gsa_eqn00267.gif) 5.E−7 yields ![](../graphics/gsa_eqn00268.gif) 0.46.

A model incorporating compressibility with additional mesh refinement (to reduce mesh distortion) is shown in [Figure 10–70](#gss-vlock-mesh) (this mesh can be generated easily by changing the edge seeds in Abaqus/CAE or another preprocessor).

**Figure 10–70** Modified mesh with refinement at both corners.

![](../graphics/gss-vlock-mesh-v.png)

The deformed shape associated with this model is shown in [Figure 10–71](#gss-vlock-defmesh).

**Figure 10–71** Deformed shape of the modified mesh.

![](../graphics/gss-vlock-defmesh-v.png)

It is clear from this figure that the mesh distortion has been reduced significantly in the critical regions of the rubber model. Examining contour plots of the pressure (without averaging across elements) reveals a smooth variation in pressure stress between elements. Thus, volumetric locking has been eliminated.
