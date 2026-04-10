# *SHEAR RETENTION







### *SHEAR RETENTIONDefine the reduction of the shear modulus associated with crack surfaces in a *CONCRETE model as a function of the tensile strain across the crack.

This option is used to give a multiplying factor, ![](../graphics/key_eqn01059.gif), that defines the modulus for shearing of cracks as a fraction of the elastic shear modulus of the uncracked concrete. If this option is used, it should follow the [*CONCRETE](ch03abk28.md) option. The [*SHEAR RETENTION](ch18abk12.md) option can also be used in conjunction with the [*FAILURE RATIOS](ch06abk04.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*FAILURE RATIOS](ch06abk04.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of shear retention behavior, in addition to temperature. If this parameter is omitted, it is assumed that the shear retention behavior depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the shear retention behavior: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of the shear retention behavior on temperature and other predefined field variables.




