# *PLASTIC TORQUE







### *PLASTIC TORQUEDefine the plastic torsional moment behavior for frame elements.

This option can be used only in conjunction with the [*FRAME SECTION](ch06abk34.md) option and is available only for FRAME3D elements. It describes the torsional moment in a frame element as a function of the plastic rotation about the element's axis.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Frame section behavior," Section 29.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingframesection)
- [*FRAME SECTION](ch06abk34.md)

**There are no parameters associated with this option.**

### **Data lines to define the variation of torsional yield moment with plastic rotation: **

**First line:**

Repeat this data line as often as necessary to define the relationship between the torsional moment and the plastic rotation. At least three pairs of data are required.




