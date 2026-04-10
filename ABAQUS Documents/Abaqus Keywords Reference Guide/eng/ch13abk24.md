# *MOHR COULOMB HARDENING







### *MOHR COULOMB HARDENINGSpecify hardening for the Mohr-Coulomb plasticity model.

This option is used to define piecewise linear hardening/softening behavior for a material defined by the Mohr-Coulomb plasticity model. It must be used in conjunction with the [*MOHR COULOMB](ch13abk23.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Mohr-Coulomb plasticity," Section 23.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB](ch13abk23.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the cohesion yield stress, in addition to temperature. If this parameter is omitted, it is assumed that the cohesion yield stress depends only on the plastic strain and, possibly, on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define Mohr-Coulomb hardening: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the cohesion yield stress on plastic strain and, if needed, on temperature and other predefined field variables.




