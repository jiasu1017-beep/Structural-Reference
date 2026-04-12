# 27.59 SubmodelSBState object







The SubmodelSBState object stores the propagating data for a Submodel load in a step. One instance of this object is created internally by the [SubmodelSB](pt01ch27pyo58.md) object for each step. The instance is also deleted internally by the [SubmodelSB](pt01ch27pyo58.md) object.

The SubmodelSBState object has no constructor or methods.

The SubmodelSBState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.59.1 Members

The SubmodelSBState object has the following members:

*globalStepState*

A SymbolicConstant specifying the propagation state of the *globalStep* member. Possible values are SET and UNCHANGED.

*globalIncrement*

An Int specifying the increment number in the global model step at which the solution will be used to specify the values of the driven variables. This argument is applicable only for linear perturbation steps.

*globalIncrementState*

A SymbolicConstant specifying the propagation state of the *globalIncrement* member. Possible values are SET and UNCHANGED.

*globalStep*

A String specifying the step in the global model from which Abaqus reads the values of the variables that will drive the submodel analysis. The String indicates the position of the step in the sequence of analysis steps. For example, *globalStep*='1' indicates the first step.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the *amplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*status*

A SymbolicConstant specifying the propagation state of the [LoadState](pt01ch27pyo42.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the load has no amplitude reference.

### 27.59.2 Corresponding analysis keywords

| [*SUBMODEL](../key/key-link.md#usb-kws-msubmodel) |
| --- |
| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), SUBMODEL |




