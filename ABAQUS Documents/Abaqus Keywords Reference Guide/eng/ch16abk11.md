# *PIPE-SOIL INTERACTION







### *PIPE-SOIL INTERACTIONSpecify element properties for pipe-soil interaction elements.

This option is used to define properties for pipe-soil interaction elements. The [*PIPE-SOIL STIFFNESS](ch16abk12.md) option must follow immediately after this option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Pipe-soil interaction elements," Section 32.12.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-epipesoil)
- ["Pipe-soil interaction element library," Section 32.12.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-epipesoillibrary)
- [*PIPE-SOIL STIFFNESS](ch16abk12.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the pipe-soil interaction elements for which properties are being defined.

### **Optional parameter: **

ORIENTATION

Set this parameter equal to the name of the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that gives the orientation of the local system used for material calculations.

**There are no data lines associated with this option.**



