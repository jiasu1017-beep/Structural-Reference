# *FLUID BEHAVIOR







### *FLUID BEHAVIORDefine fluid behavior for a fluid cavity.

This option is used to define the fluid behavior for a surface-based fluid cavity. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the fluid behavior.

### **Optional parameter: **

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to specify a fluid in which the fluid constitutive model is defined in user subroutine [`UFLUID`](../sub/sub-link.md#sub-xsl-ufluid). 

**There are no data lines associated with this option.**



