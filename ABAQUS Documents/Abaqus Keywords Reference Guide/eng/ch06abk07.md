# *FIELD







### *FIELDSpecify predefined field variable values.

This option is used to specify values for predefined field variables used in the analysis. To use this option in a restart analysis of Abaqus/Standard, either [*FIELD](ch06abk07.md) or [*INITIAL CONDITIONS](ch09abk18.md), TYPE=FIELD must have been specified in the original analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Predefined fields," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields)
- ["UFIELD," Section 1.1.32 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uufield)
- ["VUFIELD," Section 1.2.14 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpfield)

### **Optional parameter: **

VARIABLE

Set this parameter equal to the field variable number. The user must number the field variables consecutively from 1. The default is VARIABLE=1 unless the NUMBER parameter is used. The VARIABLE and NUMBER parameters are mutually exclusive.

### **Optional parameters for using the data line format: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that gives the time variation of the field variable throughout the step (see ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied linearly over the step.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

OP

Set OP=MOD (default) for existing [*FIELD](ch06abk07.md) variable values to remain, with this option modifying existing values or defining additional values.

Set OP=NEW if all existing [*FIELD](ch06abk07.md) variable values should be removed. New field variable values can be defined.

For a general analysis step, a field variable that is removed via OP=NEW is reset to the value given on the [*INITIAL CONDITIONS](ch09abk18.md) option or to zero if no initial field was defined. For a linear perturbation step, a field variable that is removed via OP=NEW is always reset to zero. If a field variable is being returned to its initial condition values, the AMPLITUDE parameter described above does not apply. Rather, the AMPLITUDE parameter given on the [*STEP](ch18abk36.md) option governs the behavior in an Abaqus/Standard analysis. The default is to linearly ramp the field variable back to its initial conditions. In an Abaqus/Explicit analysis the field variable is always linearly ramped back to its initial conditions. If the field variable is being reset to a new value (not to its initial condition) via OP=NEW, the AMPLITUDE parameter described above applies.

### **Required parameter for reading predefined field variable values from the results or output database file: **

FILE

Set this parameter equal to the name of the results (`.fil`) or output database  (`.odb`) file from which the data are read. The file extension is optional; however, if both `.fil` and `.odb` files exist, the results file will be used if the INTERPOLATE parameter is omitted. If the INTERPOLATE parameter is used, an output database file must exist. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

This parameter cannot be used in a [*STATIC](ch18abk31.md), RIKS analysis step. 

### **Optional parameters for reading predefined field variable values from the results or output database file: **

BSTEP

Set this parameter equal to the step number (of the analysis whose results file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus will begin reading field variable data from the first step available on the file read.

BINC

Set this parameter equal to the increment number (of the analysis whose results or output database file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus will begin reading field variable data from the first increment available (excluding any zero increments if the results file was written in Abaqus/Standard using [*FILE FORMAT](ch06abk08.md), ZERO INCREMENT) for step BSTEP on the results or output database file.

ESTEP

Set this parameter equal to the step number (of the analysis whose results or output database file is being used as input to this option) that ends the history data to be read. If no value is supplied, ESTEP is taken as equal to BSTEP.

EINC

Set this parameter equal to the increment number (of the analysis whose results or output database file is being used as input to this option) that ends the history data to be read. If no value is supplied, EINC is taken as the last available increment of step ESTEP on the results file.

### **Required parameter for reading predefined field variable values from the output database file: **

OUTPUT VARIABLE

Set this variable equal to the scalar nodal output variable that will be read from an output database and used to initialize a specified predefined field. For a list of scalar nodal output variables that can be used to initialize a predefined field, see ["Predefined fields," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields). 

### **Optional parameter for reading predefined field variable values from the output database file: **

INTERPOLATE

Include this parameter to indicate that the scalar nodal output variable (specified by the OUTPUT VARIABLE parameter) being read into a predefined field needs to be interpolated between dissimilar meshes. This feature is used to read nodal values from an output database file generated during a previous Abaqus analysis.

### **Required parameter for defining data in user subroutine [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) or [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield): **

USER

Include this parameter to indicate that user subroutine [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) or [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield) will be used to define field variable values. For an Abaqus/Standard analysis [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) is called for each node given on the data lines. For an Abaqus/Explicit analysis [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield) is called for each field variable or for a set of field variables when the NUMBER parameter is used.

If values are also given on the data lines, these values will be ignored. If a results file has been specified in addition to the user subroutine, values read from the results file will be passed into the user subroutine for possible modification.

### **Optional parameters for defining data in user subroutine [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) or [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield): **

NUMBER

This parameter permits multiple (possibly all) field variables to be updated simultaneously in user subroutine [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) or [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield); for example, because they are interdependent. Set this parameter equal to the number of field variables to be updated simultaneously at a point. The NUMBER and VARIABLE parameters are mutually exclusive.

BLOCKING

This parameter applies only to Abaqus/Explicit analyses. It is related to the `NBLOCK` variable used in the user subroutine argument list.

Set BLOCKING=YES to enable blocking for a given node set. The blocking size will be set to a predefined value in Abaqus/Explicit.

Set BLOCKING=NO (default) to disable blocking.

Use BLOCKING=*n* to specify the blocking size.

### **Data lines to define gradients of a predefined field variable in beams and shells: **

**First line:**

Repeat this data line as often as necessary to define a field variable at different nodes or node sets.

### **Data lines to define a predefined field variable at temperature points in beams and shells: **

**First line:**

**Subsequent lines (only needed if there are more than seven temperature points in the element):**

Repeat this set of data lines as often as necessary to define a field variable at different nodes or node sets.

### **Data lines to define a predefined field variable for solid elements using the data line format: **

**First line:**

Repeat this data line as often as necessary to define a field variable at different nodes or node sets.

### **To read values of a field variable from an Abaqus/Standard results or output database file: **

No data lines are used when field variable data are read from a results or output database file.

### **Data lines to define a field variable using user subroutine [`UFIELD`](../sub/sub-link.md#sub-xsl-ufield) or [`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield): **

**First line:**

Repeat this data line as often as necessary.




