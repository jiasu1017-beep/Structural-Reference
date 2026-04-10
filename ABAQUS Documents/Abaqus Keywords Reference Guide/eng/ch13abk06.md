# *MASS DIFFUSION







### *MASS DIFFUSIONTransient or steady-state uncoupled mass diffusion analysis.

This option is used to control uncoupled transient or steady-state mass diffusion analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Mass diffusion analysis," Section 6.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassdiffusion)

### **Optional parameters: **

DCMAX

Set this parameter equal to the maximum normalized concentration change to be allowed in an increment. Abaqus/Standard will restrict the time step to ensure that this value will not be exceeded at any node (except nodes with boundary conditions) during any increment of the analysis. If the DCMAX parameter is omitted, fixed time increments will be used.

END

Set END=PERIOD (default) to analyze the entire time period specified on the data line. Set END=SS to end the analysis when steady state is reached. 

STEADY STATE

Include this parameter to choose steady-state analysis. Transient analysis is assumed if this parameter is omitted. 

### **Data line to define time stepping in a mass diffusion analysis: **

**First (and only) line:**




