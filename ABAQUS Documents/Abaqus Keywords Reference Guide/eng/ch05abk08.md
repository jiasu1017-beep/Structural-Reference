# *ELEMENT MATRIX OUTPUT







### *ELEMENT MATRIX OUTPUTWrite element stiffness matrices and mass matrices to a file.

This option is used to write element stiffness matrices and, if available, mass matrices to the results file, a user-defined file, or the data file.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set for which this output request is being made.

### **Optional parameters: **

DLOAD

Set DLOAD=YES to write the load vector from distributed loads on the element. The default is DLOAD=NO.

FILE NAME

This parameter can be used only with the parameter OUTPUT FILE=USER DEFINED. It is used to specify the name of the file (without extension) to which the data will be written. The extension `.mtx` will be added to the file name provided by the user; see ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is not included when OUTPUT FILE=USER DEFINED is specified, the output will be written to the data file.

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

MASS

Set MASS=YES to write the mass matrix. The default is MASS=NO.

OUTPUT FILE

Set OUTPUT FILE=RESULTS FILE (default) for the data to be written to the regular results file in the format specified in ["Results file output format," Section 5.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-fformat).

Set OUTPUT FILE=USER DEFINED for the results to be written to a user-specified file in the format of the [*USER ELEMENT](ch20abk07.md), LINEAR option (["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)). The name of the file is specified using the FILE NAME parameter.

STIFFNESS

Set STIFFNESS=YES to write the stiffness matrix (or the operator matrix for heat transfer elements). The default is STIFFNESS=NO.

**There are no data lines associated with this option.**



