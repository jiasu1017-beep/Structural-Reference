# *ENERGY OUTPUT







### *ENERGY OUTPUTDefine output database requests for whole model or element set energy data.

This option is used to write whole model or element set energy requests to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **Optional parameters: **

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

VARIABLE

Set VARIABLE=ALL to indicate that all energy variables applicable to this procedure and material type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default energy output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted and no energy variables are specified on the data lines, all energy variables will be written to the output database.

PER ELEMENT SET

This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to indicate that the requested energy variables are written to the output database for each user-defined element set (all internal element sets, including the internal element sets defined in Abaqus/CAE and the internal element sets created during the analysis, are excluded).

PER SECTION

 This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to indicate that the requested energy variables are written to the output database for every user-defined element set that is associated with a section definition  (all internal element sets, including the internal element sets defined in Abaqus/CAE and the internal element sets created during the analysis, are excluded).

### **Data lines to request energy output: **

**First line:**

Repeat this data line as often as necessary to define the energy variables to be written to the output database.




