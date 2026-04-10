# *IMPORT







### *IMPORTImport information from a previous Abaqus/Explicit or Abaqus/Standard analysis.

This option is used to define the time in a previous Abaqus/Standard or Abaqus/Explicit analysis at which the specified node and element information is imported. The [*IMPORT](ch09abk04.md) option must be used in conjunction with the [*INSTANCE](ch09abk19.md) option when importing a part instance from a previous analysis. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part instance  

**Abaqus/CAE: **Supported for use in conjunction with part instances; importing selected part instances stored in an output database is supported using the File menu and importing the initial state of part instances is supported in the Load module.

##### **References:**

- ["Transferring results between Abaqus analyses: overview," Section 9.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-atransferoverview)
- [*INSTANCE](ch09abk19.md)

### **Required parameter: **

UPDATE

Set UPDATE=NO to continue the analysis without resetting the reference configuration. 

Set UPDATE=YES to continue the analysis by resetting the reference configuration to be the imported configuration. In this case displacement and strain values are calculated from the new reference configuration. 

### **Optional, mutually exclusive parameters: **

INCREMENT

When importing an analysis from Abaqus/Standard into Abaqus/Explicit or from one Abaqus/Standard analysis into another Abaqus/Standard analysis, set this parameter equal to the increment of the specified step on the Abaqus/Standard restart file from which the analysis is to be imported. If this parameter is omitted, the analysis is imported from the last available increment of the specified step.

INTERVAL

When importing an analysis from Abaqus/Explicit into Abaqus/Standard  or from one Abaqus/Explicit analysis into another Abaqus/Explicit analysis, set this parameter equal to the interval of the specified step on the Abaqus/Explicit state file from which the analysis is to be imported. If this parameter is omitted, the analysis is imported from the last available interval of the specified step.

ITERATION

This parameter is relevant only when the results are imported from a previous direct cyclic Abaqus/Standard analysis.

When importing an analysis from Abaqus/Standard into Abaqus/Explicit or from one Abaqus/Standard analysis into another Abaqus/Standard analysis, set this parameter equal to the iteration number of the specified step on the Abaqus/Standard restart file from which the analysis is to be imported. Since restart information can be written only at the end of an iteration in a direct cyclic analysis, the INCREMENT parameter is irrelevant and is ignored if the ITERATION parameter is specified. If this parameter is omitted, the analysis is imported from the last available iteration of the specified step.

### **Optional parameters: **

STATE

Set STATE=YES (default) to import the current material state of the elements at the specified step and the specified interval, increment, or iteration.

Set STATE=NO if no material state is to be imported. In this case the elements will start with no initial state or with the state as defined by the [*INITIAL CONDITIONS](ch09abk18.md) option.

STEP

Set this parameter equal to the step on the Abaqus/Explicit state file or on the Abaqus/Standard restart file from which the analysis is being imported. If this parameter is omitted, the analysis is imported from the last available step on the state file or the restart file at the specified increment, interval, or iteration.

### **Data lines to specify element sets to be imported: **

**First line:**

Repeat this data line as often as necessary to define the element sets to be imported. Up to 16 element sets can be listed per data line.

### **There are no data lines for importing a part instance. **




