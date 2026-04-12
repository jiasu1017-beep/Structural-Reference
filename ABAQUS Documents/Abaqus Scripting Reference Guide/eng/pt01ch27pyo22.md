# 27.22 ConcentratedForceState object







The ConcentratedForceState object stores the propagating data for a concentrated force in a step. One instance of this object is created internally by the [ConcentratedForce](pt01ch27pyo21.md) object for each step. The instance is also deleted internally by the [ConcentratedForce](pt01ch27pyo21.md) object.

The ConcentratedForceState object has no constructor or methods.

The ConcentratedForceState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.22.1 Members

The ConcentratedForceState object has the following members:

*cf1*

A Float or a Complex specifying the concentrated force component in the 1-direction. Although *cf1*, *cf2*, and *cf3* are optional arguments, at least one of them must be nonzero.

*cf2*

A Float or a Complex specifying the concentrated force component in the 2-direction.

*cf3*

A Float or a Complex specifying the concentrated force component in the 3-direction.

*cf1State*

A SymbolicConstant specifying the propagation state of the concentrated force component in the 1-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

*cf2State*

A SymbolicConstant specifying the propagation state of the concentrated force component in the 2-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

*cf3State*

A SymbolicConstant specifying the propagation state of the concentrated force component in the 3-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

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

### 27.22.2 Corresponding analysis keywords

| [*CLOAD](../key/key-link.md#usb-kws-hcload) (degree of freedom: 1, 2, or 3) |
| --- |




