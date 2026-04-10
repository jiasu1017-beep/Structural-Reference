# *FLUID EXPANSION







### *FLUID EXPANSIONSpecify the thermal expansion coefficient for a hydraulic fluid.

This option is used to define thermal expansion coefficients for the hydraulic fluid model. It can be used only in conjunction with the [*FLUID BEHAVIOR](ch06abk16.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)
- [*FLUID BEHAVIOR](ch06abk16.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the thermal expansion coefficient, in addition to temperature. If this parameter is omitted, it is assumed that the thermal expansion coefficient depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

ZERO

Set this parameter equal to the value of ![](../graphics/key_eqn00714.gif). The default is ZERO=0.

### **Data lines to define the thermal expansion coefficient: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to specify ![](../graphics/key_eqn00080.gif) as a function of ![](../graphics/key_eqn00075.gif) and field variables.




