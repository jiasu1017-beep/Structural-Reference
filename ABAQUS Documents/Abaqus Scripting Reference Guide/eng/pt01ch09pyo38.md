# 9.38 RetainedNodalDofsBC object







The RetainedNodalDofsBC object stores the data for a retained nodal dofs boundary condition.

The RetainedNodalDofsBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.38.1 RetainedNodalDofsBC(...)

This method creates a RetainedNodalDofsBC object.

**Path**

```
mdb.models[*name*].RetainedNodalDofsBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

**Optional arguments**

*u1*

A Boolean specifying whether to retain the degree of freedom in the 1-direction. The default value is OFF indicating that the degree of freedom is not retained.

*u2*

A Boolean specifying whether to retain the degree of freedom in the 2-direction. The default value is OFF indicating that the degree of freedom is not retained.

*u3*

A Boolean specifying whether to retain the degree of freedom in the 3-direction. The default value is OFF indicating that the degree of freedom is not retained.

*ur1*

A Boolean specifying whether to retain the rotational degree of freedom about the 1-direction. The default value is OFF indicating that the degree of freedom is not retained.

*ur2*

A Boolean specifying whether to retain the rotational degree of freedom about the 2-direction. The default value is OFF indicating that the degree of freedom is not retained.

*ur3*

A Boolean specifying whether to retain the rotational degree of freedom about the 3-direction. The default value is OFF indicating that the degree of freedom is not retained.

**Return value**

A RetainedNodalDofsBC object.

**Exceptions**

None.

### 9.38.2 setValues(...)

This method modifies the data for an existing RetainedNodalDofsBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [RetainedNodalDofsBC](pt01ch09pyo38.md#ker-retainednodaldofsbc-retainednodaldofsbc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.38.3 setValuesInStep(...)

This method modifies the propagating data for an existing RetainedNodalDofsBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*u1*

A Boolean specifying whether to retain the degree of freedom in the 1-direction.

*u2*

A Boolean specifying whether to retain the degree of freedom in the 2-direction.

*u3*

A Boolean specifying whether to retain the degree of freedom in the 3-direction.

*ur1*

A Boolean specifying whether to retain the rotational degree of freedom about the 1-direction.

*ur2*

A Boolean specifying whether to retain the rotational degree of freedom about the 2-direction.

*ur3*

A Boolean specifying whether to retain the rotational degree of freedom about the 3-direction.

**Return value**

None

**Exceptions**

None.

### 9.38.4 Members

The RetainedNodalDofsBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




