# 9.16 ConnVelocityBCState object







The ConnVelocityBCState object stores the propagating data for a velocity boundary condition in a step. One instance of this object is created internally by the [ConnVelocityBC](pt01ch09pyo15.md) object for each step. The instance is also deleted internally by the [ConnVelocityBC](pt01ch09pyo15.md) object.

The ConnVelocityBCState object has no constructor or methods.

The ConnVelocityBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.16.1 Members

The ConnVelocityBCState object has the following members:

*v1*

A Float specifying the velocity component in the connector's local 1-direction.

*v2*

A Float specifying the velocity component in the connector's local 2-direction.

*v3*

A Float specifying the velocity component in the connector's local 3-direction.

*vr1*

A Float specifying the rotational velocity component in the connector's local 4-direction.

*vr2*

A Float specifying the rotational velocity component in the connector's local 5-direction.

*vr3*

A Float specifying the rotational velocity component in the connector's local 6-direction.

*v1State*

A SymbolicConstant specifying the propagation state of the velocity component in the connector's local 1-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*v2State*

A SymbolicConstant specifying the propagation state of the velocity component in the connector's local 2-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*v3State*

A SymbolicConstant specifying the propagation state of the velocity component in the connector's local 3-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*vr1State*

A SymbolicConstant specifying the propagation state of the rotational velocity component in the connector's local 4–direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*vr2State*

A SymbolicConstant specifying the propagation state of the rotational velocity component in the connector's local 5–direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*vr3State*

A SymbolicConstant specifying the propagation state of the rotational velocity component in the connector's local 6–direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

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

### 9.16.2 Corresponding analysis keywords

| [*CONNECTOR MOTION](../key/key-link.md#usb-kws-hconnectormotion), TYPE=VELOCITY (degree of freedom: 1, 2, 3, 4, 5, or 6) |
| --- |




