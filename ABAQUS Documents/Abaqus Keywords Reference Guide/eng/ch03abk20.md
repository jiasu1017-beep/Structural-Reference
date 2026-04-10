# *CLAY PLASTICITY







### *CLAY PLASTICITYSpecify the extended Cam-clay plasticity model.

This option is used to specify the plastic part of the material behavior for elastic-plastic materials that use the extended Cam-clay plasticity model.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Critical state (clay) plasticity model," Section 23.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cclayplastic)
- [*CLAY HARDENING](ch03abk19.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies, in addition to temperature, included in the definition of the Cam-clay parameters. If this parameter is omitted, the Cam-clay parameters may depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

HARDENING

Set HARDENING=EXPONENTIAL (default for Abaqus/Standard) to specify an exponential hardening/softening law. This hardening law is not supported in Abaqus/Explicit.

Set HARDENING=TABULAR (default and only option for Abaqus/Explicit) to specify a piecewise linear hardening/softening relationship. The [*CLAY HARDENING](ch03abk19.md) option must be used in this case. HARDENING=TABULAR and the use of the INTERCEPT parameter are mutually exclusive.

INTERCEPT

This parameter applies only to Abaqus/Standard analyses.

It is used as an alternative to the direct specification of the initial yield surface size, ![](../graphics/key_eqn00172.gif), when the exponential hardening law is specified. Set this parameter equal to ![](../graphics/key_eqn00173.gif), the intercept of the virgin consolidation line with the void ratio axis in a plot of void ratio versus the logarithm of pressure stress. If this parameter is included, the value given for ![](../graphics/key_eqn00172.gif) on the data line is ignored. This parameter cannot be used when the HARDENING=TABULAR parameter is used.

### **Data lines to define Cam-clay plasticity: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the dependence of the Cam-clay parameters on temperature and other predefined field variables.




