# 4.7.2 Permanent set

### 4.7.2 Permanent set

**Products: **Abaqus/Standard  Abaqus/Explicit

Abaqus can be used to model permanent set commonly observed in filled elastomers upon unloading after initial loading.
### Approach used

Abaqus uses isotropic hardening Mises plasticity with an associated flow rule to capture permanent set. Since the underlying material is hyperelastic in nature, plasticity calculations are based on a multiplicative split of the deformation gradient into elastic and plastic components:

![](../graphics/stm_eqn07132.gif)where ![](../graphics/stm_eqn07133.gif) is the elastic part of the deformation gradient, representing the hyperelastic behavior, and ![](../graphics/stm_eqn07134.gif) is the plastic part of the deformation gradient, representing the stress-free intermediate configuration.

The plastic part of the deformation rate tensor based on the associated flow rule of the Mises yield condition is given by

![](../graphics/stm_eqn07135.gif)

In the above equation ![](../graphics/stm_eqn07136.gif) is the deviatoric part of the Kirchoff stress tensor ![](../graphics/stm_eqn07137.gif), ![](../graphics/stm_eqn02389.gif) is the effective Kirchoff stress, and ![](../graphics/stm_eqn07138.gif) is the equivalent plastic strain. The resulting system of equations is solved using standard techniques outlined in [Weber and Anand (1990)](07s01a01-References.md) and [Simo (1992)](07s01a01-References.md).

An application that uses the above mentioned approach can be found in [Govindarajan et al. (2007)](07s01a01-References.md).
### Reference

### Reference

"Permanent set in rubberlike materials,"  Section 23.7.1 of the Abaqus Analysis User's Guide