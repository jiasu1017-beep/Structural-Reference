# *PIEZOELECTRIC







### *PIEZOELECTRICSpecify piezoelectric material properties.

This option is used to define the piezoelectric properties of a material.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Piezoelectric behavior," Section 26.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpiezoelect)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the piezoelectric properties. If this parameter is omitted, the piezoelectric properties are assumed not to depend on any field variables but may still depend on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=S (default) to specify stress material coefficients for the piezoelectric property. Set TYPE=E to specify strain material coefficients for the piezoelectric property.

### **Data lines to define the piezoelectric stress coefficient matrix (TYPE=S): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the piezoelectric properties as a function of temperature and other predefined field variables.

### **Data lines to define the piezoelectric strain coefficient matrix (TYPE=E; for the shear components these coefficients relate the engineering, and not the tensorial, shear strain components to the components of the potential gradient vector): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the piezoelectric properties as a function of temperature and other predefined field variables.




