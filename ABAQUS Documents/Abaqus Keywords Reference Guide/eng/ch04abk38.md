# *DSECHARGE







### *DSECHARGEInput distributed electric surface charges for piezoelectric analysis.

This option is used to input distributed electric surface charges on a surface underlying piezoelectric elements.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Piezoelectric analysis," Section 6.7.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-apiezoelectric)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the distributed electric charge during the step. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*DSECHARGE](ch04abk38.md)s to remain, with this option defining electric charges to be added or modified. Set OP=NEW if all existing [*DSECHARGE](ch04abk38.md)s applied to the model should be removed.

### **Optional, mutually exclusive parameters for matrix generation and direct-solution, steady-state dynamics analysis: **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define distributed electric charges: **

**First line:**

Repeat this data line as often as necessary to define distributed electric charges for various surfaces.




