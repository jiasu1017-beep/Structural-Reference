# 9.22 ElectricPotentialBCState object







The ElectricPotentialBCState object stores the propagating data for a electrical potential boundary condition in a step. One instance of this object is created internally by the [ElectricPotentialBC](pt01ch09pyo21.md) object for each step. The instance is also deleted internally by the [ElectricPotentialBC](pt01ch09pyo21.md) object.

The ElectricPotentialBCState object has no constructor or methods.

The ElectricPotentialBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.22.1 Members

The ElectricPotentialBCState object has the following members:

*magnitude*

A Float specifying the electrical potential magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the electrical potential magnitude. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

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

### 9.22.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (degree of freedom: 9) |
| --- |




