# 9.17 DisplacementBaseMotionBC object







The DisplacementBaseMotionBC object stores the data for a displacement base motion boundary condition.

The DisplacementBaseMotionBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.17.1 DisplacementBaseMotionBC(...)

This method creates a DisplacementBaseMotionBC object.

**Path**

```
mdb.models[*name*].DisplacementBaseMotionBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*dof*

A SymbolicConstant specifying the constrained degree-of-freedom. Possible values for the SymbolicConstant are U1, U2, U3, UR1, UR2, UR3. The default value is U1.

**Optional arguments**

*amplitudeScaleFactor*

A Float specifying the scale factor for the amplitude curve. The default value is 1.0.

*centerOfRotation*

A [ModelDot](pt01ch07pyo12.md) object specifying a tuple containing one center of rotation.  The default value is the global origin. This argument applies only when *dof*=UR1, UR2, or UR3.

*correlation*

A [CorrelationArray](pt01ch03pyo04.md) object.

*secondaryBase*

A String specifying the name of the [SecondaryBaseBC](pt01ch09pyo39.md) object associated with this boundary condition. The default value is an empty string.

*useComplex*

A Boolean specifying whether to define the imaginary (out-of-plane) portion of the base motion record given by amplitude definition. The default value is OFF.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A DisplacementBaseMotionBC object.

**Exceptions**

None.

### 9.17.2 setValues(...)

This method modifies the data for an existing DisplacementBaseMotionBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DisplacementBaseMotionBC](pt01ch09pyo17.md#ker-displacementbasemotionbc-displacementbasemotionbc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.17.3 setValuesInStep(...)

This method modifies the propagating data for an existing DisplacementBaseMotionBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional argument**

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the boundary condition is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 9.17.4 Members

The DisplacementBaseMotionBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*amplitudeScaleFactor*

A Float specifying the scale factor for the amplitude curve. The default value is 1.0.

*useComplex*

A Boolean specifying whether to define the imaginary (out-of-plane) portion of the base motion record given by amplitude definition. The default value is OFF.

*centerOfRotation*

A [ModelDot](pt01ch07pyo12.md) object specifying a tuple containing one center of rotation.  The default value is the global origin. This argument applies only when *dof*=UR1, UR2, or UR3.

*correlation*

A [CorrelationArray](pt01ch03pyo04.md) object.

*secondaryBase*

A String specifying the name of the [SecondaryBaseBC](pt01ch09pyo39.md) object associated with this boundary condition. The default value is an empty string.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




