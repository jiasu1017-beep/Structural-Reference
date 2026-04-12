# 25.7 ActuatorSensorState object







The ActuatorSensorState object stores the propagating data of an actuator sensor in a step. One instance of this object is created internally by the [ActuatorSensor](pt01ch25pyo05.md) object for each step. The instance is also deleted internally by the [ActuatorSensor](pt01ch25pyo05.md) object.

The ActuatorSensorState object has no constructor, methods, or members.

The ActuatorSensorState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.7.1 Members

The ActuatorSensorState object has the following member:

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




