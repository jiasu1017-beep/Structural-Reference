# 27.32 CoriolisForceState object







The CoriolisForceState object stores the propagating data of a coriolis force in a step. One instance of this object is created internally by the [CoriolisForce](pt01ch27pyo31.md) object for each step. The instance is also deleted internally by the [CoriolisForce](pt01ch27pyo31.md) object.

The CoriolisForceState object has no constructor or methods.

The CoriolisForceState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.32.1 Members

The CoriolisForceState object has the following members:

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

### 27.32.2 Corresponding analysis keywords

| [*DLOAD](../key/key-link.md#usb-kws-hdload) (load type label: CORIO) |
| --- |




