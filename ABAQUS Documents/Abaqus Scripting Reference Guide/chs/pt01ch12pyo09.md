# 12.9 ConnectorOptions object







The ConnectorOptions object is used to define various options for connector behaviors. It can be used only in conjunction with [CDCTerm](pt01ch12pyo02.md), [ConnectorDamage](pt01ch12pyo03.md), [ConnectorDamping](pt01ch12pyo04.md), [ConnectorElasticity](pt01ch12pyo05.md), [ConnectorFriction](pt01ch12pyo07.md), and [ConnectorPlasticity](pt01ch12pyo10.md) objects. Because the [ConnectorDamage](pt01ch12pyo03.md) object contains two separate ConnectorOptions repositories (one for damage initiation and one for damage evolution), there are two ConnectorOptions constructors associated with that behavior—initiationOptions and evolutionOptions. The [ConnectorPlasticity](pt01ch12pyo10.md) object also contains two separate ConnectorOptions repositories (one for isotropic hardening and one for kinematic hardening), so there are two ConnectorOptions constructors associated with that behavior—isotropicOptions and kinematicOptions.

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*].options
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*].options
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].evolutionOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*].options
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].initiationOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*].options
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].isotropicOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].kinematicOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].options
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*].options
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*].options
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].evolutionOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*].options
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].initiationOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*].options
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].isotropicOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].kinematicOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].options
```

### 12.9.1 ConnectorOptions(...)

This method creates a connector options object to be used in conjunction with an allowable connector behavior option, derived component term, or connector section.

**Path**

```
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*].ConnectorOptions
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].ConnectorOptions
```

**Required arguments**

None.

**Optional arguments**

*useBehRegSettings*

A Boolean specifying whether or not to use the behavior-level settings for regularization options. This argument is applicable only for an Abaqus/Explicit analysis. The default value is ON.

*regularize*

A Boolean specifying whether or not the tabular data will be regularized. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=OFF. The default value is ON.

*defaultTolerance*

A Boolean specifying whether or not the analysis default regularization tolerance will be used. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=OFF and *regularize*=ON. The default value is ON.

*regularization*

A Float specifying the regularization increment to be used. This argument is applicable only for an Abaqus/Explicit analysis and only if *useBehRegSettings*=OFF, *regularize*=ON, and *defaultTolerance*=OFF. The default value is 0.03.

*defaultRateFactor*

A Boolean specifying whether or not the analysis default rate filter factor will be used. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. The default value is ON.

*rateFactor*

A Float specifying the rate filter factor to be used. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. This argument is also applicable only if *defaultRateFactor*=OFF. The default value is 0.9.

*interpolation*

A SymbolicConstant specifying the type of interpolation increment to be used on rate-dependent tabular data. This argument is applicable only for an Abaqus/Explicit analysis that includes isotropic hardening with tabular definition or damage initiation with plastic motion criteria. Possible values are LINEAR and LOGARITHMIC. The default value is LINEAR.

*useBehExtSettings*

A Boolean specifying whether or not to use the behavior-level settings for extrapolation options. The default value is ON.

*extrapolation*

A SymbolicConstant specifying the extrapolation technique to be used. This argument is applicable only if *useBehExtSettings*=OFF. Possible values are CONSTANT and LINEAR. The default value is CONSTANT.

**Return value**

A ConnectorOptions object.

**Exceptions**

ValueError and TextError.

### 12.9.2 setValues(...)

This method modifies the ConnectorOptions object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorOptions](pt01ch12pyo09.md#ker-connectoroptions-connectoroptions-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.9.3 Members

The ConnectorOptions object has members with the same names and descriptions as the arguments to the [ConnectorOptions](pt01ch12pyo09.md#ker-connectoroptions-connectoroptions-pyc) method.

### 12.9.4 Corresponding analysis keywords

| [*CONNECTOR BEHAVIOR](../key/key-link.md#usb-kws-mconnectorbehavior), [*CONNECTOR DAMAGE INITIATION](../key/key-link.md#usb-kws-mconnectordamageinit), [*CONNECTOR DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mconnectordamageevol), [*CONNECTOR DAMPING](../key/key-link.md#usb-kws-mconnectordamping), [*CONNECTOR DERIVED COMPONENT](../key/key-link.md#usb-kws-mconnectorderivedcomp), [*CONNECTOR ELASTICITY](../key/key-link.md#usb-kws-mconnectorelasticity), [*CONNECTOR FRICTION](../key/key-link.md#usb-kws-mconnectorfriction), and [*CONNECTOR PLASTICITY](../key/key-link.md#usb-kws-mconnectorplasticity) |
| --- |




