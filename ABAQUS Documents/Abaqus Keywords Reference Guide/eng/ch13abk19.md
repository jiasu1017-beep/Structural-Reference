# *MODAL FILE







### *MODAL FILEWrite generalized coordinate (modal amplitude) data or eigendata to the results file during a mode-based dynamic or eigenvalue extraction procedure.

This option is used during mode-based dynamic or eigenvalue extraction procedures to control the writing of generalized coordinate (modal amplitude and phase) values or eigendata to the Abaqus/Standard results file.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameter: **

FREQUENCY

This parameter is valid only in mode-based dynamic procedures.

Set this parameter equal to the output frequency, in increments. The output will always be written to the results file at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

### **Data lines to request modal output in the results file during mode-based dynamic procedures: **

**First line:**

Repeat this data line as often as necessary.

### **To write eigendata during an eigenvalue extraction procedure: **

No data lines are required; the eigendata are written automatically.




