# 25.33 FilmConditionState object







The FilmConditionState object stores the propagating data for a [FilmCondition](pt01ch25pyo31.md) object. One instance of this object is created internally by the [FilmCondition](pt01ch25pyo31.md) object for each step. The instance is also deleted internally by the [FilmCondition](pt01ch25pyo31.md) object.

The FilmConditionState object has no constructor or methods.

The FilmConditionState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.33.1 Members

The FilmConditionState object has the following members:

*interactionPropertyState*

A SymbolicConstant specifying the propagation state of the *interactionProperty* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*sinkTemperature*

A Float specifying the sink temperature.

*sinkTemperatureState*

A SymbolicConstant specifying the propagation state of the *sinkTemperature* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*sinkAmplitudeState*

A SymbolicConstant specifying the propagation state of the *sinkAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*filmCoeff*

A Float specifying the film coefficient.

*filmCoeffState*

A SymbolicConstant specifying the propagation state of the *filmCoeff* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*filmCoeffAmplitudeState*

A SymbolicConstant specifying the propagation state of the *filmCoeffAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*interactionProperty*

A String specifying the [FilmConditionProp](pt01ch25pyo32.md) object associated with this interaction.

*sinkAmplitude*

A String specifying the name of the Amplitude object that gives the variation of the sink temperature.

*filmCoeffAmplitude*

A String specifying the name of the Amplitude object that gives the variation of the film coefficient.

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

### 25.33.2 Corresponding analysis keywords

| [*SFILM](../key/key-link.md#usb-kws-hsfilm) |
| --- |
| [*FILM](../key/key-link.md#usb-kws-hfilm) |




