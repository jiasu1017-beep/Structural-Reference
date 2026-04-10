# *JOINT PLASTICITY







### *JOINT PLASTICITYSpecify plastic properties for elastic-plastic joint elements.

This option is used to define the plastic behavior for elastic-plastic joint elements. It can be used only in conjunction with the [*EPJOINT](ch05abk29.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Elastic-plastic joints," Section 32.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eepjoint)
- [*EPJOINT](ch05abk29.md)

### **Required parameter: **

TYPE

Set TYPE=SAND to specify the model for interaction of spud cans and sand. Set TYPE=CLAY to specify the model for interaction of spud cans and clay. Set TYPE=MEMBER to specify the parabolic model for structural members.

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the plasticity property values. If this parameter is omitted, it is assumed that the plasticity property values are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines for TYPE=SAND: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the plastic behavior as a function of temperature and other predefined field variables.

### **Data lines for TYPE=CLAY: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the plastic behavior as a function of temperature and other predefined field variables.

### **Data lines for TYPE=MEMBER: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the plastic behavior as a function of temperature and other predefined field variables.




