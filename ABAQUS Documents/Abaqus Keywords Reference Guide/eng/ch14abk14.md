# *NONLINEAR BH







### *NONLINEAR BHSpecify nonlinear magnetic behavior of a soft magnetic material.

This option is used to specify nonlinear magnetic behavior of a soft magnetic material.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Magnetic permeability," Section 26.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmagpermeability)

### **Required parameter: **

DIR

Set this parameter equal to the local direction (1, 2, or 3) for which the material behavior is defined in the data lines to follow; set DIR=0 to define material behavior that is inactive in the current model but is available for future use. The [*NONLINEAR BH](ch14abk14.md) option must be repeated with different values of the DIR parameter to define independent magnetic behavior in three orthogonal directions.

For isotropic nonlinear magnetic behavior, include the [*NONLINEAR BH](ch14abk14.md) option only once (DIR=1, 2, or 3).

 For orthotropic nonlinear magnetic behavior, the [*NONLINEAR BH](ch14abk14.md) option must be included three times (DIR=1, DIR=2, and DIR=3).

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the nonlinear magnetic behavior, in addition to temperature. If this parameter is omitted, the nonlinear magnetic behavior does not depend on field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define nonlinear magnetic behavior: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the magnetic flux density on the magnetic field and, if needed, on temperature and other predefined field variables.




