# 6.1 Enhancements to parallel rheological framework







**Products: **Abaqus/Standard  Abaqus/Explicit  

**Benefits: **You can now use the power law creep model or a user-defined creep model that includes pressure and total deformation dependency to define the viscous response in the viscoelastic network. In the equilibrium network, the response that includes plasticity with combined isotropic and kinematic hardening can now be defined. The implementation of nonlinear kinematic hardening will be most beneficial for applications that include cycling loading. In addition, transferring results between various Abaqus analyses is now supported for models defined using the parallel rheological framework.

**Description: **The viscous response in the viscoelastic network can be defined using a new, power law creep model that includes pressure dependency. In addition, a user-defined creep model can include dependency on pressure and total deformation through appropriate invariants. In Abaqus/Standard the equilibrium network response has been enhanced and can include plasticity with combined isotropic and nonlinear kinematic hardening. The implementation of the nonlinear kinematic hardening is based on the Armstrong-Frederick model and allows multiple backstresses to be specified. Finally, the import capability for material models defined using a parallel rheological framework is now fully supported.
**References: **

**Abaqus Analysis User's Guide**
- ["Transferring results between Abaqus analyses: overview," Section 9.2.1](../usb/usb-link.md#usb-anl-atransferoverview)
- ["Parallel rheological framework," Section 22.8.2](../usb/usb-link.md#usb-mat-cnonlinvisco)

**Abaqus Keywords Reference Guide**
- [*VISCOELASTIC](../key/key-link.md#usb-kws-mviscoelast)

**Abaqus User Subroutines Reference Guide**
- ["UCREEPNETWORK," Section 1.1.23](../sub/sub-link.md#sub-rtn-uucreepnetwork)

**Abaqus Verification Guide**
- ["Transferring results with parallel rheological framework," Section 3.14.20](../ver/ver-link.md#ver-prc-import-prf)




