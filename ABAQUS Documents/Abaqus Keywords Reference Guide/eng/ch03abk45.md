# *CONNECTOR LOAD







### *CONNECTOR LOADSpecify loads for available components of relative motion in connector elements.

This option is used to apply concentrated forces and moments to the available components of relative motion in connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Connector actuation," Section 31.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectoractuation)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the load during the step.

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step. 

LOAD CASE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the load case number. This parameter is used in [*RANDOM RESPONSE](ch17abk07.md) analysis (["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)), when it is the cross-reference for the load case on the [*CORRELATION](ch03abk77.md) option. The parameter's value is ignored in all other procedures.

OP

Set OP=MOD (default) for existing [*CONNECTOR LOAD](ch03abk45.md)s to remain, with this option modifying existing connector loads or defining additional connector loads.

Set OP=NEW if all existing [*CONNECTOR LOAD](ch03abk45.md)s applied to the model should be removed. New connector loads can be defined.

### **Optional, mutally exclusive parameters for matrix generation and steady-state dynamics analysis (direct, modal, or subspace): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading.

### **Data lines to define connector loads for specific components of relative motion: **

**First line:**

Repeat this data line as often as necessary to define connector loads.




