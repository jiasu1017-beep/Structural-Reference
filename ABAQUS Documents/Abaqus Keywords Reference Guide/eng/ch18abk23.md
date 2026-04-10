# *SOLUBILITY







### *SOLUBILITYSpecify solubility.

This option is used to define the solubility for a material diffusing through a base material. It must be used in conjunction with the [*DIFFUSIVITY](ch04abk23.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Solubility," Section 26.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-csolubility)
- [*DIFFUSIVITY](ch04abk23.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the solubility. If this parameter is omitted, it is assumed that the solubility is constant or that it depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define solubility: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the solubility as a function of temperature and other predefined field variables.




