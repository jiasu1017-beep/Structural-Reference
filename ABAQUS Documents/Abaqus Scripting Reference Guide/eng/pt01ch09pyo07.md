# 9.7 AcousticPressureBCState object







The AcousticPressureBCState object stores the propagating data for an acoustic pressure boundary condition in a step. One instance of this object is created internally by the [AcousticPressureBC](pt01ch09pyo06.md) object for each step. The instance is also deleted internally by the [AcousticPressureBC](pt01ch09pyo06.md) object.

The AcousticPressureBCState object has no constructor or methods.

The AcousticPressureBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.7.1 Members

The AcousticPressureBCState object has the following members:

*magnitude*

A Float specifying the acoustic pressure magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the acoustic pressure magnitude. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the amplitude reference. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*status*

A SymbolicConstant specifying the propagation state of the [BoundaryConditionState](pt01ch09pyo08.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the boundary condition has no amplitude reference.

### 9.7.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (degree of freedom: 8) |
| --- |




