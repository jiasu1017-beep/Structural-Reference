# *CONCRETE TENSION STIFFENING







### *CONCRETE TENSION STIFFENINGDefine postcracking properties for the concrete damaged plasticity model.

This option is used to define cracking and postcracking properties for the concrete damaged plasticity material model. The [*CONCRETE TENSION STIFFENING](ch03abk33.md) option must be used in conjunction with the [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md) and [*CONCRETE COMPRESSION HARDENING](ch03abk30.md) options. In addition, the [*CONCRETE TENSION DAMAGE](ch03abk32.md) and/or [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md) options can be used to specify tensile and/or compressive stiffness degradation damage.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete damaged plasticity," Section 23.6.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the postcracking behavior, in addition to temperature. If this parameter is omitted, the postcracking stress depends only on the cracking strain, the strain rate, and, possibly, on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=STRAIN (default) to specify the postcracking behavior by entering the postfailure stress/cracking-strain relationship. 

Set TYPE=DISPLACEMENT to define the postcracking behavior by entering the postfailure stress/cracking-displacement relationship. 

Set TYPE=GFI to define the postcracking behavior by entering the failure stress, ![](../graphics/key_eqn00241.gif), and the fracture energy, ![](../graphics/key_eqn00242.gif).

### **Data lines if the TYPE=STRAIN parameter is included (default): **

**First line:**

The first point at each value of temperature must have a cracking strain of 0.0 and gives the failure stress value, ![](../graphics/key_eqn00241.gif).

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if the TYPE=DISPLACEMENT parameter is included: **

**First line:**

The first point at each value of temperature must have a cracking displacement of 0.0 and gives the failure stress value.

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.

### **Data lines if the TYPE=GFI parameter is included: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the postcracking behavior on temperature and other predefined field variables.




