# *ELECTROMAGNETIC







### *ELECTROMAGNETICElectromagnetic response.

This option is used to calculate the low-frequency electromagnetic response of a system.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Electromagnetic analysis procedures," Section 6.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aelectricproc)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)

### **Required parameter: **

LOW FREQUENCY

Include this parameter to specify that the electromagnetic response is calculated based on the standard low-frequency assumption of neglecting the effects of displacement currents in Maxwell's equations.

### **One of the following mutually exclusive parameters is required: **

TIME HARMONIC

Include this parameter to calculate the time harmonic linear electromagnetic response of the system subjected to harmonic excitation.

TRANSIENT

Include this parameter to calculate the transient electromagnetic response of the system.

### **Optional parameters: **

DIRECT

This parameter can be used only with the TRANSIENT parameter to select direct user control of the incrementation through the step. If this parameter is used, constant increments of the size defined by the first item on the data line are used. If this parameter is omitted, Abaqus/Standard will choose the increments (after trying the user's initial time increment for the first attempt at the first increment).

STABILIZATION

Include this parameter to activate the stabilization scheme that may be needed in some situations to obtain an electromagnetic solution.  It defines a factor that is used by Abaqus in the stabilization computations. If this parameter is included without a value, the default value is assumed to be 1.0. The parameter may be set to a higher value to increase the stabilization or to a lower value to decrease it.

### **Data lines to define an electromagnetic analysis if the TIME HARMONIC parameter is included: **

**First line:**

Repeat this data line as often as necessary to define frequency ranges in which results are required.

### **Data lines to define an electromagnetic analysis if the TRANSIENT parameter is included: **

**First (and only) line:**




