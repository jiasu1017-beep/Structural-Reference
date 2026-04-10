# *HEAT TRANSFER







### *HEAT TRANSFERTransient or steady-state uncoupled heat transfer analysis.

This option is used to control uncoupled heat transfer for either transient or steady-state response.

**Products: **Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Uncoupled heat transfer analysis," Section 6.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aheattransfer)
- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)

### **Required parameters to activate an Abaqus/CFD solid heat transfer analysis: **

CENTERING

Set CENTERING=ELEMENT to select an element-centered heat transfer analysis. 

TYPE

Set TYPE=THERMAL FLOW to indicate a heat transfer analysis using Abaqus/CFD.

### **Optional parameters: **

DELTMX

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the maximum temperature change to be allowed in an increment during a transient heat transfer analysis. Abaqus/Standard will restrict the time step to ensure that this value will not be exceeded at any node (except nodes whose temperature degree of freedom is constrained via boundary conditions, MPC's, etc.) during any increment of the step. If the DELTMX parameter is omitted, fixed time increments will be used.

END

This parameter applies only to Abaqus/Standard analyses.

Set END=PERIOD (default) to analyze a specific time period. Set END=SS to end the analysis when steady state is reached. 

This parameter is relevant only for transient analysis.

STEADY STATE

Include this parameter to choose steady-state analysis. Transient analysis is assumed if this parameter is omitted. If this parameter is used in an Abaqus/CFD solid heat transfer analysis, the values given on the data line are ignored.

### **Optional parameter for cavity radiation analysis: **

MXDEM

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the maximum allowable emissivity change with temperature and field variables during an increment. If this value is exceeded, Abaqus/Standard will cut back the increment until the maximum change in emissivity is less than the specified value. If this parameter is omitted, a default value of 0.1 is used.

### **Data line to control incrementation and steady-state conditions in a pure heat transfer analysis: **

**First (and only) line:**

### **Data line to define an Abaqus/CFD solid heat transfer analysis (TYPE=THERMAL FLOW): **

**First (and only) line:**




