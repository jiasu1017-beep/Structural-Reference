# 25.63 SelfContactStdState object







The SelfContactStdState object stores the propagating data for a [SelfContactStd](pt01ch25pyo62.md) object. One instance of this object is created internally by the [SelfContactStd](pt01ch25pyo62.md) object for each step. The instance is also deleted internally by the [SelfContactStd](pt01ch25pyo62.md) object.

The SelfContactStdState object has no constructor or methods.

The SelfContactStdState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.63.1 Members

The SelfContactStdState object has the following members:

*interactionPropertyState*

A SymbolicConstant specifying the propagation state of the *interactionProperty* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*contactControlsState*

A SymbolicConstant specifying the propagation state of the *contactControls* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*interactionProperty*

A String specifying the [ContactProperty](pt01ch25pyo21.md) object associated with this interaction.

*contactControls*

A String specifying the name of the [ContactControl](pt01ch25pyo16.md) object associated with this interaction.

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

### 25.63.2 Corresponding analysis keywords

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |
| [*CONTACT PAIR](../key/key-link.md#usb-kws-hcontactpair) |
| [*MODEL CHANGE](../key/key-link.md#usb-kws-hmodelchange), TYPE=CONTACT PAIR |




