# *SOLUTION TECHNIQUE







### *SOLUTION TECHNIQUESpecify alternative solution methods.

This option is used to specify the quasi-Newton method instead of the standard Newton method for solving nonlinear equations or to specify a separated solution scheme for coupled temperature-displacement and coupled thermal-electrical procedures.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Fully coupled thermal-stress analysis," Section 6.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acouptempdisp)
- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)
- ["Convergence criteria for nonlinear problems," Section 7.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergcriteria)

### **Required parameter: **

TYPE

Set TYPE=QUASI-NEWTON to specify a quasi-Newton solution method. 

Set TYPE=SEPARATED to specify that linearized equations for the individual fields in a fully coupled procedure are to be decoupled and solved separately for each field. This option can be specified only with the [*COUPLED THERMAL-ELECTRICAL](ch03abk82.md) procedure and the [*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md) procedure without the ELECTRICAL parameter.

### **Optional parameter: **

REFORM KERNEL

This parameter can be used only with TYPE=QUASI-NEWTON. Set this parameter equal to the number of quasi-Newton iterations allowed before the kernel matrix is reformed. The default is REFORM KERNEL=8.

**There are no data lines associated with this option.**



