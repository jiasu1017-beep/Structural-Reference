# 9.5 AccelerationBCState object







The AccelerationBCState object stores the propagating data of an acceleration boundary condition in a step. One instance of this object is created internally by the [AccelerationBC](pt01ch09pyo04.md) object for each step. The instance is also deleted internally by the [AccelerationBC](pt01ch09pyo04.md) object.

The AccelerationBCState object has no constructor or methods.

The AccelerationBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.5.1 Members

The AccelerationBCState object has the following members:

*a1*

A Float specifying the acceleration component in the 1-direction.

*a2*

A Float specifying the acceleration component in the 2-direction.

*a3*

A Float specifying the acceleration component in the 3-direction.

*ar1*

A Float specifying the rotational acceleration component about the 1-direction.

*ar2*

A Float specifying the rotational acceleration component about the 2-direction.

*ar3*

A Float specifying the rotational acceleration component about the 3-direction.

*a1State*

A SymbolicConstant specifying the propagation state of the acceleration component in the 1-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*a2State*

A SymbolicConstant specifying the propagation state of the acceleration component in the 2-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*a3State*

A SymbolicConstant specifying the propagation state of the acceleration component in the 3-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ar1State*

A SymbolicConstant specifying the propagation state of the rotational acceleration component about the 1-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ar2State*

A SymbolicConstant specifying the propagation state of the rotational acceleration component about the 2-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ar3State*

A SymbolicConstant specifying the propagation state of the rotational acceleration component about the 3-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

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

### 9.5.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary), TYPE=ACCELERATION (degree of freedom: 1, 2, 3, 4, 5, or 6) |
| --- |




