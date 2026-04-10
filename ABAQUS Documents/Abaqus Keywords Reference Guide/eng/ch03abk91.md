# *CYCLIC HARDENING







### *CYCLIC HARDENINGSpecify the size of the elastic range for the combined hardening model.

This option is used to define the evolution of the elastic domain for the nonlinear isotropic/kinematic hardening model. It can be used only in conjunction with the [*PLASTIC](ch16abk14.md) option. The elastic domain remains constant during the analysis if this option is not used.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Models for metals subjected to cyclic loading," Section 23.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chardening)
- [*PLASTIC](ch16abk14.md)
- ["UHARD," Section 1.1.36 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuhard)
- ["VUHARD," Section 1.2.17 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexphard)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the cyclic hardening behavior, in addition to temperature. If this parameter is omitted, this behavior does not depend on field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

PARAMETERS

Include this parameter to provide the material parameters ![](../graphics/key_eqn00542.gif) and *b* directly.

USER

Include this parameter to define the elastic range in user subroutine [`UHARD`](../sub/sub-link.md#sub-xsl-uhard) in Abaqus/Standard analyses and user subroutine [`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard) in Abaqus/Explicit analyses. This parameter cannot be included if the kinematic hardening component is specified via half-cycle test data using DATA TYPE=HALF CYCLE on the associated [*PLASTIC](ch16abk14.md) option.

### **Optional parameter for use with the USER parameter: **

PROPERTIES

Set this parameter equal to the number of property values needed as data in user subroutine [`UHARD`](../sub/sub-link.md#sub-xsl-uhard) in Abaqus/Standard analyses and user subroutine [`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard) in Abaqus/Explicit analyses. The default is PROPERTIES=0.

### **Optional parameter if neither PARAMETERS nor USER is included: **

RATE

Set this parameter equal to the equivalent plastic strain rate, ![](../graphics/key_eqn00543.gif), for which this stress-strain curve applies.

### **Data lines to give tabular material data: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the values of the isotropic component as a function of plastic strain, temperature, and other predefined variables.

### **Data lines to define the material parameters directly (PARAMETERS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the material parameters on temperature and other predefined field variables.

### **Data lines for USER with PROPERTIES: **

**First line:**

Repeat this data line as often as necessary to define all hardening properties.




