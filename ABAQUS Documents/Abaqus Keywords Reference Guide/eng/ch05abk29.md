# *EPJOINT







### *EPJOINTDefine properties for elastic-plastic joint elements.

This option is used to define the properties for elastic-plastic joint elements. The [*JOINT ELASTICITY](ch10abk02.md) and, if plasticity is to be defined, [*JOINT PLASTICITY](ch10abk03.md) options must immediately follow this option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Elastic-plastic joints," Section 32.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eepjoint)
- [*JOINT ELASTICITY](ch10abk02.md)
- [*JOINT PLASTICITY](ch10abk03.md)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the elastic-plastic joint elements for which properties are being defined.

ORIENTATION

Set this parameter equal to the name given to the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that gives the orientation of the local system in the joint.

### **Optional parameter: **

SECTION

Set this parameter equal to SPUD CAN if the joint models a spud can. If the joint does not model a spud can, this parameter is not needed.

### **Data line to define spud can geometry with SECTION=SPUD CAN: **

**First (and only) line:**

Include the [*JOINT ELASTICITY](ch10abk02.md) and [*JOINT PLASTICITY](ch10abk03.md) options as needed to define the joint behavior.




