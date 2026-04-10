# *JOINT







### *JOINTDefine properties for JOINTC elements.

This option is used to define the properties for JOINTC elements. The [*DASHPOT](ch04abk08.md) and [*SPRING](ch18abk29.md) options must immediately follow this option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Unsupported; similar functionality is available by modeling connectors.

##### **References:**

- ["Flexible joint element," Section 32.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ejoint)
- [*DASHPOT](ch04abk08.md)
- [*SPRING](ch18abk29.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the JOINTC elements for which properties are being defined.

### **Optional parameter: **

ORIENTATION

Set this parameter equal to the name given to the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that specifies the initial orientation of the local system in the joint.

### **There are no data lines associated with this option; instead, include [*SPRING](ch18abk29.md) and [*DASHPOT](ch04abk08.md) options as needed to define the joint behavior. **




