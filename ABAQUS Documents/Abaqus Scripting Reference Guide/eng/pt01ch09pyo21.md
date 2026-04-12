# 9.21 ElectricPotentialBC object







The ElectricPotentialBC object stores the data for an electrical potential boundary condition.

The ElectricPotentialBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.21.1 ElectricPotentialBC(...)

This method creates an ElectricPotentialBC object.

**Path**

```
mdb.models[*name*].ElectricPotentialBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

**Optional arguments**

*fieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*magnitude*

A Float specifying the electrical potential magnitude. The default value is 0. The *magnitude* argument is optional if *distributionType*=USER_DEFINED.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*fixed*

A Boolean specifying whether the boundary condition should remain fixed at the current values at the start of the step. The default value is OFF.

**Return value**

An ElectricPotentialBC object.

**Exceptions**

None.

### 9.21.2 setValues(...)

This method modifies the data for an existing ElectricPotentialBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ElectricPotentialBC](pt01ch09pyo21.md#ker-electricpotentialbc-electricpotentialbc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.21.3 setValuesInStep(...)

This method modifies the propagating data for an existing ElectricPotentialBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*magnitude*

A Float or the SymbolicConstant FREED specifying the electrical potential magnitude.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the boundary condition is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 9.21.4 Members

The ElectricPotentialBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*fieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




