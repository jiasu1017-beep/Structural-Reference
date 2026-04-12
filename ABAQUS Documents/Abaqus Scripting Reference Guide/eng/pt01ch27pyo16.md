# 27.16 ConcConcFlux object







The ConcConcFlux object stores the data for a concentrated concentration flux.

The ConcConcFlux object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.16.1 ConcConcFlux(...)

This method creates a ConcConcFlux object.

**Path**

```
mdb.models[*name*].ConcConcFlux
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created. This must be the first analysis step name.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float specifying the load magnitude.

**Optional arguments**

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A ConcConcFlux object.

**Exceptions**

None.

### 27.16.2 setValues(...)

This method modifies the data for an existing ConcConcFlux object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcConcFlux](pt01ch27pyo16.md#ker-concconcflux-concconcflux-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.16.3 setValuesInStep(...)

This method modifies the propagating data for an existing ConcConcFlux object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*magnitude*

A Float specifying the load magnitude.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous static analysis step. FREED should be used if the load is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.16.4 Members

The ConcConcFlux object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




