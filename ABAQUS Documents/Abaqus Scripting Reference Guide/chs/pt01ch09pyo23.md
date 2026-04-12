# 9.23 EulerianBC object







The EulerianBC object stores the data for an Eulerian boundary condition.

The EulerianBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.23.1 EulerianBC(...)

This method creates a EulerianBC object.

**Path**

```
mdb.models[*name*].EulerianBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

**Optional arguments**

*definition*

A SymbolicConstant specifying the flow conditions to be defined. Possible values are INFLOW, OUTFLOW, and BOTH. The default value is INFLOW.

*inflowType*

A SymbolicConstant specifying the control of material flow into the Eulerian domain. Possible values are FREE, NONE, and VOID. The default value is FREE.

*outflowType*

A SymbolicConstant specifying the control of flow of material out of the Eulerian domain. Possible values are ZERO_PRESSURE, FREE, NON_REFLECTING, and EQUILIBRIUM. The default value is ZERO_PRESSURE.

**Return value**

An EulerianBC object.

**Exceptions**

None.

### 9.23.2 setValues(...)

This method modifies the data for an existing EulerianBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*definition*

A SymbolicConstant specifying the material flow conditions to be defined. Possible values are INFLOW, OUTFLOW, and BOTH. The default value is INFLOW.

*inflowType*

A SymbolicConstant specifying the control of material flow into the Eulerian domain. Possible values are FREE, NONE, and VOID. The default value is FREE.

*outflowType*

A SymbolicConstant specifying the control of material flow out of the Eulerian domain. Possible values are ZERO_PRESSURE, FREE, NON_REFLECTING, and EQUILIBRIUM. The default value is ZERO_PRESSURE.

**Return value**

None

**Exceptions**

None.

### 9.23.3 setValuesInStep(...)

This method modifies the propagating data for an existing EulerianBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*definition*

A SymbolicConstant specifying the material flow conditions to be defined. Possible values are INFLOW, OUTFLOW, and BOTH. The default value is INFLOW.

*inflowType*

A SymbolicConstant specifying the control of material flow into the Eulerian domain. Possible values are FREE, NONE, and VOID. The default value is FREE.

*outflowType*

A SymbolicConstant specifying the control of material flow out of the Eulerian domain. Possible values are ZERO_PRESSURE, FREE, NON_REFLECTING, and EQUILIBRIUM. The default value is ZERO_PRESSURE.

**Return value**

None

**Exceptions**

None.

### 9.23.4 Members

The EulerianBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*definition*

A SymbolicConstant specifying the flow conditions to be defined. Possible values are INFLOW, OUTFLOW, and BOTH. The default value is INFLOW.

*inflowType*

A SymbolicConstant specifying the control of material flow into the Eulerian domain. Possible values are FREE, NONE, and VOID. The default value is FREE.

*outflowType*

A SymbolicConstant specifying the control of flow of material out of the Eulerian domain. Possible values are ZERO_PRESSURE, FREE, NON_REFLECTING, and EQUILIBRIUM. The default value is ZERO_PRESSURE.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




