# *INTEGRATED OUTPUT







### *INTEGRATED OUTPUTSpecify variables integrated over a surface to be written to the output database.

This option is used to write integrated quantities over a surface, such as the total force transmitted across a surface, to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- ["Integrated output section definition," Section 2.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aintegratedoutputsect)
- [*OUTPUT](ch15abk03.md)
- [*SURFACE](ch18abk47.md)
- [*INTEGRATED OUTPUT SECTION](ch09abk21.md)

### **Required, mutually exclusive parameters: **

SECTION

Set this parameter equal to the name of the [*INTEGRATED OUTPUT SECTION](ch09abk21.md) (see ["Integrated output section definition," Section 2.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aintegratedoutputsect)) over which this output request is being made.

SURFACE

Set this parameter equal to the name of the surface (see ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)) over which this output request is being made.

ELSET

Set this parameter equal to the name of the element set over which this output request is being made.

### **Optional parameter: **

VARIABLE

Set VARIABLE=ALL to indicate that all integrated output variables applicable to this procedure should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default integrated output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the integrated output variables for output must be specified on the data line.

### **Data lines to request integrated output: **

**First line:**

Repeat this data line as often as necessary to define the list of variables to be written to the output database.




