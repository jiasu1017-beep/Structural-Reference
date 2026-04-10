# *CONNECTOR HARDENING







### *CONNECTOR HARDENINGDefine the plasticity initial yield value and hardening behavior in connector elements.

This option is used to specify the initial yield surface size and, optionally, the post-yield hardening behavior in connector available components of relative motion. It must be used in conjunction with the [*CONNECTOR PLASTICITY](ch03abk48.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector plastic behavior," Section 31.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnplastbehav)
- ["Models for metals subjected to cyclic loading," Section 23.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chardening)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR ELASTICITY](ch03abk41.md)
- [*CONNECTOR HARDENING](ch03abk44.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **Optional parameters: **

DEFINITION

Set DEFINITION=EXPONENTIAL LAW to specify the isotropic hardening parameters ![](../graphics/key_eqn00350.gif) and *b* directly. This parameter is valid only for TYPE=ISOTROPIC.

Set DEFINITION=HALF CYCLE (default for TYPE=KINEMATIC) to provide force/moment versus plastic motion data of a first half-cycle. This parameter is valid only for TYPE=KINEMATIC.

Set DEFINITION=PARAMETERS to specify the kinematic hardening parameters *C* and ![](../graphics/key_eqn00029.gif) directly. This parameter is valid only for TYPE=KINEMATIC.

Set DEFINITION=STABILIZED to provide force/moment versus plastic motion data of a stabilized cycle. This parameter is valid only for TYPE=KINEMATIC.

Set DEFINITION=TABULAR (default for TYPE=ISOTROPIC) to provide force/moment versus plastic motion values. Either uniaxial test data or processed data (as explained in ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)) from cyclic experiments can be used. This parameter is valid only for TYPE=ISOTROPIC.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector hardening data, in addition to temperature. If this parameter is omitted, it is assumed that the connector hardening is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

RATE FILTER FACTOR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the factor to be used for filtering the equivalent relative plastic motion rate for the evaluation of rate-dependent connector hardening data. The default value is 0.9.

RATE INTERPOLATION

This parameter applies only to Abaqus/Explicit analyses and is used only to interpolate rate-dependent connector hardening data.

Set RATE INTERPOLATION=LINEAR (default) to use linear intervals for the equivalent relative plastic motion rate while interpolating rate-dependent hardening data.

Set RATE INTERPOLATION=LOGARITHMIC to use logarithmic intervals for the equivalent relative plastic motion rate while interpolating rate-dependent hardening data. 

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector hardening data. 

Set REGULARIZE=OFF to use the user-defined tabular connector hardening data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector hardening data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

TYPE

Set TYPE=ISOTROPIC (default) to specify the initial yield surface size and, optionally, isotropic hardening data.

Set TYPE=KINEMATIC to specify kinematic hardening data.

### **Data lines for TYPE=ISOTROPIC, DEFINITION=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the size of the elastic range as a function of connector equivalent relative plastic motion, equivalent relative plastic motion rate, temperature, and field variables.

### **Data lines for TYPE=ISOTROPIC, DEFINITION=EXPONENTIAL LAW: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the size of the elastic range and the isotropic hardening parameters as functions of temperature and field variables.

### **Data lines for TYPE=KINEMATIC, DEFINITION=HALF CYCLE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define yield forces/moments as a function of connector relative plastic motion, temperature, and field variables.

### **Data lines for TYPE=KINEMATIC, DEFINITION=STABILIZED: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define yield forces/moments as a function of connector relative plastic motion, constitutive motion range, temperature, and field variables.

### **Data lines for TYPE=KINEMATIC, DEFINITION=PARAMETERS: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the yield force/moment at zero relative plastic motion and the kinematic hardening parameters as functions of temperature and field variables.




