# 25.55 PressurePenetrationState object







The PressurePenetrationState object stores the propagating data of a [PressurePenetration](pt01ch25pyo54.md) object in a step. One instance of this object is created internally by the [PressurePenetration](pt01ch25pyo54.md) object for each step. The instance is also deleted internally by the [PressurePenetration](pt01ch25pyo54.md) object.

The PressurePenetrationState object has no constructor or methods.

The PressurePenetrationState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.55.1 Members

The PressurePenetrationState object has the following members:

*penetrationTime*

A Float specifying the fraction of the current step time over which the fluid pressure on newly penetrated contact surface segments is ramped up to the current magnitude. The default value is 10–3.

*penetrationTimeState*

A SymbolicConstant specifying the propagation state of the *penetrationTime* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the *amplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*criticalPressureState*

A SymbolicConstant specifying the propagation state of the *criticalPressure* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*penetrationPressureState*

A SymbolicConstant specifying the propagation state of the *penetrationPressure* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*penetrationPressure*

A tuple of Floats specifying the fluid pressure magnitude. For steady state dynamic analyses, a tuple of Complexes specifying the fluid pressure magnitude.

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the load has no amplitude reference.

*criticalPressure*

A tuple of Floats specifying the critical contact pressure below which fluid penetration starts to occur.

*status*

A SymbolicConstant specifying the propagation state of the [InteractionState](pt01ch25pyo49.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

### 25.55.2 Corresponding analysis keywords

| [*PRESSURE PENETRATION](../key/key-link.md#usb-kws-hpressurepenetration) |
| --- |




