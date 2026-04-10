# *COMPOSITE MODAL DAMPING







### *COMPOSITE MODAL DAMPINGSpecify composite modal damping for modal analyses based on the SIM architecture.

This option can be used only with the SIM architecture and can be used only with the [*FREQUENCY](ch06abk35.md) option. It specifies the composite modal damping data that enable calculation of the weighted mass and stiffness composite damping per each of the extracted eigenmodes during an eigenvalue extraction analysis. The damping data are requested for the mass proportional fraction of critical damping and for the stiffness proportional fraction of critical damping for specified element sets. This option can also be used to assign critical damping fractions to both mass and stiffness matrix input.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Material damping," Section 26.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdampingopt)
- ["Dynamic analysis procedures: overview," Section 6.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamicproc)

### **Optional parameters: **

MASS MATRIX INPUT

Set this parameter equal to the value of fraction of critical damping for all mass matrices included in the model by using the [*MATRIX INPUT](ch13abk13.md), MATRIX=MASS option. If this parameter is omitted, the default is zero.

STIFFNESS MATRIX INPUT

Set this parameter equal to the value of fraction of critical damping for all stiffness matrices included in the model by using the [*MATRIX INPUT](ch13abk13.md), MATRIX=STIFFNESS option. If this parameter is omitted, the default is zero.

### **Data lines to define a fraction of critical damping: **

**First line:**

Repeat this data line as often as necessary to define modal damping for different elements and/or element sets.




