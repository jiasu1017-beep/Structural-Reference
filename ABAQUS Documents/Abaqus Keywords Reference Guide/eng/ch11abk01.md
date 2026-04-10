# *KAPPA







### *KAPPASpecify the material parameters for mass diffusion driven by gradients of temperature and equivalent pressure stress.

This option is used to introduce temperature- and pressure-driven mass diffusion using the material parameters ![](../graphics/key_eqn00884.gif) and ![](../graphics/key_eqn00885.gif), respectively. It must appear immediately after the [*DIFFUSIVITY](ch04abk23.md) option. For each use of the [*DIFFUSIVITY](ch04abk23.md) option, [*KAPPA](ch11abk01.md) can be used once with TYPE=TEMP and once with TYPE=PRESS. The [*KAPPA](ch11abk01.md), TYPE=TEMP and [*DIFFUSIVITY](ch04abk23.md), LAW=FICK options are mutually exclusive.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Diffusivity," Section 26.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdiffusivity)
- [*DIFFUSIVITY](ch04abk23.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of ![](../graphics/key_eqn00884.gif) or ![](../graphics/key_eqn00885.gif). If this parameter is omitted, ![](../graphics/key_eqn00884.gif) or ![](../graphics/key_eqn00885.gif) is assumed not to depend on any field variables but may still depend on concentration and temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

TYPE

Set TYPE=TEMP (default) to define ![](../graphics/key_eqn00884.gif) (governing mass diffusion caused by temperature gradients). Set TYPE=PRESS to define ![](../graphics/key_eqn00885.gif) (governing mass diffusion caused by gradients of the equivalent pressure stress).

### **Data lines to define the Soret effect factor (TYPE=TEMP): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define ![](../graphics/key_eqn00884.gif) as a function of concentration, temperature, and other predefined field variables.

### **Data lines to define the pressure stress factor (TYPE=PRESS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define ![](../graphics/key_eqn00885.gif) as a function of concentration, temperature, and other predefined field variables.




