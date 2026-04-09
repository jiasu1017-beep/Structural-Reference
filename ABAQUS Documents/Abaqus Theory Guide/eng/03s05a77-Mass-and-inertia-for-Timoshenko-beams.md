# 3.5.5 Mass and inertia for Timoshenko beams

### 3.5.5 Mass and inertia for Timoshenko beams

**Products: **Abaqus/Standard  Abaqus/Explicit

Mass and inertia properties for Timoshenko beams (including PIPE elements) in Abaqus may come from two separate sources. The first source is the beam's own density and the cross-section geometry. The second source comes from any additional mass and inertia properties per element length that may be applied at specified locations on the beam cross-section. When the mass and inertia are given only from the first source, the user has the choice of requesting either an isotropic approximation or the exact rotary inertia formulation for the beam mass matrix. When the isotropic formulation is used, the mass of the beam per length is applied to the beam's node that is located at the origin of the cross-section axis and the offset between the beam's node and the center of mass for the cross-section (if it is nonzero) is neglected in the mass matrix formulation.

Let ![](../graphics/stm_eqn03942.gif) be the beam density. Mass and the rotary inertia about the center of mass in the beam's cross-section coordinate system are defined as

![](../graphics/stm_eqn03943.gif)Here, ![](../graphics/stm_eqn01412.gif) and ![](../graphics/stm_eqn01413.gif) are measured relative to the center of mass of the cross-section.

For the isotropic (approximate) formulation the mass matrix for the element takes the form

![](../graphics/stm_eqn03944.gif)In two dimensions ![](../graphics/stm_eqn03945.gif).

In all expressions in this section the mass matrix ![](../graphics/stm_eqn03946.gif) that applies to the translational degrees of freedom is lumped for 2-node beams and consistent for 3-node beams.

When the exact formulation is used, any offset between the beam's node and the center of mass for the cross-section will produce coupling between the translational degrees of freedom and rotational degrees of freedom in the mass matrix for the element.

Let ![](../graphics/stm_eqn03947.gif) define the added mass per beam length. The combined beam mass is defined as

![](../graphics/stm_eqn03948.gif)

Let ![](../graphics/stm_eqn03949.gif) be the vector between the center of mass *C* and some point with current coordinates ![](../graphics/stm_eqn00117.gif),

![](../graphics/stm_eqn03950.gif)

For a rigid body the velocity of any point in the body is given by

![](../graphics/stm_eqn03951.gif)where ![](../graphics/stm_eqn03952.gif) is the angular velocity of the body. Taking the time derivative of this expression, the acceleration is

![](../graphics/stm_eqn03953.gif)

The local or strong form of the equilibrium equations represents the balance of linear momentum and balance of angular momentum; these two equilibrium equations are

![](../graphics/stm_eqn03954.gif)where ![](../graphics/stm_eqn03955.gif) and ![](../graphics/stm_eqn03956.gif) are external forces acting at the center of mass and external moment and ![](../graphics/stm_eqn00064.gif) is the rotary inertia tensor.

The variational or weak form of equilibrium is

![](../graphics/stm_eqn03957.gif)Taking the time derivative in the equilibrium equations, the internal or d'Alembert force contribution is

![](../graphics/stm_eqn03958.gif)where ![](../graphics/stm_eqn01597.gif) is the variation of the position of a point in the body and ![](../graphics/stm_eqn03959.gif) is the variation of the rotation of the rigid body reference node. The external loading contribution is

![](../graphics/stm_eqn03960.gif)For linear theory all nonlinear terms are neglected, so the internal force contribution simplifies to

![](../graphics/stm_eqn03961.gif)and leads to the following mass matrix for all linear and linear perturbation analyses:

![](../graphics/stm_eqn03962.gif)where ![](../graphics/stm_eqn03963.gif) denotes a skew symmetric matrix and ![](../graphics/stm_eqn03964.gif).

When the inertia of a rigid body is used with implicit time integration, the Jacobian contribution of ![](../graphics/stm_eqn03965.gif) is required. It can be written in the form

![](../graphics/stm_eqn03966.gif)where the following notation was used

![](../graphics/stm_eqn03967.gif)

![](../graphics/stm_eqn03968.gif)

![](../graphics/stm_eqn03969.gif)In the Jacobian formulation for 3-node beams, a consistent mass matrix is used for translational degrees of freedom and a lumped mass matrix is used for rotational degrees of freedom and the terms that couple translational and rotational degrees of freedom.