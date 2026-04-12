# 8.1 Initial conditions on damage initiation







**Products: **Abaqus/Standard  Abaqus/Explicit  

**Benefits: **You can now define initial conditions directly on the damage initiation measures for the ductile, shear, and the Mschenborn and Sonne forming limit diagram based damage initiation criteria.

**Description: **This capability is particularly useful in situations where a metal forming operation is carried out in one analysis, which is followed by a separate analysis that subjects the formed metal part to further deformation. The damage initiation measures at the end of the first analysis can be directly specified as initial conditions for the second analysis. An alternate but approximate way of modeling initial conditions on damage initiation is by specifying initial values of the equivalent plastic strain. Abaqus computes damage initiation measures based on the specified initial equivalent plastic strain, assuming a linear strain path between the initial (undeformed) state and the final (deformed) state. This approximation does not work well for deformation paths that deviate significantly from linearity in the strain space.
**References: **

**Abaqus Analysis User's Guide**
- ["Initial conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.2.1](../usb/usb-link.md#usb-prc-pinitialcond)

**Abaqus Keywords Reference Guide**
- [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond)

**Abaqus Verification Guide**
- ["Progressive damage and failure of ductile metals," Section 2.2.21](../ver/ver-link.md#ver-mat-damage)




