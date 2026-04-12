# 27.61 SubstructureLoadState object







The SubstructureLoadState object stores the propagating data for a substructure load in a step. One instance of this object is created internally by the [SubstructureLoad](pt01ch27pyo60.md) object for each step. The instance is also deleted internally by the [SubstructureLoad](pt01ch27pyo60.md) object.

The SubstructureLoadState object has no constructor or methods.

The SubstructureLoadState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.61.1 Members

The SubstructureLoadState object has the following members:

*loadCaseNames*

A tuple of strings specifying the names of the load cases to be activated.

*magnitude*

A Float or a Complex specifying the load magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the load magnitude. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

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

### 27.61.2 Corresponding analysis keywords

| [*SLOAD](../key/key-link.md#usb-kws-hsload) |
| --- |




