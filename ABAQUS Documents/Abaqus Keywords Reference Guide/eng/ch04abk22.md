# *DIELECTRIC







### *DIELECTRICSpecify dielectric material properties.

This option is used to define the dielectric property of a fully constrained material for use in coupled piezoelectric analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Piezoelectric behavior," Section 26.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpiezoelect)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the dielectric property. If this parameter is omitted, the dielectric property is assumed not to depend on any field variables but may still depend on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=ISO (default) for isotropic behavior. Set TYPE=ORTHO for orthotropic behavior. Set TYPE=ANISO for fully anisotropic behavior. 

### **Data lines to define isotropic behavior (TYPE=ISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dielectric property as a function of temperature and other predefined field variables.

### **Data lines to define orthotropic behavior (TYPE=ORTHO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dielectric property as a function of temperature and other predefined field variables.

### **Data lines to define anisotropic behavior (TYPE=ANISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the dielectric property as a function of temperature and other predefined field variables.




