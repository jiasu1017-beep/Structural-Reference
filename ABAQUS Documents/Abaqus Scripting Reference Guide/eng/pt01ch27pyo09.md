# 27.9 BodyForce object







The BodyForce object defines a distributed load.

The BodyForce object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.9.1 BodyForce(...)

This method creates a BodyForce object.

**Path**

```
mdb.models[*name*].BodyForce
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

**Optional arguments**

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*comp1*

A Float or a Complex specifying the body force component in the 1-direction.

**Note:**Although *comp1*, *comp2*, and *comp3* are optional arguments, at least one of them must be nonzero unless *distributionType*=USER_DEFINED.

*comp2*

A Float or a Complex specifying the body force component in the 2-direction.

*comp3*

A Float or a Complex specifying the body force component in the 3-direction.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A BodyForce object.

**Exceptions**

None.

### 27.9.2 setValues(...)

This method modifies the data for an existing BodyForce object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BodyForce](pt01ch27pyo09.md#ker-bodyforce-bodyforce-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.9.3 setValuesInStep(...)

This method modifies the propagating data for an existing BodyForce object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*comp1*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the body force component in the 1-direction. UNCHANGED should be used if the body force component is propagated from the previous analysis step.

*comp2*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the body force component in the 2-direction. UNCHANGED should be used if the body force component is propagated from the previous analysis step.

*comp3*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the body force component in the 3-direction. UNCHANGED should be used if the body force component is propagated from the previous analysis step.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.9.4 Members

The BodyForce object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

### 27.9.5 Corresponding analysis keywords

| [*DLOAD](../key/key-link.md#usb-kws-hdload) (load type label: BX, BY, BZ, BR, BXNU, BYNU, BZNU, or BRNU) |
| --- |




