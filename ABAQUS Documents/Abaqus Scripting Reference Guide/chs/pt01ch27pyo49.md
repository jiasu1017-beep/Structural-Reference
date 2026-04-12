# 27.49 PorDragBodyForce object







The PorDragBodyForce object stores the data for a fluid pore drag body force load.

The PorDragBodyForce object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.49.1 PorDragBodyForce(...)

This method creates a PorDragBodyForce object.

**Path**

```
mdb.models[*name*].PorDragBodyForce
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A Region specifying the point at which the pore drag body force value is applied.

*fieldName*

A String specifying                       The name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD.                     The default value is an empty string.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*magnitude*

A Float specifying the pore drag body force value.

**Optional arguments**

None.

**Return value**

A PorDragBodyForce object.

**Exceptions**

None.

### 27.49.2 setValues(...)

This method modifies the data for an existing PorDragBodyForce object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PorDragBodyForce](pt01ch27pyo49.md#ker-pordragbodyforce-pordragbodyforce-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.49.3 setValuesInStep(...)

This method modifies the propagating data for an existing PorDragBodyForce object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional argument**

*magnitude*

A Float specifying the pore drag body force value.

**Return value**

None

**Exceptions**

None.

### 27.49.4 Members

The PorDragBodyForce object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*fieldName*

A String specifying                       The name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD.                     The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




