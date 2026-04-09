# 4.5.1 An inelastic constitutive model for concrete

### 4.5.1 An inelastic constitutive model for concrete

**Product: **Abaqus/Standard

This section describes the smeared crack model provided in Abaqus/Standard for plain concrete. The material library in Abaqus also includes a constitutive model for concrete based on theories of scalar plastic damage, described in "Damaged plasticity model for concrete and other quasi-brittle materials,"  Section 4.5.2, which is available both in Abaqus/Standard and Abaqus/Explicit. In Abaqus/Explicit plain concrete can also be analyzed with the cracking model described in "A cracking model for concrete and other brittle materials,"  Section 4.5.3. It is intended that reinforced concrete modeling be accomplished by combining standard elements, using this plain concrete model, with "rebar elements"---rods, defined singly or embedded in oriented surfaces, that use a one-dimensional strain theory and that may be used to model the reinforcing itself. These elements are superposed on the mesh of plain concrete elements and are used with standard metal plasticity models that describe the behavior of the rebar material. This modeling approach allows the concrete behavior to be considered independently of the rebar, so this section discusses the plain concrete model only. Effects associated with the rebar/concrete interface, such as bond slip and dowel action, cannot be considered in this approach, except by modifying some aspects of the plain concrete behavior to mimic them, such as the use of "tension stiffening" to simulate load transfer across cracks through the rebar.

The theory described in this section is intended as a model of concrete behavior for relatively monotonic loadings under fairly low confining pressures (less than four to five times the largest compressive stress that can be carried by the concrete in uniaxial compression). Cracking is assumed to be the most important aspect of the behavior, and it dominates the modeling. Cracking is assumed to occur when the stresses reach a failure surface, which we call the "crack detection surface." This failure surface is taken to be a simple Coulomb line written in terms of the first and second stress invariants, *p* and *q*, that are defined below. The anisotropy introduced by cracking is assumed to be important in the simulations for which the model is intended, so the model includes consideration of this anisotropy. The model is a smeared crack model, in the sense that it does not track individual "macro" cracks: rather, constitutive calculations are performed independently at each integration point of the finite element model, and the presence of cracks enters into these calculations by the way the cracks affect the stress and material stiffness associated with the integration point. Various objections have been raised against such smeared crack models. The principal concern is that this modeling approach inherently introduces mesh sensitivity in the solutions, in the sense that the finite element results do not converge to a unique result. For example, since cracking is associated with strain softening, mesh refinement will lead to narrower crack bands. [Crisfield (1986)](07s01a01-References.md) discusses this concern in detail and concludes that [Hillerborg's (1976)](07s01a01-References.md) approach, based on brittle fracture concepts, is adequate to deal with this issue for practical purposes. This aspect of the model is discussed below in the section on cracking. For simplicity of discussion in what follows, the term "crack" is used to mean a direction in which cracking has been detected at the single constitutive calculation point in question: the closest physical concept is that there exists a continuum of micro-cracks at the point, oriented as determined by the model.

When the principal stress components are dominantly compressive, the response of the concrete is modeled by an elastic-plastic theory, using a simple form of yield surface written in terms of the first two stress invariants. Associated flow and isotropic hardening are used. This model significantly simplifies the actual behavior: the associated flow assumption generally overpredicts the inelastic volume strain; the simple yield surface used does not match all data very accurately (the third stress invariant would be needed to improve this aspect of the model); and, especially when the concrete is strained beyond the ultimate stress point, the assumption of constant elastic stiffness does not reproduce the observation that the unloading response is significantly weakened (the elastic response of the material appears to be damaged). In addition, when concrete is subjected to very high pressure stress, it exhibits inelastic response: no attempt has been made to build this behavior into the model. In spite of these limitations the model provides useful predictions for a variety of problems involving inelastic loading of concrete. The limitations are introduced for the sake of computational efficiency. In particular, assuming associated flow leads to enough symmetry in the Jacobian matrix of the constitutive model (the "material stiffness matrix") that the overall equilibrium equation solution usually does not require nonsymmetric equation solution for this reason. All of these limitations could be removed at some sacrifice in computational cost.

The cracking and compression responses of concrete that are incorporated in the model are illustrated by the uniaxial response of a specimen shown in [Figure 4.5.1&#8211;1](04s05a119.md).

Figure 4.5.1&#8211;1 Uniaxial behavior of plain concrete.

![](../graphics/cconcrete-uni-plain-nls.png)When concrete is loaded in compression, it initially exhibits elastic response. As the stress is increased, some nonrecoverable (inelastic) straining occurs, and the response of the material softens. An ultimate stress is reached, after which the material softens until it can no longer carry any stress. If the load is removed at some point after inelastic straining has occurred, the unloading response is softer than the initial elastic response: this effect is ignored in the model. When a uniaxial specimen is loaded into tension, it responds elastically until, at a stress that is typically 7&#8211;10% of the ultimate compressive stress, cracks form so quickly that---even on the stiffest testing machines available---it is very difficult to observe the actual behavior. For the purpose of developing the model, we assume that the material loses strength through a softening mechanism and that this is dominantly a damage effect, in the sense that open cracks can be represented by loss of elastic stiffness (as distinct from the nonrecoverable straining that is associated with classical plasticity effects, such as what we are using for the compressive behavior model). The model neglects any permanent strain associated with cracking; that is, we assume that the cracks can close completely when the stress across them becomes compressive.

In multiaxial stress states these observations can be generalized through the concept of surfaces of failure and of ultimate strength in stress space. These surfaces are defined below and are fitted to experimental data. Typical surfaces are shown in [Figure 4.5.1&#8211;2](04s05a119.md) and [Figure 4.5.1&#8211;3](04s05a119.md).

Figure 4.5.1&#8211;2 Concrete failure surfaces in plane stress.

![](../graphics/cconcrete-yield-pl-stress-nls.png)

Figure 4.5.1&#8211;3 Concrete failure surfaces in the (*p*&#8211;*q*) plane.

![](../graphics/cconcrete-yield-p-q-nls.png)

This model makes no attempt to include prediction of cyclic response or of the reduction in the elastic stiffness caused by inelastic straining because the model is intended for application to relatively monotonic loading cases. Nevertheless, it is likely that---even in such cases---the stress trajectories will not be entirely radial and the model must predict the response in such cases in a reasonable way. An isotropically hardening "compressive" yield surface forms the basis of the model for the inelastic response when the principal stresses are dominantly compressive. In tension once cracking is defined to occur (by the "crack detection surface" of the model), the orientation of the cracks is stored and oriented, damaged elasticity is then used to model the existing cracks. Stress components associated with an open crack are not included in the definition of the crack detection surface for detecting additional cracks at the same point, and we only allow cracks to form in orthogonal directions at a point.

Since Abaqus/Standard is an implicit, stiffness method code and the material calculations used to define the behavior of the concrete are carried out independently at each integration point in that part of the model that is made of concrete, the solution is known at the start of the time increment. The constitutive calculations must provide values of stress and material stiffness at the end of the increment, based on the current estimate of the kinematic solution for the response at the spatial integration point during the increment that provides the (logarithmic) strain, ![](../graphics/stm_eqn00399.gif), at the end of the increment.

Once cracks exist at a point, the component forms of all vector and tensor valued quantities are rotated so that they lie in the local system defined by the crack orientation vectors (the normals to the crack faces). The model ensures that these crack face normal vectors will be orthogonal, so that this local system is rectangular Cartesian. This use of a local system simplifies the computation of the damaged elasticity used for the components associated with existing cracks.

The model, thus, consists of a "compressive" yield/flow surface to model the concrete response in predominantly compressive states of stress, together with damaged elasticity to represent cracks that have occurred at a material calculation point, the occurrence of cracks being defined by a "crack detection" failure surface that is considered to be part of the elasticity. The details of this model are now presented.
### Elastic-plastic model for concrete

The model uses the classical concepts of plasticity theory: a strain rate decomposition into elastic and inelastic strain rates, elasticity, yield, flow, and hardening.
### Strain rate decomposition

We begin with a strain rate decomposition:

![](../graphics/stm_eqn06361.gif)where ![](../graphics/stm_eqn00034.gif) is the total mechanical strain rate, ![](../graphics/stm_eqn05909.gif) is the elastic strain rate (which includes crack detection strains---this elastic strain will be further decomposed when we describe the elasticity), and ![](../graphics/stm_eqn06362.gif) is the plastic strain rate associated with the "compression" surface.

We assume that the elastic part of the strain is always small, so this equation can be integrated as

![](../graphics/stm_eqn06363.gif)
### Compression yield

The "compression" surface is

![](../graphics/stm_eqn06364.gif)where *p* is the effective pressure stress, defined as

![](../graphics/stm_eqn06365.gif)and *q* is the Mises equivalent deviatoric stress:

![](../graphics/stm_eqn05675.gif)where ![](../graphics/stm_eqn05994.gif) are the deviatoric stress components; ![](../graphics/stm_eqn06211.gif) is a constant, which is chosen from the ratio of the ultimate stress reached in biaxial compression to the ultimate stress reached in uniaxial compression; and ![](../graphics/stm_eqn06366.gif) is a hardening parameter (![](../graphics/stm_eqn06367.gif) is the size of the yield surface on the *q*-axis at ![](../graphics/stm_eqn06166.gif), so that ![](../graphics/stm_eqn06367.gif) is the yield stress in a state of pure shear stress when all components of ![](../graphics/stm_eqn00033.gif) are zero except ![](../graphics/stm_eqn06368.gif)). The hardening is measured by the value of ![](../graphics/stm_eqn06369.gif): the ![](../graphics/stm_eqn06366.gif) relationship is user-specified.

This simple surface is a straight line in (*p*&#8211;*q*) space and provides a good match to experimental data over a fairly wide range of pressure stress values (up to four to five times the maximum compressive stress that can be carried by the concrete in uniaxial compression). This form of the surface means that, as the hardening (![](../graphics/stm_eqn06369.gif)) changes, the surfaces in (*p*&#8211;*q*) space are similar, so---for example---the ratio of flow stress in biaxial loading to flow stress in uniaxial loading is the same at all flow stress levels. This does not appear to be contradicted by any experimental data, and it means that only one constant (![](../graphics/stm_eqn06211.gif)) is needed to define the shape of the surface.

The value of ![](../graphics/stm_eqn06211.gif) is established from the user's data as follows. In uniaxial compression ![](../graphics/stm_eqn06370.gif) and ![](../graphics/stm_eqn06371.gif), where ![](../graphics/stm_eqn05864.gif) is the stress magnitude. Therefore, on ![](../graphics/stm_eqn06372.gif),

![](../graphics/stm_eqn06373.gif)In biaxial compression ![](../graphics/stm_eqn06374.gif) and ![](../graphics/stm_eqn06375.gif), where ![](../graphics/stm_eqn06376.gif) is the magnitude of each nonzero principal stress. Therefore, on ![](../graphics/stm_eqn06372.gif),

![](../graphics/stm_eqn06377.gif)The value of ![](../graphics/stm_eqn06378.gif) is specified by the user as part of the failure surface data (typically ![](../graphics/stm_eqn06379.gif)). ![](../graphics/stm_eqn06211.gif) can be calculated from [Equation 4.5.1&#8211;4](04s05a119.md) and [Equation 4.5.1&#8211;5](04s05a119.md) as

![](../graphics/stm_eqn06380.gif)

The "compression" surface is shown in [Figure 4.5.1&#8211;2](04s05a119.md) and [Figure 4.5.1&#8211;3](04s05a119.md).
### Hardening

The user defines the hardening by specifying the magnitude of the stress, ![](../graphics/stm_eqn06381.gif), in a uniaxial compression test as a function of the inelastic strain magnitude, ![](../graphics/stm_eqn06382.gif). These data are used to define the ![](../graphics/stm_eqn06366.gif) relationship, as follows.

In uniaxial compression ![](../graphics/stm_eqn06370.gif) and ![](../graphics/stm_eqn06371.gif), where ![](../graphics/stm_eqn05864.gif) is the stress magnitude. During active plastic loading ![](../graphics/stm_eqn06372.gif), so by using the definition of ![](../graphics/stm_eqn05274.gif) ([Equation 4.5.1&#8211;4](04s05a119.md)), we obtain ![](../graphics/stm_eqn06367.gif) immediately as

![](../graphics/stm_eqn06383.gif)
### Flow

The model uses associated flow, so if ![](../graphics/stm_eqn06372.gif) and ![](../graphics/stm_eqn06384.gif),

![](../graphics/stm_eqn06385.gif)otherwise, ![](../graphics/stm_eqn06386.gif).

In the definition of ![](../graphics/stm_eqn06362.gif), ![](../graphics/stm_eqn06387.gif) is a constant that is chosen so that the ratio of ![](../graphics/stm_eqn06388.gif) in a monotonically loaded biaxial compression test to ![](../graphics/stm_eqn06388.gif) in a monotonically loaded uniaxial compression test is ![](../graphics/stm_eqn06389.gif), a value specified by the user as part of the failure surface data (typically ![](../graphics/stm_eqn06390.gif)). The equation defining ![](../graphics/stm_eqn06387.gif) from ![](../graphics/stm_eqn06389.gif) and the other constants in the compression surface is derived next.

The gradient of the flow potential for the compressive surface is

![](../graphics/stm_eqn06391.gif)Since

![](../graphics/stm_eqn06392.gif)and

![](../graphics/stm_eqn06393.gif)then

![](../graphics/stm_eqn06394.gif)In uniaxial compression ![](../graphics/stm_eqn06370.gif), ![](../graphics/stm_eqn06371.gif), and ![](../graphics/stm_eqn06395.gif), so [Equation 4.5.1&#8211;7](04s05a119.md) defines

![](../graphics/stm_eqn06396.gif)This equation can be integrated immediately to give

![](../graphics/stm_eqn06397.gif)so ![](../graphics/stm_eqn06369.gif) is known from ![](../graphics/stm_eqn06398.gif) and the constants ![](../graphics/stm_eqn06211.gif) and ![](../graphics/stm_eqn06387.gif). [Equation 4.5.1&#8211;6](04s05a119.md) and [Equation 4.5.1&#8211;9](04s05a119.md), therefore, define the ![](../graphics/stm_eqn06366.gif) relationship from the concrete model input data once ![](../graphics/stm_eqn06387.gif) is known.

The constant ![](../graphics/stm_eqn06387.gif) is calculated from the user's definition of ![](../graphics/stm_eqn06399.gif), the ratio of ![](../graphics/stm_eqn06400.gif) to ![](../graphics/stm_eqn06398.gif), the total plastic strain components that would occur in monotonically loaded biaxial and uniaxial compression tests. In biaxial compression when both nonzero principal stresses have the magnitude ![](../graphics/stm_eqn06376.gif), ![](../graphics/stm_eqn06401.gif), ![](../graphics/stm_eqn06402.gif), and ![](../graphics/stm_eqn06403.gif), so the flow rule gives

![](../graphics/stm_eqn06404.gif)Using this equation and [Equation 4.5.1&#8211;8](04s05a119.md) then defines ![](../graphics/stm_eqn06387.gif) from ![](../graphics/stm_eqn06399.gif) and the other constants as

![](../graphics/stm_eqn06405.gif)
### Crack detection and damaged elasticity

Cracking dominates the material behavior when the state of stress is predominantly tensile. The model uses a "crack detection" plasticity surface in stress space to determine when cracking takes place and the orientation of the cracking. Damaged elasticity is then used to describe the postfailure behavior of the concrete with open cracks.

Numerically we use the "crack detection" plasticity model for the increment in which cracking takes place and subsequently use damaged elasticity once the crack's presence and orientation have been detected. As a result there is at least one increment in which we calculate crack detection "plastic" strains. Since these are really just the outcome of a numerical device to treat cracking, they are recast as elastic strains in the direction of cracking and as plastic strains in the other directions. (This means that we retain the stresses calculated for equilibrium purposes, as well as the strain decomposition of [Equation 4.5.1&#8211;1](04s05a119.md).)

The basis of the postcracked behavior is the brittle fracture concept of [Hilleborg (1976)](07s01a01-References.md). We assume that the fracture energy required to form a unit area of crack surface, ![](../graphics/stm_eqn06406.gif), is a material property. This value can be calculated from measuring the tensile stress as a function of the crack opening displacement ([Figure 4.5.1&#8211;4](04s05a119.md)), as

![](../graphics/stm_eqn06407.gif)

Figure 4.5.1&#8211;4 Cracking behavior based on fracture energy.

![](../graphics/stmfracen-cracking-nls.png)

Typical values of ![](../graphics/stm_eqn06406.gif) range from 40 N/m (0.22 lb/in) for a typical construction concrete (with ![](../graphics/stm_eqn06408.gif) 20 MPa, 2850 lb/in2) to 120 N/m (0.67 lb/in) for a high strength concrete (with ![](../graphics/stm_eqn06408.gif) 40 MPa, 5700 lb/in2).

The implication of assuming that ![](../graphics/stm_eqn06406.gif) is a material property is that, when the elastic part of the displacement, ![](../graphics/stm_eqn06409.gif) is eliminated, the relationship between the stress and the remaining part of the displacement, ![](../graphics/stm_eqn06410.gif) is fixed, regardless of the specimen size. For example, consider a specimen developing a single crack across its section as tensile displacement is applied to it: ![](../graphics/stm_eqn06411.gif) is the displacement across the crack and is not changed by using a longer or shorter specimen in the test (so long as the specimen is significantly longer than the width of the crack band, which will typically be of the order of the aggregate size). Thus, one important part of the cracked concrete's tensile behavior is defined in terms of a stress/displacement relationship. In the finite element implementation of this model we must, therefore, compute the relative displacement at an integration point to provide ![](../graphics/stm_eqn06411.gif). We do this in Abaqus by multiplying the strain by a characteristic length associated with the integration point. The characteristic crack length is based on the element geometry and formulation: it is a typical length of a line across an element for a first-order element; it is half of the same typical length for a second-order element. For beams and trusses it is a characteristic length along the element axis. For membranes and shells it is a characteristic length in the reference surface. For axisymmetric elements it is a characteristic length in the *r*&#8211;*z* plane only. For cohesive elements it is equal to the constitutive thickness. This definition of the characteristic length is used because we do not necessarily know in which direction the concrete will crack and so cannot choose the length measure in any particular direction. Thus, if there are elements in the model that have large aspect ratios, the model will likely provide different results if it is loaded in different directions and cracking occurs in such elements. This effect should be considered by the user in defining values for the material properties.

In reinforced concrete the ![](../graphics/stm_eqn01110.gif)&#8211;![](../graphics/stm_eqn06411.gif) relationship must also represent the action of the bond between the concrete and the rebar as the concrete cracks. We assume this is accommodated by increasing the value of ![](../graphics/stm_eqn06406.gif) based on comparisons with experiments on reinforced material.

We first describe the crack detection plasticity model and then discuss the damaged elasticity.
### Strain rate decomposition

We decompose the elastic strain rate of [Equation 4.5.1&#8211;1](04s05a119.md) as

![](../graphics/stm_eqn06412.gif)where ![](../graphics/stm_eqn05909.gif) is the total mechanical strain rate for the crack detection problem, ![](../graphics/stm_eqn06413.gif) is the elastic strain rate, and ![](../graphics/stm_eqn06414.gif) is the plastic strain rate associated with the crack detection surface.
### Yield

The crack detection surface is the Coulomb line

![](../graphics/stm_eqn06415.gif)where ![](../graphics/stm_eqn06416.gif) is the failure stress in uniaxial tension and ![](../graphics/stm_eqn06417.gif) is a constant that is defined from the value of the tensile failure stress, ![](../graphics/stm_eqn06418.gif), in a state of biaxial stress when the other nonzero principal stress, ![](../graphics/stm_eqn06419.gif), is at the uniaxial compression ultimate stress value, ![](../graphics/stm_eqn06420.gif). ![](../graphics/stm_eqn06421.gif) is a hardening parameter (![](../graphics/stm_eqn05865.gif) is the equivalent uniaxial tensile stress). The hardening is measured by ![](../graphics/stm_eqn04027.gif), with the ![](../graphics/stm_eqn06421.gif) relationship defined from the user-specified tension stiffening data (see [Figure 4.5.1&#8211;5](04s05a119.md)).

Figure 4.5.1&#8211;5 "Tension stiffening" model.

![](../graphics/cconcrete-ten-stiff-nls.png)

The stress measures ![](../graphics/stm_eqn06422.gif) and ![](../graphics/stm_eqn06423.gif) are defined in the same way as *p* and *q*, except that all stress components ![](../graphics/stm_eqn04933.gif) associated with open cracks (that is, if ![](../graphics/stm_eqn00904.gif) or ![](../graphics/stm_eqn01219.gif) is a crack direction in which the direct strain ![](../graphics/stm_eqn06424.gif) or ![](../graphics/stm_eqn06425.gif)) are not included in these measures: they are invariants in subspaces of the stress space.

This surface has a simple mathematical form but matches plane stress data quite well. The hardening is introduced in the particular form shown in [Equation 4.5.1&#8211;11](04s05a119.md) so that, as ![](../graphics/stm_eqn06426.gif), the surface becomes ![](../graphics/stm_eqn06427.gif), which in (*p*&#8211;*q*) space is the cone containing the principal axes of stress. This means that, as the tension stiffening is exhausted in a plane stress test, the stress point will drop back onto the nearest principal stress axis.

The value of ![](../graphics/stm_eqn06417.gif) is obtained as follows. The failure surface data include a definition of *f*, a ratio that states that, in a plane stress test cracking would occur when one principal stress has the value ![](../graphics/stm_eqn06428.gif) (![](../graphics/stm_eqn06420.gif) is the magnitude of the ultimate stress in uniaxial compression) and the other nonzero principal stress has the value ![](../graphics/stm_eqn06429.gif). Another value provided as part of the failure surface data is ![](../graphics/stm_eqn06430.gif), which defines

![](../graphics/stm_eqn06431.gif)Cracking would, therefore, occur at the point with principal stresses ![](../graphics/stm_eqn06432.gif), ![](../graphics/stm_eqn06433.gif), and *0*. For these values

![](../graphics/stm_eqn06434.gif)and

![](../graphics/stm_eqn06435.gif)Therefore, with ![](../graphics/stm_eqn06436.gif),

![](../graphics/stm_eqn06437.gif)so

![](../graphics/stm_eqn06438.gif)

The crack detection surface is shown in [Figure 4.5.1&#8211;2](04s05a119.md) and [Figure 4.5.1&#8211;3](04s05a119.md).
### Flow

The crack detection model uses the assumption of associated flow, so if ![](../graphics/stm_eqn06439.gif) and ![](../graphics/stm_eqn06440.gif),

![](../graphics/stm_eqn06441.gif)otherwise, ![](../graphics/stm_eqn06442.gif).
### Hardening

The user defines the tension stiffening behavior by specifying the magnitude of the stress, ![](../graphics/stm_eqn05865.gif), in a uniaxial tension test as a function of the inelastic strain. (When the fracture energy concept is used to define the postfailure behavior, "strain" is now defined as ![](../graphics/stm_eqn06443.gif), where *c* is the characteristic length associated with the integration point.) The ![](../graphics/stm_eqn06421.gif) relationship is defined as follows.

Using the definition of ![](../graphics/stm_eqn06444.gif), [Equation 4.5.1&#8211;11](04s05a119.md), in the flow rule above we write

![](../graphics/stm_eqn06445.gif)In uniaxial tension ![](../graphics/stm_eqn06446.gif) and ![](../graphics/stm_eqn06447.gif). Therefore, in uniaxial tension,

![](../graphics/stm_eqn06448.gif)and, hence,

![](../graphics/stm_eqn06449.gif)Upon integration [Equation 4.5.1&#8211;13](04s05a119.md) gives ![](../graphics/stm_eqn04027.gif) from ![](../graphics/stm_eqn06450.gif); and, therefore, the ![](../graphics/stm_eqn06421.gif) relationship is obtained from the tension stiffening input data.
### Damaged elasticity

Following crack detection we use damaged elasticity to model the failed material. The elasticity is written in the form

![](../graphics/stm_eqn06451.gif)where ![](../graphics/stm_eqn06452.gif) is the elastic stiffness matrix for the concrete.

Let ![](../graphics/stm_eqn00904.gif) represent a cracked direction, with corresponding direct stress ![](../graphics/stm_eqn06453.gif) and direct elastic strain ![](../graphics/stm_eqn06454.gif). In these expressions and in the remainder of this section, no summation is implied by repeated indices with a bar over them. If the fracture energy concept is used, the strains are related to the user-specified stress/displacement definition for the tension stiffening behavior by ![](../graphics/stm_eqn06455.gif), where *c* is the characteristic length associated with the integration point.

Then, in ![](../graphics/stm_eqn00424.gif), ![](../graphics/stm_eqn06456.gif) is the usual elasticity of the concrete if ![](../graphics/stm_eqn06457.gif). If ![](../graphics/stm_eqn06458.gif),

![](../graphics/stm_eqn06459.gif)where ![](../graphics/stm_eqn06460.gif) is the stress corresponding to ![](../graphics/stm_eqn06461.gif) (as defined in the tension stiffening data), and

![](../graphics/stm_eqn06462.gif)If ![](../graphics/stm_eqn06463.gif),

![](../graphics/stm_eqn06464.gif)which follows from the tension stiffening data.

We also assume no Poisson effect for open cracks: for ![](../graphics/stm_eqn06465.gif), ![](../graphics/stm_eqn06466.gif) for ![](../graphics/stm_eqn06467.gif), ![](../graphics/stm_eqn06468.gif).

The shear terms in the elasticity associated with existing crack directions are

![](../graphics/stm_eqn06469.gif)where ![](../graphics/stm_eqn06470.gif) and ![](../graphics/stm_eqn06471.gif) In these expressions *G* is the elastic shear modulus, ![](../graphics/stm_eqn06472.gif) is a constant defined by the user as part of the shear retention data (see [Figure 4.5.1&#8211;6](04s05a119.md)),

Figure 4.5.1&#8211;6 Shear retention.

![](../graphics/stmshear-retention.png)and ![](../graphics/stm_eqn06473.gif) is a linear function of ![](../graphics/stm_eqn06474.gif), ![](../graphics/stm_eqn06475.gif) and is also defined by the user in the shear retention data. Here ![](../graphics/stm_eqn06476.gif), where ![](../graphics/stm_eqn06477.gif) and ![](../graphics/stm_eqn06478.gif) are Macauley brackets, defining

![](../graphics/stm_eqn06479.gif)for any function *f*.
### Cracking

As soon as the crack detection surface (![](../graphics/stm_eqn06444.gif)) has been activated, we assume that cracking has occurred. The crack direction, ![](../graphics/stm_eqn03536.gif), is taken to be the direction of that part of the maximum principal plastic strain increment conjugate to the crack detection surface, ![](../graphics/stm_eqn06480.gif), that is orthogonal to the directions of any existing cracks at the same point. This crack orientation is stored for subsequent calculations, which are done for convenience in a local coordinate system oriented so that one of the coordinate directions is the crack direction, ![](../graphics/stm_eqn03536.gif). Cracking is irrecoverable in the sense that, once a crack has occurred at a point, it remains throughout the rest of the calculation. Following crack detection, the crack affects the calculations by damaging the elasticity, as defined above. In addition, if the elastic strain across a crack is tensile, the invariants used in the crack detection surface are defined in the stress sub-space in which all stress components associated with the open crack direction are neglected, as described in the section above on yield. This implies that no more than three cracks can occur at any point (two in a plane stress case, one in a uniaxial stress case).
### Integration of the model

The model is integrated using the backward Euler method generally used with the plasticity models in Abaqus. A material Jacobian consistent with this integration operator is used for the equilibrium iterations.
### Reference

### Reference

"Concrete smeared cracking,"  Section 23.6.1 of the Abaqus Analysis User's Guide