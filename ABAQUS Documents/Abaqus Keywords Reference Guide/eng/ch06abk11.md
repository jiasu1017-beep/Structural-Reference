# *FILM PROPERTY







### *FILM PROPERTYDefine a film coefficient as a function of temperature and field variables.

This option is used to define a film coefficient as a function of temperature and field variables for fully coupled thermal-stress analyses. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses. It can be used only in conjunction with the [*FILM](ch06abk10.md), [*CFILM](ch03abk14.md), and [*SFILM](ch18abk08.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- [*FILM](ch06abk10.md)
- [*CFILM](ch03abk14.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this film property. This label is referred to on the data lines of the [*FILM](ch06abk10.md) or [*CFILM](ch03abk14.md) options.

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of the film coefficient. If this parameter is omitted, it is assumed that the film coefficient depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the film coefficient as a function of temperature and field variables: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to create a film property table.




