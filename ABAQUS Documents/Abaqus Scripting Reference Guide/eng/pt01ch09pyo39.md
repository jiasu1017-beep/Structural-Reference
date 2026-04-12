# 9.39 SecondaryBaseBC object







The SecondaryBaseBC object stores the data for a secondary base boundary condition.

The SecondaryBaseBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.39.1 SecondaryBaseBC(...)

This method creates a SecondaryBaseBC object.

**Path**

```
mdb.models[*name*].SecondaryBaseBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*regions*

A [RegionArray](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.  Note that the usual *region* is ignored. The default value is MODEL.

*dofs*

A sequence of sequences of Ints specifying the constrained degrees-of-freedom.

**Optional arguments**

None.

**Return value**

A SecondaryBaseBC object.

**Exceptions**

None.

### 9.39.2 setValues(...)

This method modifies the data for an existing SecondaryBaseBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SecondaryBaseBC](pt01ch09pyo39.md#ker-secondarybasebc-secondarybasebc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.39.3 setValuesInStep(...)

This method modifies the propagating data for an existing SecondaryBaseBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 9.39.4 Members

The SecondaryBaseBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*dofs*

A tuple of tuples of Ints specifying the constrained degrees-of-freedom.

*regions*

A [RegionArray](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.  Note that the usual *region* is ignored. The default value is MODEL.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




