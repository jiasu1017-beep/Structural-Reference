# *EMISSIVITY







### *EMISSIVITYSpecify surface emissivity.

This option is used to define the emissivity of a surface in a cavity radiation problem. It must appear immediately after the [*SURFACE PROPERTY](ch18abk52.md) option and must be used in conjunction with the [*PHYSICAL CONSTANTS](ch16abk09.md) option, which is used to define the Stefan-Boltzmann constant.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- [*SURFACE PROPERTY](ch18abk52.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of emissivity. If this parameter is omitted, the emissivity is assumed not to depend on any field variables (but may still depend on temperature). See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the emissivity of a surface: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the emissivity as a function of temperature and user-defined field variables.




