# 25.10 CavityRadiationState object







The CavityRadiationState object stores the propagating data for a [CavityRadiation](pt01ch25pyo08.md) object. One instance of this object is created internally by the [CavityRadiation](pt01ch25pyo08.md) object for each step. The instance is also deleted internally by the [CavityRadiation](pt01ch25pyo08.md) object.

The CavityRadiationState object has no constructor or methods.

The CavityRadiationState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.10.1 Members

The CavityRadiationState object has the following members:

*blocking*

A SymbolicConstant specifying the blocking checks to be performed in the viewfactor calculations. Possible values are BLOCKING_ALL, NO_BLOCKING, and PARTIAL_BLOCKING.

*blockingState*

A SymbolicConstant specifying the propagation state of the blocking member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*blockingSurfacesState*

A SymbolicConstant specifying the propagation state of the *blockingSurfaces* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*rangeOfView*

A Float specifying the distance beyond which factors need not be calculated because surfaces are judged to be too far apart to “see” each other (due to blocking by other surfaces).

*rangeOfViewState*

A SymbolicConstant specifying the propagation state of the *rangeOfView* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*surfaceReflection*

A Boolean specifying whether reflection must be included in the cavity radiation calculations. The default value is ON.

*surfaceReflectionState*

A SymbolicConstant specifying the propagation state of the *surfaceReflection* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*viewfactorAccuracyTol*

A Float specifying the acceptable tolerance for the viewfactor calculations.

*viewfactorAccuracyTolState*

A SymbolicConstant specifying the propagation state of the *viewfactorAccuracyTol* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*blockingSurfaces*

A tuple of Strings specifying the surfaces that provide blocking inside the cavity.

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

### 25.10.2 Corresponding analysis keywords

| [*RADIATION VIEWFACTOR](#) |
| --- |




