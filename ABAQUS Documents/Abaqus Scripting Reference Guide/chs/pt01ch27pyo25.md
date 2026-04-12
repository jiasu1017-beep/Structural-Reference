# 27.25 ConcentratedPoreFluidState object







The ConcentratedPoreFluidState object stores the propagating data of a concentrated pore fluid flow load in a step. One instance of this object is created internally by the [ConcPoreFluid](pt01ch27pyo26.md) object for each step. The instance is also deleted internally by the [ConcPoreFluid](pt01ch27pyo26.md) object.

The ConcentratedPoreFluidState object has no constructor or methods.

The ConcentratedPoreFluidState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.25.1 Members

The ConcentratedPoreFluidState object has the following members:

*magnitude*

A Float specifying the load magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the load magnitude. Possible values are UNSET, SET, UNCHANGED, and FREED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the *amplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*status*

A SymbolicConstant specifying the propagation state of the [LoadState](pt01ch27pyo42.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the load has no amplitude reference.

### 27.25.2 Corresponding analysis keywords

| [*CLOAD](../key/key-link.md#usb-kws-hcload) (degree of freedom: 8) |
| --- |




