# 9.44 TemperatureBCState object







The TemperatureBCState object stores the propagating data for a temperature boundary condition in a step. One instance of this object is created internally by the [TemperatureBC](pt01ch09pyo43.md) object for each step. The instance is also deleted internally by the [TemperatureBC](pt01ch09pyo43.md) object.

The TemperatureBCState object has no constructor or methods.

The TemperatureBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.44.1 Members

The TemperatureBCState object has the following members:

*magnitude*

A Float specifying the temperature magnitude.

*magnitudeState*

A SymbolicConstant specifying the propagation state of the temperature magnitude. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*dofState*

A SymbolicConstant specifying the propagation state of the *dof* member. Possible values are SET and UNCHANGED.

*dof*

A tuple of Ints specifying the degrees of freedom to which the boundary condition is applied.

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

### 9.44.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (degree of freedom: 11 for solids; 11, 12, etc. for shells) |
| --- |




