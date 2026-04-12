# 13.3 Enhancements to user subroutine UMAT







### 13.3 Enhancements to user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat)

**Product: **Abaqus/Explicit  

**Benefits: **You can now use user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat) to define the damping part of the material response for frequency-domain viscoelastic material behavior, to define almost incompressible nonlinear elastic response for hybrid elements using a total hybrid formulation, and to fully incompressible nonlinear elastic response for hybrid elements.

**Description: **Viscoelastic behavior in the frequency domain requires specification of a storage modulus (material stiffness) and a loss modulus (material damping). The [`UMAT`](../sub/sub-link.md#sub-xsl-umat) interface and implementation has been enhanced to support the specification of both material stiffness and material damping. This feature allows you to define viscoelastic response with a complex frequency dependence that is not supported by the built-in models in Abaqus/Standard.

The default formulation used by Abaqus when a user material is used to define the response of a hybrid element is suitable for material models that use an incremental formulation (for example, metal plasticity) but is not consistent with the total formulation that is commonly used for hyperelastic materials. In the latter situation the default formulation may lead to convergence problems. Such convergence problems may be observed, for example, when an almost incompressible nonlinear elastic user material is subjected to large deformations. Abaqus/Standard now provides an alternate total formulation for such situations. This formulation is consistent with the native almost incompressible formulation used by Abaqus for hyperelastic materials and works better than the default formulation in these situations. Abaqus/Standard also provides, for the first time, the capability to define a fully incompressible response (for hybrid elements) through user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat). The total hybrid formulation can be implemented with minimal changes to an existing [`UMAT`](../sub/sub-link.md#sub-xsl-umat). For fully incompressible materials, the [`UMAT`](../sub/sub-link.md#sub-xsl-umat) needs to define the deviatoric part of the material response only.
**References: **

**Abaqus Keywords Reference Guide**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus User Subroutines Reference Guide**
- ["UMAT," Section 1.1.41](../sub/sub-link.md#sub-rtn-uumat)




