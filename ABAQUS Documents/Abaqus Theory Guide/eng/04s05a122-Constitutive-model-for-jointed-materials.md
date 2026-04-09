# 4.5.4 Constitutive model for jointed materials

### 4.5.4 Constitutive model for jointed materials

**Product: **Abaqus/Standard

The jointed material model is intended to provide a simple, continuum model for materials containing a high density of parallel joint surfaces in different orientations. The spacing of the joints of a particular orientation is assumed to be sufficiently close compared to characteristic dimensions in the domain of the model that the joints can be smeared into a continuum of slip systems. An obvious application is the modeling of geotechnical problems where the medium of interest is composed of significantly faulted rock. In this context, models similar to the one described next have been proposed in the past; see, for example, the model formulated by [Zienkiewicz and Pande (1977)](07s01a01-References.md).

The model implemented in Abaqus/Standard provides for opening of the joints, or frictional sliding of the joints, in each of these systems (a "system" in this context is a joint orientation in a particular direction at a material calculation point). In addition to the joint systems, the model includes a bulk material failure mechanism. This is based on the Drucker-Prager failure criterion.
### Joint system definitions

We consider a particular joint *a* oriented by the normal to the joint surface ![](../graphics/stm_eqn06661.gif). We define ![](../graphics/stm_eqn06662.gif) as two unit, orthogonal vectors in the joint surface. The local stress components are the pressure stress across the joint

![](../graphics/stm_eqn06663.gif)and the shear stresses across the joint

![](../graphics/stm_eqn06664.gif)where ![](../graphics/stm_eqn00033.gif) is the stress tensor. We define the shear stress magnitude as

![](../graphics/stm_eqn06665.gif)The local strain components are the normal strain across the joint

![](../graphics/stm_eqn06666.gif)and the engineering shear strain in the ![](../graphics/stm_eqn00904.gif)-direction in the joint surface

![](../graphics/stm_eqn06667.gif)where ![](../graphics/stm_eqn06668.gif) is the strain tensor.
### Strain rate decomposition

A linear strain rate decomposition is assumed, so that

![](../graphics/stm_eqn06669.gif)where ![](../graphics/stm_eqn06115.gif) is the total strain rate, ![](../graphics/stm_eqn06116.gif) is the elastic strain rate, and ![](../graphics/stm_eqn06117.gif) is the inelastic (plastic) strain rate. Supposing that several systems are active (we designate an active system by *i*, where ![](../graphics/stm_eqn06670.gif) indicates the bulk material system and ![](../graphics/stm_eqn06671.gif) is a joint system *a*), we write

![](../graphics/stm_eqn06672.gif)
### Elasticity and joint opening/closing

When all joints at a point are closed, the elastic behavior of the material is assumed to be isotropic and linear. The material cannot be elastically incompressible (Poisson's ratio must be less than 0.5).

We use a stress-based joint opening criterion whereas joint closing is monitored based on strain. Joint system *a* opens when the estimated pressure stress across the joint (normal to the joint surface) is no longer positive:

![](../graphics/stm_eqn06673.gif)In this case the material is assumed to have no elastic stiffness with respect to direct strain across the joint system. Open joints, thus, create anisotropic elastic response at a point. The joint system remains open as long as

![](../graphics/stm_eqn06674.gif)where ![](../graphics/stm_eqn06675.gif) is the component of direct elastic strain across the joint and ![](../graphics/stm_eqn06676.gif) is the component of direct elastic strain across the joint calculated in plane stress as

![](../graphics/stm_eqn06677.gif)where *E* is the Young's modulus of the material, ![](../graphics/stm_eqn01854.gif) is the Poisson's ratio, and

![](../graphics/stm_eqn06678.gif)are the direct stresses in the plane of the joint.

The shear response of open joints is governed by the shear retention parameter, ![](../graphics/stm_eqn06679.gif), which represents the fraction of the elastic shear modulus retained when the joints are open (![](../graphics/stm_eqn06679.gif)=0 means no shear stiffness associated with open joints, while ![](../graphics/stm_eqn06679.gif)=1 corresponds to elastic shear stiffness in open joints; any value between these two extremes can be used).
### Plastic behavior of joint systems

The failure surface for sliding on joint system *a* is defined by

![](../graphics/stm_eqn06680.gif)where ![](../graphics/stm_eqn06681.gif) is the friction angle for system *a*, and ![](../graphics/stm_eqn06682.gif) is the cohesion for system *a* (see [Figure 4.5.4&#8211;1](04s05a122.md)).

Figure 4.5.4&#8211;1 Joint system material model.

![](../graphics/stmjointsys-model.png)As long as ![](../graphics/stm_eqn06683.gif), joint system *a* does not slip. When ![](../graphics/stm_eqn06684.gif) joint system *a* slips. The inelastic ("plastic") strain on the system is then given by

![](../graphics/stm_eqn06685.gif)where ![](../graphics/stm_eqn06686.gif) is the rate of inelastic shear strain in direction ![](../graphics/stm_eqn00904.gif) on the joint surface, ![](../graphics/stm_eqn06687.gif) is the magnitude of the inelastic strain rate, ![](../graphics/stm_eqn06688.gif) is the dilation angle for this joint system (choosing ![](../graphics/stm_eqn06689.gif) provides pure shear flow on the joint, while ![](../graphics/stm_eqn06690.gif) causes dilation of the joint as it slips), and ![](../graphics/stm_eqn06691.gif) is the inelastic strain normal to the joint surface. In order to add the plastic flow contributions from different systems we write the tensorial plastic strain rate for joint *a* as

![](../graphics/stm_eqn06692.gif)

The sliding of the different joint systems at a point is independent, in the sense that sliding on one system does not change the failure criterion or the dilation angle for any other joint system at the same point. The model provides for up to three joint systems at a point.
### Plastic behavior of bulk material

In addition to the joint systems, the model includes a bulk material failure mechanism. This is based on the Drucker-Prager failure criterion,

![](../graphics/stm_eqn06693.gif)where ![](../graphics/stm_eqn06694.gif) is the Mises equivalent deviatoric stress (here ![](../graphics/stm_eqn00522.gif) is the deviatoric stress ![](../graphics/stm_eqn06695.gif)), ![](../graphics/stm_eqn06696.gif) is the equivalent pressure stress, ![](../graphics/stm_eqn06697.gif) is the friction angle for the bulk material, and ![](../graphics/stm_eqn06698.gif) is the cohesion for the bulk material (see [Figure 4.5.4&#8211;2](04s05a122.md)).

Figure 4.5.4&#8211;2 Bulk material model.

![](../graphics/stmbulkmat-model.png)If this failure criterion is reached, the bulk inelastic flow is defined by

![](../graphics/stm_eqn06699.gif)where

![](../graphics/stm_eqn06700.gif)is the flow potential. Here, ![](../graphics/stm_eqn06701.gif) is the magnitude of the inelastic flow rate (chosen so that ![](../graphics/stm_eqn06702.gif) in uniaxial compression in the *1*-direction) and ![](../graphics/stm_eqn06703.gif) is the dilation angle for the bulk material. This bulk failure model is a simplified version of the extended Drucker-Prager model described in "Models for granular or polymer behavior,"  Section 4.4.2. As with the joint systems, this bulk failure system is independent of the joint systems, in that bulk inelastic flow does not change the behavior of any joint system.

If ![](../graphics/stm_eqn06704.gif) in any system the flow in that system is "nonassociated." This implies that the material stiffness matrix is not symmetric, so that the unsymmetric matrix solution scheme should be invoked by the user. If the difference between ![](../graphics/stm_eqn02064.gif) and ![](../graphics/stm_eqn01219.gif) is not large, a symmetric approximation to the matrix can provide an acceptable rate of convergence of the equilibrium equations, and hence a lower overall solution cost. For this reason the unsymmetric solver is not automatically invoked for this material behavior. However, it is recommended for all cases where ![](../graphics/stm_eqn02064.gif) and ![](../graphics/stm_eqn01219.gif) are very different on any joint system.
### Integration of the model

The constitutive equations described above are integrated using the backward Euler method generally used with the plasticity models in Abaqus. A material Jacobian consistent with this integration operator is used for the overall equilibrium iterations.
### Reference

### Reference

"Jointed material model,"  Section 23.5.1 of the Abaqus Analysis User's Guide