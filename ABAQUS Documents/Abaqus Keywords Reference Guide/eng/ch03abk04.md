# *CAP PLASTICITY







### *CAP PLASTICITYSpecify the Modified Drucker-Prager/Cap plasticity model.

This option is used to define yield surface parameters for elastic-plastic materials that use the modified Drucker-Prager/Cap plasticity model. It must be used in conjunction with the [*CAP HARDENING](ch03abk03.md) option and, if creep material behavior is included in an Abaqus/Standard analysis, with the [*CAP CREEP](ch03abk02.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Modified Drucker-Prager/Cap model," Section 23.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP HARDENING](ch03abk03.md)
- [*CAP CREEP](ch03abk02.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies, in addition to temperature, included in the definition of the Drucker-Prager/Cap parameters. If this parameter is omitted, it is assumed that the Drucker-Prager/Cap parameters are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define Drucker-Prager/Cap plasticity yield surface parameters: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the dependence of the Drucker-Prager/Cap parameters on temperature and other predefined field variables.




