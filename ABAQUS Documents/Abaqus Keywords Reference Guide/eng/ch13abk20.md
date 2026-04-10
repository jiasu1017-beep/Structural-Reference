# *MODAL OUTPUT







### *MODAL OUTPUTWrite generalized coordinate (modal amplitude) data to the output database during a mode-based dynamic or complex eigenvalue extraction procedure.

This option is used during a mode-based dynamic or complex eigenvalue extraction procedure to write generalized coordinate (modal amplitude and phase) values to the Abaqus/Standard output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **Optional parameter: **

VARIABLE

Set VARIABLE=ALL to indicate that all modal variables applicable to this procedure and material type should be written to the output database.

If this parameter is omitted, the modal variables requested for output must be specified on the data lines.

### **Data lines to request modal output: **

**First line:**

Repeat this data line as often as necessary to define the modal variables to be written to the output database.




