# *CAP HARDENING







### *CAP HARDENINGSpecify Drucker-Prager/Cap plasticity hardening.

This option is used to specify the hardening part of the material model for elastic-plastic materials that use the Drucker-Prager/Cap yield surface. It must be used in conjunction with the [*CAP PLASTICITY](ch03abk04.md) option and, if creep material behavior is included in an Abaqus/Standard analysis, with the [*CAP CREEP](ch03abk02.md) option. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Modified Drucker-Prager/Cap model," Section 23.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP PLASTICITY](ch03abk04.md)
- [*CAP CREEP](ch03abk02.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the hydrostatic yield stress, in addition to temperature. If this parameter is omitted, it is assumed that the hydrostatic yield stress depends only on the volumetric plastic strain and, possibly, on the temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

SCALESTRESS

Set this parameter equal to the factor by which you want the yield stress to be scaled.

### **Data lines to define Drucker-Prager/Cap plasticity hardening: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of hydrostatic yield stress on volumetric inelastic strain (in Abaqus/Standard) or volumetric plastic strain (in Abaqus/Explicit) and, if needed, on temperature and other predefined field variables.




