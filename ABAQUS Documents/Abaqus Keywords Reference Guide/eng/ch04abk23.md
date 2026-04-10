# *DIFFUSIVITY







### *DIFFUSIVITYSpecify mass diffusivity.

This option is used to define the mass diffusivity of a material diffusing through a base material. It must be used in conjunction with the [*SOLUBILITY](ch18abk23.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Diffusivity," Section 26.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdiffusivity)
- [*SOLUBILITY](ch18abk23.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of diffusivity. If this parameter is omitted, the diffusivity is assumed not to depend on any field variables but may still depend on concentration and temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

LAW

Set LAW=GENERAL (default) to choose general mass diffusion behavior. Set LAW=FICK to choose Fick's diffusion law. LAW=FICK and the [*KAPPA](ch11abk01.md), TYPE=TEMP option are mutually exclusive.

TYPE

Set TYPE=ISO (default) to define isotropic diffusivity. Set TYPE=ORTHO to define orthotropic diffusivity. Set TYPE=ANISO to define fully anisotropic diffusivity.

### **Data lines to define isotropic diffusivity (TYPE=ISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the diffusivity as a function of concentration, temperature, and other predefined field variables.

### **Data lines to define orthotropic diffusivity (TYPE=ORTHO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the diffusivity as a function of concentration, temperature, and other predefined field variables.

### **Data lines to define anisotropic diffusivity (TYPE=ANISO): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter is used):**

Repeat this set of data lines as often as necessary to define the diffusivity as a function of concentration, temperature, and other predefined field variables.




