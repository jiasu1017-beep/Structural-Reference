# *BUCKLING LENGTH







### *BUCKLING LENGTHDefine buckling length data for buckling strut response of frame elements with PIPE sections.

This option is used to define two sets of coefficients used in the ISO equation that predicts ![](../graphics/key_eqn00138.gif) for frame elements with buckling strut response. For a user-defined buckling envelope it can be used only in conjunction with both the [*FRAME SECTION](ch06abk34.md), SECTION=PIPE, YIELD STRESS=![](../graphics/key_eqn00128.gif) option and the [*BUCKLING ENVELOPE](ch02abk17.md) option. For the default buckling envelope it can be used only in conjunction with the [*FRAME SECTION](ch06abk34.md), BUCKLING, SECTION=PIPE, YIELD STRESS=![](../graphics/key_eqn00128.gif) option, with or without the PINNED parameter.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Frame section behavior," Section 29.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingframesection)
- [*BUCKLING ENVELOPE](ch02abk17.md)
- [*FRAME SECTION](ch06abk34.md)

**There are no parameters associated with this option.**

### **Data line to define the buckling length coefficients: **

**First (and only) data line:**




