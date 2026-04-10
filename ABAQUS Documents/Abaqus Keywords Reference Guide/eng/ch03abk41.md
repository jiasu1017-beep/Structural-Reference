# *CONNECTOR ELASTICITY







### *CONNECTOR ELASTICITYDefine connector elastic behavior.

This option is used to define the elastic behavior for connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector elastic behavior," Section 31.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnelastbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **Optional parameters: **

COMPONENT

Set this parameter equal to the connector's component of relative motion for which elastic behavior is specified. For this component of relative motion the connector will act as a spring. Omit this parameter if linear coupled behavior is to be defined.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector elasticity data, in addition to temperature. If this parameter is omitted, it is assumed that the connector elasticity is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

FREQUENCY DEPENDENCE

This parameter is relevant only for coupled linear spring stiffness definitions in an Abaqus/Standard analysis. Use this parameter to define spring stiffness terms with frequency dependence.

Set FREQUENCY DEPENDENCE=OFF (default) if frequency dependence of the spring stiffness terms is not defined.

Set FREQUENCY DEPENDENCE=ON if frequency dependence of the spring stiffness terms is defined. 

INDEPENDENT COMPONENTS

This parameter can be used only if the COMPONENT and NONLINEAR parameters are included.

Set INDEPENDENT COMPONENTS=POSITION (default) to specify dependencies on components of relative position included in the elasticity definition.

Set INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION to specify dependencies on components of constitutive relative motion included in the elasticity definition.

If elasticity is dependent on only the component of constitutive relative motion specified with the COMPONENT parameter (uncoupled behavior), the INDEPENDENT COMPONENTS parameter should not be used.

NONLINEAR

This parameter can be used only if the COMPONENT parameter is included.

Include this parameter to define nonlinear elastic behavior. Omit this parameter to define linear elastic behavior.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector elastic data. 

Set REGULARIZE=OFF to use the user-defined tabular connector elastic data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector elastic data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

RIGID

Include this parameter to indicate that rigid elastic behavior is defined.

UNSYMM

This parameter is relevant only for coupled linear spring stiffness definitions in an Abaqus/Standard analysis. 

Include this parameter if the coupled linear spring stiffness matrices are not symmetric.

### **Data lines to define linear uncoupled elastic behavior (the COMPONENT parameter is included and the NONLINEAR parameter is omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the elastic stiffness as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define linear coupled elastic behavior (the COMPONENT, NONLINEAR, and UNSYMM parameters are omitted; all 21 elasticity constants must be specified, regardless of whether temperature or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the connector elastic behavior as a function of temperature and other predefined field variables

### **Data lines to define linear coupled elastic behavior with frequency dependence (the COMPONENT, NONLINEAR, and UNSYMM parameters are omitted, and FREQUENCY DEPENDENCE=ON; all 21 stiffness constants must be specified, regardless of whether frequency, temperature, or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the connector elastic behavior as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define the linear coupled stiffness matrix using unsymmetric storage (the COMPONENT and NONLINEAR parameters are omitted and the UNSYMM parameter is included; all 36 stiffness constants must be specified, regardless of whether temperature or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Fourth line:**

**Fifth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the unsymmetric connector stiffness behavior as a function of temperature and other predefined field variables.

### **Data lines to define the linear coupled stiffness matrix using unsymmetric storage and frequency dependence (the COMPONENT and NONLINEAR parameters are omitted, the UNSYMM parameter is included, and FREQUENCY DEPENDENCE=ON; all 36 stiffness constants must be specified, regardless of whether frequency, temperature, or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Fourth line:**

**Fifth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the unsymmetric connector stiffness behavior as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear elastic behavior that depends on the displacement/rotation in the direction of the specified component of relative motion (the COMPONENT and NONLINEAR parameters are included and the INDEPENDENT COMPONENTS parameter is omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the connector elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define nonlinear elastic behavior that depends on the relative positions or motions in several component directions (the COMPONENT, NONLINEAR, and INDEPENDENT COMPONENTS parameters are included): **

**First line:**

**Subsequent lines:**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the elastic stiffness as a function of connector relative position or constitutive relative motion, temperature, and other predefined field variables.

### **Data lines to define rigid-like elastic behavior if the COMPONENT parameter is omitted: **

**First line:**

Omit this data line if rigid-like elastic behavior is defined for all available components of relative motion.




