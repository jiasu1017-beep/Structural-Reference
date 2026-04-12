# 9.46 TypeBCState object







The TypeBCState object stores the propagating data for a predefined boundary condition in a step. One instance of this object is created internally by the [TypeBC](pt01ch09pyo45.md) object for each step. The instance is also deleted internally by the [TypeBC](pt01ch09pyo45.md) object.

The TypeBCState object has no constructor or methods.

The TypeBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.46.1 Members

The TypeBCState object has the following members:

*typeName*

A SymbolicConstant specifying the predefined boundary condition type. Possible values are XSYMM, YSYMM, ZSYMM, XASYMM, YASYMM, ZASYMM, PINNED, and ENCASTRE.

*typeNameState*

A SymbolicConstant specifying the propagation state of the predefined boundary condition type. The only possible value is UNCHANGED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the amplitude reference. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*status*

A SymbolicConstant specifying the propagation state of the [BoundaryConditionState](pt01ch09pyo08.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the boundary condition has no amplitude reference.

### 9.46.2 Corresponding analysis keywords

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary), TYPE=XSYMM, YSYMM, ZSYMM, XASYMM, YASYMM, ZASYMM, PINNED, or ENCASTRE |
| --- |




