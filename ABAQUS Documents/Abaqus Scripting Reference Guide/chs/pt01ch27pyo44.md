# 27.44 MomentState object







The MomentState object stores the propagating data for a moment in a step. One instance of this object is created internally by the [Moment](pt01ch27pyo43.md) object for each step. The instance is also deleted internally by the [Moment](pt01ch27pyo43.md) object.

The MomentState object has no constructor or methods.

The MomentState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.44.1 Members

The MomentState object has the following members:

*cm1*

A Float or a Complex specifying the load component in the 4-direction.

*cm2*

A Float or a Complex specifying the load component in the 5-direction.

*cm3*

A Float or a Complex specifying the load component in the 6-direction.

*cm1State*

A SymbolicConstant specifying the propagation state of the load component in the 4-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

*cm2State*

A SymbolicConstant specifying the propagation state of the load component in the 5-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

*cm3State*

A SymbolicConstant specifying the propagation state of the load component in the 6-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

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

### 27.44.2 Corresponding analysis keywords

| [*CLOAD](../key/key-link.md#usb-kws-hcload) (degree of freedom: 4, 5, or 6) |
| --- |




