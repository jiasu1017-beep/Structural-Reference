# 9.37 PorePressureBCState object







The PorePressureBCState object stores the propagating data for a pore pressure boundary condition in a step. One instance of this object is created internally by the [PorePressureBC](pt01ch09pyo36.md) object for each step. The instance is also deleted internally by the [PorePressureBC](pt01ch09pyo36.md) object.

The PorePressureBCState object has no constructor or methods.

The PorePressureBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.37.1 Members

The PorePressureBCState object has the following members:

*magnitude*

A Float specifying the pore pressure magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the pore pressure magnitude. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

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

### 9.37.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (degree of freedom: 8) |
| --- |




