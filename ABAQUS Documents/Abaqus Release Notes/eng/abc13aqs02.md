# 13.2 VUCHARLENGTH: User subroutine to define the characteristic element length at a material point







### 13.2 [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength): User subroutine to define the characteristic element length at a material point

**Product: **Abaqus/Explicit  

**Benefits: **You can now use user subroutine [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) to define the characteristic element length as a function of element topology, nodal and material point coordinates, and material orientation.

**Description: **The characteristic element length defined in user subroutine [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) is used by Abaqus in regularization schemes needed to mitigate mesh dependency in constitutive models that include strain softening. It can be used with the built-in Abaqus material models as well as with user subroutine–based material models.
**References: **

**Abaqus Keywords Reference Guide**
- [*CHARACTERISTIC LENGTH](../key/key-link.md#usb-kws-mcharacteristiclength)

**Abaqus User Subroutines Reference Guide**
- ["VUCHARLENGTH," Section 1.2.11](../sub/sub-link.md#sub-rtn-uexpucharlength)

**Abaqus Verification Guide**
- ["`VUCHARLENGTH`," Section 4.1.32](../ver/ver-link.md#ver-sub-vucharlength)




