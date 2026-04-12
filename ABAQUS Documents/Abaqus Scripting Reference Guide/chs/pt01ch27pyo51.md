# 27.51 Pressure object







The Pressure object defines a pressure load.

The Pressure object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.51.1 Pressure(...)

This method creates a Pressure object.

**Path**

```
mdb.models[*name*].Pressure
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the pressure is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float or a Complex specifying the pressure magnitude.                            

**Note:** *magnitude* is optional if *distributionType*=USER_DEFINED.

*hZero*

A Float specifying the height of the zero pressure level when *distributionType*=HYDROSTATIC.

*hReference*

A Float specifying the height of the reference pressure level when                                  *distributionType*=HYDROSTATIC.                            

**Optional arguments**

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD. The default value is an empty string.

*refPoint*

A Region specifying the reference point from which the relative velocity is determined when *distributionType*=STAGNATION or VISCOUS.

*distributionType*

A SymbolicConstant specifying how the pressure is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, HYDROSTATIC, STAGNATION, VISCOUS, TOTAL_FORCE, and DISCRETE_FIELD. The default value is UNIFORM.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A Pressure object.

**Exceptions**

None.

### 27.51.2 setValues(...)

This method modifies the data for an existing Pressure object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Pressure](pt01ch27pyo51.md#ker-pressure-pressure-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.51.3 setValuesInStep(...)

This method modifies the propagating data for an existing Pressure object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*magnitude*

A Float or a Complex specifying the pressure magnitude.

*hZero*

A Float specifying the height of the zero pressure level when *distributionType*=HYDROSTATIC.

*hReference*

A Float specifying the height of the reference pressure level when  *distributionType*=HYDROSTATIC.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load has no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.51.4 Members

The Pressure object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the pressure is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, HYDROSTATIC, STAGNATION, VISCOUS, TOTAL_FORCE, and DISCRETE_FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




