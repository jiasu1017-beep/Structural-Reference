# 9.1 BoundaryCondition object







The BoundaryCondition object is the abstract base type for other BoundaryCondition objects. The BoundaryCondition object has no explicit constructor. The methods and members of the BoundaryCondition object are common to all objects derived from the BoundaryCondition.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.1.1 deactivate(...)

This method deactivates the boundary condition in the specified step and all subsequent steps.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is deactivated.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 9.1.2 move(...)

This method moves the boundary condition state from one step to a different step.

**Required arguments**

*fromStepName*

A String specifying the name of the step from which the boundary condition state is moved.

*toStepName*

A String specifying the name of the step to which the boundary condition state is moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 9.1.3 reset(...)

This method resets the boundary condition state of the specified step to the state of the previous analysis step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition state is reset.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 9.1.4 resume()

This method resumes the boundary condition that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 9.1.5 suppress()

This method suppresses the boundary condition.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 9.1.6 delete(...)

This method allows you to delete existing boundary conditions.

**Required argument**

*indices*

A sequence of Ints specifying the index of each boundary condition to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 9.1.7 Members

The BoundaryCondition object can have the following members:

*name*

A String specifying the boundary condition repository key.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




