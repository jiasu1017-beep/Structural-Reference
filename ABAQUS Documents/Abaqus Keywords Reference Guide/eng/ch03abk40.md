# *CONNECTOR DERIVED COMPONENT







### *CONNECTOR DERIVED COMPONENTSpecify user-defined components in connector elements.

This option is used as many times as necessary in conjunction with the [*CONNECTOR FRICTION](ch03abk43.md) and [*CONNECTOR POTENTIAL](ch03abk49.md) options to define user-customized components from numbered components.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector functions for coupled behavior," Section 31.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnderivedandpotential)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR FRICTION](ch03abk43.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the derived component.

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector derived component, in addition to temperature. If this parameter is omitted, it is assumed that the connector derived components are independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

INDEPENDENT COMPONENTS

Set INDEPENDENT COMPONENTS=POSITION (default) to specify dependencies on components of relative position included in the derived component definition.

Set INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION to specify dependencies on components of constitutive relative motion included in the derived component definition.

OPERATOR

Set OPERATOR=NORM (default) to use a square root of a sum of the squares function of the contributing components.

Set OPERATOR=MACAULEY SUM to sum the contributing components with a Macauley bracket function applied to each contribution.

Set OPERATOR=SUM to sum the contributing components directly.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector derived component data. 

Set REGULARIZE=OFF to use the user-defined tabular connector derived component data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector derived component data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

SIGN

Set SIGN=POSITIVE (default) to provide an overall positive sign to the derived component definition.

Set SIGN=NEGATIVE to provide an overall negative sign to the derived component definition.

### **Data lines to define the derived component if the INDEPENDENT COMPONENTS parameter is omitted: **

**First line:**

**Subsequent lines:**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the contributions to the derived component as a function of temperature and field variables.

### **Data lines to define the derived component if the INDEPENDENT COMPONENTS parameter is included: **

**First line:**

**Second line:**

**Third line:**

**Continuation line (if needed):**

Do not repeat the first two data lines. Repeat the subsequent data lines as often as necessary to define the contributions to the derived component as a function of connector relative position or constitutive relative motion, temperature, and field variables.




