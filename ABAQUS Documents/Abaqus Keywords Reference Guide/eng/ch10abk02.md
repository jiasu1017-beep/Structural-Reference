# *JOINT ELASTICITY







### *JOINT ELASTICITYSpecify elastic properties for elastic-plastic joint elements.

This option is used to define linear elastic moduli for elastic-plastic joint elements. It can be used only in conjunction with the [*EPJOINT](ch05abk29.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Elastic-plastic joints," Section 32.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eepjoint)
- [*EPJOINT](ch05abk29.md)

### **Required parameters: **

MODULI

Set MODULI=SPUD CAN to define spud can moduli. Set MODULI=GENERAL to enter a general elastic modulus.

NDIM

Set NDIM=2 to enter values for a two-dimensional problem. Set NDIM=3 to enter values for a three-dimensional problem.

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the moduli. If this parameter is omitted, it is assumed that the moduli are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines for MODULI=SPUD CAN and NDIM=2: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines for MODULI=SPUD CAN and NDIM=3: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines for MODULI=GENERAL and NDIM=2: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines for MODULI=GENERAL and NDIM=3: **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.




