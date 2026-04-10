# *MODAL DYNAMIC







### *MODAL DYNAMICDynamic time history analysis using modal superposition.

This option is used to provide dynamic time history response as a linear perturbation procedure using modal superposition.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Transient modal dynamic analysis," Section 6.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amodaldynamic)

### **Optional parameter: **

CONTINUE

Set CONTINUE=NO (default) to specify that this step is not to carry over the initial conditions from the results of the preceding step. In this case the initial displacements are zero, and the initial velocities are taken from the [*INITIAL CONDITIONS](ch09abk18.md), TYPE=VELOCITY option if it is used; otherwise, they are zero. Step time begins at zero.

Set CONTINUE=YES to specify that this step is to carry over the initial conditions from the end of the immediately preceding [*MODAL DYNAMIC](ch13abk18.md) step or  static perturbation step. If this preceding step is a [*MODAL DYNAMIC](ch13abk18.md) step, both the velocities and the displacements from the end of this step are used as the initial conditions for the current step. If this preceding step is a static perturbation step,  the displacements from this step are used as the initial displacements for the current step and the initial velocities are taken from the [*INITIAL CONDITIONS](ch09abk18.md), TYPE=VELOCITY option if it is used; otherwise, they are zero. Step time is continued from the immediately preceding [*MODAL DYNAMIC](ch13abk18.md) or static perturbation step.

### **Data line for a transient modal dynamic analysis: **

**First (and only) line:**




