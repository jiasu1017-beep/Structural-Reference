# 2.1 AdaptiveMeshConstraint object







The AdaptiveMeshConstraint object is the abstract base type for other Arbitrary Lagrangian Eularian (ALE) style AdaptiveMeshConstraint objects. The AdaptiveMeshConstraint object has no explicit constructor. The methods and members of the AdaptiveMeshConstraint object are common to all objects derived from the AdaptiveMeshConstraint object.

**Access**

```
import step
mdb.models[*name*].adaptiveMeshConstraints[*name*]
```

### 2.1.1 deactivate(...)

This method deactivates the adaptive mesh constraint in the specified step and all subsequent steps.

**Required argument**

*stepName*

A String specifying the name of the step in which the adaptive mesh constraint is deactivated.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 2.1.2 move(...)

This method moves the adaptive mesh constraint state from one step to a different step.

**Required arguments**

*fromStepName*

A String specifying the name of the step from which the adaptive mesh constraint state is moved.

*toStepName*

A String specifying the name of the step to which the adaptive mesh constraint state is moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 2.1.3 reset(...)

This method resets the adaptive mesh constraint state of the specified step to the state of the previous analysis step.

**Required argument**

*stepName*

A String specifying the name of the step in which the adaptive mesh constraint state is reset.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 2.1.4 resume()

This method resumes the adaptive mesh constraint that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 2.1.5 suppress()

This method suppresses the adaptive mesh constraint.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 2.1.6 delete(...)

 This method allows you to delete existing adaptive mesh constraints.

**Required argument**

*indices*

A sequence of Ints specifying the index of each adaptive mesh constraint to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 2.1.7 Members

The AdaptiveMeshConstraint object can have the following members:

*name*

A String specifying the adaptive mesh constraint repository key.

*category*

A SymbolicConstant specifying the category of the adaptive mesh constraint. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the adaptive mesh constraint is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the adaptive mesh constraint's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




