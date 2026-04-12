# 27.13 BoltLoad object







The BoltLoad object defines a bolt load.

The BoltLoad object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.13.1 BoltLoad(...)

This method creates a BoltLoad object.

**Path**

```
mdb.models[*name*].BoltLoad
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created. This must be the first analysis step name.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float specifying the bolt load magnitude.

*datumAxis*

A [DatumAxis](pt01ch15pyo02.md) object specifying the orientation of the pre-tension section normal.

**Note:** *datumAxis* is required only for Solid and Shell regions; it has no meaning for Wire regions.

**Optional arguments**

*boltMethod*

A SymbolicConstant specifying the method of applying the bolt load. Possible values are APPLY_FORCE and ADJUST_LENGTH. The default value is APPLY_FORCE.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A BoltLoad object.

**Exceptions**

TextError.

### 27.13.2 setValues(...)

This method modifies the data for an existing BoltLoad object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BoltLoad](pt01ch27pyo13.md#ker-boltload-boltload-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

### 27.13.3 setValuesInStep(...)

This method modifies the propagating data for an existing BoltLoad object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*boltMethod*

A SymbolicConstant specifying the type of bolt load. Possible values are APPLY_FORCE, ADJUST_LENGTH, and FIX_LENGTH. The default is APPLY_FORCE.

*magnitude*

A Float specifying the bolt load magnitude.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.13.4 Members

The BoltLoad object can have the following members:

*name*

A String specifying the load repository key.

*datumAxis*

A [DatumAxis](pt01ch15pyo02.md) object specifying the orientation of the pre-tension section normal.

**Note:** *datumAxis* is required only for Solid and Shell regions; it has no meaning for Wire regions.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

### 27.13.5 Corresponding analysis keywords

| [*PRE-TENSION SECTION](../key/key-link.md#usb-kws-mpretension) |
| --- |
| [*NODE](../key/key-link.md#usb-kws-mnode) (for the reference node) |
| [*NSET](../key/key-link.md#usb-kws-mnset) (for the reference node) |




