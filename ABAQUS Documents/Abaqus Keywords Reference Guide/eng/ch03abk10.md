# *CECHARGE







### *CECHARGESpecify concentrated electric charges in piezoelectric analysis.

This option is used to apply electric charge to any node in a piezoelectric model.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Piezoelectric analysis," Section 6.7.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-apiezoelectric)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the electric charge during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*CECHARGE](ch03abk10.md)s to remain, with this option modifying existing electric charges or defining additional electric charges.

Set OP=NEW if all existing [*CECHARGE](ch03abk10.md)s applied to the model should be removed.

### **Optional, mutually exclusive parameters for matrix generation and direct-solution steady-state dynamics analysis: **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the concentrated electric charges.

REAL

Include this parameter (default) to define the real (in-phase) part of the concentrated electric charges.

### **Data lines to define concentrated electric charges: **

**First line:**

Repeat this data line as often as necessary to define concentrated electric charges at various nodes or node sets.




