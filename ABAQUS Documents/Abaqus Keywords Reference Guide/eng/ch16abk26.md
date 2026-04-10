# *PRESSURE EQUATION SOLVER







### *PRESSURE EQUATION SOLVERSpecify the linear solver and parameters for solving the pressure equation for incompressible flows.

This option can be used only as a suboption of the [*CFD](ch03abk13.md) option to enable the linear solver parameters for the pressure equation for incompressible flows. For a steady-state analysis this option is also used to enable the under-relaxation parameter for the pressure correction equation.

**Products: **Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **Optional parameters: **

CONVERGENCE

Set CONVERGENCE=ON to write convergence information to the log file.

Set CONVERGENCE=OFF (default) to suppress convergence information.

DIAGNOSTICS

Set DIAGNOSTICS=ON to write diagnostic information about the solver to the log file.

Set DIAGNOSTICS=OFF (default) to suppress diagnostic information.

TYPE

Set TYPE=AMG (default) to enable the Algebraic Multigrid linear solver.

Set TYPE=DSCG to enable the Diagonal Scaled Conjugate Gradient linear solver.

Set TYPE=SSORCG to enable the Symmetric Successive Over Relaxation Conjugate Gradient linear solver.

### **Data lines for TYPE=AMG: **

**First line:**

**Second line:**

**Third line:**

### **Data line for TYPE=DSCG and TYPE=SSORCG: **

**First (and only) line:**




