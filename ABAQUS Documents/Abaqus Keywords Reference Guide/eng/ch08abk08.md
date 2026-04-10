# *HYPOELASTIC







### *HYPOELASTICSpecify hypoelastic material properties.

This option is used to define a nonlinear, small-strain elastic material.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Hypoelastic behavior," Section 22.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chypoelastic)
- ["UHYPEL," Section 1.1.37 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuhypel)

### **Optional parameter: **

USER

Include this parameter if the moduli are defined in user subroutine [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel). Omit this parameter if the moduli are defined on the data lines.

### **Data lines to define hypoelasticity by specifying the material constants directly: **

**First line:**

Repeat this data line as often as necessary to define the variation of the moduli with the strain invariants.

### **To define hypoelasticity by a user subroutine: **

No data lines are used with this option when the USER parameter is specified. Instead, user subroutine [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel) must be used to define the hypoelasticity.




