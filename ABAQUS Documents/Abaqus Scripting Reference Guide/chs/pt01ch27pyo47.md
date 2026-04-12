# 27.47 PipePressure object







The PipePressure object stores the data for a pressure applied to pipe or elbow elements.

The PipePressure object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.47.1 PipePressure(...)

This method creates a [Pressure](pt01ch27pyo51.md) object.

**Path**

```
mdb.models[*name*].PipePressure
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the pressure is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float specifying the pressure magnitude. 

**Note:** *magnitude* is optional if *distributionType*=USER_DEFINED.

*diameter*

A Float specifying the effective inner or outer diameter.

*hZero*

A Float specifying the height of the zero pressure level when *distributionType*=HYDROSTATIC.

*hReference*

A Float specifying the height of the reference pressure level when *distributionType*=HYDROSTATIC.

**Optional arguments**

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are UNIFORM, HYDROSTATIC, USER_DEFINED, and FIELD. The default value is UNIFORM.

*side*

A SymbolicConstant specifying whether the pressure is applied internally or externally. Possible values are INTERNAL and EXTERNAL. The default value is INTERNAL.

**Return value**

A PipePressure object.

**Exceptions**

None.

### 27.47.2 setValues(...)

This method modifies the data for an existing PipePressure object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PipePressure](pt01ch27pyo47.md#ker-pipepressure-pipepressure-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.47.3 setValuesInStep(...)

This method modifies the propagating data for an existing PipePressure object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*magnitude*

A Float specifying the pressure magnitude.

*hZero*

A Float specifying the height of the zero pressure level when *distributionType*=HYDROSTATIC.

*hReference*

A Float specifying the height of the reference pressure level when *distributionType*=HYDROSTATIC.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous static analysis step. FREED should be used if the load has no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.47.4 Members

The PipePressure object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are UNIFORM, HYDROSTATIC, USER_DEFINED, and FIELD. The default value is UNIFORM.

*side*

A SymbolicConstant specifying whether the pressure is applied internally or externally. Possible values are INTERNAL and EXTERNAL. The default value is INTERNAL.

*diameter*

A Float specifying the effective inner or outer diameter.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




