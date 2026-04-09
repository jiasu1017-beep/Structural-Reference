# 2.7.1 Steady-state transport analysis

### 2.7.1 Steady-state transport analysis

**Product: **Abaqus/Standard

Abaqus/Standard provides a specialized analysis capability to model the steady-state behavior of a cylindrical deformable body rolling along a flat rigid surface. The capability uses a reference frame that removes the explicit time dependence from the problem so that a purely spatially dependent analysis can be performed. For an axisymmetric body traveling at a constant ground velocity and constant angular rolling velocity, a steady state is possible in a frame that moves at the speed of the ground velocity but does not spin with the body in the rolling motion. This choice of reference frame allows the finite element mesh to remain stationary so that only the part of the body in the contact zone requires fine meshing.
### Kinematics of steady-state rolling

The kinematics of the rolling problem are described in terms of a coordinate frame that moves along with the ground motion of the body. In this moving frame the rigid body rotation is described in a spatial or Eulerian manner and the deformation in a material or Lagrangian manner. It is this kinematic description that converts the steady moving contact field problem into a purely spatially dependent simulation.

We consider the case shown in [Figure 2.7.1&#8211;1](02s07a35.md), where the ground velocity of the body is described in terms of a constant cornering motion.

Figure 2.7.1&#8211;1 Constant cornering motion.

![](../graphics/corneringrolling.png)The body is rotating with a constant angular rolling velocity ![](../graphics/stm_eqn01091.gif) around a rigid axle ![](../graphics/stm_eqn00553.gif) at ![](../graphics/stm_eqn01638.gif), which in turn rotates with constant angular velocity ![](../graphics/stm_eqn01258.gif) around the fixed cornering axis ![](../graphics/stm_eqn00483.gif) through point ![](../graphics/stm_eqn01639.gif). Hence, the motion of a particle ![](../graphics/stm_eqn00141.gif) at time *t* consists of a rigid rolling rotation to position ![](../graphics/stm_eqn01640.gif), described by

![](../graphics/stm_eqn01641.gif)followed by a deformation to point ![](../graphics/stm_eqn00117.gif), and a subsequent cornering rotation (or precession) around ![](../graphics/stm_eqn00483.gif) to position ![](../graphics/stm_eqn01642.gif) so that

![](../graphics/stm_eqn01643.gif)where ![](../graphics/stm_eqn01644.gif) is the cornering rotation given by ![](../graphics/stm_eqn01645.gif) and ![](../graphics/stm_eqn01646.gif) is the skew-symmetric matrix associated with the rotation vector ![](../graphics/stm_eqn01647.gif). Similarly, ![](../graphics/stm_eqn01648.gif) is the spinning rotation matrix defined as ![](../graphics/stm_eqn01649.gif) and ![](../graphics/stm_eqn01650.gif) is the skew-symmetric matrix associated with the rotation vector ![](../graphics/stm_eqn01651.gif). The velocity of the particle then becomes

![](../graphics/stm_eqn01652.gif)To describe the deformation of the body, we define a map ![](../graphics/stm_eqn01653.gif), which gives the position of point ![](../graphics/stm_eqn00141.gif) at time *t* as a function of its location ![](../graphics/stm_eqn01640.gif) at time *t* so that ![](../graphics/stm_eqn01654.gif) It follows that

![](../graphics/stm_eqn01655.gif)where

![](../graphics/stm_eqn01656.gif)Noting that ![](../graphics/stm_eqn01657.gif), and introducing the circumferential direction ![](../graphics/stm_eqn01658.gif), where ![](../graphics/stm_eqn01659.gif) is the radius of a point on the reference body, the velocity of the reference body can be written as ![](../graphics/stm_eqn01660.gif), so that

![](../graphics/stm_eqn01661.gif)where *S* is the distance-measuring coordinate along the streamline. Using this result, together with ![](../graphics/stm_eqn01662.gif), the velocity of the particle can be written as

![](../graphics/stm_eqn01663.gif)The acceleration is obtained by a second differentiation and some manipulation:

![](../graphics/stm_eqn01664.gif)

To obtain expressions for the velocity and acceleration in the reference frame tied to the body, we use the transformations

![](../graphics/stm_eqn01665.gif)so that we obtain

![](../graphics/stm_eqn01666.gif)and

![](../graphics/stm_eqn01667.gif)For steady-state conditions these expressions reduce to

![](../graphics/stm_eqn01668.gif)and

![](../graphics/stm_eqn01669.gif)

The first term in the last expression can be identified as the acceleration that gives rise to centrifugal forces resulting from rotation about ![](../graphics/stm_eqn00483.gif). Noting that ![](../graphics/stm_eqn01670.gif) is a measure of velocity, the second term can be identified as the acceleration that gives rise to Coriolis forces. The last term combines the acceleration that gives rise to Coriolis and centrifugal forces resulting from rotation about ![](../graphics/stm_eqn00553.gif). When the deformation is uniform along the circumferential direction, this Coriolis effect vanishes so that the acceleration gives rise to centrifugal forces only.

The velocity of the center of the body ![](../graphics/stm_eqn01638.gif) (which must lie on the axis ![](../graphics/stm_eqn00553.gif)) is

![](../graphics/stm_eqn01671.gif)since the motions due to rolling and deformation vanish on the axis.

To obtain the expression for straight line motion, as shown in [Figure 2.7.1&#8211;2](02s07a35.md), we move ![](../graphics/stm_eqn01639.gif) far away from the center of the body ![](../graphics/stm_eqn01672.gif) but keep ![](../graphics/stm_eqn01673.gif) the same. In that case ![](../graphics/stm_eqn01674.gif) and, hence, in the limit

![](../graphics/stm_eqn01675.gif)

![](../graphics/stm_eqn01676.gif)which corresponds to straight line rolling.

Figure 2.7.1&#8211;2 Straight line rolling.

![](../graphics/straightlinerolling.png)
### Inertia

The virtual work contribution from the d'Alembert forces is

![](../graphics/stm_eqn01677.gif)Using the divergence theorem, the virtual work contribution becomes

![](../graphics/stm_eqn01678.gif)and the rate of virtual work becomes

![](../graphics/stm_eqn01679.gif)For straight line rolling only the last term in each expression needs to be taken into account.
### Performing a harmonic analysis about a nonlinear base state

To perform a steady-state dynamic or frequency analysis on a rolling tire, it is necessary to linearize the virtual work expressions about the base state. Assuming a harmonic solution of the form ![](../graphics/stm_eqn01680.gif), it can be shown that, for the case of straight line rolling, the linearized rate of virtual work is

![](../graphics/stm_eqn01681.gif) The first term is the load stiffness contribution due to the spinning motion about the axle. The second term is an imaginary antisymmetric gyroscopic operator. The third term is the standard mass operator.
### Contact conditions

To obtain the contact conditions, we start with the expressions for velocity derived in the previous section. For points on the surface of the deformable body

![](../graphics/stm_eqn01682.gif)where ![](../graphics/stm_eqn00483.gif) is the cornering axis (which must be normal to the rigid surface) and ![](../graphics/stm_eqn01258.gif) is the cornering angular velocity around ![](../graphics/stm_eqn00483.gif). Assuming that the velocity of a point on the foundation (or rigid surface) is ![](../graphics/stm_eqn01683.gif), the relative motion becomes

![](../graphics/stm_eqn01684.gif)where ![](../graphics/stm_eqn01685.gif). This equation can be split into normal and tangential components. The rate of penetration is

![](../graphics/stm_eqn01686.gif)For any point in contact ![](../graphics/stm_eqn01687.gif); hence,

![](../graphics/stm_eqn01688.gif)which in incremental form reduces to the standard contact condition

![](../graphics/stm_eqn01689.gif)For steady-state conditions ![](../graphics/stm_eqn01690.gif) and ![](../graphics/stm_eqn01691.gif).

Similarly, the rate of slip is

![](../graphics/stm_eqn01692.gif)where ![](../graphics/stm_eqn01693.gif) are two orthogonal unit vectors tangent to the contact surface so that ![](../graphics/stm_eqn01694.gif). For steady-state conditions ![](../graphics/stm_eqn01695.gif), so

![](../graphics/stm_eqn01696.gif)Variations in ![](../graphics/stm_eqn01697.gif) yield

![](../graphics/stm_eqn01698.gif)For straight line rolling we can replace ![](../graphics/stm_eqn01699.gif) by ![](../graphics/stm_eqn01673.gif) so that we obtain

![](../graphics/stm_eqn01700.gif)and

![](../graphics/stm_eqn01701.gif)

To complete the formulation, a relationship between frictional stress and slip velocity must be developed. A Coulomb friction law is provided for steady-state rolling. The law assumes that slip occurs if the frictional stress,

![](../graphics/stm_eqn01702.gif)is equal to the critical stress, ![](../graphics/stm_eqn01703.gif), where ![](../graphics/stm_eqn01704.gif) and ![](../graphics/stm_eqn01705.gif) are shear stresses along ![](../graphics/stm_eqn01706.gif), ![](../graphics/stm_eqn01087.gif) is the friction coefficient, and *p* is the contact pressure. On the other hand, when ![](../graphics/stm_eqn01707.gif), no relative motion occurs. The condition of no relative motion is approximated in Abaqus by stiff viscous behavior

![](../graphics/stm_eqn01708.gif)where ![](../graphics/stm_eqn01697.gif) is the tangential slip velocity and ![](../graphics/stm_eqn01709.gif) is the "stick viscosity," which follows from the relation

![](../graphics/stm_eqn01710.gif)The allowable viscous slip velocity is defined as a fraction of the circumferential velocity

![](../graphics/stm_eqn01711.gif)where ![](../graphics/stm_eqn01712.gif) is a user-defined slip tolerance.

These expressions contribute to the standard virtual work contribution for slip,

![](../graphics/stm_eqn01713.gif)and rate of virtual work for slip,

![](../graphics/stm_eqn01714.gif)
### Reference

### Reference

"Steady-state transport analysis,"  Section 6.4.1 of the Abaqus Analysis User's Guide