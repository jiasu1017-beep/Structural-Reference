# *NODE PRINT







### *NODE PRINTDefine print requests for nodal variables.

This option is used to provide tabular printed output of nodal variables (displacements, reaction forces, etc.) in the data file.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

GLOBAL

This parameter is relevant only at nodes where the [*TRANSFORM](ch19abk11.md) option has been used to define a local coordinate system.

Set GLOBAL=NO (default) to obtain printout of vector-valued nodal variables in the local directions.

Set GLOBAL=YES to obtain printout of vector-valued nodal variables in the global directions.

LAST MODE

This parameter is useful only during eigenvalue extraction for natural frequencies (["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)), complex eigenvalue extraction (["Complex eigenvalue extraction," Section 6.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acomplexfreqextract)), and eigenvalue buckling estimation (["Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling)). Set this parameter equal to the highest mode number for which output is required.

The default value is LAST MODE=*N*, where *N* is the number of modes extracted. If the MODE parameter is used, the default value is LAST MODE=*M*, where *M* is the value of the MODE parameter.

MODE

This parameter is useful only during natural frequency extraction, complex eigenvalue extraction, and eigenvalue buckling estimation. Set this parameter equal to the first mode number for which output is required. The default is MODE=1. See also the LAST MODE parameter. When performing a [*FREQUENCY](ch06abk35.md) analysis, the normalization will follow the format set by the NORMALIZATION parameter. Otherwise, the normalization is such that the largest displacement component in the mode has a magnitude of 1.0.

NSET

Set this parameter equal to the name of the node set for which this output request is being made. If this parameter is omitted, the output will be printed for all of the nodes in the model.

SUMMARY

Set SUMMARY=YES (default) to obtain a summary and the locations of the maximum and minimum values in each column of the table. Set SUMMARY=NO to suppress this summary.

TOTALS

Set TOTALS=YES to print the total of each column in the table. This is useful, for example, to sum reaction forces in a particular direction. The default is TOTALS=NO.

### **Data lines to request nodal output in the data file: **

**First line:**

Repeat this data line as often as necessary: each line defines a table. If this line is omitted, no nodal output will be printed to the data file.




