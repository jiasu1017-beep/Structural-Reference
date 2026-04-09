# 4.3.5 Models for metals subjected to cyclic loading

### 4.3.5 Models for metals subjected to cyclic loading

**Products: **Abaqus/Standard  Abaqus/Explicit

The kinematic hardening models in Abaqus are intended to simulate the behavior of metals that are subjected to cyclic loading. These models are typically applied to studies of low-cycle fatigue and ratchetting. The basic concept of these models is that the yield surface shifts in stress space so that straining in one direction reduces the yield stress in the opposite direction, thus simulating the Bauschinger effect and anisotropy induced by work hardening.

Two kinematic hardening models are available in Abaqus. The simplest model provides linear kinematic hardening and is, thus, mainly used for low-cycle fatigue evaluations. This model yields physically reasonable results if the uniaxial behavior is linearized in the plastic range (a constant work-hardening slope). This is usually best accomplished by guessing the strain levels that will be attained in the problem and linearizing the actual material behavior accordingly. It is important to recognize this restriction on the theory's ability to provide reasonable results and to provide material data accordingly. This model is available with the Mises or Hill yield surface.

The combined isotropic/kinematic hardening model is an extension of the linear model. It provides a more accurate approximation to the stress-strain relation than the linear model. It also models other phenomena---such as ratchetting, relaxation of the mean stress, and cyclic hardening---that are typical of materials subjected to cyclic loading. In addition, it is possible to superpose several kinematic hardening models, which in general will produce more accurate results when the range of changes in strain is significant and will allow more accurate modeling of the ratchetting effect. This model is available only with the Mises yield surface.

This section first describes those aspects of the formulation that are common to both models; the specific formulation of each model is presented subsequently.
### Strain rate decomposition

The total strain rate ![](../graphics/stm_eqn05737.gif) is written in terms of the elastic and plastic strain rates as

![](../graphics/stm_eqn05738.gif)
### Elastic behavior

The elastic behavior can be modeled only as linear elastic

![](../graphics/stm_eqn05739.gif)where ![](../graphics/stm_eqn05740.gif) represents the fourth-order elasticity tensor and ![](../graphics/stm_eqn05741.gif) and ![](../graphics/stm_eqn05742.gif) are the second-order stress and strain tensors, respectively.
### Plastic behavior

The models are pressure-independent plasticity models. For both models the yield surface is defined by the function

![](../graphics/stm_eqn05743.gif)where ![](../graphics/stm_eqn05744.gif) is the equivalent Mises stress or Hill's potential with respect to the backstress or "kinematic shift" ![](../graphics/stm_eqn05745.gif), and ![](../graphics/stm_eqn05285.gif) is the size of the yield surface. For example, the equivalent Mises stress is defined as

![](../graphics/stm_eqn05746.gif)where ![](../graphics/stm_eqn05747.gif) is the deviatoric part of the backstress and ![](../graphics/stm_eqn05748.gif) is the deviatoric stress tensor.

These models assume associated plastic flow:

![](../graphics/stm_eqn05749.gif)where ![](../graphics/stm_eqn05750.gif) represents the rate of plastic flow and ![](../graphics/stm_eqn05751.gif) is the equivalent plastic strain rate, ![](../graphics/stm_eqn05752.gif)
### Linear kinematic hardening model

This model is the simpler of the two kinematic hardening models available in Abaqus. The size of the yield surface, ![](../graphics/stm_eqn05753.gif), can be a function of temperature only for this model. The evolution of ![](../graphics/stm_eqn05754.gif) is defined by Ziegler's hardening rule, generalized to the nonisothermal case as

![](../graphics/stm_eqn05755.gif)where ![](../graphics/stm_eqn05756.gif) is the hardening parameter (![](../graphics/stm_eqn05756.gif) is the work-hardening slope of the isothermal uniaxial stress-strain response, ![](../graphics/stm_eqn05757.gif), taken at different temperatures) and ![](../graphics/stm_eqn05758.gif) is the rate of change of *C* with respect to time. This form of evolution law for ![](../graphics/stm_eqn05754.gif) defines the rate of ![](../graphics/stm_eqn05754.gif) due to plastic straining to be in the direction of the current radius vector from the center of the yield surface, ![](../graphics/stm_eqn05759.gif), and the rate due to temperature changes to be toward the origin of stress space. The inclusion of the ![](../graphics/stm_eqn05758.gif) term in the evolution of ![](../graphics/stm_eqn05754.gif) ensures that the material response is temperature history independent and, consequently, can be characterized with isothermal data. [Rice (1975)](07s01a01-References.md) writes this concept quite generally as

![](../graphics/stm_eqn05760.gif)The particular identification of ![](../graphics/stm_eqn05761.gif) and ![](../graphics/stm_eqn05762.gif) in [Equation 4.3.5&#8211;6](04s03a107.md) above is assumed, so the material behavior is defined by the isothermal, uniaxial work hardening data, ![](../graphics/stm_eqn05756.gif) only.
### Nonlinear isotropic/kinematic hardening model

This model is based on the work of [Lemaitre and Chaboche (1990)](07s01a01-References.md). The size of the yield surface, ![](../graphics/stm_eqn05763.gif), is defined as a function of equivalent plastic strain, ![](../graphics/stm_eqn05764.gif); temperature, ![](../graphics/stm_eqn01111.gif); and field variables, ![](../graphics/stm_eqn01501.gif). This dependency can be provided directly, can be coded in user subroutine UHARD, or can be modeled with a simple exponential law for materials that either cyclically harden or soften as

![](../graphics/stm_eqn05765.gif)where ![](../graphics/stm_eqn05766.gif) is the yield surface size at zero plastic strain, and ![](../graphics/stm_eqn05767.gif) and ![](../graphics/stm_eqn05768.gif) are additional material parameters that must be calibrated from cyclic test data.

The overall backstress is composed of multiple backstress components, where the evolution of the backstress components of the model is defined as

![](../graphics/stm_eqn05769.gif) and the overall backstress is computed from the relation

![](../graphics/stm_eqn05770.gif)where *N* is the number of backstresses, ![](../graphics/stm_eqn05771.gif) and ![](../graphics/stm_eqn05772.gif) are material parameters, and ![](../graphics/stm_eqn05773.gif) is the rate of change of ![](../graphics/stm_eqn05771.gif) with respect to temperature and field variables. This equation is the basic Ziegler law, generalized to account for temperature and field-variable dependency of ![](../graphics/stm_eqn05771.gif) and to which a "recall" term, ![](../graphics/stm_eqn05774.gif), has been added. The recall term introduces nonlinearity in the evolution law. The rate of change of ![](../graphics/stm_eqn05772.gif) with respect to temperature and field variables is not accounted for in the evolution law for ![](../graphics/stm_eqn05775.gif). Consequently, if ![](../graphics/stm_eqn05772.gif) vary with temperature, the material response predicted by the model will be temperature history dependent. However, it can be shown that this dependency on temperature history is small and fades away with increasing plastic deformation. The condition for complete temperature history independent behavior is to use constant values for ![](../graphics/stm_eqn05772.gif).

The evolution of the backstress and the isotropic hardening are illustrated in [Figure 4.3.5&#8211;1](04s03a107.md) for unidirectional loading and in [Figure 4.3.5&#8211;2](04s03a107.md) for multiaxial loading.

Figure 4.3.5&#8211;1 One-dimensional representation of the nonlinear model.

![](../graphics/chardening-comb-1d-rep.png)

Figure 4.3.5&#8211;2 Three-dimensional representation of the nonlinear model.

![](../graphics/chardening-comb-3d-rep-nls.png) The center of the yield surface is contained within a cylinder of radius ![](../graphics/stm_eqn05776.gif), which follows directly from [Equation 4.3.5&#8211;10](04s03a107.md). Therefore, the yield surface is contained within the limiting surface of radius ![](../graphics/stm_eqn05777.gif), as shown in the figures. This model can be degenerated into the linear kinematic model described above by setting ![](../graphics/stm_eqn05778.gif) and ![](../graphics/stm_eqn05779.gif), for ![](../graphics/stm_eqn05780.gif).

The physical behavior that can be captured by this model, as well as its limitations, is described in detail in the Abaqus Analysis User's Guide.
### Reference

### Reference

"Models for metals subjected to cyclic loading,"  Section 23.2.2 of the Abaqus Analysis User's Guide