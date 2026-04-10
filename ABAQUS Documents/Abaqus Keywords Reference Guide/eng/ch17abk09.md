# *RATIOS







### *RATIOSDefine anisotropic swelling.

This option is used to specify ratios that define anisotropic swelling. The [*RATIOS](ch17abk09.md) option can be used only in conjunction with the [*MOISTURE SWELLING](ch13abk25.md) option or the [*SWELLING](ch18abk56.md) option, and it should appear immediately after either one.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Moisture swelling," Section 26.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmoistureswell)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- [*MOISTURE SWELLING](ch13abk25.md)
- [*SWELLING](ch18abk56.md)

### **Optional parameter when the [*RATIOS](ch17abk09.md) option is used with the [*SWELLING](ch18abk56.md) option: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the anisotropy ratios in addition to temperature. If this parameter is omitted, it is assumed that the ratios depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define anisotropic swelling ratios: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the anisotropic swelling ratios on temperature and other field variables.




