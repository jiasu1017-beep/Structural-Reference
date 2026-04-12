# 25.27 CyclicSymmetryState object







The CyclicSymmetryState object stores the propagating data for a [CyclicSymmetry](pt01ch25pyo26.md) object. One instance of this object is created internally by the [CyclicSymmetry](pt01ch25pyo26.md) object for each step. The instance is also deleted internally by the [CyclicSymmetry](pt01ch25pyo26.md) object.

The CyclicSymmetryState object has no constructor or methods.

The CyclicSymmetryState object is derived from the [InteractionState](pt01ch25pyo49.md) object.

**Access**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.27.1 Members

The CyclicSymmetryState object has the following members:

*extractedNodalDiameter*

A SymbolicConstant specifying whether Abaqus should extract all possible nodal diameters or the nodal diameters between the user-specified values for *lowestNodalDiameter* and *highestNodalDiameter*. Possible values are ALL_NODAL_DIAMETER and SPECIFIED_NODAL_DIAMETER. The default value is ALL_NODAL_DIAMETER.

*extractedNodalDiameterState*

A SymbolicConstant specifying the propagation state of the *extractedNodalDiameter* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*lowestNodalDiameter*

An Int specifying the lowest nodal diameter to be used in the eigenfrequency analysis. The default value is 0.

*lowestNodalDiameterState*

A SymbolicConstant specifying the propagation state of the *lowestNodalDiameter* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*highestNodalDiameter*

An Int specifying the highest nodal diameter to be used in the eigenfrequency analysis. This argument value should be less than or equal to the half of the total number of sectors. The default value is 0.

*highestNodalDiameterState*

A SymbolicConstant specifying the propagation state of the *highestNodalDiameter* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*excitiationNodalDiameter*

An Int specifying the nodal diameter for which the modal-based steady-state dynamic analysis will be performed. This value should be greater than or equal to the lowest nodal diameter (specified in the *lowestNodalDiameter* parameter), and less than or equal to the highest nodal diameter (specified in the *highestNodalDiameter* parameter). The default value is 0.

*excitiationNodalDiameterState*

A SymbolicConstant specifying the propagation state of the *excitiationNodalDiameter* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

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

### 25.27.2 Corresponding analysis keywords

| [*CLOAD](../key/key-link.md#usb-kws-hcload), CYCLIC MODE |
| --- |
| [*DLOAD](../key/key-link.md#usb-kws-hdload), CYCLIC MODE |
| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), CYCLIC MODE |
| [*SELECT CYCLIC SYMMETRY MODES](../key/key-link.md#usb-kws-hselectcycsymmodes) |




