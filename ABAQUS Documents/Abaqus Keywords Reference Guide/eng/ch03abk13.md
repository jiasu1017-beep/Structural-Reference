# *CFD







### *CFDComputational fluid dynamic analysis.

This option is used to control the transport of momentum, energy, temperature, species, and other scalar variables in both transient and steady-state fluid flow problems.

**Products: **Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)

### **Required parameter: **

INCOMPRESSIBLE NAVIER STOKES

Include this parameter to specify an incompressible flow analysis.

### **Optional parameters: **

ENERGY EQUATION

Set ENERGY EQUATION=NO ENERGY (default) to specify an isothermal flow problem. 

Set ENERGY EQUATION=TEMPERATURE to specify a thermal (heat) transport problem with temperature as the primary transport scalar variable.

INCREMENTATION

This parameter is valid only for a transient flow problem.

Set INCREMENTATION=FIXED CFL (default) to set a fixed Courant-Friedrichs-Lewy (CFL) number for time marching. Abaqus/CFD automatically determines the stable time step based on the specified value of the CFL number.

Set INCREMENTATION=FIXED STEP SIZE to set a fixed time step for time marching.

STEADY STATE

This parameter is valid only for a steady-state flow problem.

### **Data lines for INCREMENTATION=FIXED CFL: **

**First line:**

**Second line:**

### **Data lines for INCREMENTATION=FIXED STEP SIZE: **

**First line:**

**Second line:**

### **Data line for steady-state flow: **

**First (and only) line:**




