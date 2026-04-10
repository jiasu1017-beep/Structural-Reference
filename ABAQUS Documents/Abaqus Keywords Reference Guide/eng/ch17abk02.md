# *RADIATION FILE







### *RADIATION FILEDefine results file requests for cavity radiation heat transfer.

This option is used to write cavity radiation variables to the Abaqus/Standard results file.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Optional, mutually exclusive parameters (if not specified, output will be provided for all cavities in the model): **

CAVITY

Set this parameter equal to the name of the cavity for which this output request is being made.

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

SURFACE

Set this parameter equal to the name of the surface for which this output request is being made.

### **Optional parameter: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written to the results file at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

### **Data lines to request results file output: **

**First line:**

Repeat this data line as often as necessary to define the surface variables to be written to the results file for the specified cavity, surface, or element set. If this line is omitted, the default variables will be used.




