# 27.21 ConcentratedForce object







The ConcentratedForce object defines a concentrated force.

The ConcentratedForce object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.21.1 ConcentratedForce(...)

This method creates a ConcentratedForce object.

**Path**

```
mdb.models[*name*].ConcentratedForce
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

**Optional arguments**

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*cf1*

A Float or a Complex specifying the concentrated force component in the 1-direction. Although *cf1*, *cf2*, and *cf3* are optional arguments, at least one of them must be nonzero.

*cf2*

A Float or a Complex specifying the concentrated force component in the 2-direction.

*cf3*

A Float or a Complex specifying the concentrated force component in the 3-direction.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*follower*

A Boolean specifying whether the direction of the force rotates with the rotation at each node of the region. You should provide the *follower* argument only if it is valid for the specified step. The default value is OFF.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the load's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. When this member is queried, it returns an Int. The default value is `None`.

**Return value**

A ConcentratedForce object.

**Exceptions**

None.

### 27.21.2 setValues(...)

This method modifies the data for an existing ConcentratedForce object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcentratedForce](pt01ch27pyo21.md#ker-concentratedforce-concentratedforce-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.21.3 setValuesInStep(...)

This method modifies the propagating data for an existing ConcentratedForce object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*cf1*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the concentrated force component in the 1-direction. UNCHANGED should be used if the concentrated force component is propagated from the previous analysis step.

*cf2*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the concentrated force component in the 2-direction. UNCHANGED should be used if the concentrated force component is propagated from the previous analysis step.

*cf3*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the concentrated force component in the 3-direction. UNCHANGED should be used if the concentrated force component is propagated from the previous analysis step.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.21.4 Members

The ConcentratedForce object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the load is distributed spatially. Possible values are UNIFORM and FIELD. The default value is UNIFORM.

*follower*

A Boolean specifying whether the direction of the force rotates with the rotation at each node of the region. You should provide the *follower* argument only if it is valid for the specified step. The default value is OFF.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the load's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. When this member is queried, it returns an Int. The default value is `None`.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




