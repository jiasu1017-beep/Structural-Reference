# *NODE FILE







### *NODE FILEDefine results file requests for nodal data.

This option is used to choose the nodal variables that will be written to the results (`.fil`) file in an Abaqus/Standard analysis or to the selected results (`.sel`) file in an Abaqus/Explicit analysis. In an Abaqus/Explicit analysis it must be used in conjunction with the [*FILE OUTPUT](ch06abk09.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **References:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **Optional parameters: **

FREQUENCY

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the output frequency, in increments. The output will always be written to the results file at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

GLOBAL

This parameter applies only to Abaqus/Standard analyses.

This parameter is relevant only at nodes where the [*TRANSFORM](ch19abk11.md) option has been used to define a local coordinate system.

Set GLOBAL=NO to write vector-valued nodal variables in the local directions.

Set GLOBAL=YES (default) to write vector-valued nodal variables in the global directions. This default is the opposite of the default on the [*NODE PRINT](ch14abk12.md) option and is used because most postprocessors assume that components are given in the global system.

LAST MODE

This parameter applies only to Abaqus/Standard analyses.

This parameter is useful only during eigenvalue extraction for natural frequencies (["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)) and for eigenvalue buckling estimation (["Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling)).

Set this parameter equal to the highest mode number for which output is required.

The default value is LAST MODE=*N*, where *N* is the number of modes extracted. If the MODE parameter is used, the default value is LAST MODE=*M*, where *M* is the value of the MODE parameter.

MODE

This parameter applies only to Abaqus/Standard analyses.

This parameter is useful only during eigenvalue extraction for natural frequencies and for eigenvalue buckling estimation. Set this parameter equal to the first mode number for which output is required. The default is MODE=1. See also the LAST MODE parameter. When performing a [*FREQUENCY](ch06abk35.md) analysis, the normalization will follow the format set by the NORMALIZATION parameter. Otherwise, the normalization is such that the largest displacement component in the mode has a magnitude of 1.0.

NSET

Set this parameter equal to the name of the node set for which the output is being written to the results file. If this parameter is omitted, the output will be written for all nodes in the model.

### **Data lines to request nodal output in the results or selected results file: **

**First line:**

Repeat this data line as often as necessary to define the nodal variables to be written to the results or selected results file.




