# *TRANSPORT EQUATION SOLVER







### *TRANSPORT EQUATION SOLVERSpecify the linear solver and parameters for solving the transport equations in an Abaqus/CFD analysis.

This option can be used only as a suboption of the [*CFD](ch03abk13.md) option to enable the linear solver parameters for solving the transport equations of scalar variables such as temperature, species concentration, turbulent eddy viscosity, turbulent kinetic energy, etc. For a steady-state analysis this option is also used to enable the under-relaxation parameter for the transport of the scalar variables.

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

Set TYPE=DSFGMRES (default) to enable the Diagonally Scaled Flexible Generalized Minimum Residual linear solver.

Set TYPE=DSGMRES to enable the Diagonally Scaled Generalized Minimum Residual linear solver.

Set TYPE=ILUFGMRES to enable the Incomplete LU factorization preconditioned Flexible Generalized Minimum Residual linear solver.

### **Data line for TYPE=DSFGMRES, TYPE=DSGMRES, and TYPE=ILUFGMRES: **

**First (and only) line:**




