# 6.5 New hybrid formulations for user-defined material behavior







**Product: **Abaqus/Standard  

**Benefits: **You can now define almost incompressible and fully incompressible nonlinear elastic material behavior with hybrid elements through user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat).

**Description: **The default formulation used by Abaqus when a user material is used to define the response of a hybrid element is suitable for material models that use an incremental formulation (for example, metal plasticity) but is not consistent with the total formulation that is commonly used for hyperelastic materials. In the latter situation the default formulation may lead to convergence problems. Such convergence problems may be observed, for example, when an almost incompressible nonlinear elastic user material is subjected to large deformations. Abaqus/Standard now provides an alternate total formulation for such situations. This formulation is consistent with the native almost incompressible formulation used by Abaqus for hyperelastic materials and works better than the default formulation in these situations. Abaqus/Standard also provides, for the first time, the capability to define a fully incompressible response through user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat). The total hybrid formulation can be implemented with minimal changes to an existing [`UMAT`](../sub/sub-link.md#sub-xsl-umat). For fully incompressible materials user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat) needs to define the deviatoric part of the material response only.
**References: **

**Abaqus Analysis User's Guide**
- ["User-defined mechanical material behavior," Section 26.7.1](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus User Subroutines Reference Guide**
- ["UMAT," Section 1.1.41](../sub/sub-link.md#sub-rtn-uumat)

**Abaqus Verification Guide**
- ["`UMAT` and `UHYPER`," Section 4.1.21](../ver/ver-link.md#ver-sub-umatuhyper)




