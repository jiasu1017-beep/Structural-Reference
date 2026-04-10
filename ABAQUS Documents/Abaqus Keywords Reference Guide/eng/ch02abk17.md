# *BUCKLING ENVELOPE







### *BUCKLING ENVELOPEDefine a nondefault buckling envelope for buckling strut response of frame elements with PIPE sections.

This option is used to define the coefficients characterizing the buckling strut envelope for the buckling strut response of frame elements. It can be used in conjunction with the [*FRAME SECTION](ch06abk34.md), SECTION=PIPE, YIELD STRESS=![](../graphics/key_eqn00128.gif) option with or without the PINNED parameter.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Frame section behavior," Section 29.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingframesection)
- [*FRAME SECTION](ch06abk34.md)

**There are no parameters associated with this option.**

### **Data line to define the buckling strut envelope: **

**First (and only) data line:**

In the above data line *A* is the cross-section area, ![](../graphics/key_eqn00128.gif) is a yield stress value, *E* is Young's modulus, *L* is the element length, *D* is the outer pipe diameter, and *t* is the pipe wall thickness.




