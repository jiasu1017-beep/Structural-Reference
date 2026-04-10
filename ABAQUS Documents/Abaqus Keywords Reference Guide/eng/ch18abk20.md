# *SLOAD







### *SLOADApply loads to a substructure.

This option is used to activate a substructure load case defined by the [*SUBSTRUCTURE LOAD CASE](ch18abk43.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)
- [*SUBSTRUCTURE LOAD CASE](ch18abk43.md)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name given to an amplitude defined by the [*AMPLITUDE](ch01abk09.md) option (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). This amplitude defines the time variation of the load case ([*SUBSTRUCTURE LOAD CASE](ch18abk43.md)) magnitude throughout the step. If this parameter is omitted, the default amplitude is that defined in ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover), for the particular procedure used in the step.

OP

Set OP=MOD (default) to modify or add to the currently active [*SLOAD](ch18abk20.md)s.

Set OP=NEW if all existing [*SLOAD](ch18abk20.md)s applied to the model should be removed and new ones possibly defined.

### **Data lines to define the loading: **

**First line:**

Repeat this data line as often as necessary to define the loadings on the substructures.




