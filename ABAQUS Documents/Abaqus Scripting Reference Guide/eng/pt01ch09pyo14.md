# 9.14 ConnDisplacementBCState object







The ConnDisplacementBCState object stores the propagating data for a connector displacement/rotation boundary condition in a step. One instance of this object is created internally by the [ConnDisplacementBC](pt01ch09pyo13.md) object for each step. The instance is also deleted internally by the [ConnDisplacementBC](pt01ch09pyo13.md) object.

The ConnDisplacementBCState object has no constructor or methods.

The ConnDisplacementBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.14.1 Members

The ConnDisplacementBCState object has the following members:

*u1*

A Float or a Complex specifying the displacement component in the connector's local 1-direction.

*u2*

A Float or a Complex specifying the displacement component in the connector's local 2-direction.

*u3*

A Float or a Complex specifying the displacement component in the connector's local 3-direction.

*ur1*

A Float or a Complex specifying the rotational component in the connector's local 4-direction.

*ur2*

A Float or a Complex specifying the rotational component in the connector's local 5-direction.

*ur3*

A Float or a Complex specifying the rotational component in the connector's local 6-direction.

*u1State*

A SymbolicConstant specifying the propagation state of the displacement component in the connector's local 1-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*u2State*

A SymbolicConstant specifying the propagation state of the displacement component in the connector's local 2-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*u3State*

A SymbolicConstant specifying the propagation state of the displacement component in the connector's local 3-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ur1State*

A SymbolicConstant specifying the propagation state of the rotational component in the connector's local 4-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ur2State*

A SymbolicConstant specifying the propagation state of the rotational component in the connector's local 5-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*ur3State*

A SymbolicConstant specifying the propagation state of the rotational component in the connector's local 6-direction. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

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

### 9.14.2 Corresponding analysis keywords

| [*CONNECTOR MOTION](../key/key-link.md#usb-kws-hconnectormotion), TYPE=DISPLACEMENT (degree of freedom: 1, 2, 3, 4, 5, or 6) |
| --- |




