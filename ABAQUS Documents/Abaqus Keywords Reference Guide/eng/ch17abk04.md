# *RADIATION PRINT







### *RADIATION PRINTDefine print requests for cavity radiation heat transfer.

This option is used to print tabular output of cavity radiation variables (radiation fluxes, view factor totals, and facet temperatures).

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

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

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

SUMMARY

Set SUMMARY=YES (default) to obtain a summary of the maximum and minimum values in each column of the table and their locations. 

Set SUMMARY=NO to suppress this summary.

TOTALS

Set TOTALS=YES to print the total of each column in the table. This is useful, for example, to sum radiation fluxes over all facets composing a radiation surface. The default is TOTALS=NO.

### **Data lines to request printed output: **

**First line:**

Repeat this data line as often as necessary: each line defines a table (or more than one table if the request is for a cavity made up of more than one surface). If this line is omitted, the default variables will be used.




