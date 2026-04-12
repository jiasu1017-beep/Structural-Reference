# 28.1 LoadCase object







The LoadCase object is used to define the loads and constraints comprising a particular loading condition and the linear response of a structure subjected to that loading condition.

**Access**

```
import step
mdb.models[*name*].steps[*name*].loadCases[*name*]
```

### 28.1.1 LoadCase(...)

This method creates a load case in a step.

**Path**

```
mdb.models[*name*].steps[*name*].LoadCase
```

**Required argument**

*name*

A String specifying the name of the object.

**Optional arguments**

*boundaryConditions*

A sequence of (String, Float) sequences specifying the name of a BoundaryCondition followed by a nonzero Float scaling factor. The default value is an empty sequence.

*loads*

A sequence of (String, Float) sequences specifying the name of a Load followed by a nonzero Float specifying a scale factor. The default value is an empty sequence.

*includeActiveBaseStateBC*

A Boolean specifying whether to include all active boundary conditions propagated or modified from the base state. The default value is ON.

**Return value**

A LoadCase object.

**Exceptions**

RangeError.

### 28.1.2 resume()

This method resumes the load case that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 28.1.3 suppress()

This method suppresses the load case.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 28.1.4 setValues(...)

This method modifies the LoadCase object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [LoadCase](pt01ch28pyo01.md#ker-loadcase-loadcase-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 28.1.5 Members

The LoadCase object has members with the same names and descriptions as the arguments to the [LoadCase](pt01ch28pyo01.md#ker-loadcase-loadcase-pyc) method.

In addition, the LoadCase object has the following member:

*suppressed*

A Boolean specifying whether the load case is suppressed or not. The default value is OFF.




