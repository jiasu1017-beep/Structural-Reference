# 27.11 BodyHeatFlux object







The BodyHeatFlux object defines body heat flux from a region or into a region.

The BodyHeatFlux object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.11.1 BodyHeatFlux(...)

This method creates a BodyHeatFlux object.

**Path**

```
mdb.models[*name*].BodyHeatFlux
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float specifying the body heat flux magnitude. *magnitude* is optional if *distributionType*=USER_DEFINED.

**Optional arguments**

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*distributionType*

A SymbolicConstant specifying how the body heat flux is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A BodyHeatFlux object.

**Exceptions**

None.

### 27.11.2 setValues(...)

This method modifies the data for an existing BodyHeatFlux object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BodyHeatFlux](pt01ch27pyo11.md#ker-bodyheatflux-bodyheatflux-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.11.3 setValuesInStep(...)

This method modifies the propagating data for an existing BodyHeatFlux object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the body heat flux is modified.

**Optional arguments**

*magnitude*

A Float specifying the body heat flux magnitude.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load has no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.11.4 Members

The BodyHeatFlux object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the body heat flux is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




