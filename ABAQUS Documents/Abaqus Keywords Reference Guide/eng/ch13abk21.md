# *MODAL PRINT







### *MODAL PRINTPrint generalized coordinate (modal amplitude) data during a mode-based dynamic procedure.

This option is used during mode-based dynamic procedures to control the printed output of generalized coordinate (modal amplitude and phase) values.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameter: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

### **Data lines to request modal output in the data file: **

**First line:**

Repeat this data line as often as necessary: each line defines a table.




