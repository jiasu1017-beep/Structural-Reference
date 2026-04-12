# 27.53 ReferencePressure object







The ReferencePressure object stores the data for a fluid reference pressure load.

The ReferencePressure object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.53.1 ReferencePressure(...)

This method creates a ReferencePressure object.

**Path**

```
mdb.models[*name*].ReferencePressure
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A Region specifying the point at which the reference pressure value is applied.

*magnitude*

A Float specifying the reference pressure value.

**Optional arguments**

None.

**Return value**

A ReferencePressure object.

**Exceptions**

None.

### 27.53.2 setValues(...)

This method modifies the data for an existing ReferencePressure object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ReferencePressure](pt01ch27pyo53.md#ker-referencepressure-referencepressure-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.53.3 setValuesInStep(...)

This method modifies the propagating data for an existing ReferencePressure object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional argument**

*magnitude*

A Float specifying the reference pressure value.

**Return value**

None

**Exceptions**

None.

### 27.53.4 Members

The ReferencePressure object can have the following members:

*name*

A String specifying the load repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




