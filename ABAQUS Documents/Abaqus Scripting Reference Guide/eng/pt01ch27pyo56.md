# 27.56 ShellEdgeLoad object







The ShellEdgeLoad object defines shell edge loads on a region.

The ShellEdgeLoad object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.56.1 ShellEdgeLoad(...)

This method creates a ShellEdgeLoad object.

**Path**

```
mdb.models[*name*].ShellEdgeLoad
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.

*magnitude*

A Float or Complex specifying the load magnitude. *magnitude* is optional if *distributionType*=USER_DEFINED 

**Optional arguments**

*distributionType*

A SymbolicConstant specifying how the shell edge load is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*angle*

A Float specifying an additional rotation of *directionVector* about an axis. The default value is 0.This parameter is available only if *traction* is GENERAL.

*axis*

A SymbolicConstant specifying the axis about which to apply an additional rotation of *directionVector*. Possible values are AXIS_1, AXIS_2, AXIS_3. The default value is AXIS_1.

This parameter is available only if *traction* is GENERAL.

*localCsys*

A [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the load's degrees of freedom. The default value is `None`, indicating that the degrees of freedom are defined in the global coordinate system or by the *userCsys* parameter if defined. This parameter is available only if *traction* is GENERAL. When this member is queried, it returns an Int.

*userCsys*

A String specifying a CSYS defined by a user-subroutine. The default value is `None`, indicating that the degrees of freedom are defined in the global coordinate system or by the *localCsys* parameter if defined. This parameter is available only if *traction* is GENERAL.

*directionVector*

A tuple of two points specifying the direction of the load. Each point is specified as a point region or a tuple of coordinates. If *traction* is SHEAR, then *directionVector* will be projected onto the region surface. This parameter is available only if *traction* is GENERAL.

*follower*

A Boolean specifying whether the direction of the force changes with rotation. The default value is ON. This parameter may be modified only if *traction* is GENERAL. You should provide the *follower* argument only if it is valid for the specified step.

*resultant*

A Boolean specifying whether to maintain a constant resultant force by defining traction per unit undeformed area. If *resultant* is OFF, traction is defined per unit deformed area. The default value is OFF. You should provide the *resultant* argument only if it is valid for the specified step.

*traction*

A SymbolicConstant specifying how to apply surface traction. Possible values are NORMAL, TRANSVERSE, SHEAR, MOMENT and GENERAL. The default value is NORMAL.

**Return value**

A ShellEdgeLoad object.

**Exceptions**

None.

### 27.56.2 setValues(...)

This method modifies the data for an existing ShellEdgeLoad object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ShellEdgeLoad](pt01ch27pyo56.md#ker-shelledgeload-shelledgeload-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.56.3 setValuesInStep(...)

This method modifies the propagating data for an existing ShellEdgeLoad object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the surface pore fluid flow is modified.

**Optional arguments**

*magnitude*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the load magnitude. UNCHANGED should be used if the magnitude is propagated from the previous analysis step.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load has no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.56.4 Members

The ShellEdgeLoad object can have the following members:

*name*

A String specifying the load repository key.

*distributionType*

A SymbolicConstant specifying how the shell edge load is distributed spatially. Possible values are UNIFORM, USER_DEFINED, and FIELD. The default value is UNIFORM.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this load. The *field* argument applies only when *distributionType*=FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




