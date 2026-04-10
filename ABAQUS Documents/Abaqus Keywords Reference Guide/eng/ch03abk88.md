# *CRUSHABLE FOAM HARDENING







### *CRUSHABLE FOAM HARDENINGSpecify hardening for the crushable foam plasticity model.

This option is used to define the hardening data for elastic-plastic materials that use the crushable foam plasticity model. It must be used in conjunction with the [*CRUSHABLE FOAM](ch03abk87.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Crushable foam plasticity models," Section 23.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccrushfoam)
- [*CRUSHABLE FOAM](ch03abk87.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the yield surface size, in addition to temperature. If this parameter is omitted, it is assumed that the size of the yield surface depends only on the volumetric plastic strain and, possibly, on the temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define crushable foam hardening: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the yield stress in uniaxial compression on the corresponding axial plastic strain and, if needed, on temperature and other predefined field variables.




