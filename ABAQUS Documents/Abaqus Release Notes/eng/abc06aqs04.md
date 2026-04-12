# 6.4 User-defined frequency domain viscoelastic behavior







**Product: **Abaqus/Standard  

**Benefits: **You can now define frequency domain viscoelastic behavior through user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat).

**Description: **Viscoelastic behavior in the frequency domain requires specification of a storage modulus (material stiffness) and a loss modulus (material damping). The [`UMAT`](../sub/sub-link.md#sub-xsl-umat) interface and implementation has been enhanced to support the specification of both material stiffness and material damping. This feature allows you to define viscoelastic response with a complex frequency dependence, which is not supported by the built-in models in Abaqus/Standard.
**References: **

**Abaqus Analysis User's Guide**
- ["User-defined mechanical material behavior," Section 26.7.1](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus User Subroutines Reference Guide**
- ["UMAT," Section 1.1.41](../sub/sub-link.md#sub-rtn-uumat)

**Abaqus Verification Guide**
- ["`UMAT` and `UHYPER`," Section 4.1.21](../ver/ver-link.md#ver-sub-umatuhyper)




