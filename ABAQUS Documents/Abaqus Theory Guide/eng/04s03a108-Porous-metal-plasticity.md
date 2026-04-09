# 4.3.6 Porous metal plasticity

### 4.3.6 Porous metal plasticity

**Products: **Abaqus/Standard  Abaqus/Explicit

The porous metal plasticity model is intended for use with *mildly voided metals*. Even though the material that contains the voids (also known as the matrix material) is assumed to be plastically incompressible, the plastic behavior of the bulk material is pressure-dependent due to the presence of voids. The model is described in the following paragraphs, followed by a brief description of the material point calculations.
### Yield condition

For a metal containing a dilute concentration of voids, based on a rigid-plastic upper bound solution for spherically symmetric deformations of a single spherical void, [Gurson (1977)](07s01a01-References.md) proposed a yield condition of the form

![](../graphics/stm_eqn05781.gif)where

![](../graphics/stm_eqn05782.gif)is the deviatoric part of the macroscopic Cauchy stress tensor ![](../graphics/stm_eqn00033.gif);

![](../graphics/stm_eqn05783.gif)is the Mises stress;

![](../graphics/stm_eqn05784.gif)is the hydrostatic pressure; *f* is the volume fraction of the voids in the material; and ![](../graphics/stm_eqn05785.gif) is the yield stress of the fully dense matrix material as a function of ![](../graphics/stm_eqn05786.gif), the equivalent plastic strain in the matrix. [Tvergaard (1981)](07s01a01-References.md) introduced the constants ![](../graphics/stm_eqn05787.gif), ![](../graphics/stm_eqn05788.gif), and ![](../graphics/stm_eqn05789.gif) (as coefficients of the void volume fraction and pressure terms) to make the predictions of the Gurson model agree with numerical studies of "ordered" voided materials in plane strain tensile fields; one can recover the original Gurson model by setting ![](../graphics/stm_eqn05790.gif).

It should be noted that ![](../graphics/stm_eqn00388.gif) implies that the material is fully dense, and the Gurson yield condition reduces to that of von Mises; ![](../graphics/stm_eqn05791.gif) implies that the material is fully voided and has no stress carrying capacity. This is illustrated in [Figure 4.3.6&#8211;1](04s03a108.md), where the yield surfaces for different levels of porosity are shown in the *p*&#8211;*q* plane.

Figure 4.3.6&#8211;1 Schematic of the yield surface in the *p*&#8211;*q* plane.

![](../graphics/cpormetplas-yield-surf.png)[Figure 4.3.6&#8211;2](04s03a108.md) compares the behavior of a porous metal (which has an initial void volume fraction of ![](../graphics/stm_eqn01259.gif)) in tension and compression against the perfectly plastic matrix material; the initial yield stress of the porous metal is ![](../graphics/stm_eqn05792.gif).

Figure 4.3.6&#8211;2 Schematic of uniaxial behavior of a porous metal.

![](../graphics/cpormetplas-uni-behav-nls.png)In compression the porous material "hardens" due to closing of the voids, and in tension it "softens" due to growth and nucleation of the voids.
### Flow rule

The plastic strains are derived from the yield potential; the presence of the first invariant of the stress tensor in the yield condition results in nondeviatoric plastic strains:

![](../graphics/stm_eqn05793.gif)where ![](../graphics/stm_eqn05794.gif) is the nonnegative plastic flow multiplier.
### Evolution of the plastic strains and f

The hardening of the (fully dense) matrix material is described through ![](../graphics/stm_eqn05795.gif). The evolution of ![](../graphics/stm_eqn05786.gif) is assumed to be governed by the equivalent plastic work expression; i.e.,

![](../graphics/stm_eqn05796.gif)

The change in volume fraction of the voids is due partly to the growth of existing voids and partly to the nucleation of voids. Growth of existing voids is based on the law of conservation of mass and is expressed as

![](../graphics/stm_eqn05797.gif)

Nucleation of voids can occur due to micro-cracking and/or decohesion of the particle-matrix interface. Abaqus assumes that the nucleation of new voids is plastic strain controlled (see [Chu and Needleman, 1980](07s01a01-References.md)), so that

![](../graphics/stm_eqn05798.gif)where

![](../graphics/stm_eqn05799.gif)The normal distribution of the nucleation strain has a mean value ![](../graphics/stm_eqn05800.gif), a standard deviation ![](../graphics/stm_eqn05801.gif), and nucleates voids with volume fraction ![](../graphics/stm_eqn05802.gif). The total rate of change of *f* is given as

![](../graphics/stm_eqn05803.gif)Voids are nucleated only in tension; Abaqus will not consider the nucleation term at a material point if the stress state is compressive.

The nucleation function ![](../graphics/stm_eqn05804.gif), which is assumed to have a normal distribution, is shown in [Figure 4.3.6&#8211;3](04s03a108.md) for different values of the parameter ![](../graphics/stm_eqn05801.gif). [Figure 4.3.6&#8211;4](04s03a108.md) shows the extent of softening in a uniaxial tension test of a porous material for different values of ![](../graphics/stm_eqn05802.gif).

Figure 4.3.6&#8211;3 Nucleation function ![](../graphics/stm_eqn05805.gif).

![](../graphics/cpormetplas-nucleation-nls.png)

Figure 4.3.6&#8211;4 Softening (in uniaxial tension) as a function of ![](../graphics/stm_eqn05802.gif).

![](../graphics/cpormetplas-soft.png)
### Integration of the elastoplastic equations

The integration of the elastoplastic equations for the porous plasticity model is carried out using the backward Euler scheme proposed by [Aravas (1987)](07s01a01-References.md). This method is briefly discussed in the following paragraphs; the user can refer to the paper for further details.

During the constitutive calculations in an increment, the stress and state variables are known at time *t* (beginning of the increment). Given a total incremental strain ![](../graphics/stm_eqn00432.gif), the stress and state variables need to be updated at ![](../graphics/stm_eqn00917.gif) (end of the increment) so that they satisfy the yield condition, flow rules, and evolution equation of the state variables. To do this, consider the elasticity equations

![](../graphics/stm_eqn05806.gif)where

![](../graphics/stm_eqn05807.gif)is the elastic predictor and

![](../graphics/stm_eqn05808.gif)is the linear isotropic elasticity tensor with *G* and *K* being the shear and bulk modulus, respectively, and ![](../graphics/stm_eqn05666.gif) and ![](../graphics/stm_eqn00064.gif) being the fourth- and second-order identity tensors, respectively. Also, in the above, the additive decomposition of strain is used to write the total incremental strain as the sum of the elastic and plastic parts. All of the stress and state variables are evaluated at ![](../graphics/stm_eqn00917.gif) unless indicated otherwise.

The yield condition, the flow rule, and the evolution of the state variables are rewritten as

![](../graphics/stm_eqn05809.gif)

![](../graphics/stm_eqn05810.gif)and

![](../graphics/stm_eqn05811.gif)where

![](../graphics/stm_eqn05812.gif)In the above ![](../graphics/stm_eqn05813.gif), ![](../graphics/stm_eqn05814.gif) are the state variables ![](../graphics/stm_eqn05786.gif) and *f*, respectively. The plastic multiplier ![](../graphics/stm_eqn00851.gif) is eliminated from the last two equations to give

![](../graphics/stm_eqn05815.gif)[Equation 4.3.6&#8211;2](04s03a108.md) is used in the elasticity [Equation 4.3.6&#8211;1](04s03a108.md) to yield

![](../graphics/stm_eqn05816.gif)![](../graphics/stm_eqn05817.gif) and ![](../graphics/stm_eqn00483.gif) are coaxial; therefore, ![](../graphics/stm_eqn00483.gif) is determined as

![](../graphics/stm_eqn05818.gif)Once ![](../graphics/stm_eqn00483.gif) is known, it is easily seen that consistent determination of the scalars ![](../graphics/stm_eqn05819.gif) and ![](../graphics/stm_eqn05820.gif) completes the solution. Therefore, the problem of integrating the pressure-dependent elastoplastic constitutive equations is reduced to solving the following two nonlinear equations for the scalars ![](../graphics/stm_eqn05819.gif) and ![](../graphics/stm_eqn05820.gif):

![](../graphics/stm_eqn05821.gif)

![](../graphics/stm_eqn05822.gif)In the above equations *p*, *q*, and ![](../graphics/stm_eqn05813.gif) are defined by

![](../graphics/stm_eqn05823.gif)

![](../graphics/stm_eqn05824.gif)

![](../graphics/stm_eqn05825.gif)where [Equation 4.3.6&#8211;8](04s03a108.md) and [Equation 4.3.6&#8211;9](04s03a108.md) are obtained by projecting [Equation 4.3.6&#8211;4](04s03a108.md) onto ![](../graphics/stm_eqn00064.gif) and ![](../graphics/stm_eqn00483.gif), respectively, and [Equation 4.3.6&#8211;10](04s03a108.md) is an alternate form of [Equation 4.3.6&#8211;3](04s03a108.md). Solving the above system of equations for the unknowns ![](../graphics/stm_eqn05826.gif) and ![](../graphics/stm_eqn05813.gif) completes the integration algorithm for the porous plasticity model.

[Equation 4.3.6&#8211;6](04s03a108.md) and [Equation 4.3.6&#8211;7](04s03a108.md) are solved for ![](../graphics/stm_eqn05819.gif) and ![](../graphics/stm_eqn05820.gif) using Newton's method; *p* and *q* are updated using [Equation 4.3.6&#8211;8](04s03a108.md) and [Equation 4.3.6&#8211;9](04s03a108.md); the state variables are updated using [Equation 4.3.6&#8211;10](04s03a108.md).
### Computing the linearization moduli

In the implicit finite element method of solving large-deformation problems, the discretized equilibrium equations result in a set of nonlinear equations for the nodal unknowns at the end of the increment. Abaqus/Standard uses Newton's method to solve these equations, which requires the computation of *linearization moduli*

![](../graphics/stm_eqn05827.gif)To compute ![](../graphics/stm_eqn05828.gif) (also known as the Jacobian), we start with the elasticity equations ([Equation 4.3.6&#8211;4](04s03a108.md)), which can be rewritten as

![](../graphics/stm_eqn05829.gif)where ![](../graphics/stm_eqn05830.gif) is the deviatoric part of ![](../graphics/stm_eqn00399.gif). From the above equation you find that

![](../graphics/stm_eqn05831.gif)Once again [Equation 4.3.6&#8211;6](04s03a108.md) and [Equation 4.3.6&#8211;7](04s03a108.md) are used in computing the variations ![](../graphics/stm_eqn05832.gif) and ![](../graphics/stm_eqn05833.gif). After some lengthy algebraic calculations, a set of linear equations is obtained that can be solved for ![](../graphics/stm_eqn05832.gif) and ![](../graphics/stm_eqn05833.gif). These derivatives are substituted into [Equation 4.3.6&#8211;11](04s03a108.md) to obtain the linearization moduli. In general this linearization moduli is not symmetric. Further details of the derivation of the Jacobian can be found in [Aravas (1987)](07s01a01-References.md).
### Reference

### Reference

"Porous metal plasticity,"  Section 23.2.9 of the Abaqus Analysis User's Guide