# *CONNECTOR FRICTION







### *CONNECTOR FRICTIONDefine friction forces and moments in connector elements.

This option is used to define friction forces and moments in connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector friction behavior," Section 31.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnfrictionbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DERIVED COMPONENT](ch03abk40.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)
- [*FRICTION](ch06abk36.md)

### **Optional parameters: **

PREDEFINED

Include this parameter to specify predefined friction behavior (if available for the connection type). Abaqus defines the contact forces and the magnitude of the tangential tractions automatically, as illustrated in ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary). 

STICK STIFFNESS

Set this parameter equal to the stick stiffness associated with frictional behavior. If this parameter is omitted, a default value (which usually is appropriate) is chosen.

### **Optional parameters used to specify user-defined friction (mutually exclusive with the PREDEFINED parameter): **

COMPONENT

Set this parameter equal to the connector's component of relative motion for which user-defined frictional behavior is specified.

Omit this parameter and use the [*CONNECTOR POTENTIAL](ch03abk49.md) option in conjunction with the [*CONNECTOR FRICTION](ch03abk43.md) option to specify coupled user-defined frictional behavior.

CONTACT FORCE

Set this parameter equal to the name of the associated [*CONNECTOR DERIVED COMPONENT](ch03abk40.md) option or the number of the connector component of relative motion that defines the friction-generating contact force.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector friction data, in addition to temperature. If this parameter is omitted, it is assumed that the friction forces and moments or the contact normal force contributions are independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

INDEPENDENT COMPONENTS

Set INDEPENDENT COMPONENTS=POSITION (default) to specify dependencies on components of relative position included in the frictional behavior definition.

Set INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION to specify dependencies on components of constitutive relative motion included in the frictional behavior definition.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector friction data. 

Set REGULARIZE=OFF to use the user-defined tabular connector friction data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector friction data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

### **Data line to define the parameters (geometric constants and internal contact forces) for predefined frictional behavior (the PREDEFINED parameter is included): **

**First (and only) line:**

No data line is required for connection type SLIPRING.

### **Data lines to define the internal contact forces for user-defined friction that does not depend on the relative positions or motions in one or more component directions (both the PREDEFINED and INDEPENDENT COMPONENTS parameters are omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the internal contact force as a function of accumulated slip, temperature, and field variables. Omit these data lines if internal contact forces do not need to be specified.

### **Data lines to define the internal contact forces for user-defined friction that depends on the relative positions or motions in one or more component directions (the PREDEFINED parameter is omitted and the INDEPENDENT COMPONENTS parameter is included): **

**First line:**

**Subsequent lines:**

**Continuation line (if needed):**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the internal contact force as a function of connector relative position or constitutive relative motion, accumulated slip, temperature, and other predefined field variables.




