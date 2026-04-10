# *RADIATION OUTPUT







### *RADIATION OUTPUTDefine output database requests for cavity radiation variables.

This option is used to write cavity radiation variables to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **Optional, mutually exclusive parameters (if not specified, output will be provided for all cavities in the model): **

CAVITY

Set this parameter equal to the name of the cavity for which this output request is being made.

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

SURFACE

Set this parameter equal to the name of the surface for which this output request is being made.

### **Optional parameter: **

VARIABLE

Set VARIABLE=ALL to indicate that all cavity radiation variables applicable to this procedure and material type should be written to the output database.

If this parameter is omitted, the cavity radiation variables requested for output must be specified on the data lines.

### **Data lines to request cavity radiation output: **

**First line:**

Repeat this data line as often as necessary to define the cavity radiation variables to be written to the output database.




