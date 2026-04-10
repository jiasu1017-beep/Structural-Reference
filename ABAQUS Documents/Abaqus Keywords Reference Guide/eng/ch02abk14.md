# *BRITTLE FAILURE







### *BRITTLE FAILURESpecify brittle failure criterion.

This option is used with the brittle cracking material model to specify brittle failure of the material. It must be used in conjunction with the [*BRITTLE CRACKING](ch02abk13.md) and the [*BRITTLE SHEAR](ch02abk15.md) options.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cracking model for concrete," Section 23.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccracking)
- [*BRITTLE CRACKING](ch02abk13.md)
- [*BRITTLE SHEAR](ch02abk15.md)

### **Optional parameters: **

CRACKS

Set CRACKS=1 (default) to indicate that an element will be removed when any local direct cracking strain (or displacement) component reaches the failure value.

Set CRACKS=2 to indicate that an element will be removed when any two direct cracking strain (or displacement) components reach the failure value.

Set CRACKS=3 to indicate that an element will be removed when all three possible direct cracking strain (or displacement) components reach the failure value.

The value for the CRACKS parameter can only be 1 for beam or truss elements. It cannot be greater than 2 for plane stress and shell elements, and it cannot be greater than 3 for three-dimensional, plane strain, and axisymmetric elements.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the failure criterion, in addition to temperature. If this parameter is omitted, it is assumed that the failure criterion depends only on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

### **Data lines if TYPE=STRAIN (default) is used on the [*BRITTLE CRACKING](ch02abk13.md) option: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if TYPE=DISPLACEMENT or GFI is included on the [*BRITTLE CRACKING](ch02abk13.md) option: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.




