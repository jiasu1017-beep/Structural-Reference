# 25.4 AcousticImpedanceState object







The AcousticImpedanceState object stores the propagating data of an [AcousticImpedance](pt01ch25pyo02.md) object in a step. One instance of this object is created internally by the [AcousticImpedance](pt01ch25pyo02.md) object for each step. The instance is also deleted internally by the [AcousticImpedance](pt01ch25pyo02.md) object.

The AcousticImpedanceState object has no constructor or methods.

The AcousticImpedanceState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.4.1 Members

The AcousticImpedanceState object has the following members:

*interactionPropertyState*

A SymbolicConstant specifying the propagation state of the *interactionProperty* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*interactionProperty*

A String specifying the name of the [AcousticImpedanceProp](pt01ch25pyo03.md) object associated with this interaction.

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

### 25.4.2 Corresponding analysis keywords

| [*SIMPEDANCE](../key/key-link.md#usb-kws-hsimpedance) |
| --- |




