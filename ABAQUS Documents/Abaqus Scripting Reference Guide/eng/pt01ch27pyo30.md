# 27.30 ConnectorMomentState object







The ConnectorMomentState object stores the propagating data for a connector moment in a step. One instance of this object is created internally by the [ConnectorMoment](pt01ch27pyo29.md) object for each step. The instance is also deleted internally by the [ConnectorMoment](pt01ch27pyo29.md) object.

The ConnectorMomentState object has no constructor or methods.

The ConnectorMomentState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.30.1 Members

The ConnectorMomentState object has the following members:

*m1*

A Float or a Complex specifying the connector moment component in the connector's local 4-direction. Although *m1*, *m2*, and *m3* are optional arguments, at least one of them must be nonzero.

*m2*

A Float or a Complex specifying the connector moment component in the connector's local 5direction.

*m3*

A Float or a Complex specifying the connector moment component in the connector's local 6-direction.

*m1State*

A SymbolicConstant specifying the propagation state of the load component in the connector's local 4-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

*m2State*

A SymbolicConstant specifying the propagation state of the load component in the connector's local 5-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

*m3State*

A SymbolicConstant specifying the propagation state of the load component in the connector's local 6-direction. Possible values are UNSET, SET, UNCHANGED, and FREED.

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

### 27.30.2 Corresponding analysis keywords

| [*CONNECTOR LOAD](../key/key-link.md#usb-kws-hconnectorload) (degree of freedom: 4, 5, or 6) |
| --- |




