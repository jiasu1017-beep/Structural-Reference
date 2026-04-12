# 25.77 SurfaceToSurfaceStdState object







The SurfaceToSurfaceStdState object stores the propagating data for a [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) object. One instance of this object is created internally by the [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) object for each step. The instance is also deleted internally by the [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) object.

The SurfaceToSurfaceStdState object has no constructor or methods.

The SurfaceToSurfaceStdState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.77.1 Members

The SurfaceToSurfaceStdState object has the following members:

*interactionPropertyState*

A SymbolicConstant specifying the propagation state of the *interactionProperty* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*interferenceType*

A SymbolicConstant specifying the interference type. Possible values are NONE, SHRINK_FIT, and UNIFORM.

*interferenceTypeState*

A SymbolicConstant specifying the propagation state of the *interferenceType* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*overclosure*

A Float specifying the allowable overclosure.

*overclosureState*

A SymbolicConstant specifying the propagation state of the *overclosure* member. Possible values are COMPUTED and DIRECTION_COSINE.

*interferenceDirectionType*

A SymbolicConstant specifying the interference direction type. Possible values are COMPUTED and DIRECTION_COSINE.

*interferenceDirectionTypeState*

A SymbolicConstant specifying the propagation state of the *interferenceDirectionType* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*directionState*

A SymbolicConstant specifying the propagation state of the *direction* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the *amplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*contactControlsState*

A SymbolicConstant specifying the propagation state of the *contactControls* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*interactionProperty*

A String specifying the name of the [ContactProperty](pt01ch25pyo21.md) object associated with this interaction.

*amplitude*

A String specifying the name of the Amplitude object that defines the magnitude of the prescribed interference during the step.

*contactControls*

A String specifying the name of the [ContactControl](pt01ch25pyo16.md) object associated with this interaction.

*direction*

A tuple of three Floats specifying the following:
- ![](../graphics/ker_eqn00083.gif)-direction cosine of the interference direction vector.
- ![](../graphics/ker_eqn00084.gif)-direction cosine of the interference direction vector.
- ![](../graphics/ker_eqn00085.gif)-direction cosine of the interference direction vector.

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

### 25.77.2 Corresponding analysis keywords

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |
| [*CONTACT PAIR](../key/key-link.md#usb-kws-hcontactpair) |
| [*CONTACT INTERFERENCE](../key/key-link.md#usb-kws-hcontactinterfer) |




