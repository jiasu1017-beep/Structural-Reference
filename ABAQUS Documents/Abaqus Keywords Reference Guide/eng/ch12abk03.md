# *LOADING DATA







### *LOADING DATAProvide loading data for uniaxial behavior models in connectors or provide data from a uniaxial or a shear loading test for fabric materials.

This option is used to define the loading response data for the uniaxial behavior of connector elements when used in conjunction with the [*CONNECTOR BEHAVIOR](ch03abk35.md) and [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md) options. 

This option is used to define the loading response from a uniaxial or a shear test for fabric materials when used in conjunction with the [*FABRIC](ch06abk01.md) and [*UNIAXIAL](ch20abk03.md) options. A fabric uniaxial test is specified with increasing strains along the specified yarn direction. A fabric shear test is specified with increasing shear strains as the fill and the warp yarns rotate with respect to each other.

If necessary, a separate unloading response can be specified using the [*UNLOADING DATA](ch20abk05.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Connector uniaxial behavior," Section 31.2.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnuniaxialbehav)
- ["Fabric material behavior," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md)
- [*FABRIC](ch06abk01.md)
- [*UNIAXIAL](ch20abk03.md)
- [*UNLOADING DATA](ch20abk05.md)

### Defining the loading response data for uniaxial behavior in connectors

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the data, in addition to temperature. If this parameter is omitted, it is assumed that the data depend only on temperature.   The DEPENDENCIES parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option. 

DIRECTION

Set DIRECTION=TENSION to define tensile behavior.

Set DIRECTION=COMPRESSION to define compressive behavior.

If this parameter is omitted, the behavior is assumed to be nonlinear elastic and the data may span both positive and negative values of the primary component. The behavior will be considered to be symmetric about the origin if the given data are limited to either positive or negative values of the primary component.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT to use constant extrapolation of the dependent variables outside the specified range of the independent variables. 

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

The default is EXTRAPOLATION=CONSTANT unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used.   The EXTRAPOLATION parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option. 

INDEPENDENT COMPONENTS

Set INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION to specify dependencies on components of constitutive relative motion included in the uniaxial behavior definition. The INDEPENDENT COMPONENTS parameter should not be used if uniaxial behavior is dependent on only the component of constitutive relative motion specified with the COMPONENT parameter on the [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md) option. The INDEPENDENT COMPONENTS parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.

REGULARIZE

Set REGULARIZE=ON to regularize the user-defined tabular loading data. 

Set REGULARIZE=OFF to use the user-defined tabular loading data directly without regularization. 

The default is REGULARIZE=ON unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used. The REGULARIZE parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.

RTOL

Set this parameter equal to the tolerance to be used to regularize the user-defined tabular loading data. If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

This parameter is ignored if REGULARIZE=OFF.

The RTOL parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.

TYPE

Set TYPE=DAMAGE to define a damage elasticity model. TYPE=DAMAGE must be used in conjunction with the DIRECTION parameter.

Set TYPE=ELASTIC (default) to define a nonlinear elastic model with or without rate dependency.

Set TYPE=PERMANENT DEFORMATION to define models that exhibit permanent deformation (plasticity) upon unloading. TYPE=PERMANENT DEFORMATION must be used in conjunction with the DIRECTION parameter.

Rate-independent elastic models do not require the definition of unloading data. Nonelastic models and rate-dependent models require the specification of unloading behavior using the [*UNLOADING DATA](ch20abk05.md) option.

### **The following parameters are optional and can be used only with TYPE=ELASTIC: **

RATE DEPENDENT

Include this parameter equal to define rate-dependent loading data. If this parameter is omitted, the data are assumed to be rate independent.

RATE INTERPOLATION

Set RATE INTERPOLATION=LINEAR (default) to use linear intervals for the relative motion rate while interpolating rate-dependent loading data.

Set RATE INTERPOLATION=LOGARITHMIC to use logarithmic intervals for the equivalent relative motion rate while interpolating rate-dependent loading data. 

This parameter is ignored if the RATE DEPENDENT parameter is omitted.

### **The following parameter is optional and can be used only with TYPE=DAMAGE: **

DAMAGE ONSET

Set this parameter equal to the displacement/strain value at which the onset of damage occurs. 

### **The following parameters are optional, mutually exclusive, and can be used only with TYPE=PERMANENT DEFORMATION: **

SLOPE DROP

Set this parameter equal to the relative drop in slope on the loading curve that defines the onset of plastic deformation. The default value is 0.1. 

YIELD ONSET

Set this parameter equal to the displacement/strain value at which the onset of yield occurs. 

### ** Data lines to define uniaxial behavior that depends on the displacement/rotation in the direction of the specified component of relative motion (the RATE DEPENDENT and INDEPENDENT COMPONENTS parameters are omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the loading curve data.

### **Data lines to define uniaxial behavior that depends on the relative positions or motions in several component directions (the RATE DEPENDENT parameter is omitted and the INDEPENDENT COMPONENTS parameter is included): **

**First line:**

**Subsequent lines:**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the loading curve data.

### **Data lines to define rate-dependent uniaxial behavior in the direction of the specified component of relative motion (the RATE DEPENDENT parameter is included and the INDEPENDENT COMPONENTS parameter is omitted): **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the loading curve data.

### **Data lines to define rate-dependent uniaxial behavior that depends on the relative motions in several component directions (the RATE DEPENDENT and INDEPENDENT COMPONENTS parameters are included): **

**First line:**

**Second line:**

**Subsequent lines:**

Do not repeat the first and second data lines. Repeat the subsequent data lines as often as necessary to define the loading curve data.

### Defining the loading response data from uniaxial tests of fabric materials

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the data, in addition to temperature. If this parameter is omitted, it is assumed that the data depend only on temperature.  The DEPENDENCIES parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option. 

DIRECTION

Set DIRECTION=TENSION for tests with the primary strain component positive.

Set DIRECTION=COMPRESSION for tests with the primary strain component negative.

If this parameter is omitted, the behavior is assumed to be nonlinear elastic and the data may span both positive and negative values of the primary strain component. The behavior will be considered to be symmetric about the origin if the given data are limited to either positive or negative values of the primary strain component.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT to use constant extrapolation of the dependent variables outside the specified range of the independent variables. 

Set EXTRAPOLATION=LINEAR (default) to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

 The EXTRAPOLATION parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.  

REGULARIZE

Set REGULARIZE=ON (default) to regularize the user-defined tabular loading data. 

Set REGULARIZE=OFF to use the user-defined tabular loading data directly without regularization. 

 The REGULARIZE parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.

RTOL

Set this parameter equal to the tolerance to be used to regularize the user-defined tabular loading data. If this parameter is omitted, the default is RTOL=0.03.

This parameter is ignored if REGULARIZE=OFF.

The RTOL parameter also applies to any subsequent unloading data defined using the [*UNLOADING DATA](ch20abk05.md) option.

TYPE

Set TYPE=DAMAGE to define a damage elasticity model. TYPE=DAMAGE must be used in conjunction with the DIRECTION parameter.

Set TYPE=ELASTIC (default) to define a nonlinear elastic model with or without rate dependency.

Set TYPE=PERMANENT DEFORMATION to define models that exhibit permanent deformation (plasticity) upon unloading. TYPE=PERMANENT DEFORMATION must be used in conjunction with the DIRECTION parameter.

Rate-independent elastic models do not require the definition of unloading data. Nonelastic models and rate-dependent models require the specification of unloading test data using the [*UNLOADING DATA](ch20abk05.md) option.

### **The following parameters are optional and can be used only with TYPE=ELASTIC: **

RATE DEPENDENT

Include this parameter equal to define rate-dependent loading data. If this parameter is omitted, the data are assumed to be rate independent.

RATE INTERPOLATION

Set RATE INTERPOLATION=LINEAR (default) to use linear intervals for strain rate while interpolating rate-dependent loading data.

Set RATE INTERPOLATION=LOGARITHMIC to use logarithmic intervals for strain rate while interpolating rate-dependent loading data. 

This parameter is ignored if the RATE DEPENDENT parameter is omitted.

### **The following parameter is optional and can be used only with TYPE=DAMAGE: **

DAMAGE ONSET

Set this parameter equal to the displacement/strain value at which the onset of damage occurs. 

### **The following parameters are optional, mutually exclusive, and can be used only with TYPE=PERMANENT DEFORMATION: **

SLOPE DROP

Set this parameter equal to the relative drop in slope on the loading curve that defines the onset of plastic deformation. The default value is 0.1. 

YIELD ONSET

Set this parameter equal to the strain value at which the onset of yield occurs. 

### ** Data lines to define rate-independent fabric response (the RATE DEPENDENT parameter is omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the loading curve data.

### **Data lines to define rate-dependent fabric response (the RATE DEPENDENT parameter is included): **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Do not repeat the first data line. Repeat the second and subsequent data lines as often as necessary to define the loading curve data.




