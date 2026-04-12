# 27.50 PorDragBodyForceState object







The PorDragBodyForceState object stores the propagating data for a Body [PorDragBodyForce](pt01ch27pyo49.md) object in a step. One instance of this object is created internally by the [PorDragBodyForce](pt01ch27pyo49.md) object for each step. The instance is also deleted internally by the [PorDragBodyForce](pt01ch27pyo49.md) object.

The PorDragBodyForceState object has no constructor or methods.

The PorDragBodyForceState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.50.1 Members

The PorDragBodyForceState object has the following members:

*magnitude*

A Float specifying the Pore drag body force magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the Pore drag body force magnitude. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

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

### 27.50.2 Corresponding analysis keywords

| [*DFLUX](../key/key-link.md#usb-kws-hdflux) |
| --- |




