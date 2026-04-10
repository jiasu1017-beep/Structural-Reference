# *INCREMENTATION OUTPUT







### *INCREMENTATION OUTPUTDefine output database requests for time incrementation data.

This option is used to write incrementation variables to the output database. It must be used in conjunction with the [*OUTPUT](ch15abk03.md), HISTORY option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **Optional parameter: **

VARIABLE

Set VARIABLE=ALL to indicate that all incrementation variables applicable to this procedure type should be written to the output database.

Set VARIABLE=PRESELECT to indicate that the default incrementation output variables for the current procedure type should be written to the output database. Additional output variables can be requested on the data lines.

If this parameter is omitted, the incrementation variables requested for output must be specified on the data lines.

### **Data lines to request incrementation output: **

**First line:**

Repeat this data line as often as necessary to define the time incrementation variables to be written to the output database.




