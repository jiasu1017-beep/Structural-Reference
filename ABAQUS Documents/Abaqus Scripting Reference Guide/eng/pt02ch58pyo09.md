# 58.9 ConnectorOptions object







The ConnectorOptions object is used to define various options for connector behaviors. It can be used only in conjunction with [CDCTerm](pt02ch58pyo02.md), [ConnectorDamage](pt02ch58pyo03.md), [ConnectorDamping](pt02ch58pyo04.md), [ConnectorElasticity](pt02ch58pyo05.md), [ConnectorFriction](pt02ch58pyo07.md), and [ConnectorPlasticity](pt02ch58pyo10.md) objects. Because the [ConnectorDamage](pt02ch58pyo03.md) object contains two separate ConnectorOptions repositories (one for damage initiation and one for damage evolution), there are two ConnectorOptions constructors associated with that behavior—initiationOptions and evolutionOptions. The [ConnectorPlasticity](pt02ch58pyo10.md) object also contains two separate ConnectorOptions repositories (one for isotropic hardening and one for kinematic hardening), so there are two ConnectorOptions constructors associated with that behavior—isotropicOptions and kinematicOptions.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).options()
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.cdcTerms(*i*).options()
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionOptions()
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).options()
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationOptions()
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).options()
sectionApi.sections()[*name*].behaviorOptions(*i*).isotropicOptions()
sectionApi.sections()[*name*].behaviorOptions(*i*).kinematicOptions()
sectionApi.sections()[*name*].behaviorOptions(*i*).options()
```

### 58.9.1 ConnectorOptions(...)

This method creates a connector options object to be used in conjunction with an allowable connector behavior option, derived component term, or connector section.

**Path**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.cdcTerms(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().cdcTerms(*i*).ConnectorOptions
sectionApi.sections()[*name*].behaviorOptions(*i*).ConnectorOptions
```

**Prototype**

```
odb_ConnectorOptions&
ConnectorOptions(bool useBehRegSettings,
                 bool regularize,
                 bool defaultTolerance,
                 double regularization,
                 bool defaultRateFactor,
                 double rateFactor,
                 const odb_String& interpolation,
                 bool useBehExtSettings,
                 const odb_String& extrapolation);
```

**Required arguments**

None.

**Optional arguments**

*useBehRegSettings*

A Boolean specifying whether or not to use the behavior-level settings for regularization options. This argument is applicable only for an Abaqus/Explicit analysis. The default value is true.

*regularize*

A Boolean specifying whether or not the tabular data will be regularized. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=false. The default value is true.

*defaultTolerance*

A Boolean specifying whether or not the analysis default regularization tolerance will be used. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=false and *regularize*=true. The default value is true.

*regularization*

A Double specifying the regularization increment to be used. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=false, *regularize*=true, and *defaultTolerance*=false. The default value is 0.03.

*defaultRateFactor*

A Boolean specifying whether or not the analysis default rate filter factor will be used. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. The default value is true.

*rateFactor*

A Double specifying the rate filter factor to be used. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. This argument is also applicable only if *defaultRateFactor*=false. The default value is 0.9.

*interpolation*

An odb_String specifying the type of interpolation increment to be used on rate-dependent tabular data. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. Possible values are "LINEAR" and "LOGARITHMIC". The default value is "LINEAR".

*useBehExtSettings*

A Boolean specifying whether or not to use the behavior-level settings for extrapolation options. The default value is true.

*extrapolation*

An odb_String specifying the extrapolation technique to be used. This argument is applicable only if *useBehExtSettings*=false. Possible values are "CONSTANT" and "LINEAR". The default value is "CONSTANT".

**Return value**

A ConnectorOptions object.

**Exceptions**

ValueError and TextError.

### 58.9.2 setValues(...)

This method modifies the ConnectorOptions object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorOptions](pt02ch58pyo09.md#ker-connectoroptions-connectoroptions-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.9.3 Members

The ConnectorOptions object has members with the same names and descriptions as the arguments to the [ConnectorOptions](pt02ch58pyo09.md#ker-connectoroptions-connectoroptions-cpp) method.

### 58.9.4 Corresponding analysis keywords

| [*CONNECTOR BEHAVIOR](../key/key-link.md#usb-kws-mconnectorbehavior), [*CONNECTOR DAMAGE INITIATION](../key/key-link.md#usb-kws-mconnectordamageinit), [*CONNECTOR DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mconnectordamageevol), [*CONNECTOR DAMPING](../key/key-link.md#usb-kws-mconnectordamping), [*CONNECTOR DERIVED COMPONENT](../key/key-link.md#usb-kws-mconnectorderivedcomp), [*CONNECTOR ELASTICITY](../key/key-link.md#usb-kws-mconnectorelasticity), [*CONNECTOR FRICTION](../key/key-link.md#usb-kws-mconnectorfriction), and [*CONNECTOR PLASTICITY](../key/key-link.md#usb-kws-mconnectorplasticity) |
| --- |




