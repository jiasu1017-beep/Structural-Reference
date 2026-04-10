# *BRITTLE CRACKING







### *BRITTLE CRACKINGDefine brittle cracking properties.

This option is used to define cracking and postcracking properties for the brittle cracking material model. The [*BRITTLE CRACKING](ch02abk13.md) option must be used in conjunction with the [*BRITTLE SHEAR](ch02abk15.md) option and must immediately precede it. The [*BRITTLE CRACKING](ch02abk13.md) option can be used in conjunction with the [*BRITTLE FAILURE](ch02abk14.md) option to specify a brittle failure criterion.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cracking model for concrete," Section 23.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccracking)
- [*BRITTLE FAILURE](ch02abk14.md)
- [*BRITTLE SHEAR](ch02abk15.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the postcracking behavior, in addition to temperature. If this parameter is omitted, it is assumed that the postcracking behavior depends only on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

TYPE

Set TYPE=STRAIN (default) to specify the postcracking behavior by entering the postfailure stress-strain relationship directly. 

Set TYPE=DISPLACEMENT to define the postcracking behavior by entering the postfailure stress/displacement relationship directly. 

Set TYPE=GFI to define the postcracking behavior by entering the failure stress, ![](../graphics/key_eqn00117.gif), and the Mode I fracture energy, ![](../graphics/key_eqn00118.gif).

### **Data lines if the TYPE=STRAIN parameter is included (default): **

**First line:**

The first point at each value of temperature must have a cracking strain of 0.0 and gives the failure stress value.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if the TYPE=DISPLACEMENT parameter is included: **

**First line:**

The first point at each value of temperature must have a cracking displacement of 0.0 and gives the failure stress value.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if the TYPE=GFI parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.




