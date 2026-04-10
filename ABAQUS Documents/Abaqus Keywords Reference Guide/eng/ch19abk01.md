# *TEMPERATURE







### *TEMPERATURESpecify temperature as a predefined field.

This option is used to specify temperature as a predefined field during an analysis.

 To use this option in a restart analysis of Abaqus/Standard, either [*TEMPERATURE](ch19abk01.md) or [*INITIAL CONDITIONS](ch09abk18.md), TYPE=TEMPERATURE must have been specified in the original analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Predefined fields," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields)
- ["UTEMP," Section 1.1.51 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutemp)

### **Optional parameters for using the data line format: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that gives the time variation of the temperature throughout the step (see ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, a linear interpolation is done over the step. 

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

OP

Set OP=MOD (default) for existing [*TEMPERATURE](ch19abk01.md) values to remain, with this option modifying existing temperatures or defining additional temperatures.

Set OP=NEW if all existing [*TEMPERATURE](ch19abk01.md) values should be removed. New temperatures can be defined.

For a general analysis step, a temperature that is removed via OP=NEW is reset to the value given on the [*INITIAL CONDITIONS](ch09abk18.md) option or to zero if no initial temperature was defined. For a linear perturbation step, a temperature that is removed via OP=NEW is always reset to zero. If temperatures are being returned to their initial condition values, the AMPLITUDE parameter described above does not apply. Rather, the AMPLITUDE parameter given on the [*STEP](ch18abk36.md) option governs the behavior in an Abaqus/Standard analysis, and the temperatures are always ramped back to their initial conditions in Abaqus/Explicit analyses. If temperatures are being reset to new values (not to initial conditions) via OP=NEW, the AMPLITUDE parameter described above applies.

### **Required parameter for reading temperatures from the results or output database file: **

FILE

Set this parameter equal to the name of the results or output database file from which the data are read. The file extension is optional; however, if both `.fil` and `.odb` files exist, the results file will be used if the INTERPOLATE parameter is omitted. If the INTERPOLATE parameter is used, an output database file must exist. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. This parameter cannot be used in a [*STATIC](ch18abk31.md), RIKS analysis step.

### **Optional parameters for reading temperatures from the results or output database file: **

ABSOLUTE EXTERIOR TOLERANCE

This parameter is relevant only for use with the INTERPOLATE parameter. Set this parameter equal to the absolute value (given in the units used in the model) by which nodes of the current model may lie outside the region of the model in the output database specified by the FILE parameter. If this parameter is not used or has a value of 0.0, the EXTERIOR TOLERANCE parameter will apply.

EXTERIOR TOLERANCE

This parameter is relevant only for use with the INTERPOLATE parameter. Set this parameter equal to the fraction of the average element size by which nodes of the current model may lie outside the region of the elements of the model in the output database specified by the FILE parameter. The default value is 0.05.

If both tolerance parameters are specified, Abaqus uses the tighter tolerance.

BSTEP

Set this parameter equal to the step number (of the analysis whose results or output database file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus will begin reading temperature data from the first step available on the file read.

BINC

Set this parameter equal to the increment number (of the analysis whose results or output database file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus will begin reading temperature data from the first increment available (excluding any zero increments if the results file was written in Abaqus/Standard using [*FILE FORMAT](ch06abk08.md), ZERO INCREMENT) for step BSTEP on the results or output database file.

ESTEP

Set this parameter equal to the step number (of the analysis whose results or output database file is being used as input to this option) that ends the history data to be read. If no value is supplied, ESTEP is taken as equal to BSTEP.

EINC

Set this parameter equal to the increment number (of the analysis whose results or output database file is being used as input to this option) that ends the history data to be read. If no value is supplied, EINC is taken as the last available increment of step ESTEP on the file read.

BTRAMP

Set this parameter equal to the starting time (measured relative to the total step time period) after which the temperatures read from the results file will be ramped to their initial condition values. The default value is ![](../graphics/key_eqn00237.gif), in which case no temperature ramping takes place. This feature is used to create a cyclic temperature history from a prior heat transfer analysis that is not cyclic.

DRIVING ELSETS

This parameter is relevant only for use with the INTERPOLATE parameter. Include this parameter to indicate that the temperature field is interpolated from a user-specified element set from the previous analysis to a user specified node set in the current job. This parameter is used to eliminate mapping ambiguity in cases where element regions in the previous analysis are close or touching. To accomplish part instance to part instance mapping, define your element and node sets to correspond to the respective instances in the previous and current analysis.

INTERPOLATE

Include this parameter to indicate that the temperature field needs to be interpolated between dissimilar meshes. This feature is used to read temperatures from an output database file generated during a heat transfer analysis or generated during a global model analysis used with the submodeling capability. This parameter and the MIDSIDE parameter are mutually exclusive. If the heat transfer analysis uses first-order elements and the current mesh is the same but uses second-order elements, use the MIDSIDE parameter instead.

MIDSIDE

Include this parameter to indicate that midside node temperatures in second-order elements are to be interpolated from corner node temperatures. This feature is used to read temperatures from a results or an output database file generated during a heat transfer analysis using first-order elements. This parameter and the INTERPOLATE parameter are mutually exclusive.

### **Required parameter for defining data in user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp): **

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to indicate that user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) will be used to define temperature values. [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) will be called for each node given on the data lines. 

If values are also given on the data lines, these values will be ignored. If a results or an output database file has been specified in addition to user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp), values read from this file will be passed into [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) for possible modification.

### **Data lines to define gradients of temperature in beams and shells: **

**First line:**

Repeat this data line as often as necessary to define temperatures at different nodes or node sets.

### **Data lines to define temperatures at temperature points in beams and shells: **

**First line:**

**Subsequent lines (only needed if there are more than seven temperature points in the element):**

If more than seven temperature values are needed at any node, continue on the next line. It may be necessary to leave blank data lines for some nodes if any other node in the model has more than seven temperature points because the total number of temperatures that Abaqus expects to read for any node is based on the maximum number of temperature values of all the nodes in the model. These trailing initial values will be zero and will not be used in the analysis.

Repeat this set of data lines as often as necessary to define temperatures at different nodes or node sets.

### **Data lines to define temperatures for solid or frame elements using the data line format: **

**First line:**

Repeat this data line as often as necessary to prescribe temperature at different nodes or node sets.

### **No data lines are needed if temperatures are read from an Abaqus results or output database file (except when the DRIVING ELSETS parameter is present) and a user subroutine is not used (FILE parameter included, USER parameter omitted). **

### **Data lines to define temperatures using user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) using the data line format (FILE parameter omitted, USER parameter included): **

**First line:**

Repeat this data line as often as necessary. [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) will be called for each node listed.

### **Data lines to define temperatures using user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp) when temperatures are read from an Abaqus results or output database file (FILE and USER parameters included): **

**First line:**

Repeat this data line as often as necessary. The nodes identified on the data lines will be assigned values from the results or output database file; optionally, these values can be modified in user subroutine [`UTEMP`](../sub/sub-link.md#sub-xsl-utemp).

### **Data lines to define temperatures when the FILE, INTERPOLATE, and DRIVING ELSETS parameters are included: **

**First line:**

Repeat this data line as often as necessary. The node set identified on the data lines will be assigned values from the element set in the results (`.fil`) or output database (`.odb`) file.  If a duplicate node is defined on a subsequent data line, it will be removed from the subsequent temperature mapping and printed out to the data (`.dat`) file.




