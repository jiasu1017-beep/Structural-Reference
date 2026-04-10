# *IMPORT CONTROLS







### *IMPORT CONTROLSSpecify tolerances used in importing model and results data.

This option is used to specify the tolerance for error checking on shell normals in Abaqus/Standard or Abaqus/Explicit when the [*IMPORT](ch09abk04.md), UPDATE=YES option is used. If the [*IMPORT CONTROLS](ch09abk05.md) option is used, it must appear after the [*IMPORT](ch09abk04.md) option. 

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Transferring results between Abaqus/Explicit and Abaqus/Standard," Section 9.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexptostd)
- [*IMPORT](ch09abk04.md)

### **Required parameter: **

NORMAL TOL

Set this parameter equal to the tolerance required for the error checking on shell normals. The default value is 0.1.

**There are no data lines associated with this option.**



