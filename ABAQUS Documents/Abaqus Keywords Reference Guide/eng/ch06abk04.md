# *FAILURE RATIOS







### *FAILURE RATIOSDefine the shape of the failure surface for a *CONCRETE model.

This option is used to define the shape of the failure surface for a concrete model. If used, it must appear after the [*CONCRETE](ch03abk28.md) option. The [*FAILURE RATIOS](ch06abk04.md) option can also be used with the [*TENSION STIFFENING](ch19abk04.md) and [*SHEAR RETENTION](ch18abk12.md) options.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*TENSION STIFFENING](ch19abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the failure ratios, in addition to temperature. If this parameter is omitted, it is assumed that the failure ratios depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the failure surface for a concrete model: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the failure ratios on temperature and other predefined field variables.




