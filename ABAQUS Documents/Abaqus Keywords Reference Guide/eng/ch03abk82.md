# *COUPLED THERMAL-ELECTRICAL







### *COUPLED THERMAL-ELECTRICALFully coupled, simultaneous heat transfer and electrical analysis.

This option is used to analyze problems where the electrical potential and temperature fields must be solved simultaneously.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)

### **Optional parameters: **

DELTMX

Include this parameter to activate automatic time incrementation in transient analysis. If the DELTMX parameter is omitted in a transient analysis, fixed time increments will be used. Set this parameter equal to the maximum temperature change to be allowed in an increment in a transient analysis. Abaqus/Standard will restrict the time step to ensure that this value will not be exceeded at any node (except nodes with boundary conditions) during any increment of the analysis. 

END

Set END=PERIOD (default) to analyze a specific time period in a transient analysis. Set END=SS to end the analysis when steady state is reached.

MXDEM

For problems including cavity radiation heat transfer, set this parameter equal to the maximum allowable emissivity change with temperature and field variables during an increment. If the value of MXDEM is exceeded, Abaqus/Standard will cut back the increment until the maximum change in emissivity is less than the value input. If this parameter is omitted, a default value of 0.1 is used.

This parameter controls the accuracy of changes in emissivity due to temperature since Abaqus/Standard evaluates the emissivity based on the temperature at the start of each increment and uses that emissivity value throughout the increment.

STEADY STATE

Include this parameter to choose steady-state thermal analysis. Transient thermal analysis is assumed if this parameter is omitted. If this parameter is included, automatic time incrementation will be used.

### **Data line to define incrementation and steady state: **

**First (and only) line:**




