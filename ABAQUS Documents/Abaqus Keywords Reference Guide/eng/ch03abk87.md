# *CRUSHABLE FOAM







### *CRUSHABLE FOAMSpecify the crushable foam plasticity model.

This option is used to specify the plastic part of the material behavior for elastic-plastic materials that use the crushable foam plasticity model. It must be used in conjunction with the [*CRUSHABLE FOAM HARDENING](ch03abk88.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Crushable foam plasticity models," Section 23.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccrushfoam)
- [*CRUSHABLE FOAM HARDENING](ch03abk88.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the crushable foam parameters, in addition to temperature. If this parameter is omitted, it is assumed that the crushable foam parameters are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

HARDENING

Set HARDENING=VOLUMETRIC (default) to specify the volumetric hardening model. 

Set HARDENING=ISOTROPIC to specify the isotropic hardening model.

### **Data lines to define the crushable foam plasticity model with volumetric hardening (HARDENING=VOLUMETRIC): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the crushable foam parameters on temperature and other predefined field variables.

### **Data lines to define the crushable foam plasticity model with isotropic hardening (HARDENING=ISOTROPIC): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the crushable foam parameters on temperature and other predefined field variables.




