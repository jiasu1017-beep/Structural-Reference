# 25.29 ElasticFoundationState object







The ElasticFoundationState object stores the propagating data for an [ElasticFoundation](pt01ch25pyo28.md) object. One instance of this object is created internally by the [ElasticFoundation](pt01ch25pyo28.md) object for each step. The instance is also deleted internally by the [ElasticFoundation](pt01ch25pyo28.md) object.

The ElasticFoundationState object has no constructor or methods.

The ElasticFoundationState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.29.1 Members

The ElasticFoundationState object has the following members:

*stiffness*

A Float specifying the foundation stiffness per area.

*stiffnessState*

A SymbolicConstant specifying the propagation state of the stiffness member. Possible values are UNSET, SET, UNCHANGED, and FREED.

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




