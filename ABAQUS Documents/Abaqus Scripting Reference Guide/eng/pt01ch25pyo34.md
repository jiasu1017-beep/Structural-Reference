# 25.34 FluidCavity object







The FluidCavity object defines a surface-based cavity.

The FluidCavity object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.34.1 FluidCavity(...)

This method creates an FluidCavity object.

**Path**

```
mdb.models[*name*].FluidCavity
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the FluidCavity object is created.

*cavityPoint*

A [Region](pt01ch45pyo03.md) object specifying the fluid cavity reference point.

*cavitySurface*

A [Region](pt01ch45pyo03.md) object specifying the surface forming the boundary of the fluid cavity.

*interactionProperty*

A String specifying the [FluidCavityProperty](pt01ch25pyo35.md) object associated with this interaction.

**Optional arguments**

*ambientPressure*

A Float specifying the magnitude of the ambient pressure. The default value is 0.0.

*thickness*

A Float specifying the out-of-plane thickness of the surface for two-dimensional models. This argument is valid only when using two-dimensional models. The default value is 1.0.

*useAdiabatic*

A Boolean specifying whether adiabatic behavior is assumed for the ideal gas. This argument is valid only when *interactionProperty* specifies a pneumatic definition. The default value is OFF.

*checkNormals*

A Boolean specifying whether the analysis will check the consistency of the surface normals. The default value is ON.

**Return value**

A FluidCavity object.

**Exceptions**

None.

### 25.34.2 setValues(...)

This method modifies the FluidCavity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidCavity](pt01ch25pyo34.md#ker-fluidcavity-fluidcavity-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.34.3 Members

The FluidCavity object has members with the same names and descriptions as the arguments to the [FluidCavity](pt01ch25pyo34.md#ker-fluidcavity-fluidcavity-pyc) method.

### 25.34.4 Corresponding analysis keywords

| [*FLUID CAVITY](../key/key-link.md#usb-kws-mfluidcavity) |
| --- |




