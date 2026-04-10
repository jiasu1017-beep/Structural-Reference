# *MAGNETOSTATIC







### *MAGNETOSTATICMagnetostatic analysis.

This option is used to indicate that the step should be analyzed as a magnetostatic load step.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Electromagnetic analysis procedures," Section 6.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aelectricproc)
- ["Magnetostatic analysis," Section 6.7.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amagnetostatic)

### **Optional parameter: **

DIRECT

This parameter selects direct user control of the incrementation through the step. If this parameter is used, constant increments of the size defined on the data line are used. If it is omitted, Abaqus will choose the increments (after trying the user's initial time increment for the first attempt at the first increment).

STABILIZATION

Include this parameter to activate the stabilization scheme that may be needed in some situations to obtain a magnetostatic solution.  It defines a factor that is used by Abaqus in the stabilization computations. If this parameter is included without a value, the default value is assumed to be 1.0. The parameter may be set to a higher value to increase the stabilization or to a lower value to decrease it.

### **Data line for a magnetostatic analysis: **

**First (and only) line:**




