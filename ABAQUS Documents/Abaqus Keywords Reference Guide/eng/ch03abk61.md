# *CONTACT FILE







### *CONTACT FILEDefine results file requests for contact variables.

This option is used to control writing contact variables (for contact surface pairs) to the Abaqus/Standard results (`.fil`) file.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

MASTER

Set this parameter equal to the name of the master surface for which this output request is being made. 

NSET

Set this parameter equal to the name of the node set for which this output request is being made.

SLAVE

Set this parameter equal to the name of the slave surface for which this output request is being made.

### **Data lines to request contact variable output in the results file: **

**First line:**

Repeat this data line as often as necessary to define the list of variables to be written. If this line is omitted, the default variables will be output.




