# *TENSION STIFFENING







### *TENSION STIFFENINGDefine the retained tensile stress normal to a crack in a *CONCRETE model.

This option is used to define the retained tensile stress normal to a crack as a function of the deformation in the direction of the normal to the crack. It must be used with and appear after the [*CONCRETE](ch03abk28.md) option. The [*TENSION STIFFENING](ch19abk04.md) option can also be used in conjunction with the [*SHEAR RETENTION](ch18abk12.md) and [*FAILURE RATIOS](ch06abk04.md) options.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*FAILURE RATIOS](ch06abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the postcracking behavior, in addition to temperature. If this parameter is omitted, it is assumed that the postcracking behavior depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=DISPLACEMENT to define the postcracking behavior by entering the displacement, ![](../graphics/key_eqn01103.gif), at which a linear loss of strength after cracking gives zero stress.

Set TYPE=STRAIN (default) to specify the postcracking behavior by entering the postfailure stress-strain relationship directly.

### **Data lines if the parameter TYPE=STRAIN is included (default): **

**First line:**

The first point at each value of temperature must be a stress fraction of 1.0 at a strain of 0.0.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if the parameter TYPE=DISPLACEMENT is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.




