# 25.58 RadiationToAmbientState object







The RadiationToAmbientState object stores the propagating data for a [RadiationToAmbient](pt01ch25pyo57.md) object. One instance of this object is created internally by the [RadiationToAmbient](pt01ch25pyo57.md) object for each step. The instance is also deleted internally by the [RadiationToAmbient](pt01ch25pyo57.md) object.

The RadiationToAmbientState object has no constructor or methods.

The RadiationToAmbientState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.58.1 Members

The RadiationToAmbientState object has the following members:

*ambientTemperature*

A Float specifying the ambient temperature.

*ambientTemperatureState*

A SymbolicConstant specifying the propagation state of the *ambientTemperature* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*ambientTemperatureAmpState*

A SymbolicConstant specifying the propagation state of the *ambientTemperatureAmp* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*emissivity*

A Float specifying the emissivity.

*emissivityState*

A SymbolicConstant specifying the propagation state of the *emissivity* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*ambientTemperatureAmp*

A String specifying the name of the Amplitude object that gives the variation of the ambient temperature with time.

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

### 25.58.2 Corresponding analysis keywords

| [*SRADIATE](../key/key-link.md#usb-kws-hsradiate) |
| --- |




