# 25.26 CyclicSymmetry object







The CyclicSymmetry object defines a cyclic symmetry analysis.

The CyclicSymmetry object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.26.1 CyclicSymmetry(...)

This method creates a CyclicSymmetry object.

**Path**

```
mdb.models[*name*].CyclicSymmetry
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the cyclic symmetry interaction should be created.

*master*

A [Region](pt01ch45pyo03.md) object specifying the master surface.

*slave*

A [Region](pt01ch45pyo03.md) object specifying the slave surface.

*repetitiveSectors*

An Int specifying the total number of sectors in the cyclic symmetric model.

*axisPoint1*

A [Region](pt01ch45pyo03.md) object specifying the first point of the axis of symmetry. The region should contain exactly one mesh node, vertex, interesting point, reference point or datum point. In a two-dimensional model *axisPoint1* is the only point used to define the axis of symmetry.

*axisPoint2*

A [Region](pt01ch45pyo03.md) object specifying the second point of the axis of symmetry. The region should contain exactly one mesh node, vertex, interesting point, reference point or datum point. In a two-dimensional model this point is ignored.

**Optional arguments**

*extractedNodalDiameter*

A SymbolicConstant specifying whether Abaqus should extract all possible nodal diameters or the nodal diameters between the user-specified values for *lowestNodalDiameter* and *highestNodalDiameter*. Possible values are ALL_NODAL_DIAMETER and SPECIFIED_NODAL_DIAMETER. The default value is ALL_NODAL_DIAMETER.

*lowestNodalDiameter*

An Int specifying the lowest nodal diameter to be used in the eigenfrequency analysis. The default value is 0.

*highestNodalDiameter*

An Int specifying the highest nodal diameter to be used in the eigenfrequency analysis. This argument value should be less than or equal to the half of the total number of sectors (as specified in the *repetitiveSectors* parameter). The default value is 0.

*excitationNodalDiameter*

An Int specifying the nodal diameter for which the modal-based steady-state dynamic analysis will be performed. This value should be greater than or equal to the lowest nodal diameter (specified in the *lowestNodalDiameter* parameter), and less than or equal to the highest nodal diameter (specified in the *highestNodalDiameter* parameter). The default value is 0.

*adjustTie*

A Boolean specifying whether or not to adjust the slave surface of the cyclic symmetry to tie it to the master surface. The default value is ON.

*positionTolerance*

A Float specifying the position tolerance. The*positionTolerance* argument applies only when *positionToleranceMethod*=SPECIFY_TOLERANCE. The default value is 0.0.

*positionToleranceMethod*

A SymbolicConstant specifying the method used to determine the position tolerance. Possible values are COMPUTED_TOLERANCE and SPECIFY_TOLERANCE. The default value is COMPUTED_TOLERANCE.

**Return value**

A CyclicSymmetry object.

**Exceptions**

None.

### 25.26.2 swapSurfaces()

This method switches the master and slave surfaces of a cyclic symmetry interaction. This command is valid only during the step in which the interaction is created.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.26.3 setValues(...)

This method modifies the data for an existing CyclicSymmetry object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CyclicSymmetry](pt01ch25pyo26.md#ker-cyclicsymmetry-cyclicsymmetry-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.26.4 setValuesInStep(...)

This method modifies the propagating data of an existing CyclicSymmetry object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

*extractedNodalDiameter*

A SymbolicConstant specifying whether Abaqus should extract all possible nodal diameters or the nodal diameters between the user-specified values for *lowestNodalDiameter* and *highestNodalDiameter*. Possible values are ALL_NODAL_DIAMETER and SPECIFIED_NODAL_DIAMETER. The default value is ALL_NODAL_DIAMETER.

*lowestNodalDiameter*

An Int specifying the lowest nodal diameter to be used in the eigenfrequency analysis. The default value is 0.

*highestNodalDiameter*

An Int specifying the highest nodal diameter to be used in the eigenfrequency analysis. This argument value should be less than or equal to the half of the total number of sectors (as specified in the *repetitiveSectors* parameter). The default value is 0.

*excitationNodalDiameter*

An Int specifying the nodal diameter for which the modal-based steady-state dynamic analysis will be performed. This value should be greater than or equal to the lowest nodal diameter (specified in the *lowestNodalDiameter* parameter), and less than or equal to the highest nodal diameter (specified in the *highestNodalDiameter* parameter). The default value is 0.

**Return value**

None

**Exceptions**

None.

### 25.26.5 Members

The CyclicSymmetry object has members with the same names and descriptions as the arguments to the [CyclicSymmetry](pt01ch25pyo26.md#ker-cyclicsymmetry-cyclicsymmetry-pyc) method.

### 25.26.6 Corresponding analysis keywords

| [*CLOAD](../key/key-link.md#usb-kws-hcload), CYCLIC MODE |
| --- |
| [*CYCLIC SYMMETRY MODEL](../key/key-link.md#usb-kws-mcycsymmodel) |
| [*DLOAD](../key/key-link.md#usb-kws-hdload), CYCLIC MODE |
| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), CYCLIC MODE |
| [*SELECT CYCLIC SYMMETRY MODES](../key/key-link.md#usb-kws-hselectcycsymmodes) |
| [*TIE](../key/key-link.md#usb-kws-mtie), CYCLIC SYMMETRY |




