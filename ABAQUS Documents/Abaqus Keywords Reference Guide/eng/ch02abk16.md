# *BUCKLE







### *BUCKLEObtain eigenvalue buckling estimates.

This option is used to control eigenvalue buckling estimation.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling)

### **Optional parameter: **

EIGENSOLVER

Use this parameter to choose the eigensolver.

Set EIGENSOLVER=SUBSPACE (default) to invoke the subspace iteration eigensolver.

Set EIGENSOLVER=LANCZOS to invoke the Lanczos eigensolver.

### **Data line for an eigenvalue buckling analysis when EIGENSOLVER=SUBSPACE: **

**First (and only) line:**

### **Data line for an eigenvalue buckling analysis when EIGENSOLVER=LANCZOS: **

**First (and only) line:**




