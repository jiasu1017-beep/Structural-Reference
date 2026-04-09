# 1.5.3 Stress rates

### 1.5.3 Stress rates

**Products: **Abaqus/Standard  Abaqus/Explicit

Many of the materials we wish to model with Abaqus are history dependent, and it is common for the constitutive equations to appear in rate form. In "Stress measures,"  Section 1.5.2, it was suggested that an appropriate stress measure for stress-sensitive materials (such as yielding materials) is the Kirchhoff stress. We, therefore, need to define the rate of Kirchhoff stress for use in the constitutive equations. This definition is not simply the material time rate of Kirchhoff stress, because the Kirchhoff stress components are associated with spatial directions in the current configuration (recall that the Kirchhoff stress is ![](../graphics/stm_eqn00534.gif), where *J* is the volume change from the reference configuration and ![](../graphics/stm_eqn00033.gif) is the Cauchy stress, defined by ![](../graphics/stm_eqn00535.gif), where ![](../graphics/stm_eqn00479.gif) and ![](../graphics/stm_eqn00483.gif) are vectors in the current configuration).

To illustrate the issue, consider a uniaxial tension specimen under constant axial force *P*, lying along the *x*-axis at time ![](../graphics/stm_eqn00536.gif) and rotated---with the axial force held constant---to lie along the *y*-axis at time ![](../graphics/stm_eqn00537.gif) (see [Figure 1.5.3&#8211;1](01s05a10-Stress-rates.md)).

Figure 1.5.3&#8211;1 Rotated specimen.

![](../graphics/stmrotated-specimen-nls.png)Write the stress components on the global ![](../graphics/stm_eqn00538.gif) rectangular Cartesian basis. At time ![](../graphics/stm_eqn00536.gif), ![](../graphics/stm_eqn00539.gif), and all other ![](../graphics/stm_eqn00540.gif), while at time ![](../graphics/stm_eqn00537.gif), ![](../graphics/stm_eqn00541.gif), and all other ![](../graphics/stm_eqn00540.gif). Obviously during ![](../graphics/stm_eqn00542.gif), ![](../graphics/stm_eqn00543.gif) and ![](../graphics/stm_eqn00544.gif), but equally clearly this rate of change of stress has nothing to do with the constitutive response of the material making up the bar. (A materially based stress, such as the second Piola-Kirchhoff stress, would stay constant during the above rotation, because its components are associated with a material basis.) The problem, then, is that the components of ![](../graphics/stm_eqn00033.gif) or ![](../graphics/stm_eqn00506.gif) are associated with current directions in space and, therefore, ![](../graphics/stm_eqn00545.gif) and ![](../graphics/stm_eqn00546.gif) will be nonzero if there is pure rigid body rotation, even though from a constitutive point of view the material is unchanged. Thus, we must divide the increment of ![](../graphics/stm_eqn00033.gif) or ![](../graphics/stm_eqn00506.gif) into two parts---one attributable to rigid body motion only and a remainder that is then, presumably, associated with the rate form of the stress-strain law.

We can derive a simple result for this purpose for any matrix whose components are associated with spatial directions. At some time *t* imagine attaching to a material point a set of base vectors, ![](../graphics/stm_eqn00008.gif), ![](../graphics/stm_eqn00547.gif) These vectors cannot stretch but are defined to spin with the same spin as the material. Recall that the spatial gradient of the material particle velocity at a point, ![](../graphics/stm_eqn00548.gif), was decomposed into a rate of deformation and a spin,

![](../graphics/stm_eqn00549.gif)

One of the concepts of the motion of the base vectors ![](../graphics/stm_eqn00008.gif) in Abaqus is that

![](../graphics/stm_eqn00550.gif)

Another concept of the motion of the base vectors ![](../graphics/stm_eqn00008.gif) used in Abaqus is

![](../graphics/stm_eqn00551.gif)where ![](../graphics/stm_eqn00552.gif). Here ![](../graphics/stm_eqn00304.gif) is the rigid body rotation in the polar decomposition of the deformation gradient ![](../graphics/stm_eqn00319.gif). The differences between these two concepts are significant only if finite rotation of a material point is accompanied by finite shear.

Now consider any matrix ![](../graphics/stm_eqn00553.gif) based on the current configuration: we can write it in terms of its components in the ![](../graphics/stm_eqn00008.gif) directions:

![](../graphics/stm_eqn00554.gif)Taking the time derivative then gives

![](../graphics/stm_eqn00555.gif)

The second and third terms are the rate of ![](../graphics/stm_eqn00553.gif) caused by the rigid body spin, so the first term is that part of ![](../graphics/stm_eqn00553.gif) caused by other effects (in the case of stress, the rate associated with the constitutive response), called the corotational rate of ![](../graphics/stm_eqn00553.gif). From the definitions of ![](../graphics/stm_eqn00008.gif) as rigid base vectors that can be considered to spin with either ![](../graphics/stm_eqn00472.gif) or ![](../graphics/stm_eqn00556.gif), we can write two corotational rates of ![](../graphics/stm_eqn00553.gif) as

![](../graphics/stm_eqn00557.gif)and

![](../graphics/stm_eqn00558.gif)where ![](../graphics/stm_eqn00559.gif) and ![](../graphics/stm_eqn00560.gif) are called the Jaumann and Green-Naghdi rates, respectively.

We, thus, have the total rate of any matrix associated with spatial directions in the current configuration as the sum of the corotational rate of the matrix and a rate caused purely by the local spin or rigid body rotation. For example, the Jaumann rate of change of Kirchhoff stress can be written as

![](../graphics/stm_eqn00561.gif)

We are assuming that the constitutive theory will define ![](../graphics/stm_eqn00562.gif), the corotational stress rate per reference volume, in terms of the rate of deformation and past history, so this equation provides a convenient link between that material model and the overall change in "true" (Cauchy) stress (which is the stress measure defined directly from the equilibrium equations). In Chapter 4, "Mechanical Constitutive Theories," where the constitutive models in Abaqus are discussed, "stress rate" per reference volume will mean ![](../graphics/stm_eqn00563.gif), the corotational rate of Kirchhoff stress, which is the stress measure work conjugate to the rate of deformation.
### Stress rates used in Abaqus

The objective stress rates used in Abaqus are summarized in [Table 1.5.3&#8211;1](01s05a10-Stress-rates.md). Objective rates are relevant only for rate form constitutive equations (e.g., elastoplasticity). For hyperelastic materials a total formulation is used; hence, the concept of an objective rate is not relevant for the constitutive law. However, when material orientations are defined, the objective rate governs the evolution of the orientations and the output will be affected.

Table 1.5.3&#8211;1 Objective stress rates.| Solver | Element Type | Constitutive Model | Objective Rate |
| --- | --- | --- | --- |
| Abaqus/Standard | Solid (Continuum) | All built-in and user-defined materials | Jaumann |
| Structural (Shells, Membranes, Beams, Trusses) | All built-in and user-defined materials | Green-Naghdi |
| Abaqus/Explicit | Solid (Continuum) | All except viscoelastic, brittle cracking, and VUMAT | Jaumann |
| Solid (Continuum) | Viscoelastic, brittle cracking, and VUMAT | Green-Naghdi |
| Structural (Shells, Membranes, Beams, Trusses) | All built-in and user-defined materials | Green-Naghdi |
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide