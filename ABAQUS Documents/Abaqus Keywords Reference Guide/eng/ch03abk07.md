# *CAST IRON PLASTICITY







### *CAST IRON PLASTICITYSpecify plastic material properties for gray cast iron.

This option is used to define the plastic properties for gray cast iron. It must be used in conjunction with the [*CAST IRON COMPRESSION HARDENING](ch03abk06.md) and [*CAST IRON TENSION HARDENING](ch03abk08.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cast iron plasticity," Section 23.2.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccastironplasticity)
- [*CAST IRON COMPRESSION HARDENING](ch03abk06.md)
- [*CAST IRON TENSION HARDENING](ch03abk08.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the material properties, in addition to temperature. If this parameter is omitted, it is assumed that the material properties depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the plastic "Poisson's ratio": **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameter ![](../graphics/key_eqn00164.gif) on temperature and field variables.




