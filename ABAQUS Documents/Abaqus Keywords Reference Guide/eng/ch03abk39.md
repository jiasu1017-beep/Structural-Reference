# *CONNECTOR DAMPING







### *CONNECTOR DAMPINGDefine connector damping behavior.

This option is used to define the damping behavior for connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector damping behavior," Section 31.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econndampingbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **Optional parameters: **

COMPONENT

Set this parameter equal to the connector's component of relative motion for which damping behavior is specified. For this component of relative motion the connector will act as a dashpot for TYPE=VISCOUS. Omit this parameter to define coupled behavior.

TYPE

Set this parameter equal to VISCOUS (default) to specify velocity proportional damping.

Set this parameter equal to STRUCTURAL to specify displacement proportional damping. This setting applies to steady-state dynamic direct and subspace projection analyses and to steady-state and transient mode-based analyses that support nondiagonal damping in Abaqus/Standard. If TYPE=STRUCTURAL, only linear damping behavior is permitted.

### **Optional parameters for TYPE=VISCOUS: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector damping data, in addition to temperature. If this parameter is omitted, it is assumed that the connector damping is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

FREQUENCY DEPENDENCE

This parameter is relevant only for coupled linear viscous damping definitions in an Abaqus/Standard analysis. Use this parameter to define viscous damping terms with frequency dependence.

Set FREQUENCY DEPENDENCE=OFF (default) if frequency dependence of the damping terms is not defined.

Set FREQUENCY DEPENDENCE=ON if frequency dependence of the damping terms is defined. 

INDEPENDENT COMPONENTS

This parameter can be used only if the COMPONENT and NONLINEAR parameters are included.

Set INDEPENDENT COMPONENTS=POSITION (default) to specify dependencies on components of relative position included in the damping definition.

Set INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION to specify dependencies on components of constitutive relative motion included in the damping definition.

If damping is dependent on only the relative velocity in the component specified with the COMPONENT parameter, the INDEPENDENT COMPONENTS parameter should not be used.

NONLINEAR

This parameter can be used only if the COMPONENT parameter is included.

Include this parameter to define nonlinear damping behavior. Omit this parameter to define linear damping behavior.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector damping data. 

Set REGULARIZE=OFF to use the user-defined tabular connector damping data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector damping data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

UNSYMM

This parameter is relevant only for linear coupled viscous damping definitions in an Abaqus/Standard analysis. 

Include this parameter if the linear coupled viscous damping matrices are not symmetric. 

### **Data lines to define linear uncoupled viscous damping behavior (TYPE=VISCOUS, COMPONENT with the NONLINEAR parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the damping coefficient as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define linear coupled viscous damping behavior (TYPE=VISCOUS with the COMPONENT, NONLINEAR, and UNSYMM parameters omitted; all 21 damping constants must be specified, regardless of whether temperature or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the connector damping behavior as a function of temperature and other predefined field variables.

### **Data lines to define linear coupled viscous damping behavior with frequency dependence (TYPE=VISCOUS with the COMPONENT, NONLINEAR, and UNSYMM parameters omitted, and FREQUENCY DEPENDENCE=ON; all 21 damping constants must be specified, regardless of whether frequency, temperature, or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the connector damping behavior as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define linear coupled viscous damping behavior using unsymmetric storage (the COMPONENT and NONLINEAR parameters are omitted and UNSYMM is included; all 36 damping constants must be specified, regardless of whether temperature or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Fourth line:**

**Fifth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the unsymmetric connector damping behavior as a function of temperature and other predefined field variables.

### **Data lines to define linear coupled viscous damping behavior using unsymmetric storage and frequency dependence (the COMPONENT and NONLINEAR parameters are omitted, the UNSYMM parameter is included, and FREQUENCY DEPENDENCE=ON; all 36 damping constants must be specified, regardless of whether frequency, temperature, or field variable dependencies are included): **

**First line:**

**Second line:**

**Third line:**

**Fourth line:**

**Fifth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than two):**

Repeat this set of data lines as often as necessary to define the unsymmetric connector damping behavior as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear viscous damping behavior that depends on the velocity in the direction of the specified component of relative motion (TYPE=VISCOUS, COMPONENT, NONLINEAR with the INDEPENDENT COMPONENTS parameter omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the connector damping behavior as a function of temperature and other predefined field variables.

### **Data lines to define linear viscous damping behavior that depends on the relative displacement, positions, or motions in several component directions (TYPE=VISCOUS, COMPONENT, NONLINEAR, INDEPENDENT COMPONENTS): **

**First line:**

**Subsequent lines:**

**Continuation line (if needed):**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the damping behavior as a function of connector relative (angular) velocity, position, or motion; temperature; and other predefined field variables.

### **Data lines to define linear, uncoupled structural damping behavior (TYPE=STRUCTURAL, COMPONENT): **

**First line:**

Repeat this data line as often as necessary to define the damping coefficient as a function of frequency.

### **Data lines to define linear, coupled structural damping behavior (TYPE=STRUCTURAL with the COMPONENT parameter omitted): **

**First line:**

**Second line:**

**Third line:**




