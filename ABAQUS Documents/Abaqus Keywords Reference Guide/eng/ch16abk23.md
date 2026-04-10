# *POST OUTPUT







### *POST OUTPUTPostprocess for output from the restart file.

This option can be used only for postprocessing to recover additional printed (`.dat`), output database (`.odb`), and results file (`.fil`) output from the restart file of a previous analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Model  

##### **References:**

- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)
- ["Restarting an analysis," Section 9.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arestart)

### **Required parameter: **

STEP

Set this parameter equal to the step number from which output is required.

### **Optional parameters: **

CYCLE

This parameter applies only to postprocessing a low-cycle fatigue analysis (see ["Low-cycle fatigue analysis using the direct cyclic approach," Section 6.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adirectcyclicfatigue)). 

Set this parameter equal to the cycle number in a low-cycle fatigue analysis from which additional output is being requested.

ITERATION

This parameter applies only to postprocessing a direct cyclic analysis (see ["Direct cyclic analysis," Section 6.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adirectcyclic)). 

Set this parameter equal to the iteration number in a direct cyclic analysis from which additional output is being requested.

### **Data lines to request output from specified increments if both the ITERATION and the CYCLE parameters are omitted: **

**First line:**

Repeat this data line as often as necessary to define the increments at which output is required.

### **To recover additional output from a previous direct cyclic analysis when the ITERATION parameter is included: **

No data lines are needed when the ITERATION parameter is specified.

### **To recover additional output from a previous low-cycle fatigue analysis when the CYCLE parameter is included: **

No data lines are needed when the CYCLE parameter is specified.




