# *USER MATERIAL







### *USER MATERIALDefine material constants for use in subroutine `UMAT`, `UMATHT`, or `VUMAT`.

This option is used to input material constants for use in a user-defined mechanical model (user subroutine [`UMAT`](../sub/sub-link.md#sub-xsl-umat) in Abaqus/Standard or user subroutine [`VUMAT`](../sub/sub-link.md#sub-xsl-vumat) in Abaqus/Explicit). In Abaqus/Standard it is also used to input material constants for use in a user-defined thermal material model (user subroutine [`UMATHT`](../sub/sub-link.md#sub-xsl-umatht)).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["User-defined mechanical material behavior," Section 26.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cusermat)
- ["User-defined thermal material behavior," Section 26.7.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cthusermat)
- ["UMAT," Section 1.1.41 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uumat)
- ["UMATHT," Section 1.1.42 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-umatht)
- ["VUMAT," Section 1.2.20 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpmat)

### **Required parameter: **

CONSTANTS

Set this parameter equal to the number of constants being entered.

### **Optional parameters: **

HYBRID FORMULATION

This parameter applies only to Abaqus/Standard analyses.

Set HYBRID FORMULATION=INCREMENTAL (default) to use an incremental Lagrange multiplier–based formulation with hybrid elements.

Set HYBRID FORMULATION=TOTAL to use a total Lagrange multiplier–based formulation with hybrid elements.

Set HYBRID FORMULATION=INCOMPRESSIBLE to define an incompressible material response with hybrid elements.

TYPE

This parameter applies only to Abaqus/Standard analyses.

Set TYPE=MECHANICAL (default) if the constants are used in defining the mechanical behavior of the material.

Set TYPE=THERMAL if the constants are used in defining the thermal constitutive behavior of the material.

If both the user-defined mechanical and the user-defined thermal behavior of the material are being modeled, the [*USER MATERIAL](ch20abk08.md) option should be repeated in the material data block such that each value of the TYPE parameter is used.

UNSYMM

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the material stiffness matrix, ![](../graphics/key_eqn01154.gif), is not symmetric or when a thermal constitutive model is used and ![](../graphics/key_eqn01155.gif) is not symmetric. This parameter causes Abaqus/Standard to use its unsymmetric equation solution procedures.

### **Data lines to define material constants: **

**First line:**

Repeat this data line as often as necessary to define all material constants.




