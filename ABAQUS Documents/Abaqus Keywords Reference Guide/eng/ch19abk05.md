# *THERMAL EXPANSION







### *THERMAL EXPANSIONDefine the thermal expansion behavior of beams.

This option can be used only in conjunction with the [*BEAM GENERAL SECTION](ch02abk05.md), SECTION=NONLINEAR GENERAL option.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Using a general beam section to define the section behavior," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- [*BEAM GENERAL SECTION](ch02abk05.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies for the thermal-expansion coefficient, in addition to temperature. If this parameter is omitted, it is assumed that the thermal-expansion coefficient is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the thermal expansion behavior: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the thermal expansion coefficient as a function of temperature and other predefined field variables.




