# *PRESSURE STRESS







### *PRESSURE STRESSSpecify equivalent pressure stress as a predefined field for a mass diffusion analysis.

This option can be used only in a [*MASS DIFFUSION](ch13abk06.md) analysis to specify pressure as a predefined field. The user defines equivalent pressure stresses at the nodes, and Abaqus/Standard interpolates the pressure to the material points.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Mass diffusion analysis," Section 6.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassdiffusion)
- ["Predefined fields," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields)

### **Optional parameters for using the data line format: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that gives the time variation of the pressure throughout the step. If the AMPLITUDE parameter is omitted, the reference magnitude is applied either immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

OP

Set OP=MOD (default) for existing [*PRESSURE STRESS](ch16abk28.md) values to remain, with this option modifying existing values or defining additional values.

Set OP=NEW if all existing [*PRESSURE STRESS](ch16abk28.md) values should be removed. New pressure stress values can be defined.

For a general analysis step, a pressure that is removed via OP=NEW is reset to the value given on the [*INITIAL CONDITIONS](ch09abk18.md) option or to zero if no initial pressure was defined. For a linear perturbation step, a pressure that is removed via OP=NEW is always reset to zero. If pressures are being returned to their initial condition values, the AMPLITUDE parameter described above does not apply. Rather, the AMPLITUDE parameter given on the [*STEP](ch18abk36.md) option governs the behavior. If pressures are being reset to new values (not to initial conditions) via OP=NEW, the AMPLITUDE parameter described above applies.

### **Required parameter for reading equivalent pressure stresses from the results file: **

FILE

Set this parameter equal to the name of the results file (including the optional `.fil` extension) from which the data are read. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

### **Optional parameters for reading equivalent pressure stresses from the results file: **

BSTEP

Set this parameter equal to the step number (of the analysis whose results file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus/Standard will begin reading pressure data from the first step available on the results file.

BINC

Set this parameter equal to the increment number (of the analysis whose results file is being used as input to this option) that begins the history data to be read. If no value is supplied, Abaqus/Standard will begin reading pressure data from the first increment available (excluding any zero increments) for step BSTEP on the results file.

ESTEP

Set this parameter equal to the step number (of the analysis whose results file is being used as input to this option) that ends the history data to be read. If no value is supplied, ESTEP is taken as equal to BSTEP.

EINC

Set this parameter equal to the increment number (of the analysis whose results file is being used as input to this option) that ends the history data to be read. If no value is supplied, EINC is taken as the last available increment of step ESTEP on the results file.

### **Required parameter for defining data in user subroutine [`UPRESS`](../sub/sub-link.md#sub-xsl-upress): **

USER

Include this parameter to indicate that user subroutine [`UPRESS`](../sub/sub-link.md#sub-xsl-upress) will be used to define equivalent pressure stress values. [`UPRESS`](../sub/sub-link.md#sub-xsl-upress) will be called for each node given on the data lines. If values are also given on the data lines, these values will be ignored. If a results file has been specified in addition to user subroutine [`UPRESS`](../sub/sub-link.md#sub-xsl-upress), values read from the results file will be passed into [`UPRESS`](../sub/sub-link.md#sub-xsl-upress) for possible modification.

### **Data lines to define pressures using the data line format: **

**First line:**

Repeat this line as often as necessary to define the pressure at different nodes or node sets.

### **To read pressures from an Abaqus/Standard results file (FILE): **

No data lines are used when pressure data are read from a results file.

### **Data lines to define equivalent pressure stresses using user subroutine [`UPRESS`](../sub/sub-link.md#sub-xsl-upress): **

**First line:**

Repeat this line as often as necessary. [`UPRESS`](../sub/sub-link.md#sub-xsl-upress) will be called for each node listed.




