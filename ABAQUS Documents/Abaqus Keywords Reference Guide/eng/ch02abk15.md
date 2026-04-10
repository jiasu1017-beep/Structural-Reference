# *BRITTLE SHEAR







### *BRITTLE SHEARDefine the postcracking shear behavior of a material used with the brittle cracking model.

This option is used to define the postcracking shear behavior of a material used in a brittle cracking model. The [*BRITTLE SHEAR](ch02abk15.md) option must be used with the [*BRITTLE CRACKING](ch02abk13.md) option and must immediately follow it. The [*BRITTLE SHEAR](ch02abk15.md) option can be used in conjunction with the [*BRITTLE FAILURE](ch02abk14.md) option to specify a brittle failure criterion.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cracking model for concrete," Section 23.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccracking)
- [*BRITTLE CRACKING](ch02abk13.md)
- [*BRITTLE FAILURE](ch02abk14.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the cracked shear behavior, in addition to temperature. If this parameter is omitted, it is assumed that the parameters defining cracked shear behavior are constant or depend only on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

TYPE

Set TYPE=RETENTION FACTOR (default) to specify the postcracking shear behavior by entering the shear retention factor–crack opening strain relationship directly.

Set TYPE=POWER LAW to specify the postcracking shear behavior by entering the material parameters *p* and ![](../graphics/key_eqn00126.gif) for the power law shear retention model.

### **Data lines if the TYPE=RETENTION FACTOR parameter is included (default): **

**First line:**

The first point at each value of temperature must have a retention factor of 1.0 and a cracking strain of 0.0.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking shear behavior on temperature and other predefined field variables.

### **Data lines if the TYPE=POWER LAW parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking shear behavior on temperature and other predefined field variables.




