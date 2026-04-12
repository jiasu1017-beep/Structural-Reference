# 25.70 StdXplCosimulationState object







The StdXplCosimulationState object stores the propagating data for a [StdXplCosimulation](pt01ch25pyo69.md) object. One instance of this object is created internally by the [StdXplCosimulation](pt01ch25pyo69.md) object for each step. The instance is also deleted internally by the [StdXplCosimulation](pt01ch25pyo69.md) object.

The StdXplCosimulationState object has no constructor or methods.

The StdXplCosimulationState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.70.1 Members

The StdXplCosimulationState object has the following member:

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

### 25.70.2 Corresponding analysis keywords

| [*CO-SIMULATION](../key/key-link.md#usb-kws-hcosimulation), |
| --- |
| [*CO-SIMULATION REGION](../key/key-link.md#usb-kws-hcosimulationregion), |
| [*CO-SIMULATION CONTROLS](../key/key-link.md#usb-kws-hcosimulationcontrols) |




