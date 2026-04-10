# *PERMANENT MAGNETIZATION







### *PERMANENT MAGNETIZATIONSpecify permanent magnetization.

This option is used to define permanent magnetization through coercivity of a permanent magnet for electromagnetic elements in a transient electromagnetic or magnetostatic analysis. This option can be used only in conjunction with the [*MAGNETIC PERMEABILITY](ch13abk01.md) option and, optionally, with the [*NONLINEAR BH](ch14abk14.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Magnetic permeability," Section 26.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmagpermeability)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["Magnetostatic analysis," Section 6.7.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amagnetostatic)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of coercivity of a permanent magnet. If this parameter is omitted, the coercivity is assumed not to depend on any field variables but may still depend on temperature. 

### **Data lines to define the coercivity vector: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Do not repeat the first data line. Repeat the second and subsequent data lines as often as necessary to define the magnitude of coercivity as a function of temperature and field variables.




