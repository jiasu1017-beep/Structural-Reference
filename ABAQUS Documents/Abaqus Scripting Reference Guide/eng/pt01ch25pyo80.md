# 25.80 XFEMCrackGrowthState object







The XFEMCrackGrowthState object stores the propagating data of an [XFEMCrackGrowth](pt01ch25pyo79.md) object in a step. One instance of this object is created internally by the [XFEMCrackGrowth](pt01ch25pyo79.md) object for each step. The instance is also deleted internally by the [XFEMCrackGrowth](pt01ch25pyo79.md) object.

The XFEMCrackGrowthState object has no constructor or methods.

The XFEMCrackGrowthState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.80.1 Members

The XFEMCrackGrowthState object has the following members:

*allowGrowth*

A Boolean specifying whether the crack is allowed to grow (propagate) during this analysis step. The default value is ON.

*allowGrowthState*

A SymbolicConstant specifying the propagation state of the *allowGrowth* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

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

### 25.80.2 Corresponding analysis keywords

| [*ENRICHMENT ACTIVATION](../key/key-link.md#usb-kws-henrichmentactivation) |
| --- |




