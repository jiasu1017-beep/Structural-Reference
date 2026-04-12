# 27.28 ConnectorForceState object







The ConnectorForceState object stores the propagating data for a connector force in a step. One instance of this object is created internally by the [ConnectorForce](pt01ch27pyo27.md) object for each step. The instance is also deleted internally by the [ConnectorForce](pt01ch27pyo27.md) object.

The ConnectorForceState object has no constructor or methods.

The ConnectorForceState object is derived from the [LoadState](pt01ch27pyo42.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.28.1 Members

The ConnectorForceState object has the following members:

*f1*

A Float or a Complex specifying the connector force component in the connector's local 1-direction.

*f2*

A Float or a Complex specifying the connector force component in the connector's local 2-direction.

*f3*

A Float or a Complex specifying the connector force component in the connector's local 3-direction.

*f1State*

A SymbolicConstant specifying the propagation state of the connector force component in the connector's local 1-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

*f2State*

A SymbolicConstant specifying the propagation state of the connector force component in the connector's local 2-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

*f3State*

A SymbolicConstant specifying the propagation state of the connector force component in the connector's local 3-direction. Possible values are UNSET, SET, UNCHANGED, and MODIFIED.

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

### 27.28.2 Corresponding analysis keywords

| [*CONNECTOR LOAD](../key/key-link.md#usb-kws-hconnectorload) (degree of freedom: 1, 2, or 3) |
| --- |




