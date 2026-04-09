# 2.3.1 Eigenvalue buckling prediction

### 2.3.1 Eigenvalue buckling prediction

**Product: **Abaqus/Standard

Abaqus/Standard contains a capability for estimating elastic buckling by eigenvalue extraction. This estimation is typically useful for "stiff" structures, where the prebuckling response is almost linear. The buckling load estimate is obtained as a multiplier of the pattern of perturbation loads, which are added to a set of base state loads. The base state of the structure may have resulted from any type of response history, including nonlinear effects. It represents the initial state to which the perturbation loads are added. The response to the perturbation loads must be elastic up to the estimated buckling load values for the eigenvalue estimates to be reasonable.

The following physical problem is addressed in eigenvalue buckling analysis: from an arbitrarily achieved base configuration with stresses ![](../graphics/stm_eqn00762.gif) in equilibrium with surface traction ![](../graphics/stm_eqn00763.gif) and body forces ![](../graphics/stm_eqn00764.gif), we consider an elastic deformation with "small" displacement gradients under additional surface tractions ![](../graphics/stm_eqn00765.gif), body forces ![](../graphics/stm_eqn00766.gif), and boundary displacements ![](../graphics/stm_eqn00767.gif), where the additional tractions and displacements are applied on mutually complementary parts of the boundary. Such a deformation is a linear perturbation on a predeformed state. A consistent application of the small-displacement gradient assumption to the kinematics and the constitutive equation from an initially stressed state leads to the solution of a linear problem as the response to the additional loading. Since the problem is linear, if ![](../graphics/stm_eqn00768.gif) is the stress response to the loads ![](../graphics/stm_eqn00769.gif), ![](../graphics/stm_eqn00770.gif), and ![](../graphics/stm_eqn00771.gif), then for loads ![](../graphics/stm_eqn00772.gif), ![](../graphics/stm_eqn00773.gif), and ![](../graphics/stm_eqn00774.gif) the stress response will be ![](../graphics/stm_eqn00775.gif).

Each distinct value of ![](../graphics/stm_eqn00280.gif) corresponds to a linear perturbation of the base state. Among these perturbed states we seek special values of ![](../graphics/stm_eqn00280.gif) that allow for the existence of nontrivial incremental displacement fields with arbitrary magnitudes as valid solutions to the problem. Such nontrivial incremental displacement fields are referred to as buckling modes. In the buckling analysis procedure in Abaqus we do not distinguish between the geometry of the base state and the linearly perturbed configurations. As a result of this assumption we can seek the buckling modes as incremental displacements out of the base state geometry with stresses ![](../graphics/stm_eqn00776.gif), applied tractions ![](../graphics/stm_eqn00777.gif), and applied body forces ![](../graphics/stm_eqn00778.gif).

The equations of equilibrium for an arbitrarily chosen configuration during buckling, referred to as the current configuration, are written in terms of the nominal stress ![](../graphics/stm_eqn00779.gif) in the base state. If ![](../graphics/stm_eqn00141.gif) represents the position of a material point in the base state, the equilibrium equations can be expressed as

![](../graphics/stm_eqn00780.gif)where ![](../graphics/stm_eqn00781.gif) is an arbitrary virtual velocity field, ![](../graphics/stm_eqn00156.gif) is the nominal traction on the boundary ![](../graphics/stm_eqn00782.gif) of the body in the base state, ![](../graphics/stm_eqn00026.gif) represents the body force per unit volume in the base state, and ![](../graphics/stm_eqn00783.gif) is the volume that the body occupies in the base state. The corresponding rate form is given by

![](../graphics/stm_eqn00784.gif)

Since we have assumed that the base state and the current state are indistinguishable, we now proceed to express the left-hand side in terms of the rate of Kirchhoff stress ![](../graphics/stm_eqn00785.gif), the velocity gradient ![](../graphics/stm_eqn00423.gif), the virtual velocity gradient ![](../graphics/stm_eqn00786.gif), and the deformation gradient ![](../graphics/stm_eqn00319.gif). Using the relations ![](../graphics/stm_eqn00787.gif), where ![](../graphics/stm_eqn00788.gif) is the Kirchhoff stress based on the base state as the reference configuration, and ![](../graphics/stm_eqn00789.gif), [Equation 2.3.1&#8211;1](02s03a17-Eigenvalue-buckling-prediction.md) takes the form

![](../graphics/stm_eqn00790.gif)We now use the relation between the rate of Kirchhoff stress ![](../graphics/stm_eqn00785.gif), the material spin ![](../graphics/stm_eqn00791.gif), and the Jaumann rate of Kirchhoff stress ![](../graphics/stm_eqn00792.gif) to transform this expression into

![](../graphics/stm_eqn00793.gif)In addition, we can replace the Kirchhoff stress ![](../graphics/stm_eqn00788.gif) with the Cauchy stress ![](../graphics/stm_eqn00794.gif) since it is assumed that the current and reference configurations are indistinguishable.

For the right-hand side of [Equation 2.3.1&#8211;1](02s03a17-Eigenvalue-buckling-prediction.md) we note that the nominal tractions ![](../graphics/stm_eqn00156.gif) and body forces ![](../graphics/stm_eqn00026.gif) are given by ![](../graphics/stm_eqn00795.gif) and ![](../graphics/stm_eqn00796.gif), where ![](../graphics/stm_eqn00797.gif) and ![](../graphics/stm_eqn00798.gif) are the elements of surface area and volume in the current configuration. For any material point the changes in ![](../graphics/stm_eqn00479.gif) and ![](../graphics/stm_eqn00178.gif) during buckling are completely characterized by the change of the deformation gradient at that point; loosely speaking, the magnitude of the applied forces at any material point is kept fixed, and the change in the applied tractions and body force intensities arises due to the change in geometry. For example, for a pressure load the magnitude of the pressure remains constant but the surface normal changes---a change that is completely characterized by the change in the deformation gradient. Since the ratios of the surface area and volume measures between the reference and current configurations can be viewed as functions of the deformation gradient ![](../graphics/stm_eqn00319.gif) only, it follows that ![](../graphics/stm_eqn00156.gif) and ![](../graphics/stm_eqn00026.gif) at any given material point also change only through their dependence on the deformation gradient; hence, their rates of change can be written as

![](../graphics/stm_eqn00799.gif)or when the current and reference configurations are indistinguishable,

![](../graphics/stm_eqn00800.gif)Assuming a hypoelastic constitutive law,

![](../graphics/stm_eqn00801.gif)where ![](../graphics/stm_eqn00802.gif) is a fourth-order tensor that can depend on the current stress, the governing equation for the buckling analysis becomes

![](../graphics/stm_eqn00803.gif)where ![](../graphics/stm_eqn00804.gif) and ![](../graphics/stm_eqn00805.gif) are the nominal tractions generated during buckling corresponding to the base state tractions ![](../graphics/stm_eqn00763.gif) and the linear perturbation tractions ![](../graphics/stm_eqn00765.gif), respectively; similar definitions apply for the nominal body force terms. The constitutive relation can represent elasticity, hypoelasticity, and hyperelasticity; rate effects and plasticity are ignored. The effective moduli are evaluated for the value of the stress and deformation in the base state.

To derive the finite element discretization for the expression above, we introduce the interpolated velocity field

![](../graphics/stm_eqn00806.gif)where ![](../graphics/stm_eqn00141.gif) represents the position in the base state. Using the standard finite element approach, the governing equations for buckling then take the form of the standard eigenvalue problem:

![](../graphics/stm_eqn00807.gif)where ![](../graphics/stm_eqn00808.gif) is the base state stiffness and ![](../graphics/stm_eqn00809.gif) is the differential stiffness. The base state stiffness is the sum of the hypoelastic tangent stiffness, the initial stress stiffness, and the load stiffness:

![](../graphics/stm_eqn00810.gif)where ![](../graphics/stm_eqn00811.gif) and ![](../graphics/stm_eqn00812.gif) are the derivatives of the nominal surface tractions and body forces with respect to the nodal displacements. Since we do not distinguish between the current configuration and the reference configuration, the partial derivatives appearing in the load stiffness terms are all evaluated at ![](../graphics/stm_eqn00813.gif) corresponding to ![](../graphics/stm_eqn00814.gif). For example, the load stiffness term for the surface tractions appearing in [Equation 2.3.1&#8211;2](02s03a17-Eigenvalue-buckling-prediction.md),

![](../graphics/stm_eqn00815.gif)transforms into the finite element expression

![](../graphics/stm_eqn00816.gif)with

![](../graphics/stm_eqn00817.gif)The differential stiffness consists of the sum of the initial stress stiffness due to the perturbation stresses and the load stiffness due to the perturbation loads:

![](../graphics/stm_eqn00818.gif)The contribution in this expression that is derived from the stress is symmetric; however, the contribution derived from the applied loads (the load stiffness) is symmetric only if the applied loading is conservative---that is, if the loads can be derived from an energy potential. If the load stiffness is nonsymmetric, the contribution will be symmetrized since Abaqus can solve eigenvalue problems only with symmetric matrices.

If the generalized nodal "loads" resulting from both applied forces ![](../graphics/stm_eqn00819.gif) and ![](../graphics/stm_eqn00820.gif) as well as prescribed displacements ![](../graphics/stm_eqn00821.gif) are denoted by ![](../graphics/stm_eqn00822.gif) and those due to ![](../graphics/stm_eqn00769.gif), ![](../graphics/stm_eqn00770.gif), and ![](../graphics/stm_eqn00823.gif) are denoted by ![](../graphics/stm_eqn00824.gif), the eigenvalues ![](../graphics/stm_eqn00825.gif) represent the multipliers that provide the estimated generalized buckling load as ![](../graphics/stm_eqn00826.gif), while the corresponding eigenvectors ![](../graphics/stm_eqn00827.gif) give the associated buckling modes. Although in most analyses the lowest mode is the only one of interest, Abaqus is able to extract several modes simultaneously. It is also worth noting that the common case of an antisymmetric buckling mode on a symmetric base state and buckling load is easily done with Abaqus.

If the tangent stiffness is predicted poorly by ![](../graphics/stm_eqn00828.gif) (that is, the structure is not "stiff" in the sense that the response is nonlinear prior to buckling), a nonlinear analysis using the Riks method is required to obtain a reliable estimate for the load carrying capacity of the structure.
### Reference

### Reference

"Eigenvalue buckling prediction,"  Section 6.2.3 of the Abaqus Analysis User's Guide