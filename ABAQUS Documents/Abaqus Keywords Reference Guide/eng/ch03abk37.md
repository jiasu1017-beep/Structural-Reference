# *CONNECTOR DAMAGE EVOLUTION







### *CONNECTOR DAMAGE EVOLUTIONSpecify connector damage evolution for connector elements.

This option is used to define connector damage evolution for connector elements that have available components of relative motion. It must be used in conjunction with the [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector damage behavior," Section 31.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econndamagebehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE INITIATION](ch03abk38.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **Required parameter: **

TYPE

Set TYPE=MOTION to use either connector constitutive relative motions (displacements/rotations) or plastic relative motions (displacement/rotations) to specify damage evolution.

Set TYPE=ENERGY to use post-damage initiation dissipation energies to specify damage evolution.

### **Optional parameters: **

AFFECTED COMPONENTS

Include this parameter to identify on the data line the components of relative motion that will be damaged.

If this parameter is omitted and the COMPONENT parameter is included on the associated [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option, only the specified component will undergo damage.

If both this parameter and the COMPONENT parameter on the associated [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option are omitted, only the components of relative motion involved in the associated [*CONNECTOR POTENTIAL](ch03abk49.md) definition will undergo damage.

DEGRADATION

Set DEGRADATION=MAXIMUM (default) to indicate that the damage value associated with this option will be first compared to damage values from other damage mechanisms (if defined) and that only the maximum value will be considered for the overall damage.

Set DEGRADATION=MULTIPLICATIVE to indicate that the damage value associated with this option will contribute multiplicatively to the overall damage.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector damage evolution, in addition to temperature. If this parameter is omitted, it is assumed that the connector damage evolution is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector damage data. 

Set REGULARIZE=OFF to use the user-defined tabular connector damage data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector damage data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

SOFTENING

This parameter can be used only in conjunction with TYPE=MOTION.

Set SOFTENING=LINEAR (default) to specify a linear damage evolution law.

Set SOFTENING=EXPONENTIAL to specify an exponential damage evolution law.

Set SOFTENING=TABULAR to specify a damage evolution law in tabular form.

### **Data lines to define the damage evolution for TYPE=MOTION, SOFTENING=LINEAR: **

**First line (needed only if the AFFECTED COMPONENTS parameter is included):**

**Second line if the AFFECTED COMPONENTS parameter is included; otherwise, first line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Do not repeat the data line that specifies the affected components. Repeat the subsequent set of data lines as often as necessary to define connector damage evolution by specifying the connector relative plastic or constitutive motion at ultimate failure as a function of mode-mix ratio, temperature, and other predefined field variables.

### **Data lines to define the damage evolution for TYPE=MOTION, SOFTENING=EXPONENTIAL: **

**First line (needed only if the AFFECTED COMPONENTS parameter is included):**

**Second line if the AFFECTED COMPONENTS parameter is included; otherwise, first line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Do not repeat the data line that specifies the affected components. Repeat the subsequent set of data lines as often as necessary to define connector damage evolution by specifying the connector relative plastic or constitutive motion at ultimate failure and the exponential law parameter as functions of mode-mix ratio, temperature, and other predefined field variables.

### **Data lines to define the damage evolution for TYPE=MOTION, SOFTENING=TABULAR: **

**First line (needed only if the AFFECTED COMPONENTS parameter is included):**

**Second line if the AFFECTED COMPONENTS parameter is included; otherwise, first line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Do not repeat the data line that specifies the affected components. Repeat the subsequent set of data lines as often as necessary to define connector damage evolution as a function of connector relative plastic or constitutive motion, mode-mix ratio, temperature, and other predefined field variables.

### **Data lines to define the damage evolution for TYPE=ENERGY: **

**First line (needed only if the AFFECTED COMPONENTS parameter is included):**

**Second line if the AFFECTED COMPONENTS parameter is included; otherwise, first line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Do not repeat the data line that specifies the affected components. Repeat the subsequent set of data lines as often as necessary to define connector damage evolution by specifying the post-initiation dissipation energy as a function of mode-mix ratio, temperature, and other predefined field variables.




