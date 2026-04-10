# *TENSION CUTOFF







### *TENSION CUTOFFSpecify tension cutoff data for the Mohr-Coulomb plasticity model.

This option is used to specify tension cutoff data to limit the load carrying capacity of the Mohr-Coulomb plasticity model near the tensile region. This option must be used in conjunction with [*MOHR COULOMB](ch13abk23.md) and [*MOHR COULOMB HARDENING](ch13abk24.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Mohr-Coulomb plasticity," Section 23.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB](ch13abk23.md)
- [*MOHR COULOMB HARDENING](ch13abk24.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the tension cutoff stress, in addition to temperature. If this parameter is omitted, it is assumed that the tensile yield stress depends only on the plastic strain and, possibly, on temperature.

### **Data lines to define tension cutoff: **

**First data line:**

**Subsequent data lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of tension cutoff on predefined field variables.




