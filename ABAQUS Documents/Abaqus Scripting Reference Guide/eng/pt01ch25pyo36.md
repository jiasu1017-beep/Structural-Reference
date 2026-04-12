# 25.36 FluidCavityState object







The FluidCavityState object stores the propagating data for an [FluidCavity](pt01ch25pyo34.md) object. One instance of this object is created internally by the [FluidCavity](pt01ch25pyo34.md) object for each step. The instance is also deleted internally by the [FluidCavity](pt01ch25pyo34.md) object.

The FluidCavityState object has no constructor or methods.

The FluidCavityState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.36.1 Members

The FluidCavityState object has the following member:

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




