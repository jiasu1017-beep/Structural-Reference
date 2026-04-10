# *ANNEAL TEMPERATURE







### *ANNEAL TEMPERATURESpecify material properties for modeling annealing or melting.

This option is used to define the annealing temperature of elastic-plastic materials. It must be used in conjunction with the [*PLASTIC](ch16abk14.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Annealing or melting," Section 23.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cannealmelt)
- [*PLASTIC](ch16abk14.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the annealing temperature. If this parameter is omitted, it is assumed that the annealing temperature is a constant. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the annealing temperature: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than seven):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameter ![](../graphics/key_eqn00076.gif) on field variables.




