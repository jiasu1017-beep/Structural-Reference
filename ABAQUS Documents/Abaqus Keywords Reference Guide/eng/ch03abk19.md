# *CLAY HARDENING







### *CLAY HARDENINGSpecify hardening for the clay plasticity model.

This option is used to define piecewise linear hardening/softening of the Cam-clay plasticity yield surface. It can be used only in conjunction with the [*CLAY PLASTICITY](ch03abk20.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Critical state (clay) plasticity model," Section 23.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cclayplastic)
- [*CLAY PLASTICITY](ch03abk20.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies, in addition to temperature, included in the definition of the hydrostatic pressure stress. If this parameter is omitted, the hydrostatic pressure stress may depend only on the volumetric plastic strain and, possibly, on the temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define hardening for Cam-clay plasticity: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the yield surface size on volumetric plastic strain and, if needed, on temperature and other predefined field variables.




