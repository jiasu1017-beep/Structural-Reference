# *CAST IRON COMPRESSION HARDENING







### *CAST IRON COMPRESSION HARDENINGSpecify hardening in compression for the gray cast iron plasticity model.

This option is used to specify the compression hardening data for gray cast iron. It must be used in conjunction with the [*CAST IRON PLASTICITY](ch03abk07.md) and [*CAST IRON TENSION HARDENING](ch03abk08.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cast iron plasticity," Section 23.2.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccastironplasticity)
- [*CAST IRON PLASTICITY](ch03abk07.md)
- [*CAST IRON TENSION HARDENING](ch03abk08.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the compressive yield stress, in addition to temperature. If this parameter is omitted, it is assumed that the compressive yield stress depends only on plastic strain and, possibly, on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define compression hardening: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the yield stress on plastic strain and, if needed, on temperature and other predefined field variables.




