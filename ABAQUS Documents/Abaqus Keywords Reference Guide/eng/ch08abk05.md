# *HOURGLASS STIFFNESS







### *HOURGLASS STIFFNESSSpecify nondefault hourglass stiffness.

This option is relevant for first-order, reduced-integration elements; second-order, reduced-integration element types M3D9R, S8R5, and S9R5; and modified tetrahedral and triangular elements. It can also be used to define an hourglass scaling factor for the stiffness associated with the drill degree of freedom (rotation about the surface normal) in shell elements and to modify the hourglass stiffness factor for the pressure Lagrange multiplier degrees of freedom for C3D4H elements.

The [*HOURGLASS STIFFNESS](ch08abk05.md) option can be used only in conjunction with the [*MEMBRANE SECTION](ch13abk16.md) option, the [*SOLID SECTION](ch18abk22.md) option, the [*SHELL SECTION](ch18abk15.md) option, or the [*SHELL GENERAL SECTION](ch18abk14.md) option. The hourglass control defined with this option affects only those elements whose section properties are defined by the immediately preceding section option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Mesh module

##### **References:**

- ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)
- [*SOLID SECTION](ch18abk22.md)

**There are no parameters associated with this option.**

### **Data line to define a nondefault hourglass stiffness: **

**First (and only) line:**




