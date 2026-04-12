# 9.27 FluidCavityPressureBC object







The FluidCavityPressureBC object stores the data for a fluid cavity pressure boundary condition.

The FluidCavityPressureBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.27.1 FluidCavityPressureBC(...)

This method creates a FluidCavityPressureBC object.

**Path**

```
mdb.models[*name*].FluidCavityPressureBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*fluidCavity*

A String specifying the name of a Fluid Cavity Interaction.

**Optional arguments**

*magnitude*

A Float specifying the fluid cavity pressure magnitude. The default value is 0.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*fixed*

A Boolean specifying whether the boundary condition should remain fixed at the current values at the start of the step. The default value is OFF.

**Return value**

A FluidCavityPressureBC object.

**Exceptions**

None.

### 9.27.2 setValues(...)

This method modifies the data for an existing FluidCavityPressureBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidCavityPressureBC](pt01ch09pyo27.md#ker-fluidcavitypressurebc-fluidcavitypressurebc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.27.3 setValuesInStep(...)

This method modifies the propagating data for an existing FluidCavityPressureBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*magnitude*

A Float or the SymbolicConstant FREED specifying the fluid cavity pressure magnitude.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the boundary condition is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 9.27.4 Members

The FluidCavityPressureBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*fluidCavity*

A String specifying the name of a Fluid Cavity Interaction.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




