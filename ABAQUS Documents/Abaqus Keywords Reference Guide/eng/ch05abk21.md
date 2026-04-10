# *ENERGY EQUATION SOLVER







### *ENERGY EQUATION SOLVERSpecify the linear solver and parameters for solving the conduction equations in an Abaqus/CFD analysis.

This option is used to enable linear solver parameters for solving the conduction equations in Abaqus/CFD. It must be used in conjunction with the [*CFD](ch03abk13.md) or [*HEAT TRANSFER](ch08abk03.md) options.

**Products: **Abaqus/CFD  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- ["Uncoupled heat transfer analysis," Section 6.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aheattransfer)
- [*CFD](ch03abk13.md)
- [*HEAT TRANSFER](ch08abk03.md)

### **Optional parameters: **

CONVERGENCE

Set CONVERGENCE=ON to write convergence information to the log file. 

Set CONVERGENCE=OFF (default) to suppress convergence information.

DIAGNOSTICS

Set DIAGNOSTICS=ON to write diagnostic information about the solver to the log file. 

Set DIAGNOSTICS=OFF (default) to suppress diagnostic information.

TYPE

Set TYPE=DSCG to enable the Diagonal Scaled Conjugate Gradient linear solver.

Set TYPE=SSORCG to enable the Symmetric Successive Over Relaxation Conjugate Gradient linear solver.

Set TYPE=DSGMRES to enable the Diagonally Scaled Generalized Minimum Residual linear solver.

Set TYPE=DSFGMRES to enable the Diagonally Scaled Flexible Generalized Minimum Residual linear solver.

Set TYPE=AMG to enable the Algebraic Multigrid linear solver.

The default is TYPE=DSCG if the node-centered solver is selected and TYPE=DSFGMRES if the element-centered solver is selected.

### **Data line for TYPE=DSCG and TYPE=SSORCG: **

**First (and only) line:**

### **Data line for TYPE=DSGMRES and TYPE=DSFGMRES: **

**First (and only) line:**

### **Data lines for TYPE=AMG: **

**First line:**

**Second line:**

**Third line:**




