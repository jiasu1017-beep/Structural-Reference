# *SOLVER CONTROLS







### *SOLVER CONTROLSSpecify controls for the iterative and direct linear solvers.

This option is used to set the control parameters for both the direct and iterative linear equation solvers.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Direct linear equation solver," Section 6.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asolveroverview)
- ["Iterative linear equation solver," Section 6.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aitrsolveroverview)

### **Optional parameters: **

CONSTRAINT OPTIMIZATION

Include this parameter to optimize the handling of hard contact and compressibility constraints associated with hybrid elements.

RESET

Include this parameter to reset all of the iterative solver controls to their default values. The option should have no data lines when this parameter is used.

If this parameter is omitted, only the iterative solver specified controls will be changed in the current step; the other controls will remain at their settings from previous steps.

### **Data line to define control parameters for the iterative solver: **

**First (and only) line:**




