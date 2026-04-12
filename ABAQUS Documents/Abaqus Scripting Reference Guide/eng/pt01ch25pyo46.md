# 25.46 IncidentWaveState object







The IncidentWaveState object stores the propagating data of an [IncidentWave](pt01ch25pyo44.md) object in a step. One instance of this object is created internally by the [IncidentWave](pt01ch25pyo44.md) object for each step. The instance is also deleted internally by the [IncidentWave](pt01ch25pyo44.md) object.

The IncidentWaveState object has no constructor or methods.

The IncidentWaveState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.46.1 Members

The IncidentWaveState object has the following member:

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

### 25.46.2 Corresponding analysis keywords

| [*INCIDENT WAVE INTERACTION](../key/key-link.md#usb-kws-hincidentwaveinteraction) |
| --- |




