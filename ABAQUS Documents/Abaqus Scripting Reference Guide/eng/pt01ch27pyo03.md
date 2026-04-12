# 27.3 BodyChargeState object







The BodyChargeState object stores the propagating data of a body charge in a step. One instance of this object is created internally by the [BodyCharge](pt01ch27pyo02.md) object for each step. The instance is also deleted internally by the [BodyCharge](pt01ch27pyo02.md) object.

The BodyChargeState object has no constructor or methods.

The BodyChargeState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.3.1 Members

The BodyChargeState object has the following members:

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

### 27.3.2 Corresponding analysis keywords

| [*DECHARGE](../key/key-link.md#usb-kws-hdecharge) (load type label: EBF) |
| --- |




